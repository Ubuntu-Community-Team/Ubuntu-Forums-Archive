---
title: "[SOLVED] help - dual boot install with XP, but grub won't load after running XP"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-11-04
I installed gutsy 7.10, and it created a dual boot situation with XP, no problems.  I was using ubuntu happily until I happened to boot back into XP for a minute, when I restarted out of XP, grub tries to load - you see one text line about grub 1.5, then the laptop resets and reboots.  It sits in this cycle endlessly.


How do I get it working again?  I can't get into XP or Ubuntu.  I can boot from the live ubuntu CD however.

---

### Post by gate on 2007-11-04
ok,boot into your liveCD. For this you need to know if you have an IDE harddrive or a SCSI/SATA. and which partition is which.

  open a terminal and run 
  ```
sudo bash
```

  then if you have an IDE drive, and Ubuntu is on the second partition, then the following should work.
  ```
mkdir /media/recovery
  mount /dev/hda1 /media/recovery
  grub-install --recheck --root-directory=/media/recovery /dev/hda

```
  for sata/scsi hard drives, replace hda with sda. different partition numbers change the number on hda1 to hda2 or whatever you need.

---

### Post by Can+~ on 2007-11-04
I guess windows made "check disk stuff" and screwed up the grub, well, if you need to boot into an specific thing, you can always use that key to select what to boot first, usually **F8**, but as a long term solution, you should reinstall grub.

*edit* someone already cared to explain how to reinstall xD

---

### Post by ubnewbie2 on 2007-11-04
Thanks everyone.  I am up and running again.  Yes, it was just grub that was messed up by Windows (and yes windows did do a check disk when I booted into it)

So is Windows going to do this every time I use it?  Sort of makes the dual-boot thing a bit awkward :-(

---

### Post by gate on 2007-11-04
no, I dual boot and it has never happened to me like that. I use that command when deploying a computer image to my lab.

   It disturbs me that it happened, but it doesn't surprise me: windows doesn't like to share a computer.

---

### Post by ubnewbie2 on 2007-11-05
> **gate said:**
> no, I dual boot and it has never happened to me like that. I use that command when deploying a computer image to my lab.

   It disturbs me that it happened, but it doesn't surprise me: windows doesn't like to share a computer.

It disturbs me even more :-)  because I tried Windows again, and it stuffed grub again.  I wonder if it has a virus that's modifying the MBR?  I have no knowledge of the history of this laptop, it is just an old discarded one from our business, so anything is possible, even though we run virus checking software.

btw:  I have found a disk called "Super Grub Disk" which boots very quickly and fixes it, almost automatically

---

### Post by gate on 2007-11-05
that isn't pleasant, I have no idea why Windows is doing that.
 
   One thought: did it do a chkdsk again? if it did, I would suspect that you resized the Windows NTFS partition, or put windows on a non-primary partition? it really can be finicky about its boot loader.

---

### Post by ubnewbie2 on 2007-11-05
> **gate said:**
> that isn't pleasant, I have no idea why Windows is doing that.
 
   One thought: did it do a chkdsk again? if it did, I would suspect that you resized the Windows NTFS partition, or put windows on a non-primary partition? it really can be finicky about its boot loader.

No it didn't chkdsk the second time. 

Before I installed ubuntu, the disk had 2 partitions. I resized the second partition only - NOT the one Windows was installed in.  When I ran Windows the first time, it did a chkdsk on the 2nd partition, so no way that should have damaged the MBR.  

Given that it didn't chkdsk the second time I booted into Windows, I am sure that the problem lies elsewhere.

---

### Post by ubnewbie2 on 2007-11-05
I fixed it !!!  I found this with a google search and it works.



If your system is using Novell ZenWorks, then remove this registry key:

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon]

"System"="ziswin.exe"

You'll need to reinstall GRUB again after doing this, but thereafter you should be fine. This setting causes some information to be written into the MBR each time you boot and thus hoses up GRUB.

---

