# pipe21 - simple functional pipes [[docs]](docs/reference.md)

## Basic version
just copy-paste it!

Most frequently used operators. It's often easier to copypaste than import.

```py
class B:
    def __init__(self, f): self.f = f
class Pipe  (B): __ror__ = lambda self, x: self.f(x)
class Map   (B): __ror__ = lambda self, x: map   (self.f, x)
class Filter(B): __ror__ = lambda self, x: filter(self.f, x)
```

or install using pip:

```py
pip install pipe21
```

## Examples

#### little docs

```py
x | Pipe(f)   == f     (x   )
x | Map(f)    == map   (f, x)
x | Filter(f) == filter(f, x)
x | Reduce(f) == reduce(f, x)
```

---

#### simple pipes

```py
range(5) | Pipe(list) # [0, 1, 2, 3, 4]
range(5) | Map(str) | Pipe(''.join) # '01234'
range(5) | Filter(lambda x: x % 2 == 0) | Pipe(list) # [0, 2, 4]
range(5) | Reduce(lambda a, b: a + b) # 10
```

---

#### print digits

```py
range(1_000_000) | Map(chr) | Filter(str.isdigit) | Pipe(''.join)
```
Output:

0123456789²³¹٠١٢٣٤٥٦٧٨٩۰۱۲۳۴۵۶۷۸۹߀߁߂߃߄߅߆߇߈߉०१२३४५६७८९০১২৩৪৫৬৭৮৯੦੧੨੩੪੫੬੭੮੯૦૧૨૩૪૫૬૭૮૯୦୧୨୩୪୫୬୭୮୯௦௧௨௩௪௫௬௭௮௯౦౧౨౩౪౫౬౭౮౯೦೧೨೩೪೫೬೭೮೯൦൧൨൩൪൫൬൭൮൯෦෧෨෩෪෫෬෭෮෯๐๑๒๓๔๕๖๗๘๙໐໑໒໓໔໕໖໗໘໙༠༡༢༣༤༥༦༧༨༩၀၁၂၃၄၅၆၇၈၉႐႑႒႓႔႕႖႗႘႙፩፪፫፬፭፮፯፰፱០១២៣៤៥៦៧៨៩᠐᠑᠒᠓᠔᠕᠖᠗᠘᠙᥆᥇᥈᥉᥊᥋᥌᥍᥎᥏᧐᧑᧒᧓᧔᧕᧖᧗᧘᧙᧚᪀᪁᪂᪃᪄᪅᪆᪇᪈᪉᪐᪑᪒᪓᪔᪕᪖᪗᪘᪙᭐᭑᭒᭓᭔᭕᭖᭗᭘᭙᮰᮱᮲᮳᮴᮵᮶᮷᮸᮹᱀᱁᱂᱃᱄᱅᱆᱇᱈᱉᱐᱑᱒᱓᱔᱕᱖᱗᱘᱙⁰⁴⁵⁶⁷⁸⁹₀₁₂₃₄₅₆₇₈₉①②③④⑤⑥⑦⑧⑨⑴⑵⑶⑷⑸⑹⑺⑻⑼⒈⒉⒊⒋⒌⒍⒎⒏⒐⓪⓵⓶⓷⓸⓹⓺⓻⓼⓽⓿❶❷❸❹❺❻❼❽❾➀➁➂➃➄➅➆➇➈➊➋➌➍➎➏➐➑➒꘠꘡꘢꘣꘤꘥꘦꘧꘨꘩꣐꣑꣒꣓꣔꣕꣖꣗꣘꣙꤀꤁꤂꤃꤄꤅꤆꤇꤈꤉꧐꧑꧒꧓꧔꧕꧖꧗꧘꧙꧰꧱꧲꧳꧴꧵꧶꧷꧸꧹꩐꩑꩒꩓꩔꩕꩖꩗꩘꩙꯰꯱꯲꯳꯴꯵꯶꯷꯸꯹０１２３４５６７８９𐒠𐒡𐒢𐒣𐒤𐒥𐒦𐒧𐒨𐒩𐩀𐩁𐩂𐩃𐴰𐴱𐴲𐴳𐴴𐴵𐴶𐴷𐴸𐴹𐹠𐹡𐹢𐹣𐹤𐹥𐹦𐹧𐹨𑁒𑁓𑁔𑁕𑁖𑁗𑁘𑁙𑁚𑁦𑁧𑁨𑁩𑁪𑁫𑁬𑁭𑁮𑁯𑃰𑃱𑃲𑃳𑃴𑃵𑃶𑃷𑃸𑃹𑄶𑄷𑄸𑄹𑄺𑄻𑄼𑄽𑄾𑄿𑇐𑇑𑇒𑇓𑇔𑇕𑇖𑇗𑇘𑇙𑋰𑋱𑋲𑋳𑋴𑋵𑋶𑋷𑋸𑋹𑑐𑑑𑑒𑑓𑑔𑑕𑑖𑑗𑑘𑑙𑓐𑓑𑓒𑓓𑓔𑓕𑓖𑓗𑓘𑓙𑙐𑙑𑙒𑙓𑙔𑙕𑙖𑙗𑙘𑙙𑛀𑛁𑛂𑛃𑛄𑛅𑛆𑛇𑛈𑛉𑜰𑜱𑜲𑜳𑜴𑜵𑜶𑜷𑜸𑜹𑣠𑣡𑣢𑣣𑣤𑣥𑣦𑣧𑣨𑣩𑱐𑱑𑱒𑱓𑱔𑱕𑱖𑱗𑱘𑱙𑵐𑵑𑵒𑵓𑵔𑵕𑵖𑵗𑵘𑵙𑶠𑶡𑶢𑶣𑶤𑶥𑶦𑶧𑶨𑶩𖩠𖩡𖩢𖩣𖩤𖩥𖩦𖩧𖩨𖩩𖭐𖭑𖭒𖭓𖭔𖭕𖭖𖭗𖭘𖭙𝟎𝟏𝟐𝟑𝟒𝟓𝟔𝟕𝟖𝟗𝟘𝟙𝟚𝟛𝟜𝟝𝟞𝟟𝟠𝟡𝟢𝟣𝟤𝟥𝟦𝟧𝟨𝟩𝟪𝟫𝟬𝟭𝟮𝟯𝟰𝟱𝟲𝟳𝟴𝟵𝟶𝟷𝟸𝟹𝟺𝟻𝟼𝟽𝟾𝟿𞅀𞅁𞅂𞅃𞅄𞅅𞅆𞅇𞅈𞅉𞋰𞋱𞋲𞋳𞋴𞋵𞋶𞋷𞋸𞋹𞥐𞥑𞥒𞥓𞥔𞥕𞥖𞥗𞥘𞥙🄀🄁🄂🄃🄄🄅🄆🄇🄈🄉🄊'


