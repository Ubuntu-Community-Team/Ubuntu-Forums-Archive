---
title: "Need a linux program that will run on 64 mbs"
date: 2012-04-01
forum: Any Other OS
---

### Post by qfertig on 2012-04-01
ok well i have an old p3 and i can't get it to install windows or puppy linux or dsl linux i also have no hdd so i would have to have it boot off the ram and then be able to install to a usb i have an old ibm thinkpad thanks!

---

### Post by BertN45 on 2012-04-01
Try Puppy Linux or Damn Small Linux, both run and install from an USB stick or CD

[http://en.wikipedia.org/wiki/Lightweight_Linux_distribution](http://en.wikipedia.org/wiki/Lightweight_Linux_distribution)

---

### Post by oldos2er on 2012-04-01
Thread moved to Other OS/Distro Talk.

---

### Post by dniMretsaM on 2012-04-02
That's really small. Even for Puppy/DSL. I think TinyCore could handle it fairly well, though.

---

### Post by Ravi5kumar on 2012-04-03
You can use SliTaz Linux OS. It is very lightweight OS and its ISO is small as 30 MB!! You can download it at [http://www.slitaz.org/](http://www.slitaz.org/)! It is capable on running on a system with 48 mb of RAM!!

---

### Post by angryfirelord on 2012-04-03
> **qfertig said:**
> ok well i have an old p3 and i can't get it to install windows or puppy linux or dsl linux i also have no hdd so i would have to have it boot off the ram and then be able to install to a usb i have an old ibm thinkpad thanks!
Older computers usually don't have USB booting, only CD-ROM, HDD, or floppy. Also, it's a bit hard to install anything if you don't have a hard drive. ;)

---

### Post by lykwydchykyn on 2012-04-03
What exactly do you hope/expect to do with this system once it's working?

In any case, tinycore is probably your best bet.  The way TC is designed, the core files are read-only, and software installs are stored in separate file archives and merged in either at boot or on-demand.

The upshot is that you could put the core files on a CD and your files & installed software on a USB drive.  It'd be clunky, but it would work.

---

### Post by qfertig on 2012-04-04
@lykwydchykyn i was hoping to use it as a laptop >_< i don't have one and my friend gave me a free laptop and i'm kinda broke so yeah

---

### Post by lykwydchykyn on 2012-04-04
> **qfertig said:**
> @lykwydchykyn i was hoping to use it as a laptop >_< i don't have one and my friend gave me a free laptop and i'm kinda broke so yeah

People use laptops for all kinds of things.  Some of them take a lot of computing power and some don't.

What I mean is, what sort of tasks do you hope to do on it?  Web browsing? Video editing? Calculating the first 10 million prime numbers? Typing your thesis? It's all fine to get a distro installed, but running applications is another thing.

You can forget about a modern web experience (flash, javascript-heavy stuff, reasonable speed) on 64 MB, for example.  You can forget about watching video for the most part, or playing any but the simplest games.

If you can put more RAM in it, the processor isn't so bad -- I have a k6-2 laptop with 256 Mb of RAM (upgraded from 64 originally) at home running Debian, and it's ok as long as I run the lightest software I can get and don't do more than one application at a time.  

And considering you don't have a hard drive and won't have swap space (unless you want to burn out that flash drive using it as swap), I don't know what's likely to be usable.

---

