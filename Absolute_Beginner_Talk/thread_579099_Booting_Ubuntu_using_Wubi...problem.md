---
title: "Booting Ubuntu using Wubi...problem"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by tiger07 on 2007-10-17
I have used wubi to boot unbuntu and the first time that i started it up i got a blank screen that was black after the ubuntu loading screen.  I eventually turned it off but it had sat blank for probably 10 minutes.....any suggestions?

---

### Post by overdrank on 2007-10-18
> **tiger07 said:**
> I have used wubi to boot unbuntu and the first time that i started it up i got a blank screen that was black after the ubuntu loading screen.  I eventually turned it off but it had sat blank for probably 10 minutes.....any suggestions?

HI and welcome, could you give us some specs on the system? Memory, video,

---

### Post by tiger07 on 2007-10-18
I have a Vista based AMD Turion X2 TL-52 computer.
2 GB ram
6150 NVIDIA Graphics card....128 dedicated and 256 shared memory

---

### Post by overdrank on 2007-10-18
> **tiger07 said:**
> I have a Vista based AMD Turion X2 TL-52 computer.
2 GB ram
6150 NVIDIA Graphics card....128 dedicated and 256 shared memory

Hi three have been some issue with that video card. I myself have not used Wubi so I don't know if this will work. When you reach the black screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure xserver-xorg
``` and choose vesa as the driver and answer a few questions.If you don't know the answers then leave the default answer given.When complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

