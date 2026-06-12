---
title: "GRUB error 2"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by J216 on 2008-02-03
I just tried to load Ubuntu 7.10 on my windows machine. When i reboot It says "GRUB error 2". What is this and how do I fix it? I think I bit off a little more than I can chew here.

---

### Post by ichbinesderelch on 2008-02-03
> # 2 : "Selected disk doesn't exist"

This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

is the hdd listed in the device list on startup? maybe you should try reinstalling grub with the ubuntu-install cd.. [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

on which partition have you installed the bootloader? if its not in the mbr /dev/sda for example it could also be a problem with unclean shutdown of ntfs partition

---

### Post by rraj.be on 2008-02-03
i too have the same problem without any solution yet.

i had shutdown the windows in wrong manner and it lead to missing of ntldr file in my windows and when i reinstalled windows i am not getting the grub menu.
could any one help me?

---

### Post by ichbinesderelch on 2008-02-03
same thing for you, you need to reinstall grub, seems like windows messes up the mbr when installing it..

---

