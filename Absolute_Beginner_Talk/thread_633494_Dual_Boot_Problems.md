---
title: "Dual Boot Problems"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by dr_alejandro on 2007-12-06
I recently upgraded my computer. 

Before
I used to have two HD one with XP and one with Ubuntu 7.10. When the computer started it would ask whether I want to run linux or windows. Now I also 

Now
I have 2 HD,  a new SATA HD with XP installed in it and on HD with linux in it.
The linux HD is still the same I had before.

The problem is that when the computer starts it goes directly to Win XP.
I am able to boot linux using a "Super GRUB Disk" i'm not if you are familiar with that. It simply lets you specify what HD you want to boot. Using this disk linux boots just fine. All the files and customizations I had before are there. Without the disk the computer goes to Win XP directly.

I would like to have the option to boot either one of the OS and boot linux without the disk.

Can somebody help me?

I already tried this:

-----------------------------------------------------------------------------------
grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 
-----------------------------------------------------------------------------------

But still Windows boots without giving me an option.

Here is a printout of fdisk (I hope is useful )


-----------------------------------------------------------------------------------
angel@mofongo:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x020a020a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02b902b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9587    77007546   83  Linux
/dev/sdb2            9588        9964     3028252+   5  Extended
/dev/sdb5            9588        9964     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc07d6ede

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    c  W95 FAT32 (LBA)
angel@mofongo:~$ 

-----------------------------------------------------------------------------------

Here is my menu.list file


-----------------------------------------------------------------------------------
title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=b478e835-00a0-4c17-84f4-3ac226046469 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=b478e835-00a0-4c17-84f4-3ac226046469 ro single
initrd        /boot/initrd.img- 2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
-----------------------------------------------------------------------------------

Thanks

---

### Post by StephUb on 2007-12-06
By using a new HD for XP you removed the grub...
So the idea..
Reinstall grub from linux on the new SATA drive windows..

---

### Post by dr_alejandro on 2007-12-06
By the way, if you look at the fdisk print out

the 320 GB is the new HD with Win XP, the 80 GB HD is the one with Ubuntu 7.10, and the 160 GB is an external HD just to store my files for backup.

Thanks

---

### Post by MQMike on 2007-12-06
grub> find /boot/grub/stage1
(hd1,0)

grub> root (hd1,0)

grub> setup (hd1)

You are very close!
You want

setup (hd0)

That is, you want to install the GRUB from the Ubuntu partition (hd1,0) to the Master Boot record of the Windows drive, which is (hd0).

(BTW, SGD may be able to fix GRUB for you, too), but try it with setup (hd0).

---

### Post by dr_alejandro on 2007-12-06
Thanks for the quick reply!

How do I install GRUB in the new HD?
Which directory do I intall it?

---

### Post by Swmmrman on 2007-12-06
If they are on 2 separate drives.  You may need to make sure the HDD boot order in the BIOS is right.   Forgot this once myself.

---

### Post by StephUb on 2007-12-06
Just remove Windows... No i am kidding.
Maybe you can switch also the master and boot on your ubuntu disk (were grub is in fact...)

---

### Post by MQMike on 2007-12-06
If you just run:

root (hd1,0)
setup (hd0)
quit

re-boot to test it, that will install GRUB to the MBR of the hd0 drive.  GRUB will be installed to the first sector (512 Bytes) of the drive; i.e., to the MBR (and Stage_1.5 will be installed after that, and Stage_2 in (hd1,0)).  You don't have to do anything else, just those 3 commands (above).

---

### Post by dr_alejandro on 2007-12-06
Thanks I'll try that as soon as I get home.

Yes, I tried to fix it with SGD but i did not work. I simply choose and option that said "fix boot .... someting". Since I didn't now what I was doing I stopped there. But I'm sure you can fix it with the disk.

Thanks,
I'll let you known what happens.

---

### Post by MQMike on 2007-12-06
What you did previously will not hurt anything.  That is, you used setup (hd1), and so now you have GRUB setup in both the MBR of hd0 and the MBR of hd1.  But since the Windows drive is set to boot first (in BIOS), everything will work fine.  If you ever need GRUB to boot the second drive hd1, then you already have GRUB set up in its MBR – that is, no harm done.  (You can now actually chainload your hd1 drive if you ever wanted to, but that’s another story).

---

### Post by dr_alejandro on 2007-12-06
The dual boot is working just fine now.

grub> find /boot/grub/stage1
(hd1,0)

grub> root (hd1,0)

grub> setup (hd0)

grub> quit

Thank you guys!!

---

### Post by MQMike on 2007-12-06
Glad you solved it!

here's some of my stuff, fyi:
(aka Qqmike)
How To Make GRUB Thumb Drive
[http://kubuntuforums.net/forums/index.php?topic=3081748.0](http://kubuntuforums.net/forums/index.php?topic=3081748.0)
(and all the many posts under it--various How-To's)

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(several topics under it, too)

A standard, of course, is Herman's:
Bigpond, home:   [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
which you probably have.

---

