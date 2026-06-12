---
title: "need help to install ati drivers"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by linuxnewbie1113 on 2007-08-11
im new to ubuntu and i need help to install the ati drivers for 01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c). Can anyone help me, i've tried a few times but everytime i do and restart my computer the xserver fails to start. can anyone give me  step by step directions to get this working. thanks in advance for your help.

---

### Post by jeremy1138 on 2007-08-11
Go here and download the ati installer...  That's what I did to get mine working...  Well working is a relative term of course considering the particular video card that I'm using but the gui works so I guess it's ok...

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

---

### Post by darksidedude on 2007-08-11
have you tried the restricted manager, if you didn't get it working yet

---

### Post by bodhi.zazen on 2007-08-12
Moved to Absolute Beginner Talk 

The location of the origional post is not primarily for support and I think you will have a better response in ABT ;)

---

### Post by MindRiot on 2007-08-12
My sister has a low profile Rage Pro graphics card in her old NEC Powermate.  She didn't need to install an ATI binary driver for the card to work properly.  Are you sure you need the driver?

---

### Post by linuxnewbie1113 on 2007-08-12
When i try runing the restricted drivers manager it comes up with a message saying your hardware does not need any restricted driver

---

### Post by Arisna on 2007-08-12
Use the software called Envy available from the below site.  I know it says nvidia in the URL, but it also eases the installation of official ATI drivers.  I've used it with good success to install a driver for the ATI Radeon FireGL v5250, and many/most/all other ATI cards are detected by this script as well.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by linuxnewbie1113 on 2007-08-12
i've tried every suggestion on this page and still no help this is my out put after i run the first half of the installtion
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

can anyone possible steer me in the rite direction to get the driver working

---

### Post by kosmo on 2007-08-13
Maybe you can checked out your xorg.conf file.

 ```
sudo gedit /etc/X11/xorg.conf
```

 In device section, you can add in Section "Device", "ati" or "atimisc" wrapper to right driver, like this:

 ```
Section "Device"
	Driver		"ati"

 or

 Section "Device"
	Driver		"atimisc"
```

 And then restart X with ctrl>alt>backspace.

 Or if you in dark console, you may try configuring X with this command:

 ```
sudo dpkg-reconfigure xserver-xorg
```

 And choose one of those drivers.

 If this can't help, maybe you can try with "r128". I don't know right driver,
because your card is very-very old.:(

---

### Post by linuxnewbie1113 on 2007-08-13
yeah i realize that the card is very old, which only leads to making my ubuntu experience a little bit harder, especially when im trying to find drivers to update. Thanks for the help and im definently gonna give it a try. All help is appriciated , thanks for answerin my questions even if they are somethin easy im still tryin to transition from xp.

---

### Post by Hobo Joe on 2007-08-13
Use Envy, my sig has a link.

---

### Post by linuxnewbie1113 on 2007-08-13
i tried envy but it was unable to detect an ati card, i have a later version then the one on your sig, could that make a difference?

---

