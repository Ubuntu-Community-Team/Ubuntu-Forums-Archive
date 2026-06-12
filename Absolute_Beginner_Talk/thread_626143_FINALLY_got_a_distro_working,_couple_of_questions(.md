---
title: "FINALLY got a distro working, couple of questions(printing, dualhead, kbd)"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Mysticle31 on 2007-11-28
So I've been playing with Linux for a couple of days now, more like a week really.  First I had to choose a distro, so I downloaded many many live CDs and played.  I had chosen SUSE, however it would NOT enable dual headed mode.  I was getting constant "cought signal 11" problems, which I learned was a program asking for memory that didn't exist.  Enabling root login so I could modify files and not get "access denied" in the gui was a major pita for me.  All is good now.  I don't know how to work the cmd line well enough to do what I needed without the gui.

Anyhow, I finally got Kubuntu reasonably up an running.  I'm an experienced windows user, so it makes me feel dumb asking some of these :).  Sorry for the book, I may split these up later.  I'm off to work for a couple hours and want to get it all out there.

1) I have an OfficeJet 7310.  Windows has a cool program available for it called FinePrint.  It's very useful for printing something.  You can see a preview of the document, deleate pages, enable duplexing, print booklets, watermarks...etc.  

Is there a program like this for Linux?  I couldn't find one.  I did find a script someone made, but I never got it to work and am under the impression that it only allows duplexing, and what I want is a little more.  At least the preview with the option to allow duplexing and delete pages.

Will the scanner and ADF still work?  

2) I have two Mitsubishi Diamond Pro CRT monitors.  I had a hell of a time making dual headed mode work in SUSE (even when it worked there were lines and artifacts), but it worked straight away in Kubuntu.  Very nice.  Then I came to find out that I can't move windows from one monitor to the other, which is part of what I want.

What happens now is: I can move my mouse from monitor 1 to monitor 2 and launch something, but what opens on monitor 1 stays on monitor 1 and vice versa.

In windows I used a program called UltraMon which gave me a taskbar on my other monitor, amoug other things.  

How can I drag windows to the other monitor yet at the same have their maximize buttons only maximize to that monitor and not the whole desktop?  I would be fine with some sort of "switch monitor" button.  

3) I have a Logitech MX5000 Keyboard with a MXLaser mouse.  The mouse has buttons on the side.  Any way to make those work?  Back, forward, switch task would be nice.

The keyboard has media buttons.  The volume slider works very nicely.  The zoom and play, stop..etc do not.  Any way to make those work?

4)  I an trying to play with compiz-fusion, but its not working.  The install was done, and the control Emerald Theme Manager and Advanced Desktop Effects applets are there, and I can poke around in them and change things.  However, nothing happens in the gui.  I'll probably make another post about this problem. I wonder if compiz-fusion can help me with my dual-headed problem?

---

### Post by parm289 on 2007-11-28
> 4) I an trying to play with compiz-fusion, but its not working. The install was done, and the control Emerald Theme Manager and Advanced Desktop Effects applets are there, and I can poke around in them and change things. However, nothing happens in the gui. I'll probably make another post about this problem. I wonder if compiz-fusion can help me with my dual-headed problem?

Go to the terminal and type:
```

emerald --replace compiz &

```
To try to get themes to show up when chosen.  This worked for me.  Also, this may reset your settings in CCSM (Compiz-Fuzion settings manager), so be careful.  Post back here if you get the "no window borders" bug.

Welcome!

---

### Post by Pumalite on 2007-11-28
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by jken146 on 2007-11-28
Hi there,
This is what I can answer:

> **Mysticle31 said:**
> 
1) I have an OfficeJet 7310.  Windows has a cool program available for it called FinePrint.  It's very useful for printing something.  You can see a preview of the document, deleate pages, enable duplexing, print booklets, watermarks...etc.  
You can usually set these options when you print, in many programs.  I think this will depend on how good the driver for your printer is though.  As for deleting pages, I have never needed a new program to do that, I just set the appropriate page range in File>Print.

[QUOTE=Mysticle31]
4)  I an trying to play with compiz-fusion, but its not working.  The install was done, and the control Emerald Theme Manager and Advanced Desktop Effects applets are there, and I can poke around in them and change things.  However, nothing happens in the gui.  I'll probably make another post about this problem. I wonder if compiz-fusion can help me with my dual-headed problem?[/QUOTE]
You may need to actually start compiz.  The command is compiz --replace

