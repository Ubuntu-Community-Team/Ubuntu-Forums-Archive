---
title: "Ubuntu/XP dual boot problem"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by drito on 2007-04-29
Hi, 
I have installed Ubuntu 6.06 on my laptop. After that I have installed Win XP. Then I tried to repair grub using:
sudo grub then find /boot/grub/stage1 etc. (I have found how to in this forum) After that I am not able to use any OS. I am getting: fsck.ext3: Bad magic number in super-block while trying to open /dev/hdc3 The super-block could not be read or does not describe a correct ext2 filesystem. Any help?

---

### Post by gary0 on 2007-04-29
Install XP first, then Ubuntu on another partition. Install Grub to the MBR on hd0 and it will detect XP and add it to its boot menu.

---

