---
title: "specto crash on launch, how do i investigate further?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by cvaty on 2007-10-03
specto, a great little tray app to mass check a ton of websites/email servers/local folders/and more have changed since it last checked and preventing you from wasting you life away checking back on old content to see if its changed:

[http://specto.sourceforge.net/](http://specto.sourceforge.net/)
[B]
unfortunatly, the program crashes on me at startup... (it worked the first few times after i installed it, but now its broke...)

what i'm wondering is, how do i produce some sort of log, or investigate this situation that led up to the crash to see how it happened.  i'm sure there are a few options, what are they?[/B]

---

### Post by cvaty on 2007-10-03
so the no brainer here is just running it from the terminal and seeing what poped up:
this is what i get

```

cvaty@cvaty-laptop:~$ specto
Traceback (most recent call last):
  File "/usr/bin/specto", line 38, in <module>
    specto = Specto()
  File "/usr/lib/python2.5/site-packages/spectlib/main.py", line 100, in __init__
    self.watch_io = Watch_io()
  File "/usr/lib/python2.5/site-packages/spectlib/watch.py", line 174, in __init__
    self.cfg = ini_namespace(file(self.file_name))
  File "/usr/lib/python2.5/site-packages/spectlib/iniparser.py", line 621, in __init__
    self.readfp(fp)
  File "/usr/lib/python2.5/site-packages/spectlib/iniparser.py", line 762, in readfp
    raise exc
ConfigParser.ParsingError: File contains parsing errors: /home/cvaty/.specto/watches.list
        [line 15]: blog [idle rantings]]



```

---

### Post by cvaty on 2007-10-03
based on this i believe my problem lies in the fact that i used brackets [ ]
and that created a syntax problem that the parser just does not like....

i will remove this watches.list  or modify it and take out the brackets and see if that helps... (always nice when you can solve your own problems)

---

### Post by cvaty on 2007-10-03
worked like a charm... you CAN NOT use brackets in the watch 'name' 
i will email the author with this issue so it can be resolved, or prohibited in the next release

---

