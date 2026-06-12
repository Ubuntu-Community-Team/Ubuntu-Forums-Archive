---
title: "Dual Booting, Help."
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by steelroots on 2005-12-01
I just installed Ubuntu.

I partitioned a section of my C drive so it could install and it works.

THe problem:

How do I dual boot? I still need windows and I don't know how to load it.

---

### Post by Robgould on 2005-12-01
Have you installed Ubuntu yet?  if not, just run the cd.  It will install grub at the end.  Grub will give you a menu when you log on to choose windows or ubuntu.

---

### Post by steelroots on 2005-12-01
[QUOTE=Robgould]Have you installed Ubuntu yet?  if not, just run the cd.  It will install grub at the end.  Grub will give you a menu when you log on to choose windows or ubuntu.[/QUOTE]


Yes I have installed it, how would I run grub? I searched my computer but it's not loaded on there?

PS: Thanks for the quick reply

---

### Post by Robgould on 2005-12-01
Have you re-booted yet?  Grub was installed on your master boot record.  When you reboot the computer you will get an option every time as to which system you want to use.  Have you rebooted yet?

---

### Post by Vlammetje on 2005-12-01
You wouldn;t need to 'run' it. Grub should be installed in your Master Boot Record and when you restart your computer it should offer you the choice of installed OS's during boot sequence. Have you tried it yet?

I assume you have a separate partition or drive that still holds your Windows install? I found that for me it was necessary to have Windows installed, then install Ubuntu with Grub and all works dandy for me.

---

### Post by meStrike on 2005-12-01
I installed windows and Ubuntu by installing linux on one partition while creating an fat32 one for windows. Then I installed widows on the fat32 and then windows worked but not linux. I installed linux again on its partition and i finaly got it to work. Not to efficeint but it works!

---

### Post by Robgould on 2005-12-01
normally you have to install linux second.  Installing windows will kill grub.

---

### Post by patrick295767 on 2005-12-02
The best is to reinstall the Grub.
For my point of vue,  it's workign better than the old Lilo ...

---

