---
title: "Dual G5 PowerMac boots CD I hear login sound but...."
date: 2011-07-31
forum: Apple Hardware Users
---

### Post by durablemrmatt on 2011-07-31
Not long after booting my monitor goes black, says no signal.  The computer eventually boots and gives me the login sound.  I have tried all the nosplash and video=ofonly options and this keeps happening.

I also have an old G4 tower and that one will boot just fine.  

The G5 has the NVidia GForce FX5200.  I am using the apple adaptor to hook it up to a Planar flatscreen monitor.

As apple has left the PowerPC computers behind, I would REALLY like to get Linux running on this box.

If anyone can help me get past this video shutoff I can probably figure everything else out.  I have LOT's of *Nix experience over in the intel world.

Thanks!

Matt Anderson

---

### Post by rsavage on 2011-08-01
You probably need to setup an xorg.conf file.  I've put a brief bit about this on my lubuntu thread [http://ubuntuforums.org/showthread.php?t=1798792](http://ubuntuforums.org/showthread.php?t=1798792) .

---

### Post by rsavage on 2011-08-01
I've just had a look at the G5 sample xorg files on linuxopjemac's website. They have some monitor specific lines in there, so if I were you I would set up my own xorg.conf:
 
sudo Xorg -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf
sudo nano /etc/X11/xorg.conf
 
You probably only want 1 device section, 1 screen section, 1 monitor section so you may have to delete some sections if it gives you two (natty did this to me). You will have to change the ServerLayout section to reflect any changes.
 
You will then have to use the cvt command to find your monitor setting for the resolution you want and add a modeline into the monitor section using the output from the cvt command. You can add as many resolutions/modelines as you like.
 
e.g.
 
$ cvt 800 600 
 
gives:
 
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz 
Modeline "800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
 
So you paste the modeline into here (uncomment the preferred mode bit if you want to set that):
 
Section "Monitor" 
Identifier "External DVI" 
Modeline "800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync 
#Option "PreferredMode" "800x600_60.00"
EndSection
 
You may also have to adjust your screen section like they've done here [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ#Screen resolution is wrong, no matter what I do!!](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ#Screen resolution is wrong, no matter what I do!!) , but hopefully the resolution(s) will be picked up automatically.
 
Let us know if you get it working and what you had to do. I want to add a bit more to my lubuntu thread so the info would be useful to me!

---

### Post by linuxopjemac on 2011-08-01
exactly, that's the way to go rsavage.

---

### Post by durablemrmatt on 2011-08-01
This in trying to run the live cd.  I can not switch to a terminal and make any changes.  Nothing I do will bring a signal back to the monitor so I can not make any changes.  If I can ever get it installed I would boot into level 3 and do all the stuff suggested.  I need to be able to see to install first!

Thanks!

Matt

---

### Post by linuxopjemac on 2011-08-01
Why don't you install from the alternate CD? Is much easier to my opinion.

---

### Post by rsavage on 2011-08-01
I gave you a link to follow.  That then links to all the relevant manuals.  So following the links it will tell you to do ctrl+alt+F1 to get to a terminal.  Have you tried this?  It may take a few reboots.  You can then add resolutions (outside of xorg.conf if you wish).  You just need to follow the links and read the documentation.

---

### Post by rsavage on 2011-08-01
I don't think there is going to be some simple yaboot parameter that is going to instantly fix your screen. Using the alternate installer maybe the simplest thing for you. However, you could try a combination of the following parameters
 
nosplash video=ofonly nouveau.modeset=0 
 
Unfortunatly, I'm not familiar with the nouveau cards, there could be some other video= thing you could try that I don't know about.
 
Sorry I can't be more help.

---

### Post by pauljwells on 2011-08-02
I have a G5 dual core running perfectly with 11.04. I had to use the alternate installer too. I suspect the adapter you are using is the culprit. Can you borrow a straightforward vga or dvi monitor and cable to get started with? I found that a dvi to vga adapter stopped my monitor from working.

---

### Post by rsavage on 2011-08-02
Some people have got an adaptor working [http://ubuntuforums.org/showthread.php?t=1033066](http://ubuntuforums.org/showthread.php?t=1033066) .  They use the cvt command like I said to do.  An explanaion of the other commands is in the documentation I linked in my lubuntu thread.
 
If you get to a login screen on the live cd then is the default user account called 'ubuntu' with no password?  Haven't run it for a while so couldn't say.
 
Alternate is probably easiest way to go though.

---

