---
title: "Ubuntu wont boot"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by aibradford on 2007-03-08
Im installing Ubuntu for the first time on my Toshiba laptop.
I partitioned my drive fine and everything seemed to go as it should. I installed GRUB to my (hda0,1) as that is the new linux partition i create to load the OS onto. 
When i reboot after everything has installed, i dont have a boot menu. It just boots directly back into windows like i nothing happened. 

Can someone help me out and explain how to get a bootloader to give me the option of what OS to start be it with GRUB or the windows bootloader. 

I have found many instances of articles online about windows not booting after installing Ubuntu, but it seems my problem is just the reverse. 

ANy help is much appreciated.

thanks

---

### Post by taurus on 2007-03-08
You should have installed GRUB to /dev/hda, /hd0, MBR.

---

### Post by aibradford on 2007-03-08
I see. Thats odd, because i was following instructions i found only and they specifically said not to load it to the MBR and onto my primary linux partition. I guess thats what I get for not getting instructions from this forum.

Do i need to reinstall the OS and put GRUB on (hd0) or is there a way to change this once i have installed it. 

thanks in advance.

---

