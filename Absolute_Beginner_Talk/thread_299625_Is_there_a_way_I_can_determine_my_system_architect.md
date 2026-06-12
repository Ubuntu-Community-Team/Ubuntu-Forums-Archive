---
title: "Is there a way I can determine my system architecture?"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by thunderstorm on 2006-11-14
I had to run this (sudo dpkg --configure -a) and it asked for my system architecture.  I don't really know what that is, or if picking the wrong option will mess up my system.  is there a way I can find this out?

---

### Post by LLRNR on 2006-11-14
I don't know what exactly is it that you want to do and I also don't know about such tools to run under linux (I'm on this ground for a very short time... but I'll "grow") but there is a tool that I like very much that runs under Windoze and it's called Aida32. Doing a quick search on [google](http://www.google.com/linux) for aida, I came up with [this](http://www.linuxquestions.org/questions/showthread.php?t=301253) and it actually seems to be a good place to start with.

HTH,

LLRNR

---

### Post by Marsolin on 2006-11-14
The command you are looking for is uname. "uname -a" will display your kernel and some additional info. Look for something like i686 or amd64. It's likely one of those.

---

### Post by scrooge_74 on 2006-11-14
> **thunderstorm said:**
> I had to run this (sudo dpkg --configure -a) and it asked for my system architecture.  I don't really know what that is, or if picking the wrong option will mess up my system.  is there a way I can find this out?

from command line type uname -a  should give you something like "Linux toshiba 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux"

---

