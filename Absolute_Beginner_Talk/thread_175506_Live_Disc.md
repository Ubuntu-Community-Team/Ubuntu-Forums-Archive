---
title: "Live Disc"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by victorm62 on 2006-05-13
I'm a complete new comer to the world of Linux, just got a Live CD 5.10 for x86, tried to load it on my HP Pavilion zd8000 laptop and failed!!!
Got to the posh brown screen which tells me it loading bits and pieces ok and then it changed to a black screen with the following.

"Failed to start the X server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem."
 
I can only see a highlighted red Yes box if there is another box it's obscured by text which does not make a lote of sense to me.

Nothing happens when I hit enter, even alt, control, delete does very little other than show me a list of actions, have to kill the power to get out of it.

Any suggestions gratefully received

---

### Post by sintez.co.za on 2006-05-13
You must edit your xorg.conf file
1. Press CTRL+ALT+F1
2.[I]nano /etc/X11/xorg.conf
[/I]3.find DEVICE and change "via" for "vesa"
4. CTRL+X
5.Y
6.CTR+ALT+backspace

Should work, but you still need to find the right driver for your card to get the best screen resolution.

If this does not work, you can try, when loading live CD to type:
*live xmodule=vesa*
then hit "enter"

---

### Post by confused57 on 2006-05-13
You could also try:
1.)Ctrl+Alt+F1
2.)sudo dpkg-reconfigure x-server.xorg
3.)Change driver as mentioned previously(try Nv,also), and take out the
     "x" for  resolutions that are too high for your monitor.

Type "startx"(without quotes) , Press "enter"

Ctrl+Alt+Del  should reboot your computer, if it freezes & nothing else works.

No guarantees, but worth a try....

---

### Post by victorm62 on 2006-05-28
Tried both suggestions still no joy.
entering nan /etc/x11..... came up with a black screen with 
GNU nano 1.3.8  File:  /etc/x11/xorg.conf  at the top of the screen
along the bottom was get help etc tried a few things  like File but nothing helped.
Put live xmodule=versa still stopped at the same place.

sudo dpkg  etc just told me xserver was not loaded

Noticed in XP that it says I've no drivers loaded for my screen, is this the issue or am I stll looking for a fix for the live disc??? 
my screen is 17" WXGA high definition bright view widescreen
ATI mobility radeon x600 driver version 5.1.2001.0

Many thanks

---

