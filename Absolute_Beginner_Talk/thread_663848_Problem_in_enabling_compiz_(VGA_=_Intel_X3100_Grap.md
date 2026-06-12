---
title: "Problem in enabling compiz (VGA = Intel X3100 Graphic Media Accelerator)"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by aria.radmand on 2008-01-10
Hi;
can anybody help me to enable compiz, on my "[Acer TravelMate 6292]("http://global.acer.com/PRODUCTS/notebook/tm6292.htm")" laptop (in ubuntu 7.1 Gutsy Gibbon)?

the result of typing "compiz" in terminal is:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by Hospadar on 2008-01-10
have you installed the restricted drivers for your hardware?

Go to System->Administration->Restricted Drivers Manager

Also, the way you really want to enable compiz is by going to System-Preferences->Appearance->Visual Effects and choosing "normal" or "extra"

If you want further control over how compiz behaves, install "compizconfig-settins-manager" from synaptic and go to "System->Preferences->Advanced Desktop Effects Settings"

---

### Post by aria.radmand on 2008-01-10
> have you installed the restricted drivers for your hardware?No, It says "Your hardware does not need any restricted driver."> Also, the way you really want to enable compiz is by going to System-Preferences->Appearance->Visual Effects and choosing "normal" or "extra"Yes, It says "Desktop effects could not be enabled."> If you want further control over how compiz behaves, install "compizconfig-settins-manager" from synaptic and go to "System->Preferences->Advanced Desktop Effects Settings"i've already installed every package that has "compiz" in it's name, in my repositories! :D
but unfortunately they are completely useless.
and for your information, i've tried what said [HERE]("http://knowledge76.com/index.php/GutsyCompizIntelX3100"), but desktop effects could not be enabled yet.

---

### Post by clayt0njknight on 2008-01-19
open a terminal

type "sudo gedit /usr/bin/compiz" and press enter (minus the quotes of course).

type your password and press enter.

scroll down to the section that says "Blacklist".

remove the line that includes intel and 965 (3rd or 4th line in blacklist section.)

save.
close gedit.
close terminal.

press alt+F2, a "run" window will open.

type compiz --replace  and press enter.

you should now have desktop effects.

---

### Post by Vadimir on 2008-01-21
this because intel x3100 is restricted. 

try to edit /usr/bin/compiz  
there are  some commented lines "like .... intel". uncomment its

---

### Post by Golem XIV on 2008-01-21
Please note that commenting out the blacklisting in /usr/bin/compiz or using SKIP_CHECKS="yes" in /etc/xdg/compiz/compiz-manager (basically the same thing) will nuke video playback capability.

To work around the video problem, you can run gstreamer-properties (it's also on the System->Preferences menu as "Multimedia Systems Selector", but it is disabled by default; run the menu editor to enable it) and under the Video tab -> Default Output -> plugin select "X Window System (No XV)".  this will enable a slower and more CPU-intensive renderer (but at least it'll work).

This will give you both Compiz effects and video playback.  Note that this will not work for some apps that require XV (like Skype 2.0 Beta).

---

### Post by issih on 2008-05-29
Um no read the threads I posted...one suggests adding

LD_LIBRARY_PATH=/usr/lib

to /etc/profile, although that doesn't sound very hopefull to me.

The other suggests deleting the hardware from the blacklist...it is feasible that the blacklist file still lists your hardware even though it is now supported if things managed to get out of sync somehow.

There are a lot of posts on the issue you mention, just google the error you recieved, ignore anything about xgl..it is no longer used...end of, anything else, give it a whirl

---

