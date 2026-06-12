---
title: "Can't Install Drivers or snap out of safe mode"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by poisonfro66 on 2008-03-26
Hello People

Yes, the Hopeless Ubuntu User is back.

My problem this time: I can't (actually I don't know how to) install my video driver(s).

My original screen resolution after installation was 1440*900
I tried to change the resolution and messed around a bit with the "screen & graphics" menu, to no avail, except that after logout and login, the whole thing snapped to safe mode, with the message that the system could not define my graphics card or screen or summat'. So now i am in safe mode. and i don't know how to go out of it.

My real problem (apart from the "can't go out of safe  mode" one) is that I can't get my computer to run the Advanced Visual Effects. This is super frustrating, because:
    -I have bought a new graphics card for that purpose (NVidia 8800 GT, 1024 MB of RAM)
    -I know that Ubuntu supposedly get along better with NVidia cards than with others

So  my real question is:

**How do I get out of safe mode and install drivers so I can run the Advanced Visual Effects?**

Please, Help!:)

---

### Post by overdrank on 2008-03-26
> **poisonfro66 said:**
> Hello People

Yes, the Hopeless Ubuntu User is back.

My problem this time: I can't (actually I don't know how to) install my video driver(s).

My original screen resolution after installation was 1440*900
I tried to change the resolution and messed around a bit with the "screen & graphics" menu, to no avail, except that after logout and login, the whole thing snapped to safe mode, with the message that the system could not define my graphics card or screen or summat'. So now i am in safe mode. and i don't know how to go out of it.

My real problem (apart from the "can't go out of safe  mode" one) is that I can't get my computer to run the Advanced Visual Effects. This is super frustrating, because:
    -I have bought a new graphics card for that purpose (NVidia 8800 GT, 1024 MB of RAM)
    -I know that Ubuntu supposedly get along better with NVidia cards than with others

So  my real question is:

**How do I get out of safe mode and install drivers so I can run the Advanced Visual Effects?**

Please, Help!:)

Hi and you can try and reconfigure you xorg with this command in the terminal ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x with the ctrl, alt, backspace keys.
Then you may look at Envy to install the drivers
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by poisonfro66 on 2008-03-27
Yes, I did all that in that order, but after logoff, the system still can't recognise my screen or my graphics card. And keep going into safe graphics mode.

btw: Screen: Chimei CMV 946D
       Graphics Card: NVidia Geforce 8800 GT, 1024 MB of RAM.

---

### Post by smartboyathome on 2008-03-27
Actually run this:
```
sudo apt-get install nvidia-glx-new
```
To install nvidia's drivers, and run this:
```
nvidia-settings
```
To get the command which will set up your xorg.conf for you. :)

---

### Post by poisonfro66 on 2008-03-27
This is what shows up, but being a n00b i have no idea what the heck  "X" is about

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

:lolflag:

---

### Post by djbsteart1 on 2008-03-27
When you were reconfiguring the xserver, what did you select as the type of graphic card? It should be nv,but there is a chances that it has been wrongly detected.

---

### Post by poisonfro66 on 2008-03-27
Well, I just chose NVidia Geforce 8 series.
My card is an Geforce 8800 GT.

How do you run that "nvidia-xconfig" thing as root?

---

