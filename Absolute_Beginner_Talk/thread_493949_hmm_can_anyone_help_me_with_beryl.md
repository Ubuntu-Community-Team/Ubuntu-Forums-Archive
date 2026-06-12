---
title: "hmm can anyone help me with beryl"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Korea91 on 2007-07-06
************************************************** ************
* Beryl system compatiblity check *
************************************************** ************

Detected xserver : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension : failed

No composite extension

hmm wat can i do to

when i do from [http://ubuntuguide.org/wiki/Ubuntu:F...eryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:F...eryl_.28ATI.29)

beryl-manager --no-force-window-manager


video card ATI MOBILITY RADEON X700
for ubuntu7.04
hmm wat can i do to

so i got this but

You need to add this to the end of /etc/X11/xorg.conf
Code:

Section "Extensions"
Option  "Composite"     "Enable"
EndSection

when i do  /etc/X11/xorg.conf it says permission denied so wat to do

---

### Post by pardesi on 2007-07-06
```
sudo gedit /etc/X11/xorg.conf 
```

---

