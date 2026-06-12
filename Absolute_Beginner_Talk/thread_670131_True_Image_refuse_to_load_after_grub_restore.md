---
title: "True Image refuse to load after grub restore"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by xena08 on 2008-01-17
I had ubuntu and vista in dual boot. After installing fresh copy of vista, naturally the grub wiped out. I restored it with this commands (mount my root partition using the livecd):

> sudo mkdir /mnt/root 
sudo mount -t ext3 /dev/sda6 /mnt/root
sudo mount -t proc none /mnt/root/proc 
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub
find /boot/grub/stage1It found mine on (hd0,5)
root (hd0,5)
setup (hd0)

Before that I could run Acoinis True Image through the Acronis rescue cd. Now I get a fatal error while trying to load the cd and True Image refuse to load from the cd.

anyone has an idea on how to fix that?

---

### Post by lswest on 2008-01-17
do you have more information on the error you get from loading the CD?

---

### Post by xena08 on 2008-01-17
I installed "Acronis Startup Recovery Manager" and now Acronis get into the Startup Recovery Manager but now the grub is missing again.

Damn! What is going on here?!

---

### Post by fiddledd on 2008-01-17
This might help you understand what is happening 

From Acronis Website:

> When Acronis Startup Recovery Manager is activated it overwrites the Master Boot Record (MBR) with its own boot code. If you have any third party boot managers installed, then you will have to reactivate them after activating the Startup Recovery Manager. For Linux loaders (e.g. LILO and GRUB) you might consider installing them to a Linux root (or boot) partition boot record instead of MBR before activating Acronis Startup Recovery Manager.

---

### Post by xena08 on 2008-01-17
How can I install grub to a Linux root (or boot) partition boot record?

Do I need to delete the Acronis loader?

---

### Post by maybeway36 on 2008-01-17
Instead of
```
setup (hd0)
```
do
```
setup (hd0,5)
```
Not sure if logical partitions (over #3) work, though.
If not you can also do
```
setup (fd0)
```
to a floppy.

---

### Post by xena08 on 2008-01-17
I see now.

How does it works? the grub should be installed in hd0,5 because?
what is so importent in this code? (say hd0,5 is the output)

> find /boot/grub/stage1

---

