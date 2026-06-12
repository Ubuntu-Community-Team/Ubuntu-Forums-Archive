---
title: "NTFS Partition No Longer Mounted?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Volsfan91 on 2007-06-09
For some reason, my NTFS partiton (hda1) doesn't appear anymore. I don't think I did anything, but I did boot into Windows... what should I do? GParted says it's still mounted... but my apps don't read it. I've already enabled read/write support.

Sorry for bothering, BTW... I've asked some dumb questions since switching.

---

### Post by taurus on 2007-06-09
What happens if you try to mount it from a terminal to see if there is any error message?

```
sudo mkdir /media/hda1
sudo mount -t ntfs-3g /dev/hda1 /media/hda1
```
Also, make sure you shutdown your Windows properly first (no hibernation stuff) before you boot into Ubuntu.

---

### Post by Volsfan91 on 2007-06-09
Ah, it did complain about an unclean shutdown. So if I just start Windows back up and shut it down properly this time, it will auto remount?

taurus, thanks a lot... I really appreciate it.

---

### Post by taurus on 2007-06-09
Yes, it should.

---

### Post by djmaxmalta on 2007-06-09
its happenig to me but i shutdown properly but no error message and gparted says if i installed the appropiate plugin hello ntfs configuration tool from add/remove... from applicatrions and yes i did, but can't be mounted???? and the sudo code u gave us told me that both partions don't exist, actually no such file or directory how come and not even my external hdd could it be that ntfs-3g that i have from ubuntu's program installer is out dated???? and couseing a major security risk??? from windows section?


> **taurus said:**
> What happens if you try to mount it from a terminal to see if there is any error message?

```
sudo mkdir /media/hda1
sudo mount -t ntfs-3g /dev/hda1 /media/hda1
```
Also, make sure you shutdown your Windows properly first (no hibernation stuff) before you boot into Ubuntu.

---

### Post by Rocket2DMn on 2007-06-09
I ran into this problem this morning when I installed some updates and had to reboot.
in terminal type 
```
sudo fdisk -l
```
My windows partition started appearing as /dev/sda1 instead of /dev/hda1
It is some sort of glitch/error, but I just changed my /etc/fstab file to match until a fix is released.

---

### Post by djmaxmalta on 2007-06-09
> **Rocket2DMn said:**
> I ran into this problem this morning when I installed some updates and had to reboot.
in terminal type 
```
sudo fdisk -l
```
My windows partition started appearing as /dev/sda1 instead of /dev/hda1
It is some sort of glitch/error, but I just changed my /etc/fstab file to match until a fix is released.
yeah, but mine are all /dev/sda 1 to sda 5 cos i have 2 windows partions, 1 ubuntu root, 1 swap and 8 mbs free windows lol

but how can i mount? then now?

---

