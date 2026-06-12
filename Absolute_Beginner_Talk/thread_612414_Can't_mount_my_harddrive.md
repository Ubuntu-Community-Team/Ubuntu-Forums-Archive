---
title: "Can't mount my harddrive"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by karl-arthur on 2007-11-13
Hi,

I'm afraid I did some serious damage to my system, and now I'm unable to mount my harddrive. The details of what I did can be read here: [http://ubuntuforums.org/showthread.php?t=572437](http://ubuntuforums.org/showthread.php?t=572437) , but to make a long story short, I ran a fsck -a, ignoring the stern warning, because, well, I'm not that smart. 
So now I get a Grub error 17 when booting, which I've been unable to do anything about, as it seems the Grub fix posts in this forum supposes a mounted harddrive (the nerve!). 

Anyway, all I really need, is to get access to my home folder, so I can make a backup and reinstall. So I tried this, booting from a live CD:

ubuntu@ubuntu:/$ sudo mount -t ext3 /dev/sda1 /media/old
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:/$ dmesg | tail
[  150.136000] Bluetooth: L2CAP socket layer initialized
[  150.484000] Bluetooth: RFCOMM socket layer initialized
[  150.484000] Bluetooth: RFCOMM TTY layer initialized
[  150.484000] Bluetooth: RFCOMM ver 1.8
[  215.500000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  230.744000] eth1: no IPv6 routers present
[  767.956000] cramfs: wrong magic
[  767.972000] Unable to identify CD-ROM format.
[  767.976000] SQUASHFS error: Can't find a SQUASHFS superblock on sda1
[  827.556000] VFS: Can't find ext3 filesystem on dev sda1.

So it seems Ubuntu can't recognize the filesystem, but I'm sure it's supposed to be ext3. Any suggestions?

---

### Post by taurus on 2007-11-13
What's the output of this command from a terminal from the LiveCD?

```
sudo fdisk -l
```

---

### Post by karl-arthur on 2007-11-13
ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

---

### Post by taurus on 2007-11-13
What if you don't include the filesystem when you try to mount it.

```
sudo mkdir /media/old
sudo mount /dev/sda1 /media/old
```

---

### Post by karl-arthur on 2007-11-13
Thanks for the tip, but I already tried that:

ubuntu@ubuntu:/$ sudo mount /dev/sda1 /media/sda1
mount: you must specify the filesystem type

---

### Post by taurus on 2007-11-13
Try using GParted LiveCD and see if you can mount /dev/sda1 with it.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by TheIrishGuy on 2007-11-13
its most likey bust, but on the off chance, you can reinstall grub if you can manage to mount the filesystem.

when mounting increment the number 1,2,3,4 etc and see if you can get anything to mount and see if thats the partition you want

umount /dev/sda1 will unmount it

sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda6 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub
find /boot/grub/stage1

*note
----------------------------
if it finds it ie.
It found mine on (hd0,5)
-------------------------------

root (hd0,5)
setup (hd0)

---

### Post by karl-arthur on 2007-11-13
I'll do that once I get a chance to burn it (kind of hard when I'm already running a live CD), but it didn't work from a Knoppix CD either (Roughly the same error msgs). But thanks for your very quick help.

---

### Post by karl-arthur on 2007-11-13
Hmm, it seems sda5 is already mounted, but I wouldn't find the home folder there, would I? And I don't know the mount point. Is it possible I might be able to reinstall grub from sda5?

---

### Post by TheIrishGuy on 2007-11-13
cd /media/sda5

ls


if you see a whole load of folders like

bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz

proceed with steps above

---

### Post by karl-arthur on 2007-11-13
Not looking very good:

ubuntu@ubuntu:/$ sudo mount -t ext3 /dev/sda5 /media/old
mount: /dev/sda5 already mounted or /media/old busy
ubuntu@ubuntu:/$ umount /dev/sda5 
umount: /dev/sda5 is not mounted (according to mtab)
ubuntu@ubuntu:/$ sudo mount /dev/sda5 /media/old
/dev/sda5 looks like swapspace - not mounted
mount: you must specify the filesystem type
ubuntu@ubuntu:/$ cd /media/sda5
bash: cd: /media/sda5: No such file or directory

---

### Post by PhilipOwrutsky on 2008-06-20
I just did an update this morning (June 20, 2008 ), which required a restart.  Doing so brings me to the grub loader, which now has two pairs of ubuntu entries instead of my usual 1 set (1 for generic and 1 for recovery).  Trying any (generic or recovery) results in a can't mount drive error.  Interestingly, my vista partition still boots (irony??)...Im going to try reinstalling grub now, but I seem to recall having difficulty doing this in the past because Im on a T61 thinkpad with nvidia card that doesn't play well with the live cd (doesn't display).  Thanks in advance for any guidance.

-Phil

---

### Post by PhilipOwrutsky on 2008-06-20
Ok so I fixed the problem.  For some reason the update had my grubloader looking at the wrong partition (hd0,2) instead of (hd0,1).  Making the appropriate changes solved the problem.  No idea if Im an isolated case with this update or not, but its straightforward to fix.

Phil

---

