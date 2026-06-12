---
title: "Files in root directory"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by V-600 on 2007-02-28
Having been looking online trying to figure out the linux file structure one common theme has occured. In the root directory (/) there should only be sub-directory's and not loose files.

The output for  ls -p is as follows:

nathan@nathan-desktop:/$ ls -p
bin/   etc/        initrd.img.old  mnt/    root/  tmp/     vmlinuz.old
boot/  home/       lib/            opt/    sbin/  usr/
cdrom  initrd/     lost+found/     proc/   srv/   var/
dev/   initrd.img  media/          pup001  sys/   vmlinuz

I know pup001 is a file placed there by puppy linux to save settings. However i have a few things like "vmlinuz" and "cdrom" present. In the terminal they show up as light blue.

Are they doing any harm there and can/should I delete them.

---

### Post by x1a4 on 2007-02-28
initrd.img.old
vmlinuz.old

Symlinks to kernel images of your previous version of the kernel, they will be removed when you remove the old version of the kernel--otherwise leave alone.  

vmlinuz
initrd.img

Symlinks to your current kernel--**leave them alone**.

---

