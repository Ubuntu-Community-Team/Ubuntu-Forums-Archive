---
title: "Just installed 7.04, Very smooth!"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Kamilion on 2007-04-18
Picked up the 7.04 April 16th DVD image from a LWN posting, I've been a long time Gentoo user, tried Ubuntu a couple months back.

Here's the posting.
[http://lwn.net/Articles/230848/](http://lwn.net/Articles/230848/)

So, I nabbed the image, burned on my desktop with nero7, labeled the disc, and stuck it in my laptop. Previously, I had Sabayon/Gentoo installed on /dev/hda3, with /boot on /dev/hda2 as fat32.

Fired up the laptop, which dualboots with Fujitsu's OEM XP home.
This is a Fujitsu Lifebook S2020, Athlon XP LV 2200+, ATI Radeon Mobility 320M (aka U1).

Whacked F-12 to get to the boot selector, picked CD...

And lo and behold, there was a completely unfamiliar ISO loader... (What is it by the way? It's REALLY spiffy!)

Picked 1024x768x32 (laptop panel's native resolution), poked about the help a bit, and launched Ubuntu.

Nice clean gensplash, looked awesome. Waited. (slow DVD-ROM...)
Finally got the X cursor as X started up. Poked the touchpad. Mouse cursor went nuts.
Fortunately, it always does this in linux, even in Gentoo and Sabayon, so I just gave it a second and it settled down.
(symptoms: flutters between the four screen corners and generates spurious clicks.)

Live desktop came right up, warned me it was using some restricted Atheros drivers for the built in wifi, battery gauge came up (strangely enough, it says it's Discharging, at 93%, although windows seems to think it's at 100%. *shrug*), and I hit the installer link on the desktop.

Went through the language selection, keyboard selection, picked Manual for partitioning, intending on reusing my existing partitions.

Oops, Ubuntu won't let me use /dev/hda2 (fat32, ~128MB) as /boot.

Well, in that case, I'll just wipe the second and third partitions (hda3 was sabayon's old partition in reiserfs) and install over the old ones.

So I open Calculator from Applications - Accessories. Tap out my free space, minus half a gig.
Type that into the installer, set it as ext3 on /, then assign the last half gig to swap.

Hit next, told it I wanted it to import my firefox settings from XP home and nothing else, gave it a username and password.

Hit next, and my jaw nearly dropped. That was it. It started on it's merry way already.

So I fired up sudoku, and played a round. In the time it took for me to clear the board, Ubuntu had JUST finished installing.

Whacked reboot, and got stuck at the "Remove the CD and hit enter" prompt. Hitting enter did nothing. Held the power button for 4 seconds to hard power it off with the ATX shortcut, and powered it back on.

Grub installed to (hd0) automatically, and even added XP Home to the list. So I fire up XP to check if it's still okay. Yep, works perfectly. I get to the login screen and restart.

This time I start up Ubuntu. Login screen came up within about a minute. Very good.
Logged in with the user I created in the installer. (I *LIKE* that it doesn't display account names.)
First thing pops up, Atheros drivers again, then asked me to update two packages.
I hit go, it asks for the admin password. Well, crap, I didn't remember setting a root password.
So I tried the account password. Went and grabbed the updates, applied 'em no sweat. I hit details, and it gave me a nice little console window to watch the progress. Very cool.

Fired up terminal, asked for glxgears. Sloooow. Darn. No hardware acceleration, just Mesa.
I'll have to figure out how to fix that. But the upside is, at least 2D's pretty freakin' quick!

So I fire up firefox. Uhoh. Didn't pick up my extentions or my bookmarks. Oh well, I can just import the bookmarks, and deal with the extentions myself. Good try though.

Hit [Second Life's page.]("http://www.secondlife.com")
Downloaded the latest linux alpha client.

Archive Manager pops up. I hit extract to homedir.

I fire up Second Life. Hooray, it works! I log in... 10FPS... WITH textures!
(Second Life doesn't support this video card in windows, as it lacks hardware texture and lighting. Mesa compensates for this in software on Linux.)

All in all, a painless installation, even keeping XP and putting it in grub automagically.
Kudos to the Ubuntu devs. You've done a very hard thing to make it so painless.
I'll still stick with gentoo on my servers, but ubuntu's definitely got a place on my desktop now.
If any of y'all are on Second Life, look me up -- I'm Kamilion Schnook. And I'll give you a free beer.

---

### Post by ajgreeny on 2007-04-18
Not certain if your graphic card is one that is covered by the open source "ati" driver but it's worth trying.
Back up your /etc/X11/xorg.conf file and then do 
sudo dpkg-reconfigure xserver-xorg
in a terminal.
Accept all the defaults as shown until you get to the graphic driver and try "ati".
Restart or Ctrl+Alt+backspace to restart x and you may be lucky with 3d.  It certainly works superbly on a Radeon 9200SE card, giving great acceleration and 1266fps.  Even will run beryl easily in feisty if you want it.
If you get nowhere at least you can restore your old working (slowly) xorg.conf

Good luck.

---

