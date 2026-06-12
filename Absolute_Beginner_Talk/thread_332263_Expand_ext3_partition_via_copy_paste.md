---
title: "Expand ext3 partition via copy paste?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Skidlz on 2007-01-05
I have an 80gb hd with an x-windows ntfs partion and an ext3 partition with ubuntu on it. The ntfs(70g ) was not reformated I just deleted everything off it and Im willing to do what ever with it. Its the classic "I want to make my ubuntu partition bigger" because I only made it 6gb. Can I just srink the ntfs, make a new ext3, copy the original ext3 to  it, delete the original and be done? I have read other how tos on it but they seem to have some useless steps.

Will this work :confused:  or am I missing something? ](*,)

Thank You!

---

### Post by Bachstelze on 2007-01-05
Yes, that should work, I remmember having done it once. You'll need to edit your fstab and GRUB config so it uses the new partition instead, that's all :)

---

### Post by bodhi.zazen on 2007-01-05
You should be able to do that with gparted:

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

But you could also format the ntfs partition to ext3 (or what have you) and mount it in say 

/media/data

---

### Post by Skidlz on 2007-01-05
Ok im using the disk as a live cd and editing the partitions that way. Should do what I do what I sayd before but not delete my current partition, reboot and use my old partition, then use ```
sudo gedit /etc/fstab
```
and do what exactly? What do I write so it sees the new partition as the filesystem?
Then ```
sudo gedit /boot/grub/grub.conf
``` ? and again what do I edit there?
If do manage to boot from my new partition is is safe to dele the old one?

Im more of a big picture person/noob I guess.

Thanks again.

---

### Post by bodhi.zazen on 2007-01-05
If you move your ubuntu root partition you will need to update both /boot/grub/menu.lst and /etc/fstab.

Here is an example:

[http://www.ubuntuforums.org/showthread.php?&t=316237](http://www.ubuntuforums.org/showthread.php?&t=316237)

---

### Post by Bachstelze on 2007-01-05
No, you need to edit them from within your live CD because if you don't you won't be able to boot your system.

Just to whatever you want with your partitions. Then :

```
sudo fdisk -l
```

to find out what your root partition is, for example on my system it gives :

```
/dev/hda1               1           8       64228+  83  Linux
/dev/hda2               9        1224     9767520   83  Linux
/dev/hda3   *        1225        2440     9767520   a5  FreeBSD
/dev/hda4            2441       14593    97618972+   5  Extended
/dev/hda5           14532       14593      498015   82  Linux swap / Solaris
/dev/hda6            2441       14530    97112862   83  Linux

```

Find out what your root partition is (/dev/hda2 for me), create a mountpoint for it :

```
sudo mkdir /mnt/root
```

mount it

```
sudo mount -t ext3 /dev/hda2 /mnt/root
```

and edit your files to match the new setup :

```
sudo nano /mnt/root/etc/fstab
sudo nano /mnt/root/boot/grub/menu.lst
sudo reboot
```

---

### Post by Skidlz on 2007-01-05
My new partition is /dev/hdb3 in grub do I change
```

title           Ubuntu, kernel 2.6.17-10-386
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=4ba408bf-86f5-4983-993e-ab3a148935de ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot

```
to
```

title           Ubuntu, kernel 2.6.17-10-386
**root            (hd3,1)**
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=4ba408bf-86f5-4983-993e-ab3a148935de ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot

```

---

### Post by bodhi.zazen on 2007-01-05
> **Skidlz said:**
> My new partition is /dev/hdb3 in grub do I change ...


Use this:
> title           Ubuntu, kernel 2.6.17-10-386
root            **(hd1,2)**
kernel          /boot/vmlinuz-2.6.17-10-386 **root=/dev/hdb3** ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot

---

### Post by Skidlz on 2007-01-06
Should I do this under ubuntu from hd not livecd? I did this under livecd and it had no effect.

---

### Post by bodhi.zazen on 2007-01-07
You must update /boot/grub/menu.lst on your ubuntu partition. 

If you can boot ubuntu , well no problems then. If not you will need to use the live CD

---

