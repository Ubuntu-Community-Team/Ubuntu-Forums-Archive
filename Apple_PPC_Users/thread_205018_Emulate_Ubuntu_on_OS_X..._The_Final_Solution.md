---
title: "Emulate Ubuntu on OS X... The Final Solution?"
date: 2006-06-27
forum: Apple PPC Users
---

### Post by zachws on 2006-06-27
I am an ubuntu addict. I post all the time (maybe too much). I really enjoy learning new computer technologies and such but I do have a standard for usability, even for OSes maintaned solely out of the goodness of peoples' hearts.

For those who have a 100% working Ubuntu installation out of the box, this may seem like craziness. I do not think the PPC version of Ubutu Dapper is up to par. It does not work for my hardware out of the box. I have pretty much the latest (read: last) PPC mac (an ibook g4).

In order to use Ubuntu I have to tweak the configuration files to speed up the mouse to passable (but not comfortable) speed and usability. graphic card acceleration does not work and cannot be enabled at this point. Airport extreme wireless does not work out of the box, and I do not care enough to haxie my way through it at this point as I use ethernet. 

In my travels I have come across "Q", an OS X port of Qemu that allows for free 'guest pc' use of other operating systems (windows variants and linux). you can download from FreeOS (within the program) a preconfigured Ubuntu installation (however i think it is breezy). If not you can install Ubuntu on a virtual disk for the program. Anyway I share all of this to offer the PPC users who love ubuntu and are waiting for it to get up to par another option to explore. 

Here is the link:
[http://www.kberg.ch/q/](http://www.kberg.ch/q/)

Just Another Idea,
Zach

---

### Post by 3rdalbum on 2006-06-28
I think you'll find that PowerPC Linux won't go much better than Ubuntu. Apple's hardware was markedly different to PC hardware (which is an open specification).

Graphics card drivers don't work because ATI and nVidea haven't ported them to PowerPC. They won't port them because there's not enough demand. There aren't too many developers concerned with PowerPC, because there aren't too many of these machines about. Especially now that Apple has jumped ship, and the most popular PowerPC-based consumer machine around has anti-Linux protection. (you know which machine I mean)

If you want the best in PowerPC Linux, try Yellow Dog. I've tried emulating x86 Linux within Qemu, and even lightweight distros were terribly slow for me. I'm not sure it's a viable solution really.

---

### Post by FredB on 2006-06-28
[QUOTE=3rdalbum]I think you'll find that PowerPC Linux won't go much better than Ubuntu. Apple's hardware was markedly different to PC hardware (which is an open specification).[/QUOTE]

At least for powerpc based Macs.

> 
Graphics card drivers don't work because ATI and nVidea haven't ported them to PowerPC. They won't port them because there's not enough demand. There aren't too many developers concerned with PowerPC, because there aren't too many of these machines about. Especially now that Apple has jumped ship, and the most popular PowerPC-based consumer machine around has anti-Linux protection. (you know which machine I mean)

Which one ? I spent a year with a Mac, and never heard about this !

> 
If you want the best in PowerPC Linux, try Yellow Dog. I've tried emulating x86 Linux within Qemu, and even lightweight distros were terribly slow for me. I'm not sure it's a viable solution really.

Yes. But Ubuntu is on some point more advanced than Yellow Dog (which is a FC4 + some little updates).

---

