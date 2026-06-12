---
title: "ATI Radeon 9250 - Help me make it fine &amp; dandy"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by hakunamatata on 2007-03-12
Hi, I have recently installed Ubuntu 6.10 (newbie!!) on my desktop, using Peak Radeon 9250. 128 MB card and Samsung SyncMaster 700IFT monitor. When I boot the PC the resolution is very high (2048 X 1536). However after logging in I am able to adjust the resolution to 800 x 600 - for this monitor, and it stays that way. What do I have to do to make everything look fine and dandy? Interestingly my Device Manager indicates:
PCI Bridge
RV 280 [Radeon 9200 PRO](Sec)
RV 280 [Radeon 9200 Pro]
I am a basic user - Office, Internet etc, not a gamer yet!
Thank You.

---

### Post by joshkidd on 2007-03-12
It's not entirely clear to me what you're looking for.  Is your resolution stuck at 800X600 after you adjust it?  Is the resolution that you're looking for not available when you try to select your screen resolution?

---

### Post by hakunamatata on 2007-03-12
Hi, What I meant was that when the PC boots up to the first splash screen and the login screen the resolution is very high. After logging in the resolution was high initially, but I have adjusted to 800 x 600 and it stays that way. 
Thanks.

---

### Post by roofchop on 2007-03-12
I only have 2 weeks on Linux myself, but have encoutered a similar problem.  I believe there are 2 ways you can go about fixing this problem.  

First back up your xorg.conf file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

If things get worse just restore the backup with:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

Then reconfigure the xorg file with:
```
sudo dpkg-reconfigure xserver-xorg
```
The defaults work for most of it, just make sure when you get to the screen with resolutions make sure the your desired resolution(s) has an "*" beside it.

The other option would be to manually edit the xorg.conf file with:
```
sudo nano /etc/X11/xorg.conf
```
Or whatever text editor you like.  Look for:
```
Section "Screen"

Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

```

and make sure your desired resolution is there.

HTH

---

### Post by joshkidd on 2007-03-12
Ok, as I understand it, the resolution on the login screen stays very high even after you set the resolution to 800X600.  Try clicking the "Make default for this computer" box in the window where you select screen resolution.

---

### Post by hakunamatata on 2007-03-12
Thank you joshkidd and roofchop.
roofchop - Being a luddite I tried your second option - too many questions in the first option - Did not work for me. Grey screen on bootup etc. Restored the xorg.conf file. Phew!
joshkidd - "Make default..." does not make any difference.

---

### Post by joshkidd on 2007-03-13
Can you post the contents of your xorg.conf file?  That might help in figuring out what's going on.  It might also be worth looking at this thread:

[http://ubuntuforums.org/showthread.php?t=151192](http://ubuntuforums.org/showthread.php?t=151192)

I think that your problem is related.

---

