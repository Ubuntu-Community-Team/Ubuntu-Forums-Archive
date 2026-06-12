---
title: "on macbookpro 5,2 stopped working"
date: 2010-03-01
forum: Apple Hardware Users
---

### Post by extralooping on 2010-03-01
hello,
ubuntu on my macbook pro 5,2 suddenly stopped working. all i get after rEFIt is a "GRUB" message with a blinking underscore and no reaction at all. i think before that happended i did some tests with opencv camera capture and installed the nvidia gfx drivers. after a reboot it stopped working..

i have no clue what do to besides reinstalling ubuntu (again :-/)...

please help

---

### Post by linuxopjemac on 2010-03-01
I assume your disk is /dev/sda , default for macbooks, and your root partition is /dev/sda4 , adapt these if necessary! )

1) Download an Ubuntu Live CD ( see [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD) ) and burn the ISO to CD.

2) Boot your macbook from the CD

3) Open a terminal, mount your original root partition

```
sudo mkdir /mnt/root
sudo mount -t ext4 /dev/sda4 /mnt/root
```


4) Set up /proc and /dev

```
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
```

5) Chroot into your original system, you're now in your own system.

```
sudo chroot /mnt/root /bin/bash
```


6) Reinstall grub (this shouldn't overwrite rEFIt, but you can keep a copy of rEFIt on CD if you're concerned)

```
sudo grub-install /dev/sda
```

10) reboot, 

11) Sync the partition table within rEFIt

12) reboot
the system should be able to boot again now (hopefully)

PS MAKE BACKUP OF ALL IMPORTANT DATA

---

### Post by extralooping on 2010-03-01
when reinstalling grub it says that
there no BIOS boot partition and thus embedding is not possible and its using blocklists which are unreliable, but after reboot evrything seemsto work.

thanks a lot

---

