---
title: "How To Run WINE - Extremely basic question!"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by flubmasterq on 2007-04-29
So, I'm kinda lost right now.
I've beeen running Ubuntu Edgy for a while now, and it's been running smooth.
I just today downloaded WINE and all that jazz,
But I can't seem to figure out how to open it >,<
Can somebody tell me how to run it?

---

### Post by bobplano on 2007-04-29
if it's an exe or something usually double-clicking opens it with wine but for the terminal

```
sudo wine *program*
```
it's not perfect so don't expect everything to run on it

---

### Post by jfinkels on 2007-04-29
from the terminal type the word "wine" followed by the name of the executable file that you want to run. for example, when I run the game "Caesar III", I type something like this:
```
wine c3.exe
```

---

### Post by Acglaphotis on 2007-04-29
It doesnt "Open" you must find the exe and execute wine before the exe, like this: 

```
wine {path to exe}
```
Or you can do a right-click and select "Open with Wine Windows Emulator" or you can do right-click>properties>open with>custom comand>wine.

I've always wondered why it says Wine Windows Emulator if Wine stands for "Wine Is Not an Emulator"

-Acgla

---

### Post by nonewmsgs on 2007-04-29
maybe you mean "winecfg" ?

---

### Post by flubmasterq on 2007-04-29
Alright, thanks, now I get it.

---

