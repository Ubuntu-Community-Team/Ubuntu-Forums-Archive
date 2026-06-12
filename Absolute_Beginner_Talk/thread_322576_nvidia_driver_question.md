---
title: "nvidia driver question"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by nibi on 2006-12-20
I just used adept to install nvidia-glx on kubuntu edgy. I am not sure if these are the ones from nvidia or not but they seem to be working all right and the nvidia logo is also displayed at startup. I would like to install beryl and i have updated my sources as well (added: deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main).
The only problem is all guides ask you to install some sort of latest driver or something. Can anyone tell me if i need to mess with the drivers any more or should i just go ahead and install beryl using: sudo apt-get install beryl   :confused:

---

### Post by bodhi.zazen on 2006-12-20
You should be fine ....

To install beryl:

```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
sudo apt-key add root@lupine.me.uk.gpg

sudo aptitude update
```

Add this to /etc/X11/xorg.conf:

> 
In the screen section:
# Enable 32-bit ARGB GLX Visuals
   Option "AddARGBGLXVisuals" "True"
# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
#  Option "DisableGLXRootClipping" "True"

At the end of the file:

Section "Extensions"
  Option "Composite" "Enable"
EndSection

Then:
```
sudo aptitude install beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings beryl-manager beryl emerald-themes
```

8)

---

