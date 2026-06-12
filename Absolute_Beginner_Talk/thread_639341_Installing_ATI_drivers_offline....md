---
title: "Installing ATI drivers offline..."
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by adredz on 2007-12-13
is there any way i can install ATI drivers offline?

---

### Post by TheLions on 2007-12-13
there is a way:

download driver from ati page, copy it to /home/, restart, pick recovery mode, in console type cd /home/, type ./(name of ati file) and auto installer will install your driver!

or check this site:

[http://wiki.serios.net/wiki/Ubuntu_ATI_proprietary_display_driver_installation_using_ATI%27s_installer](http://wiki.serios.net/wiki/Ubuntu_ATI_proprietary_display_driver_installation_using_ATI%27s_installer)

---

### Post by flamelab on 2007-12-13
I am sorry to say that , but that driver is useless and dangerous for your dependencies and system stability whitout configuration .
You 'd better install the restricted driver by going to System --> administration --> Restricted Drivers Manager and choose your graphics card (that will download and install the latest stable driver )

If you want to install the latest driver (which supports AIGLX )  , but slow , go here [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")
or install [Envy ]("http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu1_all.deb")

Please install only one of the drivers .

And you need of course internet for both ways .

@TheLions . That wiki is outdated :(

---