---

### Post by Mysticle31 on 2007-11-28
I'm not at my computer now, so I cant run the start command for compiz fusion,  I did run it though when I installed compiz fusion.  I don't remember anything happening, no sucess or error messages.  I'll try again when I get home in a couple hours.

As to printing, I know that you can select what pages to print.  However you have to print privew first to know what pages to print, and what if you only want pages 2 ,3, ,7 and 10 or something like that?

Any advise as to the monitors or keyboard/mouse?

Sorry for typos - little keyboard

---

### Post by poudin on 2007-11-28
check this thread for the mouse+keyboard issues

[http://ubuntuforums.org/showthread.php?t=65471&highlight=logitech+500](http://ubuntuforums.org/showthread.php?t=65471&highlight=logitech+500)

hope it helps...should work...just a matter of configuring it correctly..

good luck

---

### Post by Mysticle31 on 2007-11-29
Alright, I Fed this thing up BIGTIME.

I tried running the compiz --replace command and got an error.  Something along the lines of couldn't access display.  So I tried to fix it by adding permissions for all users and DISPLAY=0.0 to the environment file.  Well I fed that up.  When I rebooted I found the gui VERY lethargic.  With no idea how to fix (removing DISPLAY=0.0 didn't do it) I'm re-formatting and installing again (for the upteanth (sp??) time!)  Whoever said linux was going to be challenging to configure was NOT lying!!  The furthest I've gotten is with Kubuntu.  I have a copy of Xandros and PClinux sitting on my desk to try :P

As for the mouse, my MX Laser is a bluetooth mouse.  Those directions did not work.  I also found these ([https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)) but again dealing with a USB mouse.  I don't know if they will work. 

Any ideas as to the couldn't access display?  What is the command for Ubuntu to leave the GUI and go to text mode?  I had gotten used to init 3.  How do I get back to KDE if I'm in this mode?

Thanks for the monitor tips.  I hope they work.  I will be interesting to see if the maximize button maximizes to the whole desktop (two monitors) or just the one.  That would be a PITA.  Too bad there is no way to get a "move to monitor" button.  I would like to keep by DVR program (Myth TV probably) separate from compiz if it ever works.

---

### Post by Mysticle31 on 2007-11-29
Okie Dokie, I've got Kubuntu all up and running now.  (I find it interesting that Konqueror spell check does not recognize it's own name and Kubuntu as I type this.. ha ha)  

I decided to install the updated ATI drivers and CCC using the manual install rather then the package installer found here:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.11_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.11_Driver_Manually)

There are two interesting things to note about my install.

1) This command gave me a x server display access problem. 
kdesu kate /etc/default/linux-restricted-modules-common
to which I solved by creating the file elseware and moving it to the "directory" (windows guy here, what do they call them in Linux?)

2)  Right now the ATI CCC works perfectly, I can even enable big desktop mode.  (although I do find it annoying that all the program windows and icons are ALL on my left (secondary) monitor.  Do I have to live with it?  How do I get a task bar over there?) 

Monitor and Desplay applet shows that I'm using driver fglrx.

However when I run fglrxinfo and glxinfo I find Mesa and not ATI.  It's interesting that the ATI's CCC did not give me a "ATI Device not found" error if I was really using the Mesa drivers.  (it did that to me in suse alot)

I even went an uninstalled the xserver-xorg-video-all meta package like it says in the instructions and I am STILL reporting Mesa.  Here is my xorg.conf.  I see one of the device sections still says ATI for the drivers.  Maybe I should change it?

> Section "Monitor"
	Identifier   "DPro 2070SB"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor    "DPro 2070SB"
	DefaultDepth     24
	SubSection "Display"
		Modes    "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection



---

### Post by Mysticle31 on 2007-11-29
Any ideas as to the drivers?  It's still saying Mesa.

On another note, I played with compiz fusion and I FINALLY got compiz --replace to do something other than cannot open display.  It makes my screen go black, and then white and I have a little mouse cursor I can move around on a completely white screen!

On another note.  Bluetooth often "forgets" to pair the mouse and keyboard and I have to go do it with my other mouse and keyboard.  It's most annoying.

---

### Post by Mysticle31 on 2007-11-29
Maybe I should just say screw this and go back to XP if it's hopeless..

---

