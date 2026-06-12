---
title: "hmm wat can i do to  hmm wat can i do to"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Korea91 on 2007-07-06
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension

hmm wat can i do to 

when i do from  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

beryl-manager --no-force-window-manager


video card ATI MOBILITY RADEON X700
for ubuntu7.04
hmm wat can i do to

---

### Post by jordanmthomas on 2007-07-06
> Checking for XComposite extension : failed

No composite extension

You need to add this to the end of /etc/X11/xorg.conf
```
Section "Extensions"
Option  "Composite"     "Enable"
EndSection

```
to enable the Composite extension.  I'm not sure why it didn't mention this on your wiki page.

After adding, log out and restart X (ctrl -alt - backspace) and you should be good to go.

---

### Post by jordanmthomas on 2007-07-06
from a PM I got from Korea91:
> u tried to help me with the composite extension not working but when i do
/etc/X11/xorg.conf
it says access denied
You need to edit this file with a text editor.  Try running this in a terminal or by pressing Alt + F2:
```
gksudo gedit /etc/X11/xorg.conf
```
the gksudo gives you proper privileges for editing
the gedit is the text editor
/etc/X11/xorg.conf is the file you want to edit with gedit.

Hope this helps.

---

