---
title: "Password protected disk?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-02-18
My neighbor has a Dell Latitude 600M in which the hard disk has failed.  I downloaded Fujitsu's "low-level" format utility for the drive and it comes back saying the drive has failed - it won't even do the "low-level" format.

So, they had another smaller laptop drive (used) that they bought cheap so we decided to try it in the Dell, with the intent of just installing Ubuntu.  Well, the disk apparently has some sort of password protection, and the neighbor has no idea what it could be (probably why the drive was cheap).  We tried a DOS based program called latitude.exe which was supposed to generate the key from the service tag.  It generated a key alright, just not sure where the hard disk is that the key is for, since it didn't work with this one.

So, is there a way in Ubuntu to get around this password?  I have no clue as to how these types of things work on a PC, so I haven't been much help.

Any help would be greatly appreciated! :)

---

### Post by randy78 on 2008-02-18
If your goal is to completely start over with a clean drive, then I suggest using DBAN:
[http://dban.sourceforge.net/](http://dban.sourceforge.net/) 
Make sure to select the CD/DVD media, unless you're using a floppy ;)

This will COMPLETELY and THOROUGHLY wipe ALL data on this drive beyond recovery, so ONLY use this if you are absolutely positive that this is what you want to achieve.

After that, it's only a matter of popping in a LiveCD and re-installing.

Hope that helps!

EDIT:
DBAN should wipe all password protection on this drive, if that is what you're going for.

---

### Post by vpik01 on 2008-02-18
Not an ubuntu fix but... if you have a usb to ata cord, or a cheap usb portable hdd kit (laptop hdd sized) you may be able to plug it into another computer and work with it.  I keep one of these kits around to use my old laptop hdd's and have found it a useful option for data recovery and reformatting...  good luck

---

