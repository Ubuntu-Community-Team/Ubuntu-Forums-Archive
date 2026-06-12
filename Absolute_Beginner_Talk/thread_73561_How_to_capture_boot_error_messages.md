---
title: "How to capture boot error messages?"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by editrix on 2005-10-09
Well, I'm about to try to install Ubuntu 5.04 for the 5th time (Aborted the previous 4 due to not knowing what option to choose). When the install CD first boots, a *lot* of data speeds by. I've managed to catch words like "strange" and "can't." Since this may cause problems later on, is there some way of either slowing the text down, or writing it to some kind of file?

---

### Post by simon.schmidt on 2005-10-09
[QUOTE=editrix]Well, I'm about to try to install Ubuntu 5.04 for the 5th time (Aborted the previous 4 due to not knowing what option to choose). When the install CD first boots, a *lot* of data speeds by. I've managed to catch words like "strange" and "can't." Since this may cause problems later on, is there some way of either slowing the text down, or writing it to some kind of file?[/QUOTE]

don't worry to much about that, if it doesn't halt it's usually ok ;)

---

### Post by Wide on 2005-10-09
You can check your boot error logs with 

```
cat /var/log/dmesg

```

```
dmesg
```

```
cat /var/log/messages
```


You can also go into /var/log & see all kinds of nice info:cool:

---

### Post by editrix on 2005-10-10
[QUOTE=Wide]You can check your boot error logs with 

[CODE]cat /var/log/dmesg ...

Thanks, but that's after I've installed Ubuntu, right? I meant when the install disk first boots up.

Guess I'll take simon.schmidt's advice. As he says, "if it doesn't halt it's usually ok."

---

