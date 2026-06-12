---
title: "Trouble removing Ubuntu due to Grub bootloader"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by EGE-FB on 2007-05-12
Hi, 

I tried removing Ubuntu from my computer and reinstalling Windows back again but Grub 1.5 keeps giving the "Error 22" message and I can't boot into Windows or anything. I used GParted to delete ALL the partitions on my computer and created a new NTFS partition to which I installed Windows using the Toshiba Recovery CD.

 Now, since I deleted all the partitions and even installed Windows XP on a newly created parition on top of that, why is GRUB still there? Shouldn't it get deleted away as well? I did all of this before and it worked fine then but now it's not working for some reason. Help please.. :confused:

---

### Post by h0ax on 2007-05-12
The partitions are only a portion of it.  GRUB is written to the MBR(Master Boot Record)

When you go through the Windows install you need to overwrite the MBR.

---

### Post by oilchangeguy on 2007-05-12
> **h0ax said:**
> The partitions are only a portion of it.  GRUB is written to the MBR(Master Boot Record)

When you go through the Windows install you need to overwrite the MBR.
if the user has correctly deleted the partition this will not be an issue.
if the recovery disc is being used, i don't think this option will be available.

---

### Post by darksong on 2007-05-12
Let the Windows Installer totally overwrite everything. Don't use Gparted or anything to make your parttitons - let the windows installer do it. Make sure you format ect.

It will remove Grub.

---

### Post by seshomaru samma on 2007-05-12
anyway
boot from the windows cd
choose rescue 
and run the command
```
fixmbr
```

---

