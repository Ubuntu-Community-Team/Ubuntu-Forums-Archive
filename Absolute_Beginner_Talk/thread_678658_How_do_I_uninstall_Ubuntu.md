---
title: "How do I uninstall Ubuntu?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by skaldicpoet9 on 2008-01-26
How do I uninstall Ubuntu 7.10 and redistribute the disk space back to XP? I installed Gusty on a 10gb partition using the GPart partioner on my Gateway laptop.

---

### Post by yabbadabbadont on 2008-01-26
First, use XP's recovery console to restore the XP MBR.  You may need to boot your XP install CD for this.  Then run fixmbr and possibly fixboot.  Once your machine boots straight into XP without Grub showing up, you can use XP's drives manager to remove or reformat the Ubuntu partition.

---

### Post by skaldicpoet9 on 2008-01-26
When I booted into the recovery console I didn;t see XP MBR, how do I get to it?

---

### Post by yabbadabbadont on 2008-01-26
No.  MBR is Master Boot Record.  It is what Grub replaced when you installed Ubuntu.  You have to restore the XP version of it.  Use the "fixmbr" command.  Then make sure that the machine will boot directly into XP before you remove or reformat the Ubuntu parititon.

---

### Post by skaldicpoet9 on 2008-01-26
So I use the Grub cmd line to enter fixmbr? I just realized I don't have the XP install disk I only have the XP recovery disk that I got with the laptop...

---

### Post by Jelmoh on 2008-01-26
you should make yourself a back-up floppy..
Using XP you can format a floppy disk and choose it to be a back-up (or something like that, back-up, rescue.. something that looks like it)
Then startup from floppy drive and you should get to dos..
There type 'fixmbr' (without quotes) than restart (take floppy disk out! ;)) it should boot to XP without showing grup loader...
If that's the case you can safely repartition/reformat/remove the ubuntu partition

---

### Post by LaRoza on 2008-01-26
You can also use the Super Grub Disk to restore the Windows MBR.

Advanced->Windows (Advanced) and it is the first option.

See the link in my sig.

---

### Post by skaldicpoet9 on 2008-01-26
How do I make a back-up floppy?

---

### Post by mikewhatever on 2008-01-26
Run mbrfix.exe from Windows, then test if it worked, then proceed with partitions.
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

---

### Post by LaRoza on 2008-01-26
> **skaldicpoet9 said:**
> How do I make a back-up floppy?

Insert a floppy disk, right click on the drive icon, and make a start up disk.

---

### Post by Jelmoh on 2008-01-26
It's probably easier to download the Super Grup CD!
[Link in LaRoza's signature! ;)](http://laroza.pbwiki.com/TheLinkInMySig)
Booting to that cd you can restore the MBR too! :)

Good luck!

---

