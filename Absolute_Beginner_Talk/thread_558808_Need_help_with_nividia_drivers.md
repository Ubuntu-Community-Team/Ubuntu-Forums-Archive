---
title: "Need help with nividia drivers"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by xxhaloownerxx on 2007-09-24
Hi,

recently i figured out how to hook up my computer to diffrent monitors, as well as TV.s on my laptop running win XP, and i was wondering, where are the settings that would allow me to do such, lets say, use my monitor and the TV at the same time? so far i can only use one, either the monitor, or the TV, i have the driver installed, when i turned on desktop effects, ubuntu was very nice and installed them for me, but i have no idea how to configure them.

help? :D

---

### Post by overdrank on 2007-09-24
> **xxhaloownerxx said:**
> Hi,

recently i figured out how to hook up my computer to diffrent monitors, as well as TV.s on my laptop running win XP, and i was wondering, where are the settings that would allow me to do such, lets say, use my monitor and the TV at the same time? so far i can only use one, either the monitor, or the TV, i have the driver installed, when i turned on desktop effects, ubuntu was very nice and installed them for me, but i have no idea how to configure them.

help? :D

Hi maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=301951&highlight=nvidia+dual+monitors](http://ubuntuforums.org/showthread.php?t=301951&highlight=nvidia+dual+monitors)
And
[https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)
Also search for twinview

---

### Post by rybu on 2007-09-24
multiple displays are easier to set up with the nvidia-settings utility that comes with the nvidia drivers.  Try running that instead (anything to avoid manual editing of xorg.conf is good in my books).  I've got 2 displays working with my laptop and for the most part things are going well.  There's a couple problems.  1) xinerama is buggy.  It tends to cause 3d-accellerated apps to crash on my system.  So I use 2 displays without xinerama.  2) I can't get <CTRL>+<ALT>+F1 to function properly.  It just brings up a blank display (although I am in text mode and can log-in, etc...). 

You'll need to run nvidia-settings as root:

sudo nvidia-settings

---

### Post by Beggar on 2007-09-24
I actually disagree with the previous poster, X editing is something I think needs to be done by hand still. (Hopefully that changes with the new gutsy editor...) Do not fear though, the nvidia-settings tool will generate all of the changes you need to add, then you can just compare it to your /etc/X11/xorg.conf file, but only change whats necessary (I.E. the nvidia-settings tool will change things like your touchpad configurations, etc.) 

This is not a flame or anything, just an alternate method for acheiving the same goal. You could use the tool, it will do the exact same thing.

---

### Post by averagebeatboy on 2007-11-22
I recently inherited a Nividia AGP card with 64 MB of memory.  I am using Ubuntu 7.10 "Gutsy Gibbon." And an IBM 15" monitor so resolution rates are really important.

I have the restricted driver loaded and the only resolution I was given a choice for was 640x480.  I was reading the Nividea problems that others are having and thought I might offer my experience as maybe it will work for others AGP or not.

I have the fear of messing with the xorg.conf as nearly everyone else.  I try saving the xorg.conf to some kind of external device.  Then if things do not turn out I install Ubuntu just using the live CD and replace the conf.org I saved with the one being used by the live CD and what it has placed on my harddrive for the test spin.  This way when I remove the CD and reboot and at least I have a functioning xorg.conf so I can try something else.

xorg.conf : a nVidia Corporation NV18GL {Quadro NVS with AGP8X].

As I read the top of the xorg.conf it offered the following:  "You can try automatically updating with the following code:"

sudo dpkg - reconfigure -phigh xserver.org

I did not want to change Nividea to nv or anything else at the moment.  So I closed the xorg.conf, opened a terminal typed the command and a window in the terminal opened with two selection for modes: 1920x1440 and another 1900 I marked both of the modes checked off okay and rebooted. 

All went well and I could tell at sign-in it had changed to a 1900 mode because everything was so tiny.  The monitor displayed a message "mode out of sync".  I started to hit buttons on my monitor, but then changed my mind and let it load -- the screen looked grand -- a little small but better than 640x480. 

I went to Resolution now there was a large selection of modes to chose from.  I lowered the mode by a few.  Monitor signal went away and now I have an incredible resolution. 

Maybe this will help someone else.  Or I got lucky with an AGP.

Best,

Averagebeatboy  :guitar:

---

