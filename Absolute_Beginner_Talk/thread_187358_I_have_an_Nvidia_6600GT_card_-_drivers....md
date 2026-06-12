---
title: "I have an Nvidia 6600GT card - drivers..."
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-02
Hi,

I have a Nvidia 6600GT card. How can I see the status of my card in terms of some test. Is hardware acceleration applicable and if so is it on or off? There are a lot of settings in XP to determine that state of a graphics card. Where are these in Ubuntu?

I applied method 1
"sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`"
from
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

However I really have no idea what I am doing and I don't want to risk my system by further experimenting.

How do I determine if my grahics card is optimised?

Thanks.

---

### Post by %hMa@?b&lt;C on 2006-06-02
if you run
```
glxinfo | grep rendering
```
from terminal and the output is this 
```
direct rendering: Yes
``` then you have 3d acceleration on, if else, it is off

---

### Post by CameronCalver on 2006-06-02
Have your tried automatix?

---

### Post by slimdog360 on 2006-06-02
use synaptic to install the drivers, then use the command (I cant remember it but its in the description window in synaptic) to enable the drivers. When you restart your computer if a big NVIDIA screen comes up, you know they are installed properly. But yeah automatix does all of that with no hassle.

---

### Post by u.b.u.n.t.u on 2006-06-02
[QUOTE=jeffc313]if you run
```
glxinfo | grep rendering
```
from terminal and the output is this 
```
direct rendering: Yes
``` then you have 3d acceleration on, if else, it is off[/QUOTE]

Hi jeffc313,

When I ran the code ```
glxinfo | grep rendering
``` I got the following messgae.

"XXXXXXX@ubuntu:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0"."

What should I do now? Thanks.

---

### Post by u.b.u.n.t.u on 2006-06-02
[QUOTE=CameronCalver]Have your tried automatix?[/QUOTE]

Hi CameronCalver, no. I have no idea what that is.

Edit - I will edit and update this post.

-----------------------------------------------------------------
HOW TO OBTAIN AND INSTALL AUTOMATIX ON UBUNTU DAPPER

[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

Look for where it says:

"Installation Instructions:
To install Automatix in Ubuntu do the following from terminal(one line at a time, pressing enter after each step):"

-----------------------------------------------------------------
HOW TO START AUTOMATRIX

In the terminal type:

Automatix

You will then see some pop up windows with information - follow that. Finally you see "NVIDIA Card" etc, with tixk box to the left. Select that.

-----------------------------------------------------------------
ARE THE DRIVERS INSTALLED? YES OR NO?

Yes IF you saw the Nvidia spash screen at reboot.

Yes IF you open the terminal, type this in and get "yes".

"XXXXXXX@ubuntu:~$ glxinfo | grep rendering
direct rendering: Yes"

---

### Post by u.b.u.n.t.u on 2006-06-02
Are my about notes/instructions correct?

Why does Automatrix overlap with Synaptic?

Why doesn't Synaptic do what I had to use Automatrix for?

Thanks.

---

### Post by chameleon_789 on 2006-06-03
Without automatix, all that you need to do to enable the nvidia accelerated driver is type:
```
nvidia-xconfig
``` 
in a terminal (if that doesn't work you might need to proceed it with *sudo*). After that, you need to reboot. Once the driver's installed, before the login screen a white screen with the nvidia logo should come up (that's the best indication that the driver has installed and loaded). Otherwise if it hasn't worked, you'll either get a blank screen or an error message.

If it hasn't worked, the best thing to do is login (or reboot and run recovery mode if it's a blank screen), run *sudo aptitude* (the text mode version of synaptic), press / and search for a program called *elinks*, which is a textmode internet browser. Then  press keypad + to add it, and G to install it. Then type elinks at the command line, come back here and we can guide you on what to do next :)

---

### Post by Dr. Nick on 2006-06-03
[quote=u.b.u.n.t.u]Hi,

I have a Nvidia 6600GT card. How can I see the status of my card in terms of some test. Is hardware acceleration applicable and if so is it on or off? There are a lot of settings in XP to determine that state of a graphics card. Where are these in Ubuntu?

I applied method 1
"sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`"
from
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

However I really have no idea what I am doing and I don't want to risk my system by further experimenting.

How do I determine if my grahics card is optimised?

Thanks.[/quote]

sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r

That command installs the nvidia drivers. apt-get is just the command line version of synaptic

nvidia-glx = nvidia drivers
linux-restrictred-modules = modules needed for the card aswell. the -r is their so it gets the correct version for the running kernel.

ITs been mentioned but if you see a nviidia logo on boot your good. to check a differnt way run 

cat /etc/X11/xorg.conf and look under device section and check driver says nvidia not nv or vesa

---

### Post by u.b.u.n.t.u on 2006-06-03
Thank you !

I am adding this good advise to my study notes.

:D

---

### Post by u.b.u.n.t.u on 2006-06-03
Cool !  :D 

Now to find some Linux genre games :D (ones that don't mortgage 12 hours a day but are still fun, lol - Oblivion anyone?!)

"Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "G90f+"
    DefaultDepth    24"

Thanks !!!

---

