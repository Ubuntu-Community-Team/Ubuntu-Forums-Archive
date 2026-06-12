---
title: "How to get the Command Line?"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Handssolow on 2006-10-23
Simple I know but I want to get to the Command line without the graphical interface being active, not just a terminal window.

I've replaced my ATI graphics board with a Geforce 6600 gt using the vesa driver but I'm thinking it's slower that it should be. I've not been to get the nvidia driver to work at all.

It's looking like I need to access the command line to install the nvidia driver that I've downloaded. CTRL+ALT+F1 does nothing.

I'm assuming I've correctly identified my keyboard type having recently run

sudo dpkg-reconfigure xserver-org

more than a few times!!

Why doesn't CRTL+ALT+F1 work?

---

### Post by Bachstelze on 2006-10-23
Seems you were misleaded... You can perfectly well install the nVidia drive from within a terminal window :)

---

### Post by Lord Illidan on 2006-10-23
Wait a bit... If you are talking about installing the nvidia driver from the official website, you can do it yourself from apt-get.

Just type ```
sudo apt-get install nvidia-glx
``` from a terminal,even a gnome terminal will do. Make sure your repositories are open.

---

### Post by Bachstelze on 2006-10-23
... and then run

```
sudo nvidia-glx-config enable
```

restart X with Ctrl+Alt+BkSp, voilà :)

---

### Post by CatKiller on 2006-10-23
If you use ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then you only get asked high priority questions about your X setup. Might stop it being quite so frustrating. :)

Do any of the other virtual consoles (F2-F6) work? I think it's ```
sudo /etc/init.d/gdm stop
``` to turn off the graphical stuff, and ```
sudo /etc/init.d/gdm start
``` to turn it on again. I haven't ever tried it though, so it might not be.

Not that you need to do any of this stuff, though since, as everyone else has said, you can use apt-get/aptitude/Synaptic to install the nVidia drivers. Oh, and in the meantime the "nv" driver might be more compelling than the "vesa" one.

---

### Post by Handssolow on 2006-10-23
I'll have a go with your suggestions but I've been working at it for several hours following the advice that available on the media section I can only use the vesa driver so far.

I'm not sure if changing from ati to nvidia has helped.

Also it's an AGP slot card.

---

### Post by Bachstelze on 2006-10-23
Do just that and you should be fine :

```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```

Then restart X with Ctrl+Alt+Backspace

---

### Post by Handssolow on 2006-10-23
I'm still not able to get CTRL+ALT+F1, any further suggestions. None of my function keys work. I'm not sure why now but sudo /etc/init.d/gdm stop didn't do anything. I'm sure I've used this yesterday to stop and start the gui.

I'll need to use the command line if I want to follow tseliot's advice about installing the nvidia driver for my agp card. I'm wanting to use the full potential of my Geforce 6600 gt agp card.

I have now managed to use the  "nv" driver instead of "vesa", although I haven't noticed any graphic different apart from having to re-centralise my lcd monitor.

Running glxgears gives this response

Xlib: extension "GLX" missing on display " :0.0"
Error: couldn't get RGB, Double-buffered visual 

What's all this about then?

Google Earth reports my driver isn't up to date and a black sky with no stars.

Any change to using "nvidia" as a driver doesn't causes Xserver to crash.

There aren't any mobo bios settings I need to change are there?

---

### Post by Handssolow on 2006-10-23
Well, I'll have to apologise to any readers of my previous postings. The ultimate solution of my problem was simple.

I've now got the nvidia driver working with my Geforce 6600gt agp card which replaced my ATI Rage Fury 128 agp card, glxgears works well and so does GoogleEarth. Ok, I've had to adjust my lcd monitor again!!

It was my suggestion to consider my mobo's hardware bios settings, there was nothing I needed to change. However, I then checked the graphics card installation booklet and realised that I'd not connected the extra molex power supply to my 6600 gt card. Apologies to all for my simple error.

I used Automatix again to reinstall the nvidia Driver and it all worked.

Yes, my CTRL+ALT+Function keys still don't work, but then, that's a problem for next time.

---

### Post by Lord Illidan on 2006-10-23
> **Handssolow said:**
> Well, I'll have to apologise to any readers of my previous postings. The ultimate solution of my problem was simple.

I've now got the nvidia driver working with my Geforce 6600gt agp card which replaced my ATI Rage Fury 128 agp card, glxgears works well and so does GoogleEarth. Ok, I've had to adjust my lcd monitor again!!

It was my suggestion to consider my mobo's hardware bios settings, there was nothing I needed to change. However, I then checked the graphics card installation booklet and realised that I'd not connected the extra molex power supply to my 6600 gt card. Apologies to all for my simple error.

I used Automatix again to reinstall the nvidia Driver and it all worked.

Yes, my CTRL+ALT+Function keys still don't work, but then, that's a problem for next time.

Simple error that anyone can make. About the function keys, could it be you have an F-lock key on your keyboard?

This might also help : [http://www.faqs.org/docs/Linux-HOWTO/Keyboard-and-Console-HOWTO.html#ss7.1](http://www.faqs.org/docs/Linux-HOWTO/Keyboard-and-Console-HOWTO.html#ss7.1)

---

### Post by Handssolow on 2006-10-23
It's another day and I'd still like to know how I can use CONTROL+ALT+F1 to close the gui and to get to a command line rather than use a terminal window, though I must add that it's less important now I've got the nvidia driver working rather than vesa.

Function keys can be programmed using System>Preferences>Keyboard shortcuts. However, closing the gui doesn't seem to be an option.

---

### Post by CatKiller on 2006-10-23
You don't need to set it up as a keyboard shortcut. Perhaps you don't have any virtual consoles running? For example, if I do **ps ax**, part of the output is > 4969 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 4970 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4971 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4972 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4973 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4974 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 These are the virtual consoles that are running and accessible through the F1-6 shortcuts. I don't know how to make them happen if they aren't there already, or a more sensible way to check if they're running, but it's something to think about.

---

### Post by maaronB on 2006-10-23
> **Handssolow said:**
> l.
...
It's looking like I need to access the command line to install the nvidia driver that I've downloaded. CTRL+ALT+F1 does nothing.

...

Why doesn't CRTL+ALT+F1 work?

Are you holding down CTRL + ALT then (while still holding them down) pressing F!.  And that does nothing?  Because it should change you to tty1.

edit:
Just for an FYI when CTRL+ALT+F! works correctly it doesn't actually close the GUI.  It just shifts to a virtual terminal.  The GUI is still open under CTRL+ALT+F7.

---

### Post by Paul133 on 2006-10-23
And there are 6 graphical consoles and 6 non graphical consoles?

---

### Post by maaronB on 2006-10-23
> **Paul133 said:**
> And there are 6 graphical consoles and 6 non graphical consoles?

I don't think so.  I believe the default is Ctrl+ALT+F1 - F6 are non-graphical and F7 is graphical.  The rest are nothing/free for you to configure.  

Also the graphical setup is not set up to be F7 it is set up to be the first nonused console.  So if you added another nongraphical for somereason it would become F7 and the graphical would become F8.

This is kind of advanced though.  I have read about people setting up multiple distro's on different consoles so that they can quickly switch between them.  But that is probably not something to be covered in the Beginner forum.

---

### Post by furiousV on 2006-10-23
I'm very very surprised you actually managed to boot into a full desktop environment, an operating system even, *without* the molex connector plugged in :confused: :confused: 

And if I remember correctly (writing from Win2000), Ctrl+Alt+F7 to F10 are graphic consoles. At least in SUSE 10 they were.

---

