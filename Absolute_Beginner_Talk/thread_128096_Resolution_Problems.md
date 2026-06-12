---
title: "Resolution Problems"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by Screaming Monkey on 2006-02-10
Hey there...I've installed, with no problems, Xubuntu on one of my computers, however I can't get the screen resolution to what I know the card is capable of.  I reconfigured with all of the appropriate information and still can only get a 640 x 480 resolution.  I had windows 98 (*gack*) on there before and was easily running 800 x 600.  There is a Cirrus Logic card in there.  Any help would be appreciated.  I would like to get it to at least 800 x 600 res'n.

---

### Post by benblur4 on 2006-02-26
I am having the exact same problem.
I can hardly read anything!

---

### Post by schenkin on 2006-02-26
have you triend manually reconfiguring your xorg.conf file?

The screen resolution utility in KDE only lets you switch between resolutions specified in the configuration file. To add the resolutions there, either run "sudo dpkg-reconfigure xserver-xorg" and make sure to select the proper resolution. Also, I think some drivers won't allow above 600x800, before I got the new drivers installed for my card i used VESA which allowed higher res's and seems to work on most card.

If that doesn't work you can try manually adding the resolution to your conf file:

sudo nano /etc/X11/xorg.conf

in "Section 'Screen'" add your desired resolution to each "SubSection 'Display'" Next to Modes. For instance, change:

[INDENT]Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon X700 (RV410)"
	Monitor    "DELL 2005FPW"
	DefaultDepth     24
	SubSection "Display"
[INDENT]		Depth     1
		Modes    "800x600" "640x480"[/INDENT]
	EndSubSection[/INDENT]

to:

[INDENT]Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon X700 (RV410)"
	Monitor    "DELL 2005FPW"
	DefaultDepth     24
	SubSection "Display"
[INDENT]		Depth     1
		Modes    **"1024x768"** "800x600" "640x480"[/INDENT]
	EndSubSection[/INDENT]

then save the file. Make sure to do this for each subsection. You may have to tell KDE to use this new resolution in "System Settings" > "Display" . 

I hope this isn't too wrong and it helps, i'm a newbie myself but this is what I did to fix a similar problem on my machine.

---

### Post by Sandlst on 2006-02-26
Try schenkin's post before trying this one

I always have this problem on a fresh install for some reason, heres how I fix it:

First, make a backup of xorg.conf in terminal (Applications/Accessories/Terminal)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

If something goes wrong after following this post it will dump you into a command prompt, enter these commands:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

Fun time!

Before you do this, see if you can find the vertical and horizontal sync/refresh rates for your monitor-it will ask  you for these at some point-my screen was a laptop screen and I lost the manual, but the default option worked fine for me, putting an incorrect value in here however can DESTROY YOUR MONITOR so procede at your own risk:
run this in a terminal:```
sudo dpkg-reconfigure xserver-xorg
```
you can select things by moving the curser with arrow keys, then pressing space to select stuff.  Default options should work fine for most everything-eventually, it will ask you to select resolutions you would like X to use-select the ones you want, but note that it has already selected some resolutions (the list can keep scrolling down off the screen) which tripped me up for a while-try deselecting these as well as selecting the ones you want. After it finishes hit ctrl+alt+backspace two times, and hopefully you will be in business.  Post back if you have any problems

Arg should have refreshed the thread before posting, schenkin's solution is much, much safer to do, and probobly would have prevented many headaches Ive had making this work in the past :)

---

### Post by schenkin on 2006-02-26
Woops, forgot to say to backup it up! always do that first!

---

### Post by agarwaldvk on 2006-02-26
Hi

Try this link :-

[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

I had identical problem. I fixed it using guidelines there.

I am an absolute beginner myself and hence not suggesting anything but the above link does provide for some very good tips.


Best regards


Deepak Agarwal

---

### Post by LucidParody on 2006-03-14
[QUOTE=Sandlst]After it finishes hit ctrl+alt+backspace two times, and hopefully you will be in business.  Post back if you have any problems[/QUOTE]

Hi, I'm using the live cd, to see if I can get get my monitor resolution working before I install.  I can't seem to ctrl+alt+backspace to restart my xserver.  Is there any other way to restart the xserver on the live CD?

---

### Post by LucidParody on 2006-03-17
bump...anyone?

please dont make me continue using windows. :cry:

---

