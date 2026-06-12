---
title: "Need help booting desktop ubuntu"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Link360 on 2006-08-30
I downloaded the desktop version of ubuntu and put it on a disk.
I then restarted my computer with the disk in.
My computer started up and seemed like it was fine, but then it 
stopped loading and came to a point where it said 
[DR-DOS]A:\>
and it wanted me to type something but I have no idea what to type. Please Help.

---

### Post by nazgulord on 2006-08-31
Are you on an older computer by any chance? Sometimes older computers do not recognize bootable CDs of Linux distros. However, when this happened to me, it wouldn't go to a DOS prompt, but would give an isolinux error.

Do you know what the boot order in your BIOS is? It may not be looking for the CD during boot.

You might also want to look at these threads:

[http://ubuntuforums.org/showthread.php?t=246934](http://ubuntuforums.org/showthread.php?t=246934)

[http://ubuntuforums.org/showthread.php?t=227858](http://ubuntuforums.org/showthread.php?t=227858)

nazgulord.

---

### Post by Link360 on 2006-08-31
I have a brand new computer so that shouldnt be a problem.

Im not sure of the Bios order, but how would i change it to boot 
CD first.

---

### Post by nazgulord on 2006-08-31
Actually, I think the threads I posted links to maybe more helpful as they seem to correspond to the situation better than my experiences.

Sorry for any trouble.

nazgulord.

---

### Post by Ptero-4 on 2006-08-31
Hi Link360. Your problem sounds like there's a DOS (or Windoze XP) boot floppy in the floppy drive. See if there's a floppy and take it out of the drive. If there's no floppy in there, then the only other posible explanation is that the BIOS is faking a DOS floppy (obviously to prevent booting a linux CD).

---

