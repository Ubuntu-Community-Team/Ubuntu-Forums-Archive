---
title: "screen resolution stuck at 640 X 480"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by patla on 2006-09-29
newbie Q. the screen resolution it's stuck at 640 X 480. On another post they ask "What graphics card are you using?" but it is never answered.

I have an on HP mobo ati radeon Xpress 200 chipset.
in the device manager reads:
Unknown (0x5a3f)
  RS480 [Radeon Xpress 200G Series]
Would the driver be missing? or Something? I'm new so I don't know how to figure this out

---

### Post by madmetal on 2006-09-29
first open a terminal...
type 
glxinfo | grep direct
if the answer is  
direct rendering: Yes
then you are ok with 3d acceleration and drivers.
if not install ati's drivers.
then open terminal once more and type
sudo gedit /etc/X11/xorg.conf
find resolution and change it with the ones your monitor and vga card support...
i think thats all...
:-k

---

### Post by nthdegree on 2006-09-29
sudo dpkg-reconfigure xserver-xorg

That is if I remember correctly *scratches head* (it might be xorg-xserver).  That will give you a a wizard to configure the graphical display, which will allow you to choose what drivers you wish etc.

It should detect the correct drivers etc. for you without a problem and allow you to choose resolution and refresh rates, if there is still an issue then re-run the command above and make sure the driver chosen is **vesa** which should support more than 640x480.

---

### Post by bulldog on 2006-09-29
> **nthdegree said:**
> sudo dpkg-reconfigure xserver-xorg

That is if I remember correctly *scratches head* (it might be xorg-xserver).  That will give you a a wizard to configure the graphical display, which will allow you to choose what drivers you wish etc.

It should detect the correct drivers etc. for you without a problem and allow you to choose resolution and refresh rates, if there is still an issue then re-run the command above and make sure the driver chosen is **vesa** which should support more than 640x480.

It's ```
sudo dpkg-reconfigure -phigh  xserver-xorg 
``` but you use it mostly if the X-server is crasht.

That's not the case and it want install your drivers that's something you have to do yourself.

---

