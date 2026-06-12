---
title: "did I do something wrong?"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Chuck_W on 2006-03-19
I tried to install Ubuntu 5.1 on an old Dell PC. It is a Pentium 3, 800mhz with 128mb RAM and a 3.2gb hard drive. The onboard video was flaky under Windows so I added a Matrox PCI card. The Ubuntu install process seemed to go ok. No crashes or error messages. When the computer is started I get the splash screen where it says it is loading modules, etc. After that is done it goes to a black screen with a flashing cursor. Soon the cursor stops flashing, there is about 10 seconds of hard drive chatter and then nothing. It does not respond to the keyboard. About 10-20 minutes later there was some additional hard drive activity but then nothing. Where do I go from here?
Thanks

---

### Post by gymsmoke on 2006-03-19
Chuck~
Have you tried going back through the installation ?  It sounds like something went awry during the install...
I'm also pretty new to Ubuntu, but I'll be happy to try and help as much as I can...
Possibilities:
check the HCL list?  Maybe that particular video card isn't there...
Will the monitor sync with the video card/mode? - I had a world of trouble with this on other distro's...

---

### Post by az on 2006-03-19
[QUOTE=Chuck_W]I tried to install Ubuntu 5.1 on an old Dell PC. It is a Pentium 3, 800mhz with 128mb RAM and a 3.2gb hard drive. The onboard video was flaky under Windows so I added a Matrox PCI card. The Ubuntu install process seemed to go ok. No crashes or error messages. When the computer is started I get the splash screen where it says it is loading modules, etc. After that is done it goes to a black screen with a flashing cursor. Soon the cursor stops flashing, there is about 10 seconds of hard drive chatter and then nothing. It does not respond to the keyboard. About 10-20 minutes later there was some additional hard drive activity but then nothing. Where do I go from here?
Thanks[/QUOTE]

Hit escape as you boot to reveal the grub boot menu if it is not already shown.  Pick the rescue mode entry.  Boot that.

Once at the command line type

apt-get -f install
(to see if any packages were not properly installed)
apt-get install ubuntu-desktop
(to see if any packages are missing)
dpkg-reconfigure xserver-xorg
(that reconfigures your graphics.  Your card is supported, but it mey be misconfigured.  You can try to pick the vesa driver and see if that works.)
Type 
init 2
to try to restart the desktop.  Lemme know if that worked...

---

### Post by Chuck_W on 2006-03-19
This seems to be a video issue. The Matrox card uses the generic S3 driver under Windows and the onboard video is ignored. It seems that Linux blows past that. During the configuration process I told it to use the S3 driver but later it asked for a name and the default was the onboard (nvidia TNT2 model 64). The next thing will be to remove the Matrox card and reconfigure for the nvidia. Will post back with results.

---

### Post by Chuck_W on 2006-03-19
Well, that didn't work. After reconfiguring and restarting it pops up with "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly." There was no useful (to me) information from the X server output. It may be that the configuration process asks questions that I can only guess at. It wanted to know what the PCI id is. With the Matrox card removed I am using the integrated NVIDIA TNT2 4X AGP onboard video. I have no idea as to what should go there as well as the answer to other questions. At this point I'm going to give it a rest. This is my third attempt at Linux. The first was Slackware 3.3 from 1997 followed by NetBSD 1.5.2 from 2001 and now Ubuntu. I have yet to get to where I could actually do something! It was actually easier to set up Windows NT on a Pentium Pro 180 machine! My next step will be to try to contact a local user group and see if I can't get some hands-on help.
Thanks again.

---

### Post by Mustard on 2006-03-19
I assume you've got two systems, since you are posting in here.  You can always try the IRC support channel at irc.freenode.net on #ubuntu.

---

### Post by az on 2006-03-19
[QUOTE=Chuck_W]Well, that didn't work. After reconfiguring and restarting it pops up with "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly." There was no useful (to me) information from the X server output. It may be that the configuration process asks questions that I can only guess at. It wanted to know what the PCI id is. With the Matrox card removed I am using the integrated NVIDIA TNT2 4X AGP onboard video. I have no idea as to what should go there as well as the answer to other questions. At this point I'm going to give it a rest. This is my third attempt at Linux. The first was Slackware 3.3 from 1997 followed by NetBSD 1.5.2 from 2001 and now Ubuntu. I have yet to get to where I could actually do something! It was actually easier to set up Windows NT on a Pentium Pro 180 machine! My next step will be to try to contact a local user group and see if I can't get some hands-on help.
Thanks again.[/QUOTE]


So, you removed the matrox card, booted into recovery mode, reconfigured X and then rebooted?

Every time you change video hardware, you will need to re-run the X configuration from recovery mode.

For your onboard video chip, boot into recovery mode and run
dpkg-reconfigure -phigh xserver-xorg
it will not ask you any of the questions as before.  Go into init 2 

init 2
and it should work (tm)

---

### Post by Chuck_W on 2006-03-20
Thanks AZZ. It worked! This is being written from my "new" Ubuntu computer. Unfortunately, there are always trade-offs. I now remember why I put the Matrox card in to begin with. Something with the onboard video is flaky and it wants to put streaks across the screen. It is useable but annoying. With more research I'm sure I'll find a way to have Ubuntu ignore the onboard video and go only to the Matrox card. Thanks again. You've been a lot of help. Hopefully someday I will be able to "pay it forward".

---

### Post by az on 2006-03-20
[QUOTE=Chuck_W]Thanks AZZ. It worked! This is being written from my "new" Ubuntu computer. Unfortunately, there are always trade-offs. I now remember why I put the Matrox card in to begin with. Something with the onboard video is flaky and it wants to put streaks across the screen. It is useable but annoying. With more research I'm sure I'll find a way to have Ubuntu ignore the onboard video and go only to the Matrox card. Thanks again. You've been a lot of help. Hopefully someday I will be able to "pay it forward".[/QUOTE]

Are the streaks sorta like interference?  It could be that your refresh rate does not jibe with your monitor's.  Try changing the refresh rate if you have that option in the screen-resolution preferences.


You should be able to configure it to use the matrox card.  Just boot into recovery mode the first time you use the matrox card and rerun the dpkg-reconfigure xserver-xorg script.

The nitty-gritty is that once X tries to use the hardware it sometimes can have difficulty trying to autodetect it again.  So if you try to use the nv (nvidia) driver with the matrox card, it may fail, but X will still be running and taking up the ressource (in memory)  When you ask X to detect the card, it screws up.  You can kill X by running

sudo /etc/init.d/gdm stop

or just not start gdm, which is what you do by booting into recovery mode.

---

### Post by Chuck_W on 2006-03-21
Some good ideas,azz. For the time being I'm going to put up with it. I may look into putting Ubuntu on another machine and scrap this one. The video problem is not unique. A quick search reveals that the Dell Optiplex GX200's are known for this. And the 128mb RAM results in a lot of disk access. Finally, I'm pushing my luck with the fairly small HD - there's not a lot of space left. I may have a lead on another machine. We'll see how that works out.
Thanks

---

