---
title: "Can't change screen resolution - intel 915 graphics"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by wacked215 on 2007-08-24
Hey all,

I have a Dell Inspiron B130 laptop with the Intel 915 integrated graphics. After installing Ubuntu, I installed the xserver-org-video-intel package because the resolution was stuck at 1024 x 768. Now it is working at 1280 x 800 (the maximum), however, whenever I try to change the resolution, the system shows what looks like a starting up display where it is loading processes and indicating [OK] afterwards, and then goes back to my logon screen.

I am reasonably sure that it is a resolution problem, because the system used to reset when I started Stellarium, but after I ran it from the safe mode terminal and set the default resolution to 1280 x 800, it started working like a charm. Maybe it is just the windows manager that crashes when the resolution changes? I am sure there is a simple fix to this, but haven't been able to find one on the forums. Thanks!

David

---

### Post by nitro_n2o on 2007-08-24
maybe adding the correct refresh rates to your /etc/X11/xorg.conf will solve your problem.. google for the correct horizontal and vertical refresh rates and add them to the xorg.conf

---

### Post by ramjet_1953 on 2007-08-24
Some people do have problems with the new driver, which is still in beta, I believe. Especially if you have a application that changes resolution "on the fly", like a lot of games.

You may want to try re-installing the i810 driver and use 915resolution, instead, which in most cases behaves itself a bit better.

If you check out this link, it will show you how to use either driver:

 [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

Regards,
Roger :cool:

---

### Post by topbot on 2007-08-24
sudo apt-get install 915resolution

---

### Post by imjustsomeguy72 on 2007-08-29
I seem to have more or less exactly the same problem. However, I'm mainly trying to achieve lower resolutions which are required by some older applications (mainly games)

I cannot select any resolution in the "preferences>screen resolution" menu, the only one being displayed is my native 1024x768. When try to run applications that would normally automatically adjust the resolution, they crash and give me an error regarding the incorrect resolution. I have tried 915resolution, but my resolution already appears in the list, so I assume that won't help me at all?

I also tried the xserver-xorg-video-intel driver, but this doesn't really help either. While the driver works, and X starts up properly when using, it still doesn't allow me to change resolutions properly. What DOES happen is that 3 seemingly random resolutions (640x480, 800x600 and 1024x1024) accompany my native res in Screen Resolution. If I select one, X crashes, then restarts and takes me back to the log in screen. My Xorg appears to be fine (I think...)

---

### Post by justleen on 2007-08-29
> **topbot said:**
> sudo apt-get install 915resolution



try that, worked for me

after install you need to edit /etc/default/915config 
(not sure of the file name, but its in that dir) and edit the correct resolution for your screen.

---

### Post by imjustsomeguy72 on 2007-08-29
915resolution was one of the first things I tried. The resolutions I wanted were already in the BIOS list, and I went ahead and put 640x480 into the config file just to see what would happen. I rebooted, and it was in 1024x768 again. Absolutely nothing happened.

which was why I tried xserver-xorg-video-intel, but that's not helping either. Is it possible to make X work entirely from the conf file? I think that it overrides some of the settings because it thinks it knows better.

hey, maybe it does? :)

---

