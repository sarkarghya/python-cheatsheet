Comprehensive Python Cheatsheet
===============================


Contents
--------
**&nbsp;&nbsp;&nbsp;** **1. Collections:** **&nbsp;** **[`List`](#list)**__,__ **[`Dictionary`](#dictionary)**__,__ **[`Set`](#set)**__,__ **[`Tuple`](#tuple)**__,__ **[`Range`](#range)**__,__ **[`Enumerate`](#enumerate)**__,__ **[`Iterator`](#iterator)**__,__ **[`Generator`](#generator)**__.__  
**&nbsp;&nbsp;&nbsp;** **2. Types:** **&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**  **[`Type`](#type)**__,__ **[`String`](#string)**__,__ **[`Regular_Exp`](#regex)**__,__ **[`Format`](#format)**__,__ **[`Numbers`](#numbers-1)**__,__ **[`Combinatorics`](#combinatorics)**__,__ **[`Datetime`](#datetime)**__.__  
**&nbsp;&nbsp;&nbsp;** **3. Syntax:** **&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**  **[`Args`](#arguments)**__,__ **[`Inline`](#inline)**__,__ **[`Closure`](#closure)**__,__ **[`Decorator`](#decorator)**__,__ **[`Class`](#class)**__,__ **[`Duck_Type`](#duck-types)**__,__ **[`Enum`](#enum)**__,__ **[`Exception`](#exceptions)**__.__  
**&nbsp;&nbsp;&nbsp;** **4. System:** **&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**  **[`Exit`](#exit)**__,__ **[`Print`](#print)**__,__ **[`Input`](#input)**__,__ **[`Command_Line_Arguments`](#command-line-arguments)**__,__ **[`Open`](#open)**__,__ **[`Path`](#paths)**__,__ **[`OS_Commands`](#os-commands)**__.__  
**&nbsp;&nbsp;&nbsp;** **5. Data:** **&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**  **[`JSON`](#json)**__,__ **[`Pickle`](#pickle)**__,__ **[`CSV`](#csv)**__,__ **[`SQLite`](#sqlite)**__,__ **[`Bytes`](#bytes)**__,__ **[`Struct`](#struct)**__,__ **[`Array`](#array)**__,__ **[`Memory_View`](#memory-view)**__,__ **[`Deque`](#deque)**__.__  
**&nbsp;&nbsp;&nbsp;** **6. Advanced:** **&nbsp;&nbsp;&nbsp;**  **[`Threading`](#threading)**__,__ **[`Operator`](#operator)**__,__ **[`Introspection`](#introspection)**__,__ **[`Metaprograming`](#metaprogramming)**__,__ **[`Eval`](#eval)**__,__ **[`Coroutines`](#coroutines)**__.__  
**&nbsp;&nbsp;&nbsp;** **7. Libraries:** **&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**  **[`Progress_Bar`](#progress-bar)**__,__ **[`Plot`](#plot)**__,__ **[`Table`](#table)**__,__ **[`Curses`](#curses)**__,__ **[`Logging`](#logging)**__,__ **[`Scraping`](#scraping)**__,__ **[`Web`](#web)**__,__ **[`Profile`](#profiling)**__,__  
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;** **[`NumPy`](#numpy)**__,__ **[`Image`](#image)**__,__ **[`Audio`](#audio)**__,__ **[`Games`](#pygame)**__,__ **[`Data`](#pandas)**__.__


Main
----
```python
if __name__ == '__main__':     # Runs main() if file wasn't imported.
    main()
```


List
----
```python
<list> = <list>[from_inclusive : to_exclusive : ±step_size]
```

```python
<list>.append(<el>)            # Or: <list> += [<el>]
<list>.extend(<collection>)    # Or: <list> += <collection>
```

```python
<list>.sort()
<list>.reverse()
<list> = sorted(<collection>)
<iter> = reversed(<list>)
```

```python
sum_of_elements  = sum(<collection>)
elementwise_sum  = [sum(pair) for pair in zip(list_a, list_b)]
sorted_by_second = sorted(<collection>, key=lambda el: el[1])
sorted_by_both   = sorted(<collection>, key=lambda el: (el[1], el[0]))
flatter_list     = list(itertools.chain.from_iterable(<list>))
product_of_elems = functools.reduce(lambda out, el: out * el, <collection>)
list_of_chars    = list(<str>)
```
* **Module [operator](#operator) provides functions itemgetter() and mul() that offer the same functionality as [lambda](#lambda) expressions above.**

```python
<list>.insert(<int>, <el>)     # Inserts item at index and moves the rest to the right.
<el>  = <list>.pop([<int>])    # Returns and removes item at index or from the end.
<int> = <list>.count(<el>)     # Returns number of occurrences. Also works on strings.
<int> = <list>.index(<el>)     # Returns index of the first occurrence or raises ValueError.
<list>.remove(<el>)            # Removes first occurrence of the item or raises ValueError.
<list>.clear()                 # Removes all items. Also works on dictionary and set.
```


Dictionary
----------
```python
<view> = <dict>.keys()                          # Coll. of keys that reflects changes.
<view> = <dict>.values()                        # Coll. of values that reflects changes.
<view> = <dict>.items()                         # Coll. of key-value tuples that reflects chgs.
```

```python
value  = <dict>.get(key, default=None)          # Returns default if key is missing.
value  = <dict>.setdefault(key, default=None)   # Returns and writes default if key is missing.
<dict> = collections.defaultdict(<type>)        # Creates a dict with default value of type.
<dict> = collections.defaultdict(lambda: 1)     # Creates a dict with default value 1.
```

```python
<dict> = dict(<collection>)                     # Creates a dict from coll. of key-value pairs.
<dict> = dict(zip(keys, values))                # Creates a dict from two collections.
<dict> = dict.fromkeys(keys [, value])          # Creates a dict from collection of keys.
```

```python
<dict>.update(<dict>)                           # Adds items. Replaces ones with matching keys.
value = <dict>.pop(key)                         # Removes item or raises KeyError.
{k for k, v in <dict>.items() if v == value}    # Returns set of keys that point to the value.
{k: v for k, v in <dict>.items() if k in keys}  # Returns a dictionary, filtered by keys.
```

### Counter
```python
>>> from collections import Counter
>>> colors = ['blue', 'blue', 'blue', 'red', 'red']
>>> counter = Counter(colors)
>>> counter['yellow'] += 1
Counter({'blue': 3, 'red': 2, 'yellow': 1})
>>> counter.most_common()[0]
('blue', 3)
```


Set
---
```python
<set> = set()
```

```python
<set>.add(<el>)                                 # Or: <set> |= {<el>}
<set>.update(<collection> [, ...])              # Or: <set> |= <set>
```

```python
<set>  = <set>.union(<coll.>)                   # Or: <set> | <set>
<set>  = <set>.intersection(<coll.>)            # Or: <set> & <set>
<set>  = <set>.difference(<coll.>)              # Or: <set> - <set>
<set>  = <set>.symmetric_difference(<coll.>)    # Or: <set> ^ <set>
<bool> = <set>.issubset(<coll.>)                # Or: <set> <= <set>
<bool> = <set>.issuperset(<coll.>)              # Or: <set> >= <set>
```

```python
<el> = <set>.pop()                              # Raises KeyError if empty.
<set>.remove(<el>)                              # Raises KeyError if missing.
<set>.discard(<el>)                             # Doesn't raise an error.
```

### Frozen Set
* **Is immutable and hashable.**
* **That means it can be used as a key in a dictionary or as an element in a set.**
```python
<frozenset> = frozenset(<collection>)
```


Tuple
-----
**Tuple is an immutable and hashable list.**
```python
<tuple> = ()
<tuple> = (<el>,)                           # Or: <el>,
<tuple> = (<el_1>, <el_2> [, ...])          # Or: <el_1>, <el_2> [, ...]
```

### Named Tuple
**Tuple's subclass with named elements.**

```python
>>> from collections import namedtuple
>>> Point = namedtuple('Point', 'x y')
>>> p = Point(1, y=2)
Point(x=1, y=2)
>>> p[0]
1
>>> p.x
1
>>> getattr(p, 'y')
2
>>> p._fields  # Or: Point._fields
('x', 'y')
```


Range
-----
```python
<range> = range(to_exclusive)
<range> = range(from_inclusive, to_exclusive)
<range> = range(from_inclusive, to_exclusive, ±step_size)
```

```python
from_inclusive = <range>.start
to_exclusive   = <range>.stop
```


Enumerate
---------
```python
for i, el in enumerate(<collection> [, i_start]):
    ...
```


Iterator
--------
```python
<iter> = iter(<collection>)                 # `iter(<iter>)` returns unmodified iterator.
<iter> = iter(<function>, to_exclusive)     # A sequence of return values until 'to_exclusive'.
<el>   = next(<iter> [, default])           # Raises StopIteration or returns 'default' on end.
<list> = list(<iter>)                       # Returns a list of iterator's remaining elements.
```

### Itertools
```python
from itertools import count, repeat, cycle, chain, islice
```

```python
<iter> = count(start=0, step=1)             # Returns updated value endlessly. Accepts floats.
<iter> = repeat(<el> [, times])             # Returns element endlessly or 'times' times.
<iter> = cycle(<collection>)                # Repeats the sequence endlessly.
```

```python
<iter> = chain(<coll_1>, <coll_2> [, ...])  # Empties collections in order.
<iter> = chain.from_iterable(<collection>)  # Empties collections inside a collection in order.
```

```python
<iter> = islice(<coll>, to_exclusive)       # Only returns first 'to_exclusive' elements.
<iter> = islice(<coll>, from_inclusive, …)  # `to_exclusive, step_size`.
```


Generator
---------
* **Any function that contains a yield statement returns a generator.**
* **Generators and iterators are interchangeable.**

```python
def count(start, step):
    while True:
        yield start
        start += step
```

```python
>>> counter = count(10, 2)
>>> next(counter), next(counter), next(counter)
(10, 12, 14)
```


Type
----
* **Everything is an object.**
* **Every object has a type.**
* **Type and class are synonymous.**

```python
<type> = type(<el>)                          # Or: <el>.__class__
<bool> = isinstance(<el>, <type>)            # Or: issubclass(type(<el>), <type>)
```

```python
>>> type('a'), 'a'.__class__, str
(<class 'str'>, <class 'str'>, <class 'str'>)
```

#### Some types do not have built-in names, so they must be imported:
```python
from types import FunctionType, MethodType, LambdaType, GeneratorType
```

### Abstract Base Classes
**Each abstract base class specifies a set of virtual subclasses. These classes are then recognized by isinstance() and issubclass() as subclasses of the ABC, although they are really not. ABC can also manually decide whether or not a specific class is its virtual subclass, usually based on which methods the class has implemented. For instance, Iterable ABC looks for method iter() while Collection ABC looks for methods iter(), contains() and len().**

```python
>>> from collections.abc import Sequence, Collection, Iterable
>>> isinstance([1, 2, 3], Iterable)
True
```

```text
+------------------+------------+------------+------------+
|                  |  Sequence  | Collection |  Iterable  |
+------------------+------------+------------+------------+
| list, range, str |    yes     |    yes     |    yes     |
| dict, set        |            |    yes     |    yes     |
| iter             |            |            |    yes     |
+------------------+------------+------------+------------+
```

```python
>>> from numbers import Integral, Rational, Real, Complex, Number
>>> isinstance(123, Number)
True
```

```text
+--------------------+----------+----------+----------+----------+----------+
|                    | Integral | Rational |   Real   | Complex  |  Number  |
+--------------------+----------+----------+----------+----------+----------+
| int                |   yes    |   yes    |   yes    |   yes    |   yes    |
| fractions.Fraction |          |   yes    |   yes    |   yes    |   yes    |
| float              |          |          |   yes    |   yes    |   yes    |
| complex            |          |          |          |   yes    |   yes    |
| decimal.Decimal    |          |          |          |          |   yes    |
+--------------------+----------+----------+----------+----------+----------+
```


String
------
```python
<str>  = <str>.strip()                       # Strips all whitespace characters from both ends.
<str>  = <str>.strip('<chars>')              # Strips all passed characters from both ends.
```

```python
<list> = <str>.split()                       # Splits on one or more whitespace characters.
<list> = <str>.split(sep=None, maxsplit=-1)  # Splits on 'sep' str at most 'maxsplit' times.
<list> = <str>.splitlines(keepends=False)    # Splits on [\n\r\f\v\x1c\x1d\x1e\x85…] and \r\n.
<str>  = <str>.join(<coll_of_strings>)       # Joins elements using string as a separator.
```

```python
<bool> = <sub_str> in <str>                  # Checks if string contains a substring.
<bool> = <str>.startswith(<sub_str>)         # Pass tuple of strings for multiple options.
<bool> = <str>.endswith(<sub_str>)           # Pass tuple of strings for multiple options.
<int>  = <str>.find(<sub_str>)               # Returns start index of the first match or -1.
<int>  = <str>.index(<sub_str>)              # Same but raises ValueError if missing.
```

```python
<str>  = <str>.replace(old, new [, count])   # Replaces 'old' with 'new' at most 'count' times.
<str>  = <str>.translate(<table>)            # Use `str.maketrans(<dict>)` to generate table.
```

```python
<str>  = chr(<int>)                          # Converts int to Unicode char.
<int>  = ord(<str>)                          # Converts Unicode char to int.
```
* **Also: `'lstrip()'`, `'rstrip()'`.**
* **Also: `'lower()'`, `'upper()'`, `'capitalize()'` and `'title()'`.**

### Property Methods
```text
+---------------+----------+----------+----------+----------+----------+
|               | [ !#$%…] | [a-zA-Z] |  [¼½¾]   |  [²³¹]   |  [0-9]   |
+---------------+----------+----------+----------+----------+----------+
| isprintable() |   yes    |   yes    |   yes    |   yes    |   yes    |
| isalnum()     |          |   yes    |   yes    |   yes    |   yes    |
| isnumeric()   |          |          |   yes    |   yes    |   yes    |
| isdigit()     |          |          |          |   yes    |   yes    |
| isdecimal()   |          |          |          |          |   yes    |
+---------------+----------+----------+----------+----------+----------+
```
* **Also: `'isspace()'` checks for `'[ \t\n\r\f\v…]'`.**


Regex
-----
```python
import re
<str>   = re.sub(<regex>, new, text, count=0)  # Substitutes all occurrences with 'new'.
<list>  = re.findall(<regex>, text)            # Returns all occurrences as strings.
<list>  = re.split(<regex>, text, maxsplit=0)  # Use brackets in regex to include the matches.
<Match> = re.search(<regex>, text)             # Searches for first occurrence of the pattern.
<Match> = re.match(<regex>, text)              # Searches only at the beginning of the text.
<iter>  = re.finditer(<regex>, text)           # Returns all occurrences as match objects.
```

* **Search() and match() return None if they can't find a match.**
* **Argument `'flags=re.IGNORECASE'` can be used with all functions.**
* **Argument `'flags=re.MULTILINE'` makes `'^'` and `'$'` match the start/end of each line.**
* **Argument `'flags=re.DOTALL'` makes dot also accept the `'\n'`.**
* **Use `r'\1'` or `'\\1'` for backreference.**
* **Add `'?'` after an operator to make it non-greedy.**

### Match Object
```python
<str>   = <Match>.group()                      # Returns the whole match. Also group(0).
<str>   = <Match>.group(1)                     # Returns part in the first bracket.
<tuple> = <Match>.groups()                     # Returns all bracketed parts.
<int>   = <Match>.start()                      # Returns start index of the match.
<int>   = <Match>.end()                        # Returns exclusive end index of the match.
```

### Special Sequences
* **By default, decimal characters, alphanumerics and whitespaces from all alphabets are matched unless `'flags=re.ASCII'` argument is used.**
* **As shown below, it restricts special sequence matches to the first 128 characters and prevents `'\s'` from accepting `'[\x1c-\x1f]'`.**
* **Use a capital letter for negation.**
```python
'\d' == '[0-9]'                                # Matches decimal characters.
'\w' == '[a-zA-Z0-9_]'                         # Matches alphanumerics and underscore.
'\s' == '[ \t\n\r\f\v]'                        # Matches whitespaces.
```


Format
------
```python
<str> = f'{<el_1>}, {<el_2>}'
<str> = '{}, {}'.format(<el_1>, <el_2>)
```

### Attributes
```python
>>> from collections import namedtuple
>>> Person = namedtuple('Person', 'name height')
>>> person = Person('Jean-Luc', 187)
>>> f'{person.height}'
'187'
>>> '{p.height}'.format(p=person)
'187'
```

### General Options
```python
{<el>:<10}                                     # '<el>      '
{<el>:^10}                                     # '   <el>   '
{<el>:>10}                                     # '      <el>'
{<el>:.<10}                                    # '<el>......'
{<el>:0}                                       # '<el>'
```
* **Options can be generated dynamically: `f'{<el>:{<str/int>}[…]}'`.**
* **Adding `'!r'` before the colon converts object to string by calling its [repr()](#class) method.**

### Strings
```python
{'abcde':10}                                   # 'abcde     '
{'abcde':10.3}                                 # 'abc       '
{'abcde':.3}                                   # 'abc'
{'abcde'!r:10}                                 # "'abcde'   "
```

### Numbers
```python
{123456:10}                                    # '    123456'
{123456:10,}                                   # '   123,456'
{123456:10_}                                   # '   123_456'
{123456:+10}                                   # '   +123456'
{123456:=+10}                                  # '+   123456'
{123456: }                                     # ' 123456'
{-123456: }                                    # '-123456'
```

### Floats
```python
{1.23456:10.3}                                 # '      1.23'
{1.23456:10.3f}                                # '     1.235'
{1.23456:10.3e}                                # ' 1.235e+00'
{1.23456:10.3%}                                # '  123.456%'
```

#### Comparison of presentation types:
```text
+--------------+----------------+----------------+----------------+----------------+
|              |    {<float>}   |   {<float>:f}  |   {<float>:e}  |   {<float>:%}  |
+--------------+----------------+----------------+----------------+----------------+
|  0.000056789 |   '5.6789e-05' |    '0.000057'  | '5.678900e-05' |    '0.005679%' |
|  0.00056789  |   '0.00056789' |    '0.000568'  | '5.678900e-04' |    '0.056789%' |
|  0.0056789   |   '0.0056789'  |    '0.005679'  | '5.678900e-03' |    '0.567890%' |
|  0.056789    |   '0.056789'   |    '0.056789'  | '5.678900e-02' |    '5.678900%' |
|  0.56789     |   '0.56789'    |    '0.567890'  | '5.678900e-01' |   '56.789000%' |
|  5.6789      |   '5.6789'     |    '5.678900'  | '5.678900e+00' |  '567.890000%' |
| 56.789       |  '56.789'      |   '56.789000'  | '5.678900e+01' | '5678.900000%' |
+--------------+----------------+----------------+----------------+----------------+
```
```text
+--------------+----------------+----------------+----------------+----------------+
|              |  {<float>:.2}  |  {<float>:.2f} |  {<float>:.2e} |  {<float>:.2%} |
+--------------+----------------+----------------+----------------+----------------+
|  0.000056789 |    '5.7e-05'   |      '0.00'    |   '5.68e-05'   |      '0.01%'   |
|  0.00056789  |    '0.00057'   |      '0.00'    |   '5.68e-04'   |      '0.06%'   |
|  0.0056789   |    '0.0057'    |      '0.01'    |   '5.68e-03'   |      '0.57%'   |
|  0.056789    |    '0.057'     |      '0.06'    |   '5.68e-02'   |      '5.68%'   |
|  0.56789     |    '0.57'      |      '0.57'    |   '5.68e-01'   |     '56.79%'   |
|  5.6789      |    '5.7'       |      '5.68'    |   '5.68e+00'   |    '567.89%'   |
| 56.789       |    '5.7e+01'   |     '56.79'    |   '5.68e+01'   |   '5678.90%'   |
+--------------+----------------+----------------+----------------+----------------+
```
* **When both rounding up and rounding down are possible, the one that returns result with even last digit is chosen. That makes `'{6.5:.0f}'` a `'6'` and `'{7.5:.0f}'` an `'8'`.**

### Ints
```python
{90:c}                                   # 'Z'
{90:b}                                   # '1011010'
{90:X}                                   # '5A'
```


Numbers
-------
### Types
```python
<int>      = int(<float/str/bool>)       # Or: math.floor(<float>)
<float>    = float(<int/str/bool>)       # Or: <real>e±<int>
<complex>  = complex(real=0, imag=0)     # Or: <real> ± <real>j
<Fraction> = fractions.Fraction(0, 1)    # Or: Fraction(numerator=0, denominator=1)
<Decimal>  = decimal.Decimal(<str/int>)  # Or: Decimal((sign, digits, exponent))
```
* **`'int(<str>)'` and `'float(<str>)'` raise ValueError on malformed strings.**
* **Decimal numbers can be represented exactly, unlike floats where `'1.1 + 2.2 != 3.3'`.**
* **Precision of decimal operations is set with: `'decimal.getcontext().prec = <int>'`.**

### Basic Functions
```python
<num> = pow(<num>, <num>)                # Or: <num> ** <num>
<num> = abs(<num>)                       # <float> = abs(<complex>)
<num> = round(<num> [, ±ndigits])        # `round(126, -1) == 130`
```

### Math
```python
from math import e, pi, inf, nan, isinf, isnan
from math import sin, cos, tan, asin, acos, atan, degrees, radians
from math import log, log10, log2
```

### Statistics
```python
from statistics import mean, median, variance, stdev, pvariance, pstdev
```

### Random
```python
from random import random, randint, choice, shuffle, gauss, seed

<float> = random()                       # A float inside [0, 1).
<int>   = randint(from_inc, to_inc)      # An int inside [from_inc, to_inc].
<el>    = choice(<list>)                 # Keeps the list intact.
```

### Bin, Hex
```python
<int> = ±0b<bin>                         # Or: ±0x<hex>
<int> = int('±<bin>', 2)                 # Or: int('±<hex>', 16)
<int> = int('±0b<bin>', 0)               # Or: int('±0x<hex>', 0)
<str> = bin(<int>)                       # Returns '[-]0b<bin>'.
```

### Bitwise Operators
```python
<int> = <int> & <int>                    # And
<int> = <int> | <int>                    # Or
<int> = <int> ^ <int>                    # Xor (0 if both bits equal)
<int> = <int> << n_bits                  # Left shift (>> for right)
<int> = ~<int>                           # Not (also: -<int> - 1)
```


Combinatorics
-------------
* **Every function returns an iterator.**
* **If you want to print the iterator, you need to pass it to the list() function first!**

```python
from itertools import product, combinations, combinations_with_replacement, permutations
```

```python
>>> product([0, 1], repeat=3)
[(0, 0, 0), (0, 0, 1), (0, 1, 0), (0, 1, 1), ..., (1, 1, 1)]
```

```python
>>> product('abc', 'abc')                    #   a  b  c
[('a', 'a'), ('a', 'b'), ('a', 'c'),         # a x  x  x
 ('b', 'a'), ('b', 'b'), ('b', 'c'),         # b x  x  x
 ('c', 'a'), ('c', 'b'), ('c', 'c')]         # c x  x  x
```

```python
>>> combinations('abc', 2)                   #   a  b  c
[('a', 'b'), ('a', 'c'),                     # a .  x  x
 ('b', 'c')]                                 # b .  .  x
```

```python
>>> combinations_with_replacement('abc', 2)  #   a  b  c
[('a', 'a'), ('a', 'b'), ('a', 'c'),         # a x  x  x
 ('b', 'b'), ('b', 'c'),                     # b .  x  x
 ('c', 'c')]                                 # c .  .  x
```

```python
>>> permutations('abc', 2)                   #   a  b  c
[('a', 'b'), ('a', 'c'),                     # a .  x  x
 ('b', 'a'), ('b', 'c'),                     # b x  .  x
 ('c', 'a'), ('c', 'b')]                     # c x  x  .
```


Arguments
---------
### Inside Function Call
```python
<function>(<positional_args>)                  # f(0, 0)
<function>(<keyword_args>)                     # f(x=0, y=0)
<function>(<positional_args>, <keyword_args>)  # f(0, y=0)
```

### Inside Function Definition
```python
def f(<nondefault_args>):                      # def f(x, y):
def f(<default_args>):                         # def f(x=0, y=0):
def f(<nondefault_args>, <default_args>):      # def f(x, y=0):
```


Splat Operator
--------------
### Inside Function Call
**Splat expands a collection into positional arguments, while splatty-splat expands a dictionary into keyword arguments.**
```python
args   = (1, 2)
kwargs = {'x': 3, 'y': 4, 'z': 5}
func(*args, **kwargs)
```

#### Is the same as:
```python
func(1, 2, x=3, y=4, z=5)
```

### Inside Function Definition
**Splat combines zero or more positional arguments into a tuple, while splatty-splat combines zero or more keyword arguments into a dictionary.**
```python
def add(*a):
    return sum(a)
```

```python
>>> add(1, 2, 3)
6
```

#### Legal argument combinations:
```python
def f(x, y, z):                # f(x=1, y=2, z=3) | f(1, y=2, z=3) | f(1, 2, z=3) | f(1, 2, 3)
def f(*, x, y, z):             # f(x=1, y=2, z=3)
def f(x, *, y, z):             # f(x=1, y=2, z=3) | f(1, y=2, z=3)
def f(x, y, *, z):             # f(x=1, y=2, z=3) | f(1, y=2, z=3) | f(1, 2, z=3)
```

```python
def f(*args):                  # f(1, 2, 3)
def f(x, *args):               # f(1, 2, 3)
def f(*args, z):               # f(1, 2, z=3)
def f(x, *args, z):            # f(1, 2, z=3)
```

```python
def f(**kwargs):               # f(x=1, y=2, z=3)
def f(x, **kwargs):            # f(x=1, y=2, z=3) | f(1, y=2, z=3)
def f(*, x, **kwargs):         # f(x=1, y=2, z=3)
```

```python
def f(*args, **kwargs):        # f(x=1, y=2, z=3) | f(1, y=2, z=3) | f(1, 2, z=3) | f(1, 2, 3)
def f(x, *args, **kwargs):     # f(x=1, y=2, z=3) | f(1, y=2, z=3) | f(1, 2, z=3) | f(1, 2, 3)
def f(*args, y, **kwargs):     # f(x=1, y=2, z=3) | f(1, y=2, z=3)
def f(x, *args, z, **kwargs):  # f(x=1, y=2, z=3) | f(1, y=2, z=3) | f(1, 2, z=3)
```

### Other Uses
```python
<list>  = [*<collection> [, ...]]
<set>   = {*<collection> [, ...]}
<tuple> = (*<collection>, [...])
<dict>  = {**<dict> [, ...]}
```

```python
head, *body, tail = <collection>
```


Inline
------
### Lambda
```python
<func> = lambda: <return_value>
<func> = lambda <arg_1>, <arg_2>: <return_value>
```

### Comprehensions
```python
<list> = [i+1 for i in range(10)]                         # [1, 2, ..., 10]
<set>  = {i for i in range(10) if i > 5}                  # {6, 7, 8, 9}
<iter> = (i+5 for i in range(10))                         # (5, 6, ..., 14)
<dict> = {i: i*2 for i in range(10)}                      # {0: 0, 1: 2, ..., 9: 18}
```

```python
>>> [l+r for l in 'abc' for r in 'abc']
['aa', 'ab', 'ac', ..., 'cc']
```

### Map, Filter, Reduce
```python
<iter> = map(lambda x: x + 1, range(10))                  # (1, 2, ..., 10)
<iter> = filter(lambda x: x > 5, range(10))               # (6, 7, 8, 9)
<obj>  = reduce(lambda out, x: out + x, range(10))        # 45
```
* **Reduce must be imported from functools module.**

### Any, All
```python
<bool> = any(<collection>)                                # Is `bool(el)` True for any element.
<bool> = all(<collection>)                                # Is True for all elements or empty.
```

### Conditional Expression
```python
<obj> = <exp_if_true> if <condition> else <exp_if_false>
```

```python
>>> [a if a else 'zero' for a in (0, 1, 2, 3)]
['zero', 1, 2, 3]
```

### Named Tuple, Enum, Dataclass
```python
from collections import namedtuple
Point = namedtuple('Point', 'x y')
point = Point(0, 0)
```

```python
from enum import Enum
Direction = Enum('Direction', 'n e s w')
direction = Direction.n
```

```python
from dataclasses import make_dataclass
Creature = make_dataclass('Creature', ['loc', 'dir'])
creature = Creature(point, direction)
```


Imports
-------
```python
import <module>            # Imports a built-in or '<module>.py'.
import <package>           # Imports a built-in or '<package>/__init__.py'.
import <package>.<module>  # Imports a built-in or '<package>/<module>.py'.
```
* **Package is a collection of modules, but it can also define its own objects.**
* **On a filesystem this corresponds to a directory of Python files with an optional init script.**
* **Running `'import <package>'` does not automatically provide access to the package's modules unless they are explicitly imported in its init script.**


Closure
-------
**We have a closure in Python when:**
* **A nested function references a value of its enclosing function and then**
* **the enclosing function returns the nested function.**

```python
def get_multiplier(a):
    def out(b):
        return a * b
    return out
```

```python
>>> multiply_by_3 = get_multiplier(3)
>>> multiply_by_3(10)
30
```

* **If multiple nested functions within enclosing function reference the same value, that value gets shared.**
* **To dynamically access function's first free variable use `'<function>.__closure__[0].cell_contents'`.**

### Partial
```python
from functools import partial
<function> = partial(<function> [, <arg_1>, <arg_2>, ...])
```

```python
>>> import operator as op
>>> multiply_by_3 = partial(op.mul, 3)
>>> multiply_by_3(10)
30
```
* **Partial is also useful in cases when function needs to be passed as an argument, because it enables us to set its arguments beforehand.**
* **A few examples being: `'defaultdict(<function>)'`, `'iter(<function>, to_exclusive)'` and dataclass's `'field(default_factory=<function>)'`.**

### Non-Local
**If variable is being assigned to anywhere in the scope, it is regarded as a local variable, unless it is declared as a 'global' or a 'nonlocal'.**

```python
def get_counter():
    i = 0
    def out():
        nonlocal i
        i += 1
        return i
    return out
```

```python
>>> counter = get_counter()
>>> counter(), counter(), counter()
(1, 2, 3)
```


Decorator
---------
**A decorator takes a function, adds some functionality and returns it.**

```python
@decorator_name
def function_that_gets_passed_to_decorator():
    ...
```

### Debugger Example
**Decorator that prints function's name every time it gets called.**

```python
from functools import wraps

def debug(func):
    @wraps(func)
    def out(*args, **kwargs):
        print(func.__name__)
        return func(*args, **kwargs)
    return out

@debug
def add(x, y):
    return x + y
```
* **Wraps is a helper decorator that copies the metadata of the passed function (func) to the function it is wrapping (out).**
* **Without it `'add.__name__'` would return `'out'`.**

### LRU Cache
**Decorator that caches function's return values. All function's arguments must be hashable.**

```python
from functools import lru_cache

@lru_cache(maxsize=None)
def fib(n):
    return n if n < 2 else fib(n-2) + fib(n-1)
```
* **CPython interpreter limits recursion depth to 1000 by default. To increase it use `'sys.setrecursionlimit(<depth>)'`.**

### Parametrized Decorator
**A decorator that accepts arguments and returns a normal decorator that accepts a function.**
```python
from functools import wraps

def debug(print_result=False):
    def decorator(func):
        @wraps(func)
        def out(*args, **kwargs):
            result = func(*args, **kwargs)
            print(func.__name__, result if print_result else '')
            return result
        return out
    return decorator

@debug(print_result=True)
def add(x, y):
    return x + y
```


Class
-----
```python
class <name>:
    def __init__(self, a):
        self.a = a
    def __repr__(self):
        class_name = self.__class__.__name__
        return f'{class_name}({self.a!r})'
    def __str__(self):
        return str(self.a)

    @classmethod
    def get_class_name(cls):
        return cls.__name__
```
* **Return value of repr() should be unambiguous and of str() readable.**
* **If only repr() is defined, it will also be used for str().**

#### Str() use cases:
```python
print(<el>)
print(f'{<el>}')
raise Exception(<el>)
loguru.logger.debug(<el>)
csv.writer(<file>).writerow([<el>])
```

#### Repr() use cases:
```python
print([<el>])
print(f'{<el>!r}')
>>> <el>
loguru.logger.exception()
Z = dataclasses.make_dataclass('Z', ['a']); print(Z(<el>))
```

### Constructor Overloading
```python
class <name>:
    def __init__(self, a=None):
        self.a = a
```

### Inheritance
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age  = age

class Employee(Person):
    def __init__(self, name, age, staff_num):
        super().__init__(name, age)
        self.staff_num = staff_num
```

### Multiple Inheritance
```python
class A: pass
class B: pass
class C(A, B): pass
```

**MRO determines the order in which parent classes are traversed when searching for a method:**
```python
>>> C.mro()
[<class 'C'>, <class 'A'>, <class 'B'>, <class 'object'>]
```

### Property
**Pythonic way of implementing getters and setters.**
```python
class MyClass:
    @property
    def a(self):
        return self._a

    @a.setter
    def a(self, value):
        self._a = value
```

```python
>>> el = MyClass()
>>> el.a = 123
>>> el.a
123
```

### Dataclass
**Decorator that automatically generates init(), repr() and eq() special methods.**
```python
from dataclasses import dataclass, field

@dataclass(order=False, frozen=False)
class <class_name>:
    <attr_name_1>: <type>
    <attr_name_2>: <type> = <default_value>
    <attr_name_3>: list/dict/set = field(default_factory=list/dict/set)
```
* **For arbitrary type use `'typing.Any'`.**
* **Objects can be made sortable with `'order=True'` and immutable with `'frozen=True'`.**
* **For object to be hashable, all attributes must be hashable and frozen must be True.**
* **Function field() is needed because `'<attr_name>: list = []'` would make a list that is shared among all instances.**
* **Default_factory can be any [callable](#callable).**

#### Inline:
```python
from dataclasses import make_dataclass
<class> = make_dataclass('<class_name>', <coll_of_attribute_names>)
<class> = make_dataclass('<class_name>', <coll_of_tuples>)
<tuple> = ('<attr_name>', <type> [, <default_value>])
```

### Slots
**Mechanism that restricts objects to attributes listed in 'slots' and significantly reduces their memory footprint.**

```python
class MyClassWithSlots:
    __slots__ = ['a']
    def __init__(self):
        self.a = 1
```

### Copy
```python
from copy import copy, deepcopy

<object> = copy(<object>)
<object> = deepcopy(<object>)
```


Duck Types
----------
**A duck type is an implicit type that prescribes a set of special methods. Any object that has those methods defined is considered a member of that duck type.**

### Comparable
* **If eq() method is not overridden, it returns `'id(self) == id(other)'`, which is the same as `'self is other'`.**
* **That means all objects compare not equal by default.**
* **Only the left side object has eq() method called, unless it returns NotImplemented, in which case the right object is consulted.**

```python
class MyComparable:
    def __init__(self, a):
        self.a = a
    def __eq__(self, other):
        if isinstance(other, type(self)):
            return self.a == other.a
        return NotImplemented
```

### Hashable
* **Hashable object needs both hash() and eq() methods and its hash value should never change.**
* **Hashable objects that compare equal must have the same hash value, meaning default hash() that returns `'id(self)'` will not do.**
* **That is why Python automatically makes classes unhashable if you only implement eq().**

```python
class MyHashable:
    def __init__(self, a):
        self._a = a
    @property
    def a(self):
        return self._a
    def __eq__(self, other):
        if isinstance(other, type(self)):
            return self.a == other.a
        return NotImplemented
    def __hash__(self):
        return hash(self.a)
```

### Sortable
* **With total_ordering decorator, you only need to provide eq() and one of lt(), gt(), le() or ge() special methods.**
```python
from functools import total_ordering

@total_ordering
class MySortable:
    def __init__(self, a):
        self.a = a
    def __eq__(self, other):
        if isinstance(other, type(self)):
            return self.a == other.a
        return NotImplemented
    def __lt__(self, other):
        if isinstance(other, type(self)):
            return self.a < other.a
        return NotImplemented
```

### Iterator
* **Any object that has methods next() and iter() is an iterator.**
* **Next() should return next item or raise StopIteration.**
* **Iter() should return 'self'.**
```python
class Counter:
    def __init__(self):
        self.i = 0
    def __next__(self):
        self.i += 1
        return self.i
    def __iter__(self):
        return self
```

```python
>>> counter = Counter()
>>> next(counter), next(counter), next(counter)
(1, 2, 3)
```

#### Python has many different iterator objects:
* **Sequence iterators returned by the [iter()](#iterator) function, such as list\_iterator and set\_iterator.**
* **Objects returned by the [itertools](#itertools) module, such as count, repeat and cycle.**
* **Generators returned by the [generator functions](#generator) and [generator expressions](#comprehensions).**
* **File objects returned by the [open()](#open) function, etc.**

### Callable
* **All functions and classes have a call() method, hence are callable.**
* **When this cheatsheet uses `'<function>'` as an argument, it actually means `'<callable>'`.**
```python
class Counter:
    def __init__(self):
        self.i = 0
    def __call__(self):
        self.i += 1
        return self.i
```

```python
>>> counter = Counter()
>>> counter(), counter(), counter()
(1, 2, 3)
```

### Context Manager
* **Enter() should lock the resources and optionally return an object.**
* **Exit() should release the resources.**
* **Any exception that happens inside the with block is passed to the exit() method.**
* **If it wishes to suppress the exception it must return a true value.**
```python
class MyOpen:
    def __init__(self, filename):
        self.filename = filename
    def __enter__(self):
        self.file = open(self.filename)
        return self.file
    def __exit__(self, exc_type, exception, traceback):
        self.file.close()
```

```python
>>> with open('test.txt', 'w') as file:
...     file.write('Hello World!')
>>> with MyOpen('test.txt') as file:
...     print(file.read())
Hello World!
```


Iterable Duck Types
-------------------
### Iterable
* **Only required method is iter(). It should return an iterator of object's items.**
* **Contains() automatically works on any object that has iter() defined.**
```python
class MyIterable:
    def __init__(self, a):
        self.a = a
    def __iter__(self):
        return iter(self.a)
    def __contains__(self, el):
        return el in self.a
```

```python
>>> obj = MyIterable([1, 2, 3])
>>> [el for el in obj]
[1, 2, 3]
>>> 1 in obj
True
```

### Collection
* **Only required methods are iter() and len().**
* **This cheatsheet actually means `'<iterable>'` when it uses `'<collection>'`.**
* **I chose not to use the name 'iterable' because it sounds scarier and more vague than 'collection'.**
```python
class MyCollection:
    def __init__(self, a):
        self.a = a
    def __iter__(self):
        return iter(self.a)
    def __contains__(self, el):
        return el in self.a
    def __len__(self):
        return len(self.a)
```

### Sequence
* **Only required methods are len() and getitem().**
* **Getitem() should return an item at index or raise IndexError.**
* **Iter() and contains() automatically work on any object that has getitem() defined.**
* **Reversed() automatically works on any object that has len() and getitem() defined.**
```python
class MySequence:
    def __init__(self, a):
        self.a = a
    def __iter__(self):
        return iter(self.a)
    def __contains__(self, el):
        return el in self.a
    def __len__(self):
        return len(self.a)
    def __getitem__(self, i):
        return self.a[i]
    def __reversed__(self):
        return reversed(self.a)
```

### ABC Sequence
* **It's a richer interface than the basic sequence.**
* **Extending it generates iter(), contains(), reversed(), index() and count().**
* **Unlike `'abc.Iterable'` and `'abc.Collection'`, it is not a duck type. That is why `'issubclass(MySequence, abc.Sequence)'` would return False even if MySequence had all the methods defined.**
```python
from collections import abc

class MyAbcSequence(abc.Sequence):
    def __init__(self, a):
        self.a = a
    def __len__(self):
        return len(self.a)
    def __getitem__(self, i):
        return self.a[i]
```

#### Table of required and automatically available special methods:
```text
+------------+------------+------------+------------+--------------+
|            |  Iterable  | Collection |  Sequence  | abc.Sequence |
+------------+------------+------------+------------+--------------+
| iter()     |    REQ     |    REQ     |    Yes     |     Yes      |
| contains() |    Yes     |    Yes     |    Yes     |     Yes      |
| len()      |            |    REQ     |    REQ     |     REQ      |
| getitem()  |            |            |    REQ     |     REQ      |
| reversed() |            |            |    Yes     |     Yes      |
| index()    |            |            |            |     Yes      |
| count()    |            |            |            |     Yes      |
+------------+------------+------------+------------+--------------+
```
* **Other ABCs that generate missing methods are: MutableSequence, Set, MutableSet, Mapping and MutableMapping.**
* **Names of their required methods are stored in `'<abc>.__abstractmethods__'`.**


Exceptions
----------
### Basic Example
```python
try:
    <code>
except <exception>:
    <code>
```

### Complex Example
```python
try:
    <code_1>
except <exception_a>:
    <code_2_a>
except <exception_b>:
    <code_2_b>
else:
    <code_2_c>
finally:
    <code_3>
```
* **Code inside the `'else'` block will only be executed if `'try'` block had no exceptions.**
* **Code inside the `'finally'` block will always be executed (unless a signal is received).**

### Catching Exceptions
```python
except <exception>:
except <exception> as <name>:
except (<exception>, [...]):
except (<exception>, [...]) as <name>:
```
* **Also catches subclasses of the exception.**
* **Use `'traceback.print_exc()'` to print the error message to stderr.**
* **Use `'print(<name>)'` to print just the cause of the exception (its arguments).**

### Raising Exceptions
```python
raise <exception>
raise <exception>()
raise <exception>(<el> [, ...])
```

#### Re-raising caught exception:
```python
except <exception> as <name>:
    ...
    raise
```

### Exception Object
```python
arguments = <name>.args
exc_type  = <name>.__class__
filename  = <name>.__traceback__.tb_frame.f_code.co_filename
func_name = <name>.__traceback__.tb_frame.f_code.co_name
line      = linecache.getline(filename, <name>.__traceback__.tb_lineno)
error_msg = ''.join(traceback.format_exception(exc_type, <name>, <name>.__traceback__))
```

### Built-in Exceptions
```text
BaseException
 +-- SystemExit                   # Raised by the sys.exit() function.
 +-- KeyboardInterrupt            # Raised when the user hits the interrupt key (ctrl-c).
 +-- Exception                    # User-defined exceptions should be derived from this class.
      +-- ArithmeticError         # Base class for arithmetic errors.
      |    +-- ZeroDivisionError  # Raised when dividing by zero.
      +-- AttributeError          # Raised when an attribute is missing.
      +-- EOFError                # Raised by input() when it hits end-of-file condition.
      +-- LookupError             # Raised when a look-up on a collection fails.
      |    +-- IndexError         # Raised when a sequence index is out of range.
      |    +-- KeyError           # Raised when a dictionary key or set element is not found.
      +-- NameError               # Raised when a variable name is not found.
      +-- OSError                 # Errors such as “file not found” or “disk full” (see Open).
      |    +-- FileNotFoundError  # When a file or directory is requested but doesn't exist.
      +-- RuntimeError            # Raised by errors that don't fall into other categories.
      |    +-- RecursionError     # Raised when the maximum recursion depth is exceeded.
      +-- StopIteration           # Raised by next() when run on an empty iterator.
      +-- TypeError               # Raised when an argument is of wrong type.
      +-- ValueError              # When an argument is of right type but inappropriate value.
           +-- UnicodeError       # Raised when encoding/decoding strings to/from bytes fails.
```

#### Collections and their exceptions:
```text
+-----------+------------+------------+------------+
|           |    List    |    Set     |    Dict    |
+-----------+------------+------------+------------+
| getitem() | IndexError |            |  KeyError  |
| pop()     | IndexError |  KeyError  |  KeyError  |
| remove()  | ValueError |  KeyError  |            |
| index()   | ValueError |            |            |
+-----------+------------+------------+------------+
```

#### Useful built-in exceptions:
```python
raise TypeError('Argument is of wrong type!')
raise ValueError('Argument is of right type but inappropriate value!')
raise RuntimeError('None of above!')
```

### User-defined Exceptions
```python
class MyError(Exception):
    pass

class MyInputError(MyError):
    pass
```


Exit
----
**Exits the interpreter by raising SystemExit exception.**
```python
import sys
sys.exit()                        # Exits with exit code 0 (success).
sys.exit(<el>)                    # Prints to stderr and exits with 1.
sys.exit(<int>)                   # Exits with passed exit code.
```


Print
-----
```python
print(<el_1>, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
```
* **Use `'file=sys.stderr'` for messages about errors.**
* **Use `'flush=True'` to forcibly flush the stream.**

### Pretty Print
```python
from pprint import pprint
pprint(<collection>, width=80, depth=None, compact=False, sort_dicts=True)
```
* **Levels deeper than 'depth' get replaced by '...'.**


Input
-----
**Reads a line from user input or pipe if present.**

```python
<str> = input(prompt=None)
```
* **Trailing newline gets stripped.**
* **Prompt string is printed to the standard output before reading input.**
* **Raises EOFError when user hits EOF (ctrl-d/ctrl-z⏎) or input stream gets exhausted.**


Open
----
**Opens the file and returns a corresponding file object.**

```python
<file> = open(<path>, mode='r', encoding=None, newline=None)
```
* **`'encoding=None'` means that the default encoding is used, which is platform dependent. Best practice is to use `'encoding="utf-8"'` whenever possible.**
* **`'newline=None'` means all different end of line combinations are converted to '\n' on read, while on write all '\n' characters are converted to system's default line separator.**
* **`'newline=""'` means no conversions take place, but input is still broken into chunks by readline() and readlines() on either '\n', '\r' or '\r\n'.**

### Modes
* **`'r'`  - Read (default).**
* **`'w'`  - Write (truncate).**
* **`'x'`  - Write or fail if the file already exists.**
* **`'a'`  - Append.**
* **`'w+'` - Read and write (truncate).**
* **`'r+'` - Read and write from the start.**
* **`'a+'` - Read and write from the end.**
* **`'t'`  - Text mode (default).**
* **`'b'`  - Binary mode.**

### Exceptions
* **`'FileNotFoundError'` can be raised when reading with `'r'` or `'r+'`.**
* **`'FileExistsError'` can be raised when writing with `'x'`.**
* **`'IsADirectoryError'` and `'PermissionError'` can be raised by any.**
* **`'OSError'` is the parent class of all listed exceptions.**

### File Object
```python
<file>.seek(0)                      # Moves to the start of the file.
<file>.seek(offset)                 # Moves 'offset' chars/bytes from the start.
<file>.seek(0, 2)                   # Moves to the end of the file.
<bin_file>.seek(±offset, <anchor>)  # Anchor: 0 start, 1 current position, 2 end.
```

```python
<str/bytes> = <file>.read(size=-1)  # Reads 'size' chars/bytes or until EOF.
<str/bytes> = <file>.readline()     # Returns a line or empty string/bytes on EOF.
<list>      = <file>.readlines()    # Returns a list of remaining lines.
<str/bytes> = next(<file>)          # Returns a line using buffer. Do not mix.
```

```python
<file>.write(<str/bytes>)           # Writes a string or bytes object.
<file>.writelines(<collection>)     # Writes a coll. of strings or bytes objects.
<file>.flush()                      # Flushes write buffer.
```
* **Methods do not add or strip trailing newlines, even writelines().**

### Read Text from File
```python
def read_file(filename):
    with open(filename, encoding='utf-8') as file:
        return file.readlines()
```

### Write Text to File
```python
def write_to_file(filename, text):
    with open(filename, 'w', encoding='utf-8') as file:
        file.write(text)
```


Paths
-----
```python
from os import getcwd, path, listdir
from glob import glob
```

```python
<str>  = getcwd()                   # Returns the current working directory.
<str>  = path.join(<path>, ...)     # Joins two or more pathname components.
<str>  = path.abspath(<path>)       # Returns absolute path.
```

```python
<str>  = path.basename(<path>)      # Returns final component of the path.
<str>  = path.dirname(<path>)       # Returns path without the final component.
<tup.> = path.splitext(<path>)      # Splits on last period of the final component.
```

```python
<list> = listdir(path='.')          # Returns filenames located at path.
<list> = glob('<pattern>')          # Returns paths matching the wildcard pattern.
```

```python
<bool> = path.exists(<path>)        # Or: <Path>.exists()
<bool> = path.isfile(<path>)        # Or: <DirEntry/Path>.is_file()
<bool> = path.isdir(<path>)         # Or: <DirEntry/Path>.is_dir()
```

### DirEntry
**Using scandir() instead of listdir() can significantly increase the performance of code that also needs file type information.**

```python
from os import scandir
```

```python
<iter> = scandir(path='.')          # Returns DirEntry objects located at path.
<str>  = <DirEntry>.path            # Returns whole path as a string.
<str>  = <DirEntry>.name            # Returns final component as a string.
<file> = open(<DirEntry>)           # Opens the file and returns file object.
```

### Path Object
```python
from pathlib import Path
```

```python
<Path> = Path(<path> [, ...])       # Accepts strings, Paths and DirEntry objects.
<Path> = <path> / <path> [/ ...]    # One of the paths must be a Path object.
```

```python
<Path> = Path()                     # Returns relative cwd. Also Path('.').
<Path> = Path.cwd()                 # Returns absolute cwd. Also Path().resolve().
<Path> = Path.home()                # Returns user's home directory.
<Path> = Path(__file__).resolve()   # Returns script's path if cwd wasn't changed.
```

```python
<Path> = <Path>.parent              # Returns Path without the final component.
<str>  = <Path>.name                # Returns final component as a string.
<str>  = <Path>.stem                # Returns final component without extension.
<str>  = <Path>.suffix              # Returns final component's extension.
<tup.> = <Path>.parts               # Returns all components as strings.
```

```python
<iter> = <Path>.iterdir()           # Returns dir contents as Path objects.
<iter> = <Path>.glob('<pattern>')   # Returns Paths matching the wildcard pattern.
```

```python
<str>  = str(<Path>)                # Returns path as a string.
<file> = open(<Path>)               # Opens the file and returns file object.
```


OS Commands
-----------
### Files and Directories
* **Paths can be either strings, Paths or DirEntry objects.**
* **Functions report OS related errors by raising either OSError or one of its [subclasses](#exceptions-1).**

```python
import os, shutil
```

```python
os.chdir(<path>)                    # Changes the current working directory.
os.mkdir(<path>, mode=0o777)        # Creates a directory. Mode is in octal.
os.makedirs(<path>, mode=0o777)     # Creates all directories in the path.
```

```python
shutil.copy(from, to)               # Copies the file. 'to' can exist or be a dir.
shutil.copytree(from, to)           # Copies the directory. 'to' must not exist.
```

```python
os.rename(from, to)                 # Renames/moves the file or directory.
os.replace(from, to)                # Same, but overwrites 'to' if it exists.
```

```python
os.remove(<path>)                   # Deletes the file.
os.rmdir(<path>)                    # Deletes the empty directory.
shutil.rmtree(<path>)               # Deletes the directory.
```

### Shell Commands
```python
import os
<str> = os.popen('<shell_command>').read()
```

#### Sends '1 + 1' to the basic calculator and captures its output:
```python
>>> from subprocess import run
>>> run('bc', input='1 + 1\n', capture_output=True, text=True)
CompletedProcess(args='bc', returncode=0, stdout='2\n', stderr='')
```

#### Sends test.in to the basic calculator running in standard mode and saves its output to test.out:
```python
>>> from shlex import split
>>> os.popen('echo 1 + 1 > test.in')
>>> run(split('bc -s'), stdin=open('test.in'), stdout=open('test.out', 'w'))
CompletedProcess(args=['bc', '-s'], returncode=0)
>>> open('test.out').read()
'2\n'
```


JSON
----
**Text file format for storing collections of strings and numbers.**

```python
import json
<str>    = json.dumps(<object>, ensure_ascii=True, indent=None)
<object> = json.loads(<str>)
```

### Read Object from JSON File
```python
def read_json_file(filename):
    with open(filename, encoding='utf-8') as file:
        return json.load(file)
```

### Write Object to JSON File
```python
def write_to_json_file(filename, an_object):
    with open(filename, 'w', encoding='utf-8') as file:
        json.dump(an_object, file, ensure_ascii=False, indent=2)
```


Pickle
------
**Binary file format for storing objects.**

```python
import pickle
<bytes>  = pickle.dumps(<object>)
<object> = pickle.loads(<bytes>)
```

### Read Object from File
```python
def read_pickle_file(filename):
    with open(filename, 'rb') as file:
        return pickle.load(file)
```

### Write Object to File
```python
def write_to_pickle_file(filename, an_object):
    with open(filename, 'wb') as file:
        pickle.dump(an_object, file)
```


CSV
---
**Text file format for storing spreadsheets.**

```python
import csv
```

### Read
```python
<reader> = csv.reader(<file>)       # Also: `dialect='excel', delimiter=','`.
<list>   = next(<reader>)           # Returns next row as a list of strings.
<list>   = list(<reader>)           # Returns list of remaining rows.
```
* **File must be opened with a `'newline=""'` argument, or newlines embedded inside quoted fields will not be interpreted correctly!**

### Write
```python
<writer> = csv.writer(<file>)       # Also: `dialect='excel', delimiter=','`.
<writer>.writerow(<collection>)     # Encodes objects using `str(<el>)`.
<writer>.writerows(<coll_of_coll>)  # Appends multiple rows.
```
* **File must be opened with a `'newline=""'` argument, or '\r' will be added in front of every '\n' on platforms that use '\r\n' line endings!**

### Parameters
* **`'dialect'` - Master parameter that sets the default values.**
* **`'delimiter'` - A one-character string used to separate fields.**
* **`'quotechar'` - Character for quoting fields that contain special characters.**
* **`'doublequote'` - Whether quotechars inside fields get doubled or escaped.**
* **`'skipinitialspace'` - Whether whitespace after delimiter gets stripped.**
* **`'lineterminator'` - Specifies how writer terminates rows.**
* **`'quoting'` - Controls the amount of quoting: 0 - as necessary, 1 - all.**
* **`'escapechar'` - Character for escaping 'quotechar' if 'doublequote' is False.**

### Dialects
```text
+------------------+--------------+--------------+--------------+
|                  |     excel    |   excel-tab  |     unix     |
+------------------+--------------+--------------+--------------+
| delimiter        |       ','    |      '\t'    |       ','    |
| quotechar        |       '"'    |       '"'    |       '"'    |
| doublequote      |      True    |      True    |      True    |
| skipinitialspace |     False    |     False    |     False    |
| lineterminator   |    '\r\n'    |    '\r\n'    |      '\n'    |
| quoting          |         0    |         0    |         1    |
| escapechar       |      None    |      None    |      None    |
+------------------+--------------+--------------+--------------+
```

### Read Rows from CSV File
```python
def read_csv_file(filename):
    with open(filename, encoding='utf-8', newline='') as file:
        return list(csv.reader(file))
```

### Write Rows to CSV File
```python
def write_to_csv_file(filename, rows):
    with open(filename, 'w', encoding='utf-8', newline='') as file:
        writer = csv.writer(file)
        writer.writerows(rows)
```

Bytes
-----
**Bytes object is an immutable sequence of single bytes. Mutable version is called bytearray.**

```python
<bytes> = b'<str>'                       # Only accepts ASCII characters and \x00-\xff.
<int>   = <bytes>[<index>]               # Returns int in range from 0 to 255.
<bytes> = <bytes>[<slice>]               # Returns bytes even if it has only one element.
<bytes> = <bytes>.join(<coll_of_bytes>)  # Joins elements using bytes as a separator.
```

### Encode
```python
<bytes> = bytes(<coll_of_ints>)          # Ints must be in range from 0 to 255.
<bytes> = bytes(<str>, 'utf-8')          # Or: <str>.encode('utf-8')
<bytes> = <int>.to_bytes(n_bytes, …)     # `byteorder='big/little', signed=False`.
<bytes> = bytes.fromhex('<hex>')         # Hex pairs can be separated by spaces.
```

### Decode
```python
<list>  = list(<bytes>)                  # Returns ints in range from 0 to 255.
<str>   = str(<bytes>, 'utf-8')          # Or: <bytes>.decode('utf-8')
<int>   = int.from_bytes(<bytes>, …)     # `byteorder='big/little', signed=False`.
'<hex>' = <bytes>.hex()                  # Returns a string of hexadecimal pairs.
```

### Read Bytes from File
```python
def read_bytes(filename):
    with open(filename, 'rb') as file:
        return file.read()
```

### Write Bytes to File
```python
def write_bytes(filename, bytes_obj):
    with open(filename, 'wb') as file:
        file.write(bytes_obj)
```


Struct
------
* **Module that performs conversions between a sequence of numbers and a bytes object.**
* **System’s type sizes and byte order are used by default.**

```python
from struct import pack, unpack, iter_unpack
```

```python
<bytes>  = pack('<format>', <num_1> [, <num_2>, ...])
<tuple>  = unpack('<format>', <bytes>)
<tuples> = iter_unpack('<format>', <bytes>)
```

### Example
```python
>>> pack('>hhl', 1, 2, 3)
b'\x00\x01\x00\x02\x00\x00\x00\x03'
>>> unpack('>hhl', b'\x00\x01\x00\x02\x00\x00\x00\x03')
(1, 2, 3)
```

### Format
#### For standard type sizes start format string with:
* **`'='` - system's byte order (usually little-endian)**
* **`'<'` - little-endian**
* **`'>'` - big-endian (also `'!'`)**

#### Integer types. Use a capital letter for unsigned type. Minimum and standard sizes are in brackets:
* **`'x'` - pad byte**
* **`'b'` - char (1/1)**
* **`'h'` - short (2/2)**
* **`'i'` - int (2/4)**
* **`'l'` - long (4/4)**
* **`'q'` - long long (8/8)**

#### Floating point types:
* **`'f'` - float (4/4)**
* **`'d'` - double (8/8)**



Operator
--------
**Module of functions that provide the functionality of operators.**
```python
from operator import add, sub, mul, truediv, floordiv, mod, pow, neg, abs
from operator import eq, ne, lt, le, gt, ge
from operator import and_, or_, xor, not_
from operator import itemgetter, attrgetter, methodcaller
```

```python
import operator as op
elementwise_sum  = map(op.add, list_a, list_b)
sorted_by_second = sorted(<collection>, key=op.itemgetter(1))
sorted_by_both   = sorted(<collection>, key=op.itemgetter(1, 0))
product_of_elems = functools.reduce(op.mul, <collection>)
union_of_sets    = functools.reduce(op.or_, <coll_of_sets>)
last_el          = op.methodcaller('pop')(<list>)
```


Introspection
-------------
**Inspecting code at runtime.**

### Variables
```python
<list> = dir()                             # Names of local variables (incl. functions).
<dict> = vars()                            # Dict of local variables. Also locals().
<dict> = globals()                         # Dict of global variables.
```

### Attributes
```python
<list> = dir(<object>)                     # Names of object's attributes (incl. methods).
<dict> = vars(<object>)                    # Dict of writable attributes. Also <obj>.__dict__.
<bool> = hasattr(<object>, '<attr_name>')  # Checks if getattr() raises an AttributeError.
value  = getattr(<object>, '<attr_name>')  # Raises AttributeError if attribute is missing.
setattr(<object>, '<attr_name>', value)    # Only works on objects with __dict__ attribute.
delattr(<object>, '<attr_name>')           # Equivalent to `del <object>.<attr_name>`.
```

### Parameters
```python
from inspect import signature
<Sig>  = signature(<function>)             # Function's Signature object.
<dict> = <Sig>.parameters                  # Dict of function's Parameter objects.
<str>  = <Param>.name                      # Parameter's name.
<memb> = <Param>.kind                      # Member of ParameterKind enum.
```

Index
-----
* **Only available in the [PDF](https://transactions.sendowl.com/products/78175486/4422834F/view).**
* **Ctrl+F / ⌘F is usually sufficient.**
* **Searching `'#<title>'` on a [webpage](https://gto76.github.io/python-cheatsheet/) will limit the search to the titles.**
