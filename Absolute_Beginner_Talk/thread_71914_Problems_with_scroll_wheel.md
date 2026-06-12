---
title: "Problems with scroll wheel"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by Delvien on 2005-10-04
Hi guys , having problem with my BT mouse., i have the Microsoft intellimouse for Bluetooth 2.0, [img]http://i.pricerunner.com/prod/6_4_9_315045s/100x200/Microsoft_Wireless_IntelliMouse_Explorer_Bluetooth_2_0.jpg[/img]

And i am having troubles configuring the Forward and back buttons. AND THE SCROLL WHEEL, the scroll wheel and the f/b buttons are not recognized in XEV.


I am running Breezy Badger, and work with internal bluetooth card, not dongle, 

Can ANYONE help me,

---

### Post by Wide on 2005-10-04
You may want to take a look at [this post](http://ubuntuforums.org/showthread.php?t=65471), it may help:D

---

### Post by Delvien on 2005-10-04
[QUOTE=Wide]You may want to take a look at [this post](http://ubuntuforums.org/showthread.php?t=65471), it may help:D[/QUOTE]

that is tailored for logitech USB wired mice..

Im asking about the MS intellimouse Bluetooth..  big big difference, there are no USB connections, just a internal card, and a mouse that sends the sig out

---

### Post by Delvien on 2005-10-05
bump for responses !

---

### Post by Delvien on 2005-10-05
bump for problem not solved yet , sorry guys

---

### Post by Ampersand on 2005-10-05
Have a look at your /etc/X11/xorg.conf file. In the InputDevice option for your mouse, does it have the option "ZAxisMapping"?

---

### Post by mtron on 2005-10-06
could you figure it out?

How does the configuration for this device work?

---

### Post by Ampersand on 2005-10-06
For the scroll wheel, open a terminal, and run 'gksudo gedit /etc/X11/xorg.conf'. In the section about the mouse (starts with 'Section "InputDevice"'), make sure that the line

```
 
Option		"ZAxisMapping"		"4 5"

```

is present.

---

### Post by Delvien on 2005-10-09
[QUOTE=Ampersand]For the scroll wheel, open a terminal, and run 'gksudo gedit /etc/X11/xorg.conf'. In the section about the mouse (starts with 'Section "InputDevice"'), make sure that the line

```
 
Option		"ZAxisMapping"		"4 5"

```

is present.[/QUOTE]

It is set to that, but still doesnt work. Ived tried 15 combinations, rebooting the PC each time, it just does not work. Does ANYONE know a method that will make  my MS intellimouse for bluetooth work.. that they know works.. not "read this guide on some mouse you dont have"

---

### Post by markrez on 2005-10-12
What laptop do you have?  I am looking for a bluetooth mouse to work with bluetooth on my HP nc8230. I have read that the MS BT mice don't like to play with internal BT, they want the dongle only.

---

### Post by Delvien on 2005-10-16
[QUOTE=markrez]What laptop do you have?  I am looking for a bluetooth mouse to work with bluetooth on my HP nc8230. I have read that the MS BT mice don't like to play with internal BT, they want the dongle only.[/QUOTE]


i have a Dell inspiron 6000 with internal bluetooth, my GF uses the dongle, i threw mine away :P



Bad news, scrolly button still doesnt work

---

