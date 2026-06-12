---
title: "Cannot mount extranal drive, error"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Northsider on 2008-03-15
I have had this working very recently, but now all of the sudden it will not mount and I cannot open it.  I get this error:
[IMG]http://i25.tinypic.com/10f8768.png[/IMG]

I don't know what that means, any ideas?  I usually use Kubuntu, but now I have been booting into Ubuntu...I don't think that makes a difference, I get the same error in both.

---

### Post by meindian523 on 2008-03-15
If you are not using RAID,reboot into Windows and shut it down cleanly.Then try booting into Ubuntu again.

---

### Post by glennric on 2008-03-15
Can you boot to windows?  Try doing what the error tells you to do.

---

### Post by Northsider on 2008-03-15
I dont even have windows...

EDIT: erm, I did use it in my gf's XP latop, doh!  I'll try that, thanks.

---

### Post by dasunst3r on 2008-03-15
You got this error because you unplugged the external drive without ejecting / "safely removing" it.  Regardless of what OS you use, it is highly recommended that you "safely remove" / unmount your external disks before pulling them.  In the event you can't get access to a Windows box, do the following in the terminal:
[list=1]
[*]sudo apt-get install ntfsprogs (this installs a collection of programs for working with NTFS partitions
[*]sud ntfsfix /dev/sdb (Attempts to fix the NTFS partition and make it clean.  Replace /dev/sdb with whatever your device is, although it's usually that)
[/list]

---

### Post by Northsider on 2008-03-15
> john@john-laptop:~$ sudo ntfsfix /dev/sda1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS partition /dev/sda1 was processed successfully.


I already had the ntfsprogs, but I ran the second command

---

