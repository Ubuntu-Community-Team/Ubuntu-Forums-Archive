---
title: "Dual widescreen monitors in GustyGibbon"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by graben3 on 2007-12-30
I have an ATI radeon 9550 graphic card with two widescreen 1680x1050 monitors with DRI support but unfortunately beryl/compiz refuses to start. 

When I configure my screens in ATI Catalyst control center, I can't set the right resolution. If i set it in my xorg.conf file, it only works on one monitor.

My screens display a streched image since i can't get the two screens to have 3320 pixels wide together. The catalyst control center only allows 2560 px wide (2 x 1280px) so I end up having 2x 1280x1024 screens with my widescreen monitors.

Anoyone have an idea how to fix this... I just switched to widescreen dual monitor. i previously had 2x 1280x1024 LCD monitors and it was working. Why is this not working anymore ?

---

### Post by Nikitas350 on 2007-12-31
Try to configure the monitors using "Screen and graphics". If you have the ubuntu 7.10 you can find it if go to system---->administration--->screen and graphics...

---

### Post by graben3 on 2007-12-31
i tried this first even before installing the ATI proprietary drivers. it always made things worse... if I setup the second monitor to be at the right of the default one, it eigther did mirror my screen or simply made it not work.

I tried another time just to be sure it was not working before answering your post. Nope, the X server would not even start anymore. i saw the 'running in low res' dialog box that appears since ubuntu 7.10 when changes to xorg.conf are not OK. Then I clicked continue... the 2 screen went blank and I heard the login screen sound so I figured none of the screens worked.

To be noticed, the screens and graphics utility only sees 1 big 2560x1024 screen when I open it up running my working dual screen xorg.conf. it doesn't show the second monitor as active.

I used the One Big Desktop in the ATI catalyst Control center to make my 2 screens work together. This is the only option i found to have 3d accel and 2 screens. 

I did not touch my xorg.conf file manually this time (i am not at my first attempt to get dual screen working under linux !) 

any suggestions of what I could do to get my dual monitors to the optimal resolution ?

---

