---
title: "very new to ubuntu (help in live cd)"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by cyboincomp on 2005-12-23
hey guys 
i got hold of ubuntu live cd from linux mag 
i happily changed my bios to boot from cd then booted from the cd 

and to my surprise after few clicks abt my system and abt 15 minutes of 
scrolling text with all setting ok except 
the one which connected to the ubuntu server after the system date verification 

which did not affect the proceedings 
and 10 min later i was glaring at the rising sun screen of ubuntu with my mouse immobile and no key stroke from my keyboard seem to 

create even a frill on the screen 

ya with the the rising sun i get a toolbar like thing on top of screen 
plz tell me what to do 

sys confg 

celeron 1.2 ghz 128 ram 
i key keyboard 
logitech three button mouse 
40 gb hdd 
samsung combo 


then on digit open source i was told to do the following
*********************************************************
try ctrl+alt+F2,there may be a virtual console login to it and type: 
Code: 
dpkg-reconfigure xserver-xorg 

afterwards give your mouse's port whether ps2 or usb and keyboard type like pc104 for a 104 key keybrd..when the dialog asks..also gave the proper driver of your video card type from the menu which shows in nucurses..if everythings done..try logging out ..and mouse may work...(hmm..dont restart...)..if u really stuck in just press ctrl+alt+backspace...
*********************************************************
but 
i tried ctrl+alt+f2 
it got me to a dos like screen where when i typed dpkg-reconfigure xserver-xorg 
it told me i require root privilages and when i typed root it says u should b in lowest level of "sh" 
typing sh gives 
$sh 3.00: 
still when i type root it tell to go into lowest "sh" 
then i pressed ctrl+alt+f7 to get to desktop 
where o popup window told "question" 
and some applet couldnt b loaded 

pressing ctrl+alt+back 
rebooted me with my immobile curser staring right into my face 

plz help

---

### Post by linear on 2005-12-23
Try: **sudo** dpkg-reconfigure xserver-xorg

In Ubuntu, the root user is disabled by default.

---

