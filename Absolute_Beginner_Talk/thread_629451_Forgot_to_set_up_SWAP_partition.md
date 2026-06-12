---
title: "Forgot to set up SWAP partition"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by JacobRogers on 2007-12-02
I think I forgot to setup a swap drive when installing 7.10.  I've been running for some time now without much issues.  But I've been trying to trouble shoot getting suspend to work on my laptop and I was looking at the System Monitor and it doesn't show i have a swap file.

I know how to boot into gparted and create a swap partition, but after I do that is there anything I need to do to make my operating system recognize it?

Thanks in advance.

Screenshot of my System Monitor:
[IMG]http://i21.photobucket.com/albums/b270/zerokey2003/Screenshot-8.png[/IMG]

---

### Post by overdrank on 2007-12-02
Hi and my swap does not show there either but you could use this command ```
sudo fdisk -l
```
TO insure you have swap and if you don't this link may help
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
Good luck!

---

### Post by JacobRogers on 2007-12-02
Thanks for that,  here's what I get.  I guess maybe I do have a swap drive.  I remember making one...

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3673    29503341    7  HPFS/NTFS
/dev/sda2           12137       12149      104422+   e  W95 FAT16 (LBA)
/dev/sda4            3674       12136    67979047+   5  Extended
/dev/sda5           11786       12136     2819376   82  Linux swap / Solaris
/dev/sda6            3674       11785    65159577   83  Linux

Edit: that's hard to read.  Here's a screenshot:

[IMG]http://i21.photobucket.com/albums/b270/zerokey2003/Screenshot-1-3.png[/IMG]

---

