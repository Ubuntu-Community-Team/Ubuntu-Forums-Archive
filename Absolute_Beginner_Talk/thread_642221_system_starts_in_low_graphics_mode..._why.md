---
title: "system starts in low graphics mode... why???"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by cyclingman on 2007-12-16
After fiddling around trying to attach a second monitor using "Screen and graphics" I managed to mess something up and now every time I turn my system on, it informs me that it is running in low graphics mode and I have to change it, I don't know what to change as I am a total beginner.

I don't know what my graphics card is (anyone wanna point me in the right direction) if that is what I need.

Sorry for my overload of newbishness, help is much appreciated.

---

### Post by overdrank on 2007-12-16
> **cyclingman said:**
> After fiddling around trying to attach a second monitor using "Screen and graphics" I managed to mess something up and now every time I turn my system on, it informs me that it is running in low graphics mode and I have to change it, I don't know what to change as I am a total beginner.

I don't know what my graphics card is (anyone wanna point me in the right direction) if that is what I need.

Sorry for my overload of newbishness, help is much appreciated.

Hi and what is the model of the graphics card ?
You can try and reconfigure your xorg
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by rexxxlo on 2007-12-16
system>preferences> hardware information

should be able to find the graphics card thre

use that info to edit this command

> sudo dpkg-reconfigure xserver-xorg

just follow the steps it is quite easy

---

### Post by cyclingman on 2007-12-16
Thanks, I typed in the code and have been prompted with instructions. I first clicked yes to do it automatically or something. But i am now having difficulty finding my graphics card information using the hardware information (there is a lot of information there, and i don't know which one it is). Any more help, would er... help

P.S, im using Gusty Gibbon 7.10

---

### Post by Gone fishing on 2007-12-16
If your lucky and added the new screen using a gui tool it may have made a backup of your xorg.cont file /etc/X11/xorg.conf rename that backup xorg.conf and restart the X server Alt, Control, Back space with luck you will be back where you started (It's alway worth making a backup of xorg.conf before you play with the screen resolution etc)

---

### Post by cyclingman on 2007-12-16
To the previous post, I can find the file "xorg.conf". Are you saying that I have to rename this to "xorg.cont" right? After looking around, I found I could rename it using the mv command, I had to use sudo because it asked for permission.

After checking, I found that there was a "xorg.cont" in the folder. I then did the ctlr, alt, and bkspace, logged in, but it was still the same.

Am I doing it right? and is there just no luck, or have I misunderstood? I will go back to trying to find the graphics card :(   If anyone can help, pleeease!

---

### Post by cyclingman on 2007-12-17
[SIZE="7"]SOLVED,[/SIZE] 

using rexxlo's method. thanks :)

---

