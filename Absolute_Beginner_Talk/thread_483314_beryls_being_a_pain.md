---
title: "beryls being a pain"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by timelord29 on 2007-06-24
i have ubuntu 7.04 fiesty fawn and i cant get beryl to work! i installed it correctly but whenever i start the program my whole screen turns white and i cant interface with the computer! can someone tell me how to fix this in a way that a first-timer can understand? i just started using ubuntu.

---

### Post by ajmorris on 2007-06-24
> **timelord29 said:**
> i have ubuntu 7.04 fiesty fawn and i cant get beryl to work! i installed it correctly but whenever i start the program my whole screen turns white and i cant interface with the computer! can someone tell me how to fix this in a way that a first-timer can understand? i just started using ubuntu.

Can you please go into a terminal (start menu >> Accessories >> terminal) and type ```
grep|glxinfo
``` then scroll to the top of the output and look for a line like this : 
direct rendering: Yes


Also what graphics card/chip are you using?

and can you please post your /etc/X11/xorg.conf file.

---

### Post by timelord29 on 2007-06-25
i have an ATI Radeon XPRESS  series graphics card but i found out that its a problem with the desktop effects. i tried turning them on without beryl and the whole screen turned white. how do i fix this?

---

### Post by FurryNemesis on 2007-06-25
Is the driver for that card installed?

---

### Post by timelord29 on 2007-06-25
also i checked grep|glxinfo and it said:
direct rendering: no
also i have no idea what a /etc/X11/xorg.conf is. i just started using ubuntu

---

### Post by timelord29 on 2007-06-25
well i just installed ubuntu on my new hard drive yesterday and everything else is working that involves graphics (youtube videos, prepackaged games, etc). if it isnt installed, how would i find out and how do i install it?

---

### Post by cogadh on 2007-06-25
You can't use Beryl without first installing a 3D accellerated driver for your video card. Follow these instruction for installing the correct driver for your video:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Follow these instruction for installing/setting up Beryl:
[http://wiki.beryl-project.org/wiki/Support_for_ATI_cards](http://wiki.beryl-project.org/wiki/Support_for_ATI_cards)

---

### Post by FurryNemesis on 2007-06-25
Like this:

Go to Applications > Add/Remove

In the top left corner, click on "Show: All available apps" in the drop down menu

Search for "ati binary" then install the ati binary xorg driver from the list.

---

### Post by timelord29 on 2007-06-25
well i got it to boot up and my screen stayed intact but beryl itself isnt working. i opened up the config and looked around and none of the settings, default or otherwise make it work.

---

