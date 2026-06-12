---
title: "Need a new Grub boot floppy"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by johnleonard on 2006-09-21
Hi - I have a dual boot machine which by default boots to XP, with Dapper accessible using Grub on a floppy. This worked well until idiocy struck: while trying to duplicate my Grub boot floppy I accidently reformatted it (forgetting to replace my boot floppy with a new one). Doh!

So, I now have no working copy of Grub, and am unable to boot into Ubuntu. 

How do I create a new boot floppy that will allow me back in? Any help much appreciated!

John

---

### Post by jd65pl on 2006-09-21
Hi john,

You may find this[http://yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#GRUB]("http://yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#GRUB") useful

Thanks

J

---

### Post by jd65pl on 2006-09-21
On second thoughts this seems exactly what you may want!

[http://www.ubuntuforums.org/showthread.php?t=6195]("http://www.ubuntuforums.org/showthread.php?t=6195")

---

### Post by johnleonard on 2006-09-21
Thanks - problem is I can't get into Ubuntu to issue the necessary commands. Is this something I can do using Live CD?

---

### Post by jd65pl on 2006-09-21
yeah sure using a live cd is a good option.

J

---

### Post by johnleonard on 2006-09-21
I'll give it a go.

Cheers!

---

### Post by jd65pl on 2006-09-21
Post back if it works for you,

Thanks

J

---

### Post by xyz on 2006-09-21
Just in case...
[http://www.ubuntuforums.org/showthread.php?t=259777&page=3](http://www.ubuntuforums.org/showthread.php?t=259777&page=3)

---

### Post by johnleonard on 2006-09-21
I found this while looking for a solutiion - has anyone tried it? Will my existing Linux partitions be overwritten?
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by jd65pl on 2006-09-21
Are you trying to make a boot floppy or use grub to dual boot? If you are trying to recover grub for a dual boot try 
[this...]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

J

---

### Post by xyz on 2006-09-21
I did and I really didn't do this > DO NOT FORMAT THEM like the HowTo said. I can only speak for myself but it worked fine.
At the time, I had used the Breezy Badger Live CD, though.
Good luch.

---

### Post by johnleonard on 2006-09-21
Thanks! The second item (Using the Alternate/Install CD and Overwriting the Windows bootloader) looks to be the same as [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub). That's what I was going to try. Hopefully it will give me an option to create another grub boot floppy which is what I want. I don't need it to dual boot as my PC boots into XP from the hard drive by default.

---

### Post by jd65pl on 2006-09-21
The kind of process described in that howto: makes me lot nervous! I'm sure it worked for that guy tho.

J

---

### Post by johnleonard on 2006-09-22
This worked for me [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Back in action again with Grub on a new floppy. Many thanks to all who helped.

John

---

### Post by NoWhereMan on 2006-09-22
this works ;)
[http://ubuntuforums.org/showthread.php?t=155684&highlight=grub#9](http://ubuntuforums.org/showthread.php?t=155684&highlight=grub#9)

use rawrite [http://www.chrysocome.net/rawwrite](http://www.chrysocome.net/rawwrite) to write on the floppy (win32)

---

