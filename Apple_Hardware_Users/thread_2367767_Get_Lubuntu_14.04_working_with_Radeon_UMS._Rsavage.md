---
title: "Get Lubuntu 14.04 working with Radeon UMS. Rsavages thread and links no work!"
date: 2017-08-03
forum: Apple Hardware Users
---

### Post by blackjok3r on 2017-08-03
[https://ubuntuforums.org/showthread.php?t=2294789](https://ubuntuforums.org/showthread.php?t=2294789)

I really need the files in the above thread. I have an ibook G3 with 384mb of ram, I have a 512MB stick on order to give me 640MB, as is the MAX. Currently 12.04 LXDE is only using like 120mb so this shoudl work fine.  

I have tried for 2 weeks to get Gentoo working but ran into the [radeon driver error]("https://wiki.debian.org/PowerPC/FAQ#How_do_I_get_graphics_working.3F") and have no picture with KMS enabled. Anything over Lubuntu 12.04 is not working for me. I have managed to get 14.04 to boot off a USB stick but it runs on fbdev driver and is really slow and colors are only 8bit. 

I got 12.04 installed and back ported MESA drivers to 7.11 to get 350fps in glxgears. I have no 2D acceleration on my desktop (or its just so incredibly slow that it seems like its not working) and its pretty much useless to browse the internet using firefox-39. In my research I came across the thread above where there was packages to enable the UMS drivers that I have now in 14.04. This will give me a much newer firefox or possibly even a webkit2 version of the midori browser. The thread has been closed though and the links are all dead.

Does anyone have the files? I can't find a way to message rsavage in this forum unless I'm blind. :confused:

---

### Post by abtabt on 2017-08-10
Hi i cant give you the files but 
If you install or Use live lubuntu 16.04 or 14.04 and install htop then you can see whats
take CPU and if swap is used  .and l always install Compton for the sluggish Windows drawing/teering (lubuntu )
and i use always xorg.conf to get it right 
(1024*768 800*400 and 16 bit , 24 bit etc) 
Some of the framebuffer need to have a xorg.conf to work and some can use
it when you boot .

---

### Post by rsavage on 2017-08-11
I believe ppcluddite hosts a copy of the file you want.  For the others, I didn't remove them (except the Ubuntu mate 14.04 ISO), onedrive just silently cancelled the links.

---

