---
title: "wont load ubuntu"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Semorph on 2007-10-29
hello, im having a problem where i have duel booted windows xp and ubuntu. i partitioned 100GB free space using gpart, then used the ubuntu installer to do all the work.
all seemed to go fine but when i rebooted and tried to load ubuntu (it did show up in the list of OS to load) i get the loading bar, and then after that the screen goes black and i get the ubuntu loading cursor
which is not spinning. i left it on the screen overnight to see if it would load but it dident.
so any help on this would be appreciated thx in advance:)

ps. im nooby when it comes to linux it just seems to be a good system

---

### Post by taurus on 2007-10-29
Can you post the spec of your machine especially the graphic card?  Wait for it to boot up, then see if you get a login prompt when you press <Ctrl><Alt>F2.  If you do, then log in with your username and password and reconfigure your X again with

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure xserver-xorg
sudo shutdown -r now
```

---

### Post by overdrank on 2007-10-29
> **Semorph said:**
> hello, im having a problem where i have duel booted windows xp and ubuntu. i partitioned 100GB free space using gpart, then used the ubuntu installer to do all the work.
all seemed to go fine but when i rebooted and tried to load ubuntu (it did show up in the list of OS to load) i get the loading bar, and then after that the screen goes black and i get the ubuntu loading cursor
which is not spinning. i left it on the screen overnight to see if it would load but it dident.
so any help on this would be appreciated thx in advance:)

ps. im nooby when it comes to linux it just seems to be a good system

Hi and welcome, if you could give us some specs on the system and which version of ubuntu you are using? Also you may try and press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and then hit enter and then  b to boot. This will allow you to see any errors if any. Hope this helps. Good luck!
Edit and Taurus has some good info also. :)

---

### Post by Semorph on 2007-10-29
as far as my sys spec here they are
dell inspirion 530
CPU intel core 2 duo e4400 @ 2.00 GHz
Video NVIDIA GeForce 8300 GS display ram 512mb
OS: windows xp home edition sp2 
and im installing ubuntu v 7.10.
if i missed any thing let me know
ill go look into your advice just posted my specs first, thx

---

### Post by Semorph on 2007-10-29
ok i have done what you guys say when i press ctrl alt and f2 it tells me the status of it loading and it says OK next to all of them
as far as removeing quiet splash is it this line: kernel   /boot/vvmlinuz-2.6.22-1-generic root=UUID ect. (lots of numbers)then at the end: 1b7d651a4f7 ro quiet splash
and then can i, and do i need to get it back if i remove it.

---

### Post by overdrank on 2007-10-29
> **Semorph said:**
> ok i have done what you guys say when i press ctrl alt and f2 it tells me the status of it loading and it says OK next to all of them
as far as removeing quiet splash is it this line: kernel   /boot/vvmlinuz-2.6.22-1-generic root=UUID ect. (lots of numbers)then at the end: 1b7d651a4f7 ro quiet splash
and then can i, and do i need to get it back if i remove it.

Hi if you remove the quiet splash it will return when you reboot the system no worries there. That is just one way to see the boot process and see errors.  Then continue with taurus instructions and configure your xorg and you may have to choose vesa for the driver and hope this will get you to the desktop (GUI) :KS

---

### Post by Semorph on 2007-10-29
ok well maybe i missed something installing it... how do i edit the xorg and what am i supposed to do with it, sry im a noob:confused:
tho i did remove quiet splash and it showed me the boot progress and i saw no errors but it was moving pretty fast
i deleted "quiet splash" off the front of the command line.
then like it does evry time it freezes on what looks like the screen right before the desktop, all i have is that animated spining cursor but its not spinning. so i have been holding down power button to unfreeze...

---

