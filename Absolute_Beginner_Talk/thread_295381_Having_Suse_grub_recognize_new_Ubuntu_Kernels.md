---
title: "Having Suse grub recognize new Ubuntu Kernels"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2006-11-08
I posted this same message on a suse forum but they aren't quite as fast as the guys (and girls) on this forum. Okay, basically I have Suse 10.1 and Ubuntu on the same system. I installed Suse on my system after I installed Ubuntu so the Grub that loads my system is the one for Suse. Because of this it doesn't automatically load new kernels when I upgrade Ubuntu. Can someone give me a step by step guide to editing the Grub loader to load my newest Ubuntu kernel or possibly when I tell it to load ubuntu it could go to the ubuntu grub where the kernel list is updated automatically.

---

### Post by bodhi.zazen on 2006-11-08
The way I do it is as follows:

[list=number][*]From Ubuntu, update your kernel.


[*]Open a terminal.


[*]mount your suse root partition.
```
sudo mkdir /mnt/suse  # if needed
sudo mount /dev/hdxy /mnt/suse
```

[*]Still in a terminal, identify your new (ubuntu) kernel```
ls /boot
``` It is the "vmlinuz" with the highest number.


[*]Still in a terminal, open /suse_root menu.lst:```
sudo gedit /mnt/suse/boot/grub/menu.lst
```
_Note_: That is a small "L" and not the number 1.
 

[*]Update the **kernel /boot/[color=red]vmlinuz-x.y.z[/color] in the Ubuntu stanza**

[*]Save and exit.[/list]

There may be a tool in SUSE to do just this, but last time I looked it was not automatic and it takes just as much time.

HTH 8)

---

### Post by mongooseman1128 on 2006-11-09
okay I get to the first command and this is what I get
```
charlie@charlie-desktop:~$ sudo mount /dev/hda2 /mnt/suse
Password:
mount: mount point /mnt/suse does not exist
charlie@charlie-desktop:~$ sudo mount /dev/hda2
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
when I rund dmesg the output that seems important is
```
 [17179953.368000] NTFS-fs error (device hda2): ntfs_fill_super(): Not an NTFS vo lume. 
```

---

### Post by bodhi.zazen on 2006-11-09
> **mongooseman1128 said:**
> okay I get to the first command and this is what I get
```
charlie@charlie-desktop:~$ sudo mount /dev/hda2 /mnt/suse
Password:
mount: mount point /mnt/suse does not exist
charlie@charlie-desktop:~$ sudo mount /dev/hda2
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
when I rund dmesg the output that seems important is
```
 [17179953.368000] NTFS-fs error (device hda2): ntfs_fill_super(): Not an NTFS vo lume. 
```

Sorry, you need to use an existing mount point (?/mnt/hda2)```
sudo mount /dev/hda2 /mnt/hda2
```

Or make the mount point first:```
sudo mkdir /mnt/suse
sudo mount /dev/hda2 /mnt/suse
....
```

---