#### chunked

```py
>>> range(5) | Chunked(2) | Pipe(list)
[(0, 1), (2, 3), (4,)]
```

---

## Extended version
```py
import pipe21 as P
# from pipe21 import * # or use this to use Map, Filter, etc (without P.)
```

#### FizzBuzz

```py
import itertools
import pipe21 as P

(
    range(1, 100)
    | P.Map(lambda i: (i, itertools.compress(('Fizz', 'Buzz'), (i % 3 == 0, i % 5 == 0))))
    | P.MapValues(''.join)
    | P.Map(lambda kv: kv[1] or kv[0])
    | P.Pipe(list)
)

[1, 2, 'Fizz', 4, 'Buzz', 'Fizz', 7, 8, 'Fizz', 'Buzz', 11, 'Fizz', 13, 14, 'FizzBuzz', 16, 17, 'Fizz', 19, 'Buzz', 'Fizz', 22, 23, 'Fizz', 'Buzz', 26, 'Fizz', 28, 29, 'FizzBuzz', 31, 32, 'Fizz', 34, 'Buzz', 'Fizz', 37, 38, 'Fizz', 'Buzz', 41, 'Fizz', 43, 44, 'FizzBuzz', 46, 47, 'Fizz', 49, 'Buzz', 'Fizz', 52, 53, 'Fizz', 'Buzz', 56, 'Fizz', 58, 59, 'FizzBuzz', 61, 62, 'Fizz', 64, 'Buzz', 'Fizz', 67, 68, 'Fizz', 'Buzz', 71, 'Fizz', 73, 74, 'FizzBuzz', 76, 77, 'Fizz', 79, 'Buzz', 'Fizz', 82, 83, 'Fizz', 'Buzz', 86, 'Fizz', 88, 89, 'FizzBuzz', 91, 92, 'Fizz', 94, 'Buzz', 'Fizz', 97, 98, 'Fizz']
```

