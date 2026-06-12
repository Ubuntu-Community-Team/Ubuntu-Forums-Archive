---
title: "Slow graphics in 5.10"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by cls1chuck on 2006-04-08
Ok, I have 5.10 installed on my system (an ABIT NF7-S2, which has Trident Cyberblade-XP video, and NVIDIA n/s bridge). When I move a window (by dragging on the desktop), I see 'ghosting'
.  Device Mgr shows device type and capabilities as 'unknown' for my CyberBlade XP;  lspci listing is below.

Do I have a driver problem, an archaic PC (1.7Ghz AMD w/512MB RAM), or is this just 'linux'?

lspci listing:

0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (r ev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0080 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0084 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 0087 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 0087 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 0088 (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 008 a (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation: Unknown device 008b (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation: Unknown device 0085 (rev a3)
0000:00:0b.0 IDE interface: nVidia Corporation: Unknown device 008e (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)
0000:02:0b.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 8d)

---

### Post by dermotti on 2006-04-08
You have nvidia-glx installed?

---

### Post by taurus on 2006-04-08
You need to install nVidia driver for your video card.  Here is a link for you so read it and follow it.  Let me know if you run into problems...

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

---

### Post by cls1chuck on 2006-04-09
According to Ubuntu (and Windows), I have a Trident video card - do I still need the nVidia drivers?  I have nVidia chipset for my Abit NF7-S2 mobo (north/south), and I know ONE (Southbridge, I think) controls the graphics, but I don't think (according to what I had in the list I posted) that the VIDEO card is nVidia.
Are the instructions you gave me for nVidia chipset or an nVidia video card?
When I went to follow the directions, I got to the part about modifying the 'device' section.  The example on line showed the device as nvidia, but my copy shows Trident.  this leads me to believe I should *NOT* attempt this change.  Am I correct in this assumption?

Not trying to question the help you are providing, I'm just a bit confused and want to be sure of what I'm doing.

Thanks!

---

### Post by dcstar on 2006-04-09
[QUOTE=cls1chuck]According to Ubuntu (and Windows), I have a Trident video card - do I still need the nVidia drivers?  I have nVidia chipset for my Abit NF7-S2 mobo (north/south), and I know ONE (Southbridge, I think) controls the graphics, but I don't think (according to what I had in the list I posted) that the VIDEO card is nVidia.
Are the instructions you gave me for nVidia chipset or an nVidia video card?
When I went to follow the directions, I got to the part about modifying the 'device' section.  The example on line showed the device as nvidia, but my copy shows Trident.  this leads me to believe I should *NOT* attempt this change.  Am I correct in this assumption?

Not trying to question the help you are providing, I'm just a bit confused and want to be sure of what I'm doing.

Thanks![/QUOTE]
You are correct, your video is listed as Trident, but possibly there was a problem when installing in detecting it.

Open a terminal and do:
```
sudo dpkg-reconfigure xserver-xorg
```
See if it picks out a Trident or Nvidia driver for your hardware, otherwise see if you can manually select one.

If you restart X and it doesn't work, then CTRL-ALT-F1, log in and repeat the procedure.

---

### Post by cls1chuck on 2006-04-09
I believe my video card *IS* a Trident CyberBlade.  Should I try nvidia even if i have a Trident?  I cannot tell by looking at the card; the sticker on it says "3DForce G-32", for which I Googled and found links to a company called Jado, which says it is a Trident.  So I think that part is correct.  BTW, Lavalys EVEREST also IDs it as Trident CyberBlade.
Thanks,

---

### Post by taurus on 2006-04-09
Try using Trident first to see if it works and if not, you can always go with nvidia later.

---

### Post by cls1chuck on 2006-04-10
I get an error when trying to run dpkg:

 sudo dpkg -reconfigure xserver-xorg
dpkg: conflicting actions --control and --remove

NOTE: I *DID* shut down Gnome first!

also, glxheads (I got this idea from another thread) returns:

glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Xlib:  extension "GLX" missing on display ":0.0".
Error on display :0 - Unable to find RGB, double-buffered visual

---

### Post by taurus on 2006-04-10
[QUOTE=cls1chuck]I get an error when trying to run dpkg:

sudo dpkg -reconfigure xserver-xorg
[/QUOTE]
It's
```

sudo dpkg-reconfigure xserver-xorg

```
You have an extra space between dpkg and -reconfigure!!!  ;)

---

### Post by cls1chuck on 2006-04-10
Darn - I was just going to post that I figured that out - but you were too quick ;)

So now I did the reconfigure; let it autodetect; there is good news and bad news in the results.
Good - it appears (through limited and unscientific testing) that I am getting less 'ghosting' when i drag windows
Bad - 3-D games such as penguin-racer and slune do not start, and glxgears/glxheads now show an error message:
***
ubuntu:~$ glxheads
glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Xlib:  extension "GLX" missing on display ":0.0".
Error on display :0 - Unable to find RGB, double-buffered visual
***

ideas?  Also, note this line from my lspci (which has not changed but has me concerned):
***
ubuntu:~$ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (r ev c1)
***

Thanks again everyone for continuing to help me with this!

---

### Post by taurus on 2006-04-10
Did you look at the link in my previous post, #3, to install nVidia driver for your video card?  See if it removes the ghosting that you have experienced on your machine.

---

### Post by cls1chuck on 2006-04-10
Thanks, but my card is a Trident, not nVidia.  FYI I tried manually selecting nVidia when I did the dpkg-reconfigure, but gnome would not start. It only starts when I pick Trident.
Turns out ghosting is *STILL* there when I have multiple windows open.

Also, see my previous post - since monkeying with this, none of the '3D' games (e.g. penguinrace) I installed will start. I even restored the .CONF file. 
glxinfo:

chuck@aopen-ubuntu:~$ glxinfo |head
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
c

---

