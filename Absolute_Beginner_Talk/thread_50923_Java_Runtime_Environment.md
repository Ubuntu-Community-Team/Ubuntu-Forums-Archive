---
title: "Java Runtime Environment??"
date: 2005-07-21
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-07-21
I want to install VASSAL which means I need to install Java, but I'm not sure what I need to install exactly. I see in the guide about installing Java as a plugin for Mozilla Firefox but I'm not sure that's what I want or need. Can someone please help me out here?

Thanks!

---

### Post by DJ_Max on 2005-07-21
Look at this thread.
[http://ubuntuforums.org/showthread.php?t=50855](http://ubuntuforums.org/showthread.php?t=50855)

---

### Post by grofaz on 2005-07-22
Thanks. But before I get further into it and check out the recommended  thread, which looks complicated for a Linux idiot like myself, I tried this:

sudo apt-get install sun-j2re1.5

as shown in the guide, and got a can't find package message. Is there an additional repository beyond the extras source.list described in the guide? I also downloaded the tar directly from Sun but it's a little bit over my head to install it correctly. Lot's of command line mumbo jumbo I'm not familiar with yet.

---

### Post by poofyhairguy on 2005-07-22
[QUOTE=grofaz]Thanks. But before I get further into it and check out the recommended  thread, which looks complicated for a Linux idiot like myself, I tried this:

sudo apt-get install sun-j2re1.5

as shown in the guide, and got a can't find package message. [/QUOTE]

Hmm..so you replaced the sources.list and it doesn't work...hmm...thats odd.

WAIT!! Are you using the 64 bit version? Java (and media codecs) do not come so easily in the 64 bit version.

---

### Post by grofaz on 2005-07-22
Nope. 32 bit version.

---

### Post by poofyhairguy on 2005-07-22
[QUOTE=grofaz]Nope. 32 bit version.[/QUOTE]

Hmm...I know!

Ok. You added the sources.list from the guide correct? now do this command and try to install Java again:

sudo apt-get update

---

### Post by grofaz on 2005-07-22
That's it! You are genius. Thank you for helping me.

---

### Post by poofyhairguy on 2005-07-22
[QUOTE=grofaz]That's it! You are genius. Thank you for helping me.[/QUOTE]

No problem, its why I'm here. If you want to know, what that command basically did is tell apt-get to notice the new sources.list. To update itself.

---

