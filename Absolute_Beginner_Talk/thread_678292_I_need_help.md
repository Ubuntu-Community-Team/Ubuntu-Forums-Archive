---
title: "I need help"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by gecko113 on 2008-01-25
i uninstalled Ubuntu 7.1o on my external hard drive and now once i boot up my laptop it says Grub error it went to 5 then to error 22 then error 21 n now i've followed this [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) but now instead of using the ext3 i changed it to ntfs and my vista is under my sda1 (sudo mount -t ntfs /dev/sda1 /mnt/root) then i typed up to "sudo mount -o bind /dev /mnt/root/dev" then i get a message mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

---

### Post by LaRoza on 2008-01-25
Use the Super Grub Disk to restore the MBR of the Laptop.

Install Grub on the external.

See the link in my sig.

---

