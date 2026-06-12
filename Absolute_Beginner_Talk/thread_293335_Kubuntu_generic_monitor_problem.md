---
title: "Kubuntu generic monitor problem"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by CroEragon on 2006-11-05
I just started with Kubuntu and made stupid mistake and i need help to solve it!

I installed Ubuntu 6.10 (dual-boot with XP) this morning everything went good except printer (Brother, i actually do not care) and screen resolution. I have about 5 years of experience with Windows, mainly XP but a bit with ME. After presentation of speech recognition software, anti piracy measures and "Blue pill" on Vista i decided to take better look at Linux especially Ubuntu. 
After installation i couldn't adjust resolution. It was stuck on 600x400. I don't like GNOME so i installed KDE (sudo aptitude kubuntu-desktop or similar command, im not sure)) and resolution problem remained (i expected that). So i changed my monitor in settings and made really silly mistake. I change it on resolution wich my LCD cannot show. I rebooted and then understood what i did. Now when i try to choose Linux in GRUB menu it shows message "Out of Bound" and stays like that. A have some knowledge about Windows command line but absolutely no kowledge about Linux commands. 
How can i change my monitor to previous one so i can choose the correct one?
Wich command should i use?
Or can i boot Knoppix to change some text file or use FS-Drive to do same from Windows?
I ran out of options that i know.
Can you help?
Thanks in advance.

---

### Post by Ecthelion on 2006-11-05
To reconfigure your xserver do

```
sudo dpkg-reconfigure xserver-xorg
```

Follow the steps and be carefull to set the right resolutions and refresh rates....

---

