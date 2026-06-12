---
title: "Is my NVidia beefy enough for Xgl?"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by NewRubberSoul on 2006-09-27
Hi Everyone.  Sorry for the Noob question, but here goes...  

I've seen the videos online for Xgl and they look amazing.  I bought my desktop four years ago, though so I'm not sure that it's beefy enough to support Xgl.

I have a nVidia **NV15 [GeForce2 GTS/Pro**], 512 MB of RAM, and an Intel Pentium 4.  I tried googling and searching the forums, but can't tell if my video card would support Xgl.

I already set up the nVidia drivers with Easy Ubuntu.

I'd love to get Xgl working with Gnome.  Thanks in advance for the help.

---

### Post by ian.l on 2006-09-28
If your nVidia driver is installed properly and you can run glxgears from the shell, then it should work.

---

### Post by NewRubberSoul on 2006-09-28
```
brian@brian-desktop:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```

Is this a dependency issue, then or does it mean that my video card wouldn't support it?

---

### Post by curtisf14 on 2006-09-28
Make sure that in the file /etc/X11/xorg.conf, there is a line in the "Device" section of the file that reads:

```
	Driver		"nvidia"
```

That line should not read:

```
	Driver		"nv"
```

If it does, change the "nv" to "nvidia".  In order to edit the file, you will need to run the command:

```
sudo gedit /etc/X11/xorg.conf
```

See if that works.

---

### Post by kerry_s on 2006-09-28
Do you have the proprietary nvidia drivers? Check your  /etc/X11/xorg.conf it should have this->
Driver		"nvidia"

If not then you need to install the drivers.

sudo apt-get install nvidia-glx

then change your driver to say "nvidia" like above.
then exit and do ctrl+alt+backspace

---

### Post by NewRubberSoul on 2006-09-28
](*,) 

Uh Oh.  Big Uh Oh.

So I did the apt-get for the nvidia drivers and my terminal told me that they had already been installed with the most up to date package.

Then, I went in with sudo gedit and changed "nv" to "nvidia" in xorg.conf.  I saved, closed, and then as recommended hit ctrl-alt-backspace.  

This logged me out of my session and put me at a terminal screen.  I entered my password and lo and behold... The Blue Screen of Death!  I don't know what I did wrong.

I'm typing this message from another computer right now.  I was able to boot the computer up with a Knoppix cd to try and change that xorg.cong file manually but I've having permission problems trying to change it.  

The BSOD said something about X wasn't configured properly.  One last thing:  I tried booting up from a Korroraa live cd to test xgl, etc. a few weeks ago and got a similar error message.

Please Help!

---

### Post by prototype_angel on 2006-09-28
Ummm... the blue screen of death is a windows only thing. I don't think you should've changed the drivers, the conf should've updated manually, now it's not showing the proper drivers.

I'd suggest you boot into the failsafe and use nano to change the driver back to nv.

But I'm a newbie at linux, better let a pro confirm, but I'm guessing it should help

---

### Post by meborc on 2006-09-28
you need to reconfigure your xserver
```
sudo dpkg-reconfigure xserver-xorg
```

go through the questions... usually the default answers will do the trick... just mark the driver nvidia and the resolution that your card+monitor supports... :)

---

### Post by NewRubberSoul on 2006-09-28
Prototype Angel, about the Blue Screen.  You're right, that's a windows thing.  It startled me the same way though...

This is what makes me remember why I'm a Linux user.  I can't believe how quickly people reply!  Okay, so I got my system to boot up with X again.  I followed the advice to reconfigure X.  The first few attempts failed and X wouldn't start.  I was selecting "Nvidia" as the driver.  When I selected "nv"  it started working.

I'm still interested in whether a good enough video card to use xgl, but I'm kind of confused.  Thanks for everyones help. ;)

---

### Post by george29 on 2006-09-28
check out the link below.. but i think with the geforce2 series of graphics cards aren't up to the job if you want to run both xgl and compiz. 
[http://www.tectonic.co.za/view.php?id=1153](http://www.tectonic.co.za/view.php?id=1153)

additionally your graphics card might not be in the unified nvidia driver.. check out the link below. hence the problem when you tried to use it.

[http://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-a.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-a.html)

hope you get things sorted.
George

---

