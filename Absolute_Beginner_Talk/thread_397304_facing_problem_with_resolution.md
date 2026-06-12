---
title: "facing problem with resolution"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by black_ice on 2007-03-30
hello all 

my ubuntu was working well and every thing was great ....... 

but after i run sudo dpkg-reconfigure -phigh xserver-xorg to increase resolution settings i found that there is any change happened in the resolution list at the preferences menu ? ! ?

and after that there is a kind of flickering at the browsers when i made apage down option 

and also at the games there is aflicker also what is the problem ? >>>

---

### Post by black_ice on 2007-03-30
Can Any one help me ? ?

---

### Post by ed-j on 2007-03-30
Hi !

What grapics card are you using? Nvidia? ATI? What kind of monitor are you using?

Please let me know.   :-)

---

### Post by black_ice on 2007-03-30
itis on my laptop and iam using ati card with shared memory = 128 MB

but i donot have any problems with my screen all what i need to fix this flicking happened ........ ? !

the problem also i feel that the resolution is taking altof memory when i make the page down when browsing i feel that every thing stops is that related to the resolution issue ? . ... .....

---

### Post by ed-j on 2007-03-31
Go into Add/Remove in accessories and you will find ATI Binary Drivers for a selection ATI graphics. Install these if you have not done so.

This might stop the "flickering" with the windows. Hope this helps!  :)

---

### Post by black_ice on 2007-03-31
i have it already installed but all the problem after i running this command sudo dpkg-reconfigure -phigh xserver-xorg and i want to add new resolution schemes the flickering happend i tried to change it from the menu system and also itis still exist :(

---

### Post by ed-j on 2007-04-01
Type the command [COLOR="SeaGreen"]sudo dpkg-reconfigure xserver-xorg[/COLOR] without the [COLOR="Red"]-phigh[/COLOR] Check that the graphics drivers match your card?

Best I can do!    :-)

---

### Post by tommcd on 2007-04-01
If that does not help, have a look at /etc/X11/xorg.conf. Check that the horizontal sync and vertical sync is within range of  what is specified in your laptop's manual or website. You can change it with <sudo nano -w /etc/X11/xorg.conf> via recovery mode if the GUI is problematic, or use <gksudo gedit /etc/X11/xorg.conf> from ubuntu GUI. Just back up your xorg.conf first for safety like this <sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak>. Then either reboot or restart the GUI with ctrl+alt+backspace.

---

