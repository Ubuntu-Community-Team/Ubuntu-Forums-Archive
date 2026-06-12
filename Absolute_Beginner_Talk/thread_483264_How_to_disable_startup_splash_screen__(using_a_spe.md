---
title: "How to disable startup splash screen ? (using a specific software)"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by tempuraaddict on 2007-06-24
During my first installation of Feisty on my T41 I was able to install an application, either via automatix or the built in add-remove feature I cant remember anymore. 

The said software was listed under System/Administration. It allowed me to disable the startup splash screen and dictate the screen resolution for the text output of the ubuntu startup screen.

This is my 2nd installation of Feisty and I cant remember how to install the said software feature as I cannot remember its name. (2nd installation is using the entire hard disk, my first was having to dual boot with XP)

Would appreciate any help. Thanks.

---

### Post by BobCFC on 2007-06-24
if you are using GRUB you can set options at boot time.   Open the grub config as root such as


```
gksudo gedit /boot/grub/menu.lst
```


scroll down and find the entry you normally use..    change **splash** to **nosplash** and add **vga=795** to start console in 1280x1024x32

There are other options for vga but I think that is the highest.


You can also delete quiet to get even more info if you are having problems.

---

