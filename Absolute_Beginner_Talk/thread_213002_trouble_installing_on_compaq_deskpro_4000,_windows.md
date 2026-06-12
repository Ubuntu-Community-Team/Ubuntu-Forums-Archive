---
title: "trouble installing on compaq deskpro 4000, windows 2k"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by macgig on 2006-07-10
trying to install on a compaq deskpro 4000, windows 2k on there now. 

it's an older machine...200 mhz pent mmx. 96 megs ram... 

booting from cd, I get an error: "ACPI: unable to locate RSDP"

then, it gets to install screen... and works for awhile... loading I guess? or trying to boot/load?

eventually, the monitor goes back to the text: ACPI: unable to locate RSDP"


with a blinking cursor. 

help!

---

### Post by john_spiral on 2006-07-10
I'm not sure about the problems you are having but give xubuntu a try it's suited for older machines with less ram.

[http://www.xubuntu.org/](http://www.xubuntu.org/)


a bit of wikipedia and google gave me the following:

RSDP: Root System Description Pointer (ACPI)
ACPI: Advanced Configuration and Power Interface

Might be throwing a fit because the memory is full during installation?

---

### Post by macgig on 2006-07-12
I was unable to boot or install on this pc using either version. 

what are the hardware requirments i wonder? guess this pc dont meet all or some of them? :confused:

---

### Post by macgig on 2006-07-17
for what its worth... 

I did manage to install xubuntu on this system.. but it ran so poorly I had to put windows 2000 back on it. :(

it was having odd video/screen behavior after the install.... moving the mouse would erase the stuff on the screen. :confused: 

not sure why, perhaps the video card isnt fast enough? :-k

---

### Post by PeX-i on 2006-11-06
Do you have original S3 ViRGE/GX on your machine? I got it work when I changed the video driver "s3virge" to "vesa" in /etc/X11/xorg.conf

---

### Post by lemonsCC on 2006-11-15
how did you change this?  dpkg.....blah blah  or go into the file in a text editor?

Dam compaq and there screwy cards!

---

### Post by TorontoFish on 2006-12-04
I had the same problem and fixed it by following PeX-i's recommendation. I used this:
```
sudo nano -w /etc/X11/xorg.conf
```
and changed the driver line to "vesa". Good luck!

---

