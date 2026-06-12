---
title: "Wrong Kernel is chosen on Reboot...How to change?"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-04-15
I have 3 kernal options when I go into GRUB on a reboot.  They are listed in the wrong order, the i386 one is the 2nd choice and I have to manually go into GRUB and choose this kernal or the wrong one is chosen.  How can I change the kernal boot order?

---

### Post by aysiu on 2007-04-15
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by kc5hwb on 2007-04-16
This file is blank....
```
gksudo gedit /boot/grub/menu.lst 
```

Here is the ls cmd in the /boot/grub dir

```
root@SAMSON:/boot/grub# ls
default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5       reiserfs_stage1_5
e2fs_stage1_5  menu.lst           stage1
fat_stage1_5   menu.lst~          stage2

```

---

### Post by kc5hwb on 2007-04-17
Should this file be blank?  The link above indicates that there should be some lines in this file that I need to change.

---

### Post by Bachstelze on 2007-04-17
No, the file isn't supposed to be blank. Try to reinstall GRUB first :

```
sudo grub-install /dev/hda
```

(assuming you want to install it on the MBR of /dev/hda of course)

---

### Post by kc5hwb on 2007-04-17
Actually this guy is a SATA150 drive, so it sees it as SDA1.

I ran this command and got no errors.  The changed the option to 2, rebooted and it worked great.

Thanks

---

