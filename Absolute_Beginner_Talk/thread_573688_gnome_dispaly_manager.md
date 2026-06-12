---
title: "gnome dispaly manager"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-11
Hi,

i'm stuck in gnome display manager and I don't really know how to get out of it. I basically need the command to get back to normal ubuntu 7.04 window. 

Thnx

---

### Post by Shazaam on 2007-10-11
Why? Can you tell us anything more?

---

### Post by steveneddy on 2007-10-11
> **limac said:**
> Hi,

i'm stuck in gnome display manager and I don't really know how to get out of it. I basically need the command to get back to normal ubuntu 7.04 window. 

Thnx

Huh?

Maybe a few more details?

---

### Post by rsambuca on 2007-10-11
I am not sure what you are talking about, but try Control-Alt-Backspace.

---

### Post by limac on 2007-10-12
hi,

I am stuck in the gnome display manager. It is like a complete black background sort of thing where the text is in the color white and it asks you to type the command which you want the computer to obey.  

It it enough or is it still uncler??

Thnx

---

### Post by rsambuca on 2007-10-12
You are not at a gdm screen.  It sounds like you are at a command line prompt.  Try entering the following command

startx

---

### Post by limac on 2007-10-12
hi,
even if i use that command it says the following:
Fatal Server Error
no screens found
XIO: fatal 10 error 104 (Connection reset by peer) on x server "0.0"
after 0 requests (0 known processed) with 0 events remaining.

So how can I resolve it?
Thnx

---

### Post by rsambuca on 2007-10-12
Did you ever have the Ubuntu desktop working on this computer?

If you did, what were you doing just prior to it not working?

---

### Post by limac on 2007-10-12
hey,

Yeah it was working on that computer. I was trying to download envy NVIDIA driver and then when it was done downloading, I was asked to restart the computer and so I did. Now when It restarted it said "failed to start X server (your graphical interface).

And then after doing what I was asked for doing, the command line promt showed up and that's when and how it started.

Thnx

---

### Post by rsambuca on 2007-10-12
Enter this at the terminal then:```
sudo nano /etc/X11/xorg.conf
```Change the driver from "nvidia" to "nv".  Then press Control-O to save it and then Control-X to exit.  You should then be able to boot up.  You'll then have to find a different method of installing the proprietary nvidia driver.

---

### Post by limac on 2007-10-12
hi

it's kinda working. its saying ^X Exit on the bottom, my mouse is disabled in here and if I press ^X then enter it's not working. so what should I do??

---

### Post by rsambuca on 2007-10-12
Did you make the changes?  You can use the arrow keys on your keyboard.

---

### Post by arashcuzi on 2007-10-12
after you edit the xorg.conf you have to save it with I believe the command is alt-O and then close it with alt-X i believe, the controls are at the bottom, then you can type in the following

sudo /etc/init.d/gdm start

it should restart for you, if not, do this

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

when you installed envy it backed up your original xorg file it also might be called xorg.conf.old so if you get an error use that one instead of xorg.conf.backup.  then run

sudo /etc/init.d/gdm start 

or press alt-f7 and it should bring you to where you need to be.

I know what you issue is, make sure you have the new kernel

sudo apt-get install dist-upgrade

otherwise your nvidia driver will break xserver, I learned that the hard way.

---

### Post by limac on 2007-10-12
what nvidia files should I change to nv?
and When I press ctrl x it shows a message saying save modified changes .
Then how and where am I suppose to press Y or n

---

### Post by arashcuzi on 2007-10-12
look for this string:

Section "Device"
	Identifier	"nVidia Corporation GE Force Go 7800 GTX"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"DisableGLXRootClipping"	"True"

In the section "device" change driver (where it says nvidia above) to read "nv"

then ctrl-O to save, ctrl-X to exit

then restart x (i think ctrl-alt-backspace will do, or type type sudo /etc/init.d/gdm start)

and follow the rest of the directions from my last post

pm me if you have difficulties

---

