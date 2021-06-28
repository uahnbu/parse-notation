# parse-notation
```javascript
function parseNotation(str) {
  const dict = 'akmgtpezy';
  let shift = 0;
  return str
    .split('').reverse().join('')
    .replace(
      /\d+[a-z]/gi,
      (a, i, pad) => (
        shift += (pad = dict.indexOf(a.slice(-1)) * 3 - i - a.length + 1 - shift) - 1,
        a.slice(0, -1) + '0'.repeat(pad)
      )
    )
    .split('').reverse().join('');
}

console.log(parseNotation('1k1'));
console.log(parseNotation('1m1k150'));
console.log(parseNotation('1g27m3k45'));
console.log(parseNotation('88z22e11t66g999'));
console.log(parseNotation('1m150k3'));

> 1001
> 1001150
> 1027003045
> 88022000011066000000999
> 1150003
```
```javascript
function parseNotation(str) {
  const dict = 'akmgtpezy'; 
  let shift = 0;
  return str
    .split('').reverse().join('')
    .replace(
      /\d+[a-z]/gi,
      (a, i, pad) => (
        shift += (pad = dict.indexOf(a.slice(-1)) * 3 - i - a.length + 1 - shift) - 1,
        '0'.repeat(pad) + a.slice(0, -1)
      )
    )
    .split('').reverse().join('');
}

console.log(parseNotation('1k1'));
console.log(parseNotation('1m1k150'));
console.log(parseNotation('1g27m3k45'));
console.log(parseNotation('88z22e11t66g999'));
console.log(parseNotation('1m150k3'));

> 1100
> 1100150
> 1270300450
> 88220110000660999000000
> 1150300
```
