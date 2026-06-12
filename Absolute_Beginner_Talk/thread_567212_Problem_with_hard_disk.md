---
title: "Problem with hard disk"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by tkafik on 2007-10-04
I have 2 hard disk:
one for ubuntu and one for windows XP.
After i installet the ubuntu the hard disk with ubuntu doesnt appear and i cant use ubuntu.
someone said to me wrote in terminal in live cd:

sudo fdisk -l.

I wrote and this is the result:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2551    20490876    7  HPFS/NTFS
/dev/sda2            2552       20023   140343840    f  W95 Ext'd (LBA)
/dev/sda5            2552       20023   140343808+   7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9331    74951226   83  Linux
/dev/hdc2            9332        9729     3196935    5  Extended
/dev/hdc5            9332        9729     3196903+  82  Linux swap / Solaris

what the meaning?
what i need to do?

---

### Post by Yoooder on 2007-10-04
fdisk -l lists all the partitions of your harddrive, and in turn what OS is using what drives.

So you have 2 drives, 1 SATA 160GB (/dev/sda) with 3 partitions (sda1, sda2, sda5) and a PATA/IDE 80GB drive (/dev/hdc) with three partitions (hda1, hda2, and hda3).

What this tells us is that your machine does have a Linux drive as well as a Windows drive, and it appears that Linux was installed (or at least the filesystem was created).

Now for another question:  When you first turn on your computer, after it flashes either your PC information in text or a logo (the motherboard or PC manufacturer's usually) does the Windows XP "loading" screen appear right away?  Are they any other screens between the time you turn on the computer and before the Windows screen comes up?  For that matter, your machine is booting to Windows XP or is XP unavailable to you as well?

Depending on your response, what it sounds like to me right now is that you will need to tell your computer to boot from your 80GB drive, rather than the 160.  This is usually done by "Entering Setup" right after you press the power button on your computer, some computers also have a "Select Boot Device" option immediately after they are powered on.

---

### Post by tkafik on 2007-10-04
When i turn on the computer first time I saw black and the monitor wrote :"no signal"
i wait 2 hours and i did reboot.
After this reboot the windows come up.

How can I choose that the computer boot from the 80GB hard disk?

---

### Post by SpiritIsReality on 2007-10-04
howdy
This could be the case of the "grub , installed to the mbr, getting confused by a mix of sata, and pata/ide drives". Once I find a link or two, I'll post back here. Hopefully others who know better about it than I do will post long before I find something.
buds.

[http://www.google.ca/search?as_q=+sata+grub&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=ide+pata+&as_eq=raid&lr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images](http://www.google.ca/search?as_q=+sata+grub&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=ide+pata+&as_eq=raid&lr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images)
first link on the list should hopefully work.
hdc is the master on the secondary ide. secondary ide is usually used for cdroms.hdc and hdd.
could try to hook ide cable up to primary terminal, and the slave plug, making the hd recognized as  hdb.(switch pin on back of hd to slave)
then you would have sda and hdb.
then reinstall grub to sd0.
If the switching cables is not something you want to do right now, just leave it as is, try to reinstall grub to sd0.(sd zero)
pc repair online
[http://www.google.ca/search?hl=en&q=intitle%3Afree+intitle%3Abooks+%22pc+repair%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=intitle%3Afree+intitle%3Abooks+%22pc+repair%22&btnG=Google+Search&meta=)
[http://www.emu.edu.tr/english/facilitiesservices/computercenter/bookslib/Upgrading%20PCs%20Illustrated/](http://www.emu.edu.tr/english/facilitiesservices/computercenter/bookslib/Upgrading%20PCs%20Illustrated/)

---

