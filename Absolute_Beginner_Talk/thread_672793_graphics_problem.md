---
title: "graphics problem"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by KezzerDrix on 2008-01-20
driver -- intel experiemental modesetting driver

the problem I cant turn on any "eyecandy" not even "normal" setting.

Do I need to install a driver or something?

I get this when I type compiz in a terminal

leftblank on purpose:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

Thanks
Kezz

---

### Post by A4006 on 2008-01-20
Part of your problem could be not enough video memory, which causes compiz to give you lots of annoying messages when trying to enable desktop effects.  Otherwise, what type of video card do you have (Nvidia/ATI), and is it integrated or a add-on card?  You can install Nvidia and ATI drivers using Envy <http://albertomilone.com/nvidia_scripts1.html>, and the Compiz-Fusion settings manager is available using Add/Remove programs and searching for "compiz".

---

