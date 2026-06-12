---
title: "wine installation softwares"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by lucky_chouhan on 2006-12-06
hi i am download real player, winamp, dumeter, internet download manager, acrobat reader and lots of more...

problem is where is stored this application or how to run.

---

### Post by CatKiller on 2006-12-06
Why? All of those thing are either available natively, or have functional equivalents.

Anyway, programs you install with Wine end up on your pretend C: drive that's in ~/.wine/drive_c.

---

### Post by bodhi.zazen on 2006-12-06
> **lucky_chouhan said:**
> hi i am download real player, winamp, dumeter, internet download manager, acrobat reader and lots of more...

problem is where is stored this application or how to run.

See CatKiller's post for location....

to run a program in wine:

wine /path/to/program.exe

It can be difficult because of the space in "Program Files"

use program\ Files or "double quotes"

Even better tab completion.

To add a launcher,```
'wine /home/user_name/.wine/c/Program Files/program.exe'
```

See also [How to wine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by sunexplodes on 2006-12-06
Yeah. or just go into your home folder, make sure you can view hidden files, and then navigate to the directory, and double click the exe file like you would in windows.

Although I'd agree you don't need most of those apps, there are linux equivalents for most (if not all of those).

---

### Post by lucky_chouhan on 2006-12-07
ok some time for testing.

Thanks for all you.

---

