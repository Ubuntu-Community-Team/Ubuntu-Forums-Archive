---
title: "GRUB error"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by YodaMstr on 2008-02-03
Hey all, I've got a friend who's giving Ubuntu a spin.  Well, problem is, he couldn't get GRUB to install and it froze his install.  So I suggested he install sans GRUB, and then come back later with superGRUB.  However, superGRUB apparently returns a "file not found" error when he tries to install.  Any help?

Edit:  He has two internal HDDs if this is of any significance.

---

### Post by YodaMstr on 2008-02-03
bump

---

### Post by spiderbatdad on 2008-02-03
try using noapic nolapic vga=771 options at install options screen. Also, does his system meet minimum requirements? Perhaps the alternate cd would work if the above parameters don't

---

### Post by phidia on 2008-02-03
The system specs including the output of fdisk -l (run from live cd) would be helpful.
He can also try to use the live cd to re-install grub.
Was one of the  drives unplugged or their positions changed during the install?

---

### Post by YodaMstr on 2008-02-03
@spiderbat:  Is that on the SuperGRUB CD, or Ubuntu LiveCD?

@phidia:  I'm getting him to go on his LiveCD right now.  I've had some bad experiences trying to install GRUB from the LiveCD, so if there's an alternative, it'd be nice.

---

### Post by YodaMstr on 2008-02-03
```
Disk /dev/sda: 40.0 GB, 40016019456 bytes

255 heads, 63 sectors/track, 4865 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x05740574



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        1216     9767488+   7  HPFS/NTFS

/dev/sda2            1217        4864    29302560    f  W95 Ext'd (LBA)

/dev/sda5            1217        4864    29302528+   7  HPFS/NTFS



Disk /dev/sdb: 120.0 GB, 120034123776 bytes

255 heads, 63 sectors/track, 14593 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x11af4710



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS
```

---

### Post by YodaMstr on 2008-02-04
I'm pretty sure we could get it to work if we could get the /boot folder onto his Ubuntu install.  We could SuperGRUB the rest, I imagine.  Any ideas?

---

### Post by tosk on 2008-02-04
As far as I'm aware, GRUB won't install on NTFS. You need a Linux partition for GRUB to store it's files.

---

### Post by spiderbatdad on 2008-02-04
[QUOTE=YodaMstr;4264783]@spiderbat:  Is that on the SuperGRUB CD, or Ubuntu LiveCD?


F6 option on the ubuntu live cd at the install options screen. Delete the end of the kernel line up to and including ro --quiet splash, replace with noapic nolapic vga=771 BTW XP should be freshly defragged before installing ubuntu...though of course you can run the live cd without doing so.

---

### Post by oedha on 2008-02-04
may i ?
error 21 means that your linux was deleted ( if i am not wrong )
to fix this....you need windows installation cd.....and go to recovery mode
then fixboot, fixmbr
by looking at your fdisk....i didnt see linux partition....

regards;
~E~

---

### Post by Squatsandmilk on 2008-02-05
Hi guys, I'm Yodamstr's friend that he's talking about.

When I'm installing Ubuntu, I format my 30gb partition on hd0 to ext3, and then install it to there.  I normally uncheck "Install bootloader", as per Yodamstr's instructions to me (If I do have Ubuntu try to install it, it will give me an error saying something about grub-install failed.)  After this is done, I reboot my computer on the SuperGRUB cd.  While I'm trying to install SGD, I continually get an error stating "Error 15: File not found."  I believe yesterday I even got an Error 12, but I can't recall if that was the right number or not.

I have tried all of the suggestions that have been posted in the thread.  When I altered the Linux Kernel, all it did was bring me to a black screen, and I had to restart my computer.

Any further help is greatly appreciated.

---

### Post by phidia on 2008-02-06
> **Squatsandmilk said:**
> Hi guys, I'm Yodamstr's friend that he's talking about.

When I'm installing Ubuntu, I format my 30gb partition on hd0 to ext3, and then install it to there.  I normally uncheck "Install bootloader", as per Yodamstr's instructions to me (If I do have Ubuntu try to install it, it will give me an error saying something about grub-install failed.)  After this is done, I reboot my computer on the SuperGRUB cd.  While I'm trying to install SGD, I continually get an error stating "Error 15: File not found."  I believe yesterday I even got an Error 12, but I can't recall if that was the right number or not.

I have tried all of the suggestions that have been posted in the thread.  When I altered the Linux Kernel, all it did was bring me to a black screen, and I had to restart my computer.

Any further help is greatly appreciated.

Where are you on this situation now?

If it's not working at all (no boot) than I think a good plan is to try to install grub from a live cd or the alternate cd.

The booting guide [here]("https://wiki.ubuntu.com/Booting") could be useful.

---

