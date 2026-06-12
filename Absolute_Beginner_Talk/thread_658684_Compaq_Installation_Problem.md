---
title: "Compaq Installation Problem"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by customisbetter on 2008-01-04
iv got a compaq sr1800nx with ati graphics. after installing ubuntu the screen is hard to read and my monitor keeps saying that the resolution is not the recommended 1280x1024. i have it set to that in the preferences or whatever but th monitor keeps flipping out and shutting off. Whats the deal?
any help is appreciated.

---

### Post by overdrank on 2008-01-04
> **customisbetter said:**
> iv got a compaq sr1800nx with ati graphics. after installing ubuntu the screen is hard to read and my monitor keeps saying that the resolution is not the recommended 1280x1024. i have it set to that in the preferences or whatever but th monitor keeps flipping out and shutting off. Whats the deal?
any help is appreciated.

Hi and welcome, A quick search of the web shows  that system has the ATI x200m intergrated graphics. I have not had much luck helping with them but here goes
you can try and boot into recovery mode which is usually the second choice in the grub. Then reconfigure your xorg with this command ```
sudo dpkg-reconfigure xserver-xorg
``` Choose vesa as the driver and if you do not know the answers to the other question then leave as the default answer given. Then use the command ```
reboot
```  or ***startx*** and hopefully this will get you to a GUI, Desktop. Good luck.

---

### Post by customisbetter on 2008-01-04
i'm sorry but i did'nt understand any of that. Grub? Xorg?
this is my first attempt at linux.

---

### Post by overdrank on 2008-01-04
> **customisbetter said:**
> i'm sorry but i did'nt understand any of that. Grub? Xorg?
this is my first attempt at linux.

Ok the grub is the boot loader, if you dual boot with windows or others you should see the grub and let you choose which to boot too. If you are not dual booting then you will see the grub loading, so at that point you will use the esp key and then you should be able to choose recovery mode. Usually the second on the grub. The xorg is the file that configure your graphics and the command I gave you will allow you to reconfigure it. If you can see the screen good enough to enable your restricted driver you may try that under systems, administration, restricted drivers. Good luck!

---

### Post by customisbetter on 2008-01-05
thanks, i'll try that,  well, today. its 1 in the morning here and i have to set up everything again so i'll try it when i wake up.

---

### Post by customisbetter on 2008-01-20
i did it and now it works!!! thanks!!!!

---

