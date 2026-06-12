---
title: "Read Linux Partition in Windows"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by justinmiller87 on 2007-10-06
Hey all, just a quick question.

For those times I have to boot into XP, does anyone have a suggestion to let me access my ext partitions?

Thanks.

---

### Post by meierfra on 2007-10-06
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by Sef on 2007-10-06
Get [fs-driver.]("http://www.fs-driver.org/")

---

### Post by justinmiller87 on 2007-10-06
Much appreciated. Thanks. It's for x86 systems only, and I'll be building a 64-bit PC soon. Is there anything I could use for that if I don't make it an Ubuntu-exclusive box?

---

### Post by maddog39 on 2007-10-06
The fact that you are building a 64bit system is pretty much irrelevant. Since windows XP is 32bit period, unless you physically buy the 64 bit version, which I don't recommend unless you absolutely know what your doing/using it for.

[Edit]
In your case I dont recommend you install the 64bit version of Ubuntu either.

---

### Post by shifty_powers on 2007-10-06
> **maddog39 said:**
> The fact that you are building a 64bit system is pretty much irrelevant. Since windows XP is 32bit period, unless you physically buy the 64 bit version, which I don't recommend unless you absolutely know what your doing/using it for.

[Edit]
In your case I dont recommend you install the 64bit version of Ubuntu either.

well i am guessing that he is going to be using vista, in which case it most definitely come in a 64 bit version quite easily...

---

### Post by rmockler on 2007-10-06
WOW !!  The fs-driver is a super recommendation.  I downloaded, installed, and in minutes I was able to successfully access my Ubuntu partition from Windows.  This is a great tool, I can't believe that anyone who dual-boots wouldn't want it.

---

### Post by mgmiller on 2007-10-06
Just be careful using it.  Since it only supports ext2 and not ext3, if you are writing to your ext3 drive from windows and windows freezes or goes down for some reason, you risk messing up your ext3 journal.  This is a theoretical problem, but it is quite real.  It can _usually_ be fixed by running e2fsck, which should happen automatically on reboot, but, you never know.

I guess the moral of this story is backup, backup, backup.  Then, if something blows up, you just smile and restore everything.  :lolflag:

---

### Post by justinmiller87 on 2007-10-06
> **shifty_powers said:**
> well i am guessing that he is going to be using vista, in which case it most definitely come in a 64 bit version quite easily...
Actually, I am building it from scratch and I do not want anything to do with Vista; not now, not ever. So no,  I won't be using Vista. XP for me, and only in very rare occasions do I plan on using it. Actually, I  may just keep it at a dual boot on my laptop and make the desktop I'm building strictly Ubuntu. [Here is](http://ubuntuforums.org/showthread.php?p=3450347#post3450347) the computer I intend to build, with a 64-bit AMD processor. The way you are both implying, I am able to use the x86 architecture OS on a 64-bit PC. That doesn't seem to make any sense to me though.

---

