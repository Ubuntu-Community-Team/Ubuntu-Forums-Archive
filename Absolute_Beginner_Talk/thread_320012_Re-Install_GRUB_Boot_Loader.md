---
title: "Re-Install GRUB Boot Loader"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by mengd2002 on 2006-12-16
At present I am booting Ubuntu from a floppy disk.  I would like to re-install GRUB so it will boot from the MBR of the primary hard drive?  How would I go about doing this?  

Thank you,

Don

---

### Post by Bachstelze on 2006-12-16
1. Boot from a Live CD (Ubuntu's will work fine)

2. Become root : *sudo -i*

3. Create a mountpoint for your root partition : *mkdir /mnt/root*

4. Mount it : *mount -t ext3 /dev/whatever /mnt/root*

4b. If you have a separate /boot partition, mount it too : *mount -t ext3 /dev/whatever /mnt/root/boot*

5. Install GRUB : *grub-install --root-directory=/mnt/root /dev/whatever*

6. Reboot

---

### Post by Sef on 2006-12-16
Read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

---

### Post by confused57 on 2006-12-16
The easiest way I've found is using the live cd:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

