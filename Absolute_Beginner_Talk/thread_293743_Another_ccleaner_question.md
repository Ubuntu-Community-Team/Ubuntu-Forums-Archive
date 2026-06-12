---
title: "Another ccleaner question"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Miguellint on 2006-11-05
Hi all...I appreciate that ccleaner isn't that necessary in ubuntu but it has one feature I quite like.

It has a "three-pass secure file delete" option which can be added to the right-click menu of the recycle bin. When you empty the trash it's wiped three times. (I'm not paranoid....it's just that they're out to get me :-)

Is there any software with a similar feature (multi-pass secure file deletion) in ubuntu.

Many thanks
Miguel

---

### Post by Dr. Nick on 2006-11-06
maybe something like this
[http://ubuntuforums.org/showthread.php?t=253502&highlight=secure+delete](http://ubuntuforums.org/showthread.php?t=253502&highlight=secure+delete)

---

### Post by spinflick on 2006-11-06
Sorry for butting in but I just installed Wipe, but how do you use it? :rolleyes:

---

### Post by Dr. Nick on 2006-11-06
not exactly sure since i havent used it personally, Open a terminal and try
 
man wipe
 
for a instruction page, if their isnt one you may have to google

---

### Post by Miguellint on 2006-11-06
> **Dr. Nick said:**
> maybe something like this
[http://ubuntuforums.org/showthread.php?t=253502&highlight=secure+delete](http://ubuntuforums.org/showthread.php?t=253502&highlight=secure+delete)

Thank you Dr.Nick

Exactly what I wanted and the "man wipe" command gave a good how-to-use.

Many thanks
Miguel :-)

---

### Post by yme on 2007-02-20
I don't have the expertise myself but I am told that such wiping and overwriting does not work on ext3, the default ubuntu filesystem, because it is 'journaling'. See:

[http://ubuntuforums.org/showthread.php?t=96698&highlight=delete+journaling+filesystems](http://ubuntuforums.org/showthread.php?t=96698&highlight=delete+journaling+filesystems)

---

### Post by peabody on 2007-08-03
Actually it does it work per default.  There are several levels of journaling in ext3.  Per default, only metadata is journaled so the file itself will be zapped.  Data recovery tools could potentially be used to determine the filename and date, but nothing else.

There is a way to turn on journaling such that all data written is journaled.  Much safer for data integrity but slows down i/o and increases fragmentation.

---