---

#### play random music from youtube links in markdown files:

```py
import pathlib
import random
import itertools
import re
import operator
import webbrowser
import pipe21 as P


(
    pathlib.Path.home() / 'GoogleDrive/knowledge/music'    # take a directory
    | P.Pipe(lambda x: x.rglob('*.md'))                    # find all markdown files
    | P.FlatMap(lambda p: open(p).read().splitlines())     # read all lines from all files and flatten into a single iterable
    | P.Map(lambda l: re.findall(r'\[(.+)\]\((.+)\)', l))  # check: is a line has a markdown link
    | P.Filter(bool)                                       # keep only lines with a link
    | P.Map(operator.itemgetter(0))                        # extract a link
    | P.Map(operator.itemgetter(1))                        # extract a link
    | P.Pipe(list)                                         # convert iterable of links into a list
    | P.Pipe(random.choice)                                # choose random link
    | P.Pipe(webbrowser.open)                              # open link in browser
)
```

All available methods reference is [here](docs/reference.md)

## similar tools
- [pytoolz/toolz: A functional standard library for Python.](https://github.com/pytoolz/toolz/)
- [nekitdev/iters.py: Rich Iterators for Python.](https://github.com/nekitdev/iters.py)
- [R adds native pipe and lambda syntax | Hacker News](https://news.ycombinator.com/item?id=25316608)
- [mpypl - Google Search](https://www.google.com/search?q=mpypl&oq=mpypl&aqs=chrome..69i57j0l6j69i60.1343j0j7&sourceid=chrome&ie=UTF-8)
- [JulienPalard/Pipe: A Python library to use infix notation in Python](https://github.com/JulienPalard/Pipe)
- [Pydash: A Kitchen Sink of Missing Python Utilities | by Khuyen Tran | Towards Data Science](https://towardsdatascience.com/pydash-a-bucket-of-missing-python-utilities-5d10365be4fc)
- [Write Clean Python Code Using Pipes | by Khuyen Tran | Oct, 2021 | Towards Data Science](https://towardsdatascience.com/write-clean-python-code-using-pipes-1239a0f3abf5)
- [A trick to have arbitrary infix operators in Python | Hacker News](https://news.ycombinator.com/item?id=30057048)
- [PySpark - RDD API](https://spark.apache.org/docs/latest/api/python/reference/pyspark.html#rdd-apis)
- [altimin/fcollections](https://github.com/altimin/fcollections)
- [InvestmentSystems/function-pipe: Tools for extended function composition and pipelines in Python](https://github.com/InvestmentSystems/function-pipe)
- [kachayev/fn.py: Functional programming in Python: implementation of missing features to enjoy FP](https://github.com/kachayev/fn.py)
- [man-group/mdf: Data-flow programming toolkit for Python](https://github.com/man-group/mdf)
- [0101/pipetools: Functional plumbing for Python](https://github.com/0101/pipetools)
- [EntilZha/PyFunctional: Python library for creating data pipelines with chain functional programming](https://github.com/EntilZha/PyFunctional)
- [jasondelaat/pymonad: ](https://github.com/jasondelaat/pymonad)
- [machow/siuba: Python library for using dplyr like syntax with pandas and SQL](https://github.com/machow/siuba)
- [pipeop · PyPI](https://pypi.org/project/pipeop/)
