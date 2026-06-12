---
title: "Live cd vertical green lines won't work"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by tybach on 2006-12-19
I try to boot with the live cd and it gets through the loading screen and then it just shows vertical green lines and I can't see/do anything.  Anything helps, I'm a complete n00b.

-Thanks

I have a:
Amd 64 3200+
1gb 3200 Ram
Pny Geforce 6600gt
ECS 755-A2 (v1.0)

---

### Post by bodhi.zazen on 2006-12-19
You probably need to install the nvidia drivers.

This may at least give you a working GUI, although it is a fix at the command line.

Hit Ctrl-Alt-F1 this will bring you to a command prompt.

Type:```
sudo nano /etc/X11/xorg.conf
```

This is a long file. Scroll down (with the arrow keys) to the device section, it will look something like this:> Section "Device"
	Identifier	"twinview"
	VideoRam	256000
	VendorName	"nVidia Corporation"
	BoardName	"Video device"
	Driver		"nvidia"

Change whatever is on the Driver line to:```
Driver "vesa"
```

Ctrl-X to exit, type Y to save your edit.

Then:```
sudo /etc/init.d/gdm restart
```

If needed, Ctrl-Alt-F7 to change back to the gui. Wait for the auto log-in sequence :)

If everything else is to your satisfaction you can install to HD then sort out the nvidia driver 8)

---

### Post by tybach on 2006-12-19
When do I press ctrl alt f1 because when it boots I cannot see anything but the green lines.  Then I hear the startup sound.

---

### Post by bodhi.zazen on 2006-12-19
> **tybach said:**
> When do I press ctrl alt f1 because when it boots I cannot see anything but the green lines.  Then I hear the startup sound.

Try Crtl-Alt-F1 after the start up sound.

---

### Post by tybach on 2006-12-19
Well I got ubuntu installed to my computer using the alternate install disk.  I boot up and still have green lines...  If I hit ctrl+alt+f1 the lines turn black and white and I can't read or see anything.  Is there some alternate way to install my drivers?

---

### Post by bodhi.zazen on 2006-12-19
Ouch !

Well congratulations on the install from the alternate CD.

I am sorry, but your situation is dire indeed. It will obviously be quite difficult to configure/install if you can not read the screen :(

Do you have a spare monitor ? Perhaps, if you are lucky, an alternate monitor may just be legible.

---

### Post by tybach on 2006-12-19
Okay as I get one step further to figuring this out I have another problem.

I changed my driver to "vera" and when I do the apt-get install nvidia-glx it asks for 

Please insert the disk labeled:
Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)
in drive /cdrom/

Both my live and alternate cd are not named that.  What should I do?

---

### Post by bodhi.zazen on 2006-12-19
Try the Alternate CD, the one you installed with....

If that does not work, remove the cd from your source list like this:

```
sudo nano /etc/apt/sources.list
```

Place a # in the front of the line referring to your CD ROM

Ctrl-X to exit nano, type Y to save your edit.

Then:```
sudo aptitude update
```

The continue installing the nvidia drivers ....

---

### Post by tybach on 2006-12-20
Got the drivers installed!  Now when I go to enable them it says "Unable to load Nvidia Kernel Driver!  Be sure to have installed the Nvidia driver for your running kernel"

I have no idea what that means...  I can feel it getting closer!

---

### Post by bodhi.zazen on 2006-12-20
You have not yet installed the nvidia drivers then. I am guessing you have the open source driver, which may work:

edit /etc/X11/xorg.conf

Change Drivers "vesa"

to 

Drivers "nv"

start X

What how-to did you follow to install the nvidia drivers ?

---

### Post by tybach on 2006-12-20
Okay well I got automatix2 to get my nvidia drivers to work.  Do I need to install my motherboard drivers or usb2.0?

---

### Post by bodhi.zazen on 2006-12-20
Should not need to install usb drivers.

What motherboard driver are you asking about ?

---

