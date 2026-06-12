---
title: "Dapper - brightness SiS 650 chipset (Desknote A928)"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Ba|der on 2007-05-02
Hi,

Is there a simply way to change brightness for Ubuntu Dapper Drake (6.06) with SiS 650 chipset on a desknote A928. I played a bit with xgamma, but it seems not to affect the brightness. Various post on this forums suggest different solution for each chipset, often a echo 1 to 10 into some files... Is there such a simple way for SiS also, as I need this for using the desknote outdoors.

I was hoping to avoid downloading some drivers (like [http://www.winischhofer.eu/linuxsisvga.shtml](http://www.winischhofer.eu/linuxsisvga.shtml)) that might mess up Ubuntu, as I'm not so keen on reinstalling it right now.

Any suggestions?

- Balder

APPEND: Just for info The FN+ F7/F8 that is marked with the suns are not working in Ubuntu, or in BIOS / Windows for that matter. In Windows I use a program from SIS.com called SIS tray, due to it lives in the Windows system tray. It makes me easely change brightness and many other settings with sliders.

---

### Post by Ba|der on 2007-05-02
I decided to go for the third party driver and sisctrl at [http://www.winischhofer.eu/linuxsisvga.shtml](http://www.winischhofer.eu/linuxsisvga.shtml) anyway. It seems to work fine, (I used to binary version available for download for the driver and used the ubuntu/debian package manager Synaptic for the sisctrl. I also needed to edit my xorg.conf as the program asked me to.) but it would be nice not having to mess with this things. Also future Ubuntu updates might break somethink, so I'm a bit weary of using basic software from differnt sources then they will not be tested with each other before it might break.

---

