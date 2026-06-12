---
title: "Can't delete oddly named files"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by bgschley on 2006-08-22
Hi there,

I need some help please... I a few weeks ago I switched on my PC and a set of files had appeared in my home directory. I don't know if they are remanents of files that I had deleted before sutting down, but what ever they are, I am starting to get annoyed with them. They have extremely long file names and wehnever I try to rename, delete, etc, I am told that the file doen't exist. Any idea what they are and how to get rid of them?

I'm using KDE at the moment.

Cheers

George

PS screenshot attached.

---

### Post by meng on 2006-08-22
Try command
kdesu konqueror
and see if you can delete them with root privileges.
This may not work, but I figure it can't hurt.

---

### Post by Iowan on 2006-08-22
A bit more primitive (but that's how I think), you might list the directory from a terminal.  I've had files that looked like they were named with unprintable characters - but they looked fine in a terminal - something weird with the font, I guess.

---

### Post by Brunellus on 2006-08-22
your problem is file permissions.  meng's suggestion to use kdesu konqueror would work.  you could also change their ownership.

---

### Post by A2A on 2006-08-22
Those do look like some foreign language fonts (japanese, korean perhaps).  I like the idea suggested by Iowan, where he suggests you do a directory listing via terminal.  
On another note, perhaps your computer was compromised and someone placed those files there.  It does happen a lot so it's not something you should ignore.

Regards,

---

### Post by bgschley on 2006-08-22
Hi, thanks for all the comments. I've tried deleting them using kdesu but no go. All of the files say that they are 0 bytes. I've tried deleting them through the command line but no go either...

Any other thoughts?

Cheers

George

---

### Post by Iowan on 2006-08-22
Use wildcards?  Do the files show up via command line?  You could try moving the "keepers" to another directory, then **sudo rm -i ***.  The **-i** option will help avoid deleting any files that shouldn't be deleted.Still somewhat risky, though...

---

### Post by bgschley on 2006-08-25
Cheers Iowan,

Sudo rm -i * worked. Hopefully nothing important got hammered.

Thanks for your help... much happier now :-)

Cheers

George

---

