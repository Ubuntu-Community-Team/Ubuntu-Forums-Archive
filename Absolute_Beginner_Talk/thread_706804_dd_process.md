---
title: "dd process"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Cha1n5aW on 2008-02-24
Occasionally my notebook begins getting very very hot and my wireless connection drops, and everything seems to start running very very slowly.  When I run "top" to see what's going on, I notice a process at the top of the list piggin out on my resources called simply "dd".  I've tried some web searching but cannot find much information, prolly because searching a term like dd produces very useless results.  I checked my processes after booting, and dd is not listed there initially.  I'm not sure what is loading this process, and why it isnt' unloading on its own.  Is there a way I can prevent this from affecting me any further?

Thanks
- Shawn

---

### Post by .Michael on 2008-02-24
dd copys and coverts files.
files are anything on a linux system. Hard Drives, Ethernet cards...


[QUOTE=man dd]Copy a file, converting and formatting according to the operands.[/QUOTE]

Like /dev/hda is your hard drive.
/dev/tty7 is what ubuntu puts you on for GDM and sessions

EDIT: Check this out: [http://ubuntuforums.org/announcement.php?f=73]("http://ubuntuforums.org/announcement.php?f=73")

---

### Post by bobbybobington on 2008-02-24
from what I can tell, dd is the process involved with copying files, so I think it isn't ending after it is done. I agree that google results don't really help much :).

---

### Post by Cha1n5aW on 2008-02-24
Much thanks, I'm guessing its safe to just kill the process then if I'm not copying anything.  I believe the process may have been started when I was copying files to & from a flash drive earlier on.  Strange how it didn't go away on its own, perhaps some sort of bug.  I am suspicious tho, as it seems to use alot of resources for a command that shouldn't be doing anything.  *sigh*

- Shawn

---

### Post by jfinkels on 2008-02-24
[http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29)

Did you run run the command "dd" at any time in the past?

---

### Post by Cha1n5aW on 2008-02-26
jfinkels, nope, not intentionally anyways.  Haven't encountered it since tho.

---

