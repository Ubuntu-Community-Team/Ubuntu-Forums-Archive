---
title: "Installing Monitor Driver for Samsung 913n?"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by catstar on 2006-05-07
Hi,

I am an absolute beginner :rolleyes:  and since buying my new samsung 913n 19" TFT - I have become a little unstuck.

I'm afraid I don't know how to install the driver for the monitor as it seems to require executing x-window and creating x86 config file, I have tried a few things, but ultimately I don't know what to do.

Can some kind person give me a break down of exactly what I have to do in order to get this sorted?  At present the monitor is working, however the text is huge.  It would be great if someone could help, thanks.  :confused:

---

### Post by richbarna on 2006-05-07
You can change the resolution from the keyboard.
> <Ctrl><Alt><+> 
 (in X-windows) Change to the next X-server resolution (if you set up the X-server to more than one resolution). For multiple resolutions on my standard SVGA card/monitor, I have the following line in the file /etc/X11/XF86Config (the first resolution starts on default, the largest resolution determines the size of the "virtual screen"): 
 Modes "1024x768" "800x600" "640x480" "512x384" "480x300" "400x300" "1152x864"Z 
 Of course, first I had to configure the X server, either by using Xconfigurator, xf86config, or manually by edition the file /etc/X11/XF86Config, so that it supports the above resolutions (mostly the matter of uncommenting the line that defines my video chipset, and specifying the synchronization frequencies my monitor supports). XFdrake (Mandrake configuration utility) can do it from GUI. See also the commands xvidtune and xvidgen. 
<Ctrl><Alt><-> 
 (in X-windows) Change to the previous X-server resolution.
I found this at :- [http://www.er.uqam.ca/nobel/r10735/unixcomm.html]("http://www.er.uqam.ca/nobel/r10735/unixcomm.html")

---

