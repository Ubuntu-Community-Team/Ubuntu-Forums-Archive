---
title: "No GUI"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Jimmy4eyes on 2007-02-20
I just installed Ubuntu on my spare desktop machine to check it out and begin learning what I could. It all went well and I was using it for a couple of days when it occured to me that I had no sound. I found a post elsewhere on this site with a detailed tutorial of what to check and how to correct that problem.

I followed it, correctly I thought, but after a reboot that was indicated at one point, I now find I've lost my graphical interface. It boots through okay, till I get login and password prompts, which then leaves me with, what to me, seems like the Ubuntu equivalent of the C: prompt in DOS.

A little research round the net suggested that typing the word startx at this prompt would give me back my UI. I did this, but what I got was a cross in the centre of the screen and a mess of color as a background, and nothing I can work with. I can only describe it like the blocky low res screen you get when you boot windows into safe mode, but much much worse. 

Can anyone please advise me what I should do. Please remember I know nothing at all about Ubuntu or any other variety of Linux. This was supposed to be the start of my learning curve but I've already fallen flat on my face it seems.

---

### Post by taurus on 2007-02-20
After you log in (before you run the startx command), run

```
sudo dpkg-reconfigure xserver-xorg
(and if you're not sure about a question, just use the default and use **vesa** as the driver for your graphic card for now.)
startx
```

---

### Post by jonti on 2007-02-20
You haven't fallen flat on your face at all :) 

It may be that all you need to do is to reconfigure the xserver-xorg package. That's the stuff that looks after the graphical interface ("GUI"). Have a look at the dpkg-reconfigure command.  If you type "man dpkg-reconfigure" you'll get some info about it. 

The command ...
sudo dpkg-reconfigure xserver-xorg
can be used to reconfigure the xserver-xorg package.

---

### Post by Zuuswa on 2007-02-20
Well, first you should post your system specifications, and any peculiar error messages you get whilst booting your machine.  A link to the guide you followed might help as well.  If your video driver was messed up, you can try entering the following command into the terminal (or command prompt/console/etc.):
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Jimmy4eyes on 2007-02-20
Following the advice from Taurus, I get the q & a shown below. It gives me a grey screen with rainbow lines running vertically down it, and what looks like a proper mouse cursor. Changing only the desired X server driver to vesa as Taurus suggested gives me a solid dark blue screen with no mouse cursor.


Attempt to autodetect video hardware : yes

Select the desired X server driver : nv

Screen then shows NVIDIA Corporation NVCrush11 [GeoForce2 MX Integrated Graphics]

Video Cards Bus Identifier : PCI:2:0:0

The next screen asks me to enter the amount of memory (in kb) to be used by my video card. I have no idea what to enter here so I left it blank

Use kernel framebuffer device interface? : No

Autodetect keyboard layout? : No

Please select your keyboard layout : uk

Please select the XKB rule set to use : xorg

Please select your keyboard model : pc104

Please select your keyboard variant : uk

Please select your keyboard options : 	uk

Please choose the entry that best describes your mouse : ImPs/2

Emulate 3 button mouse : Yes

Select the X.Org server modules that should be loaded by default : bitmap
								                                 ddc
								                                 dri
								                                 extmod
								                                 freetype
								                                 glx
								                                 int10
								                                 type1
								                                 vbe
								
Write default Files section to configuration file? : Yes

Attempt monitor autodetection? : Yes

Enter an identifier for your monitor : HP56

Select the video modes you would like the X server to use : 1024 x 768
								                       800 x 600
								                       640 x 480

Please choose a method for selecting your monitor characteristics : Advanced

Enter your monitor's horizontal sync range : 28-51

Enter your monitor's vertical refresh range : 43-60

Write monitor sync ranges to configuration file? : Yes

Please select your desired default color depth in bits : 24

Oh, and as I was typing this info into my laptop, the desktop screensaver appeared to kick in, although it only blanked the screen till I moved the mouse.

---

### Post by Jimmy4eyes on 2007-02-20
I forgot to give the link to the sound tutorial I originally followed. It's [[COLOR="Blue"]here[/COLOR]]("http://www.ubuntuforums.org/showthread.php?p=2181295&posted=1#post2181295")

---

