# Finding Wrong Punctuation Before Publishing

This is a collection of Regular Expressions to be used before publishing a document in order to find wrong punctuation. I recommend using them in the order shown here.

> Be careful! Markdown removes trailing spaces in code, so the “replace with” is sometimes not displayed correctly. I use `·` as a symbol for one space in the replace section.

### No Empty Lines
*If you are not writing in Markdown there should be no empty lines in your text. Instead your paragraphs should have some spacing underneith them.*

Search for `\n{2,}`

Replace with `\n`

### No Double Spaces
*Sometimes one accidentally types two spaces instead of one.*

Search for `[ ]{2,}`

Replace with `·`

### No En-Dash instead of a Hyphen
*Within a word there should be a hypen, not an en-dash.*

Search for `([\S])[–]([\S])`

Replace with `$1-$2`

### No Hyphen instead of an En-Dash
*In between two words or two show a range, an en-dash is the right choice, not a hyphen.*

Search for `([ ])[-]([ ])`

Replace with `·–·`

### No three periods instead of an ellipses
*An ellipses is a single character, not three periods.*

Search for `[.]{3}`

Replace with `…`

### Space after Punctuation
*After punctuation there should be a space.*

Search for `[.,!?](?!\d)\w`

Check those by hand, as URLs may be selected as well.

### No multiple Punctuation
*Using multiple punctuation is bad style!!!*

Search for `([.,!?]){2,}`

Replace with `$1`

### No wrong apostrophe
*Replaces a dumb quote within a word with a real apostrophe.*

Search for `([\w])[']`

Replace with `$1’`

### English Quotation Marks
*Replaces single and double dumb quotes with proper English quotation marks.*

Search for `(\s)["„”](\w)`

Replace with `$1“$2`

Search for `(\w)["“„](\s)`

Replace with `$1”$2`

Search for `(\s)['‚’](\w)`

Replace with `$1‘$2`

Search for `(\w)['‘‚](\s)`

Replace with `$1’$2`

#### Find English Double Quotation Marks Within Double Quotation Marks
*Experimental: finds double quotes within other double quotes and replaces them with single quotes.*

Search for `(“[^”]*)(“)` or better `(?<=“[^”]*)(“)` (not supported in JavaScript)

Replace with `$1‘`

Search for `(”)(?=[^“]*”)`

Replace with `’`

### German Quotation Marks
*Replaces single and double dumb quotes with proper German quotation marks.*

Search for `(\s)["”“](\w)`

Replace with `$1„$2`

Search for `(\w)["”„](\s)`

Replace with `$1“$2`

Search for `(\s)['‘’](\w)`

Replace with `$1‚$2`

Search for `(\w)['’‚](\s)`

Replace with `$1‘$2`

#### Find German Double Quotation Marks Within Double Quotation Marks
*Experimental: finds German double quotes within other double quotes and replaces them with German single quotes.*

Search for `(„[^“]*)(„)` or better `(?<=„[^“]*)(„)` (not supported in JavaScript)

Replace with `$1‚`

Search for `(“)(?=[^„]*“)`

Replace with `‘`
