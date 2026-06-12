---
title: "[SOLVED] Installing over an existing installation"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by felin on 2007-11-01
Hi there, 
I have Ubuntu 7.10 x64 and windows xp dual boot installed on a computer. For several reasons (borked my xorg.conf / want to revert to 32 bit Ubuntu instead of x64) I would like to do a fresh installation of Ubuntu on the Ubuntu part of my hard drive. I am using 7.10 beta as I have that cd image already.

When I start the process i reach the partitioning stage and get stuck: It gives me options eg where do I want swap (sda?) - and am scared to continue in case I lose my xp partition. is there a guide for this - will I lose my ubuntu documents in current installation (don't mind losing them).

I have searched but cannot find a guide to this situation, so any general advice would be very appreciated.

Thanks

---

### Post by PmDematagoda on 2007-11-01
The architecture of the OS is no reason for a graphical failure. Could you please tell us your problems before changing to 32 bit from 64 bit.

---

### Post by hoges on 2007-11-01
If you already have 7.04, then there should already be a swap partition on the hdd. When you get to the partitioning stage, what do you see? You should have 3 partitions - ext3 for the installed ubuntu, sawp and ntfs windows.

Maybe post a screenshot as an example?

---

### Post by felin on 2007-11-01
> **PmDematagoda said:**
> The architecture of the OS is no reason for a graphical failure. Could you please tell us your problems before changing to 32 bit from 64 bit.

Hi there - thanks for this response - I have used ubuntu since dapper and love it - but have had more problems with x64 than any other installation - have used it for a long time now on one computer. I just feel that the processes required to get things to work in the 64 bit are (or have been) lengthy, and from being a daily visitor to the x64 part of this forum I see more problems than benefits - especially with third party stuff. So it's not really my messing up of the graphics that's set me on this path, but seeing this as an opportunity to change a system I'm not happy with.

[QUOTE=hoges]If you already have 7.04, then there should already be a swap partition on the hdd. When you get to the partitioning stage, what do you see? You should have 3 partitions - ext3 for the installed ubuntu, sawp and ntfs windows.

Maybe post a screenshot as an example?[/QUOTE]

Thanks for this - I will post one when I get home

---

### Post by PmDematagoda on 2007-11-01
I will admit that not everything works on 64 bit, but it is rather good and powerful, and the third party apps you are talking about could be installed by compiling the source or just by using "sudo dpkg -i --force-architecture nameof.deb"

---

### Post by felin on 2007-11-01
> **PmDematagoda said:**
> I will admit that not everything works on 64 bit, but it is rather good and powerful, and the third party apps you are talking about could be installed by compiling the source or just by using "sudo dpkg -i --force-architecture nameof.deb"
Thanks for your advice - I have taken it and fixed the graphics problem instead of reinstalling and it seems in the process that I have a newer version of the restricted driver - and things that didn't work seem to be working, so it was double sound advice! I have also tried the suggestion you made about installing stuff and it is working for me. Thanks.

These are my partitions, by the way, although I have no idea what they mean!!> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32105b60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12017    96526521    7  HPFS/NTFS
/dev/sda2           12018       23815    94767435   83  Linux
/dev/sda3           23816       24321     4064445    5  Extended
/dev/sda5           23816       24321     4064413+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff41a22f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39074616    c  W95 FAT32 (LBA)

---

### Post by PmDematagoda on 2007-11-02
Wait, is your GUI problem solved? If it is, then is there any necessity in reinstalling Ubuntu?

---

### Post by mikewhatever on 2007-11-02
>  Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32105b60

Device Boot Start End Blocks Id System
/dev/sda1 * 1 12017 96526521 7 HPFS/NTFS
/dev/sda2 12018 23815 94767435 83 Linux
/dev/sda3 23816 24321 4064445 5 Extended
/dev/sda5 23816 24321 4064413+ 82 Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff41a22f

Device Boot Start End Blocks Id System
/dev/sdb1 1 4865 39074616 c W95 FAT32 (LBA)


When you get to partitioning stage, choose manual. The 'difficult' part is to edit the mount points, so you may want to write these down.

/dev/sda1 -->/media/windows
/dev/sda2 -->/
/dev/sda5 -->sawp
/dev/sdb1 -->/media/storage

You can change the mount points for the first and last ones, but not the others.
Format /dev/sda2 only. You will loose all data on that partition.
To edit a mount point, right click on the partition.

---

### Post by felin on 2007-11-02
> **PmDematagoda said:**
> Wait, is your GUI problem solved? If it is, then is there any necessity in reinstalling Ubuntu?
Yes, as I said above I think that you have helped me avoid serious headaches with your very sound advice. Thank you very much.

---

### Post by PmDematagoda on 2007-11-02
Glad to hear your problem was solved:), but remember, don't use that command to install all the .debs, if there is a 64 bit version of that .deb, then use it since applications are not 100% guaranteed to work when this command is used.

---

