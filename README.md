# comment.js

Fast and Simple API Documentation builder.

Inspired by one of the firsts versions of dr.js by Dmitry Baranovskiy.

At that moment dr.js was not as powerful or flexible enough for me and I made some PRs but there was little people concerned so I decided making this fork with the idea to keep improving it as a different library.
I hope no remorse for taking the awesome and fun syntax for writing the comments :)

## Example comment.js blocks

```js
/*\
 * Name
 [ type ]
 * Description: use # to write raw html which be rendered as is
 # <ul>
 #  <li>list</li>
 # </ul>
 > Arguments
 - arg1 (string) The first argument (make a link to another section of the doc: @itemname2)
 - arg2 (object) The third argument is an object of `key/value` pairs
 o {
 o  key1 (string) The first key/value
 o  key2 (boolean) The second key/value
 o }
 - arg3 (boolean) #optional The second argument is optional and will be display as itemname(arg1, arg2, [arg3])
 = (object) the return value for the function
 > Usage
 | itemname('example', {
 |    key1: 'hello world',
 |    key2: true
 |  });
\*/
```

### Syntax reference

`/*\` Start a comment.js block.

`*` Renders a paragraph.

`[type]` Type of the object, could be one of `method` or `property`.

`#` Renders plain HTML.

`>` Renders a heading.

`-` `param` `(type)` `#optional` Param description see `@section2`. Words between \`backticks` will be rendered inside a \<code> tag.

\`backticks` Use backticks to highlight code inside paragraphs.

`#optional` Adding `#optional` keyword after the param type will indicate an optional parameter.

`@section2` Use `@` like `@section-name` to create a link to a section named `section-name` inside the docs.

Define an object.
```
o {
o   key1 (string) Description for key1
o   key2 (boolean) Description for key2
o }
```

`=` (type) Description for the returned value.

Use the pipe `|` to render code examples inside a `<pre>` tag that will be highlighted with [google prettify](https://code.google.com/p/google-code-prettify/).
```
| function example('example', {
|    key1: 'hello world',
|    key2: true
|  });
```

`\*/` End comment.js block.

## Examples

```javascript
/*\
 * subscribe
 [ method ]
 * Subscribe a handler to a specified channel
 > Arguments
 - channel (string) the channel to subscribe to
 - handler (function) the function to execute when it's channel is published recieving the @publish data
 > Usage
 | var handle = subscribe('some/channel', function (name, lastName) {
 |   console.log(name + ' ' + lastName);
 | });
\*/
var subscribe = function (channel, handler) {
  (channels[channel] = channels[channel] || []).push(handler);
  return [channel, handler];
};
```

## Author
Denis Ciccale ([@tdecs](http://twitter.com/tdecs))

## License
See [LICENSE.txt](https://raw.github.com/dciccale/comment.js/master/LICENSE.txt)
