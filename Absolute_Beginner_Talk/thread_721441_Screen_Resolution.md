---
title: "Screen Resolution"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by gjj391 on 2008-03-11
Need some help here...

 I have my gutsy set to 1024 X 768 which i just installed and love very much, but everything is very very bloated an enlarged. Anyone encounter this problem before?

---

### Post by ansicplusplus on 2008-03-11
Hy,
I am not sure. Is your problem really that you are stuck with 1024x768 but you want something higher like 1280x1024 f.e. ?
Yours, ansicplusplus

---

### Post by gjj391 on 2008-03-11
Well, its like if there is a photo, it looks great on whatever else, but the person will look short and fat now on my screen. Its almost like everything is distorted.

I have a dell vostro 1500 with a 15.4 true life

---

### Post by reeseslover531 on 2008-03-11
Do you know what the native resolution of that monitor is?

---

### Post by gjj391 on 2008-03-11
okay i got it working in the (Admin > screens and graphics)

but now when i restart... it goes back to the ole bloated resolution.

---

### Post by ansicplusplus on 2008-03-11
Hy,
from what google told me I think you need to set the resolution to about 1680x1050. 
You can do that using the menu "system" -> "administration" -> "screens and graphics". 
If you can't find your exact model just try the button "Detect".
Yours,ansicplusplus

---

### Post by ansicplusplus on 2008-03-11
> **gjj391 said:**
> but now when i restart... it goes back to the ole bloated resolution.
It looks like ubuntu has trouble detecting your graphics card and switches to failsafe settings. Did you check the graphics card settings in the same menu?

---

### Post by mikecomua on 2008-03-11
You might try to edit your xorg.conf file.
First open terminal and type ```
sudo -i
```  than backup your xorg.conf ```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bac
```. Edit your xorg.conf ```
gedit /etc/X11/xorg.conf
```. Scroll down to Section "Screen" and look at the resolutions. You might try to cross everything, but your desired resolution out.
Or ```
sudo dpkg-reconfigure xserver-xorg
```
If this doesn't work, just restore your xorg.conf from the backup :guitar:

---

