---
title: "Uh OHH!"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by gugin on 2007-04-21
I duel booted xp\feisty on my delll insperion e1505 duelcore without problems. Grub works fine. Xp Media center ed. ntfs. 

Here's the problem: I tried to do the same on my desktop running xp pro (ntfs). It didn't go so well. The install was smooth....or so I thought. After installing ubuntu I rebooted as prompted. My PC wont boot at all. so I booted to the feisty cd again. Reinstalled again. no change. no boot. 

Booted from xp cd into recovery and ran fixmbr, chkdsk, and fixboot.Still says "Error loading Operating system"  i booted from xp cd and repaired windows. No change. Same message. Any Ideas??

AMD 64 3500+

:confused: 
TIA
Justin

---

### Post by st33med on 2007-04-21
Ok coupla questions:
Did you set up one of the partitions with a boot flag (if you installed the partition manually)?
Did you set the BIOS to load off of CD only?
What else do you know about your computer?
Did you install the 64-bit Ubuntu?

---

### Post by bulldog on 2007-04-21
Can you give us the output of this command```
sudo fdisk -l
``` it's a lowercase L not a one.
You can perform this command from a terminal in a live cd session.

---

### Post by gugin on 2007-04-21
> **st33med said:**
> Ok coupla questions:
Did you set up one of the partitions with a boot flag (if you installed the partition manually)?
Did you set the BIOS to load off of CD only?
What else do you know about your computer?
Did you install the 64-bit Ubuntu?

Thanks for the response. I didn't set partitions manually. There is a boot flag. The BIOS is set to use the 1st sata hd in boot order. I installed the 32bit x86. 

I built the puter. So it only has 2x 512mb ddr2 pc3200 kingston. msi 6600gt pci-ex. SLi is disabled. asus a8n sli-delux. duel gigbit lan.

---

### Post by st33med on 2007-04-21
Hmmm... Haven't a clue of what is happening. Maybe your hard drive is loose?

Follow bulldog's instructions

---

### Post by gugin on 2007-04-21
> **bulldog said:**
> Can you give us the output of this command```
sudo fdisk -l
``` it's a lowercase L not a one.
You can perform this command from a terminal in a live cd session.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       27810   223383793+   7  HPFS/NTFS
/dev/sda2   *       27811       38535    86148562+  83  Linux
/dev/sda3           38536       38913     3036285    5  Extended
/dev/sda5           38536       38913     3036253+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       21080   169325068+   7  HPFS/NTFS
/dev/sdb2   *       21081       30023    71834647+  83  Linux
/dev/sdb3           30024       30401     3036285    5  Extended
/dev/sdb5           30024       30401     3036253+  82  Linux swap / Solaris

Disk /dev/sdc: 502 MB, 502267904 bytes
32 heads, 32 sectors/track, 958 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         958      490479+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(956, 31, 32) logical=(957, 31, 31)
ubuntu@ubuntu:~$

---

### Post by gugin on 2007-04-21
So I have changed the boot flag to sda. That didn't work. I reinstalled windows. No that didn't work either. It looks like my mbr is corrupted. I created a new mbr. It still won't boot into an OS.

---

### Post by alexlex on 2007-04-21
it really sounds like a problem with bios or hard drive. if you reinstalled windows it would of completely rewritten the mbr even fixmbr command would have done the same thing

---

### Post by gugin on 2007-04-21
> **alexlex said:**
> it really sounds like a problem with bios or hard drive. if you reinstalled windows it would of completely rewritten the mbr even fixmbr command would have done the same thing

Yeah I agree, but I've never had a problem until I installed Feisty. I defaulted the BIOS.  I pulled the HD. Now I'm going to install windows on a new hd.

---

### Post by Dolphin on 2007-04-21
Same thing happened to me.
Try putting one of your other drives in higher boot priority.
Even though I installed Ubuntu on sda, the automated installer stuck GRUB on hda for some weird reason.  So I just put hda on higher boot priority.

---

### Post by z1p101 on 2007-04-22
From what you posted your windows partition is not flagged as boot which causes problems most  of the time.
I think with he live disk you should be able to change it. Type sudo fdisk /dev/sda and I think the command is a to change boot flag.

also you have a lot of drives going on here so with the live cd, with what you posted should be sda2,  look at the /boot/grub/grub.conf file and that will tell you where the system is looking for each OS. Post it if you can

---

### Post by gugin on 2007-04-23
> **z1p101 said:**
> From what you posted your windows partition is not flagged as boot which causes problems most  of the time.
I think with he live disk you should be able to change it. Type sudo fdisk /dev/sda and I think the command is a to change boot flag.

also you have a lot of drives going on here so with the live cd, with what you posted should be sda2,  look at the /boot/grub/grub.conf file and that will tell you where the system is looking for each OS. Post it if you can

Man. I don't know what to do. I pulled out all three HD's. I put one back in. It wasn't  the former primary hd, but  a different hd. I deleted the ubuntu partitions and installed windows. On reboot I get "disk read error cntrl at del to reboot" I never had a problem with this pc until I installed feisty. My PC is dead. I have data on all 3 hd's that I need, so I can't format. I went back into the bios and tried to find a reason to this madness. I defaulted the bios again thinking that might do some good, but it didn't. Feisty runs good on my laptop, so does windows.

---

