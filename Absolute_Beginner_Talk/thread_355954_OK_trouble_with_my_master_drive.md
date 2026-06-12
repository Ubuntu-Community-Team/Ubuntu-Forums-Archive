---
title: "OK trouble with my master drive"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by timmins on 2007-02-07
OK, here is my situation, Ihave my 160 GB master drive and my 40GB slave drive, where my system is stored. I have just installed ubuntu edgy, and I am attempting to mount my 160GB  drive with all of my media files. 

I have followed these directions:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

and under Gparted it says that my 160 gigger is an ext3 extension.

but when I type in: sudo fdisk -l  I get this:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19457   156288321    7  HPFS/NTFS

which says it is ntfs.

I was able to access these files before using UBUNTU 6.06 without ntfs-3g.

Can someone please tell me how to mount this volume or direct me to a thread that will tell me how to mount it?

Thanks very much.
-Kyle

---

### Post by timmins on 2007-02-07
to the top^

---

### Post by timmins on 2007-02-07
Any links would be much apppreciated.

Thanks
-Kyle

---

### Post by confused57 on 2007-02-07
Maybe something on this mounting "howto" will help:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by timmins on 2007-02-07
Thanks, I'll check it out and get back to you when I figure it out.

Thanks
-Kyle

---

### Post by timmins on 2007-02-08
I'm having trouble with the tutorial you gave me,It seem to be only fluent with 6.06. does anyone else have in ideas for an idiot novice?

Thanks

---

### Post by timmins on 2007-02-08
Hi, I've selected me mount point to be /home/kyle/My\Media/, can someone direct me to the next step either in the tutorial or here? I'm running edgy based of my 40GIG slave HD.

Thanks

---

### Post by confused57 on 2007-02-08
Is this the tutorial you followed?:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu](http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu)

What happens when you click on "Places", then "Home Folder", is there a "My Media" folder?

I've never heard of having a device mounted in a directory in the home directory, so don't know if it'll work or not.

Did you happen to partition your 160 Gb drive with something like Partition Magic?   Sometimes PM & Linux don't get along too well.

I've never had any trouble mounting a partition in the /media or /mnt directories...I have a data parition mounted in /media, which I have automatically mounted by adding a line to /etc/fstab...an icon for the drive is placed on the desktop.

---

