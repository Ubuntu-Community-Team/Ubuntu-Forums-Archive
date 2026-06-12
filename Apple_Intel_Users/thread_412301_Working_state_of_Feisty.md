---
title: "Working state of Feisty"
date: 2007-04-17
forum: Apple Intel Users
---

### Post by thephotoman on 2007-04-17
I have an Intel Core Duo Macbook, and I was wondering about the state of installing Ubuntu on that particular piece of hardware.  Last time I tried was shortly after the release of Dapper, and while I had some success, some problems with a new kernel and LiLo hosed that installation.  Therefore, I'm a little hesitant to leave my Parallels install behind, but there are just some things you can't do in Parallels, particularly with regards to USB devices.

I seem to remember, however, that the touchpad barely worked and that sound was barely audible.  Also, I remember having difficulty with the wireless.

My questions are myriad:

1. Do you have to do any fiddling with LiLo in order for the system to work, or does the CD's installer script Just Work (tm)?

2. Is sound any better?

3. What is the mechanism for middle and right click with the touchpad?  I have a mouse, but frequently don't have the space to use it.

4. Wireless doesn't have any hiccups now, does it?

---

### Post by Game_Ender on 2007-04-18
I installed Feisty on a new Intel Mac Mini and the wireless worked out of the box (from the Live CD even) and required no special changes to the machine accept making sure I have the latest firemware and OS X is completely updated.  Good luck.

---

### Post by benanzo on 2007-04-18
I have a fully updated Feisty installed on a black core duo macbook.  Almost everything Just Works.

[COLOR="Red"]**Works out of the box**[/COLOR]

All the major hardware components ie usb, firewire, sata, cd/dvd, ethernet,  multicore processing, etc.

Wireless - everything about the wireless on the first gen (core duo) macbooks works perfectly.  WEP, WPA, WPA2, Monitor/Ad Hoc/AP mode work great.  NetworkManager (installed by default in Feisty) does a great job of managing your wireless networks and in conjunction with gnome-keyring-manager (also default) handles your WEP/WPA encryption seemlessly without editing conf files.

IR Remote - A nice little addition that came along with the mactel-linux patches upstream.  It is preconfigured to control the standard gnome multimedia apps like totem/rhythmbox etc  Play/Pause, Volume Up/Down, Next/Previous all work great.  No config necessary.  Just open the Keyboard Shortcuts menu and change the keys if you want them to do something else.

Screen brightess control - works.  Use F1 and F2 to control it.  There's even a nice little brightness applet you can put on your panel.  A little meter pops up on the screen to show you how bright it is when you're adjusting it.  GNOME is making great improvements in laptop usability.

Suspend to disk - Surprising...Just Works.  The gnome-power-manager does a good job of managing the CPU scaling and other advanced ACPI features in the macbook.  I set my laptop to sleep when the lid is closed only if on battery power and it Works 100% of the time.  Wakeup takes about 5 secs.

Onboard speakers/headphone sensing - This has been fixed since edgy beta.  The onboard speakers properly mute when headphones are plugged in and unmute when they are taken out.

Advanced keyboard features - The Fn key does what it is supposed to.  Again, fixed since Edgy beta.

Advanced touchpad features - Scrolling, tap-to-click, 1 finger L-click 2 fingers R-click, etc all work great with the very latest Feisty updates.  Feisty final will be solid on this.  Previous to the latest update, like if you were to install Herd 5, you would not have the advanced touchpad features.  But the latest updates have added the inclusion of the synaptics driver and a basic config in xorg.conf to enable it for tap-to-click, 2 finger right-click and scrolling with the right-most side of the touchpad.  By default, however, the F11 and F12 keys are configured to be left and right click respectively.  I have added my own config to make the right Apple key left click and the lower Enter key delete (that's just where I'm used to it being.)  Without my config the default is for the apple "delete" key to be backspace and Fn+"delete"  is delete.  You can add any number of different options to the xorg.conf synaptics section to get it to behave like it does in OS X (like 2 finger scrolling etc.)

My custom script:
```
#!/bin/bash
#
# Configures Macbook's right apple key to be right mouse-click
# and lower enter key to be delete.
# Install xkbset (sudo apt-get install xkbset)
# chmod +x "name_of_this_script"
# set GNOME to run it at login.

xmodmap -e 'keycode 116 = Pointer_Button3'
xmodmap -e 'keycode 108 = Delete'
xkbset m
```

Composite desktop/compiz/beryl - since intel open sourced the drivers for their chips, and the macbooks have the intel GMA950 chips, composite desktop with AIGLX work out-of-the-box.  Since Feisty includes X.org 7.2 the experience is even better.  I get great framerates on everything except the blur plugin and the rain plugin.  I have to have those disabled because otherwise my desktop crawls.  Everything else is wonderful.

[COLOR="Red"]**Works, but not by default**[/COLOR]

iSight - the isight driver is included in the Feisty kernel.  However, you need the iSight firmware for it to create the proper device file so you can use it.

Here's the steps:
Download [http://people.freedesktop.org/~rbultje/linux-uvc-0.1.0-e.tar.gz](http://people.freedesktop.org/~rbultje/linux-uvc-0.1.0-e.tar.gz)
Extract it.  You want the extract.c utility included inside.
The driver itself is already included in the Feisty kernel.
Grab your iSight firmware from your MacOS partition.
You'll find it in /System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
As root, run 'extract' on this file and the firmware should be installed.  The kernel driver will
automatically notice the firmware has been loaded and will setup a v4l2 device for you to use.
Open ekiga and you should see yourself.

[COLOR="Red"]**Sorta works**[/COLOR]

Hibernate - I put it in this category because sometimes it works and sometimes it doesn't.  Often it will go into hibernation and wake up fine but sometimes instead of waking up it will just cold boot.  No clue, no rhyme, no reason...sorta works..

**[COLOR="Red"]I can't get it to work[/COLOR]**

Microphone...any of them.  Line in/mic in/front mic (isight) I can't get any mic to record anything.  I have tinkered with ALSA and gnome-volume-control and sound recorder to no avail.  Hopefully this will get fixed sometime.



All in all, Ubuntu on the first-gen macbooks is just about 100% functional with just a couple hiccups.  One big one (sound recording) and one not-so-big (hibernate.)

Now is a good time to put Ubuntu on a MacBook

---

### Post by viciouslime on 2007-04-18
Unfortunately, on second gen macbooks (core2duo) it is quite a different story. Wireless doesn't work, this is the case across all distros at the moment as madwifi doesn't yet support the macbook's chipset. There has recently been a development in this area, however it only supports unencrypted networks and has very poor range. Furthermore, this developement version of the driver must of course be compiled and installed manually.

Sound was working wonderfully, then about 3weeks ago someone, somwhere did something and the volume controls now adjust treble and bass and their is no way what-so-ever (that I am currently aware of) of controlling the volume.

Power management is working very well.

iSight was at one point working out of the box, I didn't have to do anything regarding firmware... this is no longer the case however.

The touchpad requires an edit of xorg.conf to make right clicking and two finger scrolling work, but nothing major.

That's about it really, everything else works.

---

### Post by Chrisj303 on 2007-04-18
> **viciouslime said:**
> Unfortunately, on second gen macbooks (core2duo) it is quite a different story. Wireless doesn't work, this is the case across all distros at the moment as madwifi doesn't yet support the macbook's chipset. There has recently been a development in this area, however it only supports unencrypted networks and has very poor range. Furthermore, this developement version of the driver must of course be compiled and installed manually.

Sound was working wonderfully, then about 3weeks ago someone, somwhere did something and the volume controls now adjust treble and bass and their is no way what-so-ever (that I am currently aware of) of controlling the volume.

Power management is working very well.

iSight was at one point working out of the box, I didn't have to do anything regarding firmware... this is no longer the case however.

The touchpad requires an edit of xorg.conf to make right clicking and two finger scrolling work, but nothing major.

That's about it really, everything else works.

Oh god:( , thats exactly what i didn't want to hear. Hopefully this will be sorted out for the final release, especially the wireless - for me this is becoming a show stopper.

303

---

### Post by Seamyst on 2007-04-18
I can't get my iPod (4G) to connect via the firewire port, which works fine on my Tiger partition.  It doesn't recognize that I plugged anything in, is all.  I just looked for the USB connector and didn't find it, which means my ex probably took it when he moved.

Is there anything I can/should do to get my firewire port working, or should I just order a USB connector from Apple?  This is, at the moment, the only thing that's not working on my computer - everything else (aside from the camera, which I haven't tried yet) works fine with Ubuntu.

---

### Post by Chrisj303 on 2007-04-19
Why is it such a headache getting basic functionality on mac's running ubuntu?

Seeing as the range of components found in Apple Mac's is a tiny fraction of that of the PC world - you would have thought we would have had it easy, a long time ago.

Are we ignored?, does anybody who has a say in the feisty releases care about apple intel users?

I was hoping that feisty would solve a lot of the problems i've been having since i installed ubuntu on my macbook, but it looks like i'm out of luck :(

"UBUNTU - Linux for everybody (apart from mac users)"

303

---

### Post by mustang on 2007-04-19
> **Chrisj303 said:**
> Why is it such a headache getting basic functionality on mac's running ubuntu?

Seeing as the range of components found in Apple Mac's is a tiny fraction of that of the PC world - you would have thought we would have had it easy, a long time ago.

Are we ignored?, does anybody who has a say in the feisty releases care about apple intel users?

I was hoping that feisty would solve a lot of the problems i've been having since i installed ubuntu on my macbook, but it looks like i'm out of luck :(

"UBUNTU - Linux for everybody (apart from mac users)"

303

First off, I wouldn't really expect a lot of sympathy from developers in the first place to put linux on a macbook. Think about how tiny of a percentage we are compared to those who follow the traditional path of installing osx and being done with it.

Are we ignored? Of course not: [https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=macbook&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=macbook&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

And I can't find the official bug posting but one of the goals for feisty was full mactel support. So you have to give credit to the dev's for helping us. You also have to understand their priorities (are rightly) devoted elsewhere to everyone else.

One point I would argue is that the hardware across each generation of macbooks is homogeneous so one would think it would be fairly easy to get full hardware support working. Such is not the case I'm afraid.

> Suspend to disk - Surprising...Just Works. The gnome-power-manager does a good job of managing the CPU scaling and other advanced ACPI features in the macbook. I set my laptop to sleep when the lid is closed only if on battery power and it Works 100% of the time. Wakeup takes about 5 secs.

Now this just boggles my mind. How are you, a first generation owner at that, able to get suspend-to-ram working? We've had huge difficulty getting suspend working. Did you use any tweaks, modifications, etc?
More about suspend detailed here: [http://ubuntuforums.org/showthread.php?t=398381](http://ubuntuforums.org/showthread.php?t=398381)

To the OP, there are two factors that would drive away from putting linux on a macbook: suspend and power management. Now apparently some macbook owners have gotten suspend to work (like benanzo) but others haven't. Also, I get about 4 hours in OSX, about 2 hours of battery life in Ubuntu. I'm a student constantly on the go and that makes a big difference for me.

---

### Post by Seamyst on 2007-04-19
I'm just happy I got Feisty Ubuntu to *install* on my MacBook, after having that incredibly annoying grub install error with Edgy.  That was apparently a major bug, judging from all the bug-report-update emails I got.  At least it works, and mouse and keyboard work (setting aside the minor fiddling to decrease the sensitivity of the touchpad), and I only occasionally get a kernel panic on boot up.

I mean, yeah, it'd be great if everything worked perfectly right out of the box, but you can't even get that with Windows.  (Or should that be, you especially can't get that with Windows? :wink: )

---

### Post by ronocdh on 2007-04-19
> To the OP, there are two factors that would drive away from putting linux on a macbook: suspend and power management. Now apparently some macbook owners have gotten suspend to work (like benanzo) but others haven't. Also, I get about 4 hours in OSX, about 2 hours of battery life in Ubuntu. I'm a student constantly on the go and that makes a big difference for me.
I hear that. Worse, the inability to suspend reliably and consistently means I've come to use OS X on the days when I have many back-to-back classes. Not a big deal, because I use NeoOffice there and I'm good about syncing my documents (I take notes in OO Writer) between OS X and Ubuntu.

Also, Chrisj303, madwifi drivers may not work in C2D Books, but I've been using ndiswrapper for months now. Works on WEP networks fine, great range (reception is sometimes listed as better than in OS X, haven't tested that extensively, though).

Glad to hear about sound and headphones!

---

### Post by ronocdh on 2007-04-19
> **Seamyst said:**
> I'm just happy I got Feisty Ubuntu to *install* on my MacBook, after having that incredibly annoying grub install error with Edgy.  That was apparently a major bug, judging from all the bug-report-update emails I got.  At least it works, and mouse and keyboard work (setting aside the minor fiddling to decrease the sensitivity of the touchpad), and I only occasionally get a kernel panic on boot up.

I mean, yeah, it'd be great if everything worked perfectly right out of the box, but you can't even get that with Windows.  (Or should that be, you especially can't get that with Windows? :wink: )

I won't have a chance to install until late tonight. Are you saying the GRUB kludge is no longer necessary? Do you triple boot or double?

---

### Post by Breepee on 2007-04-19
I've got a Macbook 1.1 on which I ofcourse want to use Ubuntu too, including the remote. Since it suspends to disk fast and coming back fast, makes it a little more bareble that suspend to ram still doesn't work reliable.

What I'm curious about is battery life and running Ubuntu exclusively. I bought the machine mostly because of it's great battery life (4-5hrs is possible) so of course I'd like Ubuntu to get me in that range too (Dapper supposedly got to 2 hrs typically). Can someone comment on that?

Then my final question: running Ubuntu exclusively: possible? When Ubuntu works, I've no need anymore for OSX (not that great anyway), and since bootcamp costs money or is timebombed, I'd like to know how difficult it is to get it to work without those.

---

### Post by ronocdh on 2007-04-19
> **Breepee said:**
> I've got a Macbook 1.1 on which I ofcourse want to use Ubuntu too, including the remote. Since it suspends to disk fast and coming back fast, makes it a little more bareble that suspend to ram still doesn't work reliable.

What I'm curious about is battery life and running Ubuntu exclusively. I bought the machine mostly because of it's great battery life (4-5hrs is possible) so of course I'd like Ubuntu to get me in that range too (Dapper supposedly got to 2 hrs typically). Can someone comment on that?

Then my final question: running Ubuntu exclusively: possible? When Ubuntu works, I've no need anymore for OSX (not that great anyway), and since bootcamp costs money or is timebombed, I'd like to know how difficult it is to get it to work without those.

I don't recommend you use Boot Camp for dual booting. If you are triple booting with XP, then use Boot Camp to burn a driver CD, but nothing beyond that. I partitioned my drive for triple boot by using the terminal in OS X. I then installed XP from a SP2 CD and then the Boot Camp drivers CD (although I now use many non-Apple drivers for my hardware in XP).

Furthermore, I don't recommend you get rid of OS X. It is rock stable to have as a backup OS, and more importantly, it's necessary for firmware upgrades on your hardware.

As for power management, see posts above.

---

### Post by mustang on 2007-04-19
> **Breepee said:**
> I've got a Macbook 1.1 on which I ofcourse want to use Ubuntu too, including the remote. Since it suspends to disk fast and coming back fast, makes it a little more bareble that suspend to ram still doesn't work reliable.

What I'm curious about is battery life and running Ubuntu exclusively. I bought the machine mostly because of it's great battery life (4-5hrs is possible) so of course I'd like Ubuntu to get me in that range too (Dapper supposedly got to 2 hrs typically). Can someone comment on that?

Then my final question: running Ubuntu exclusively: possible? When Ubuntu works, I've no need anymore for OSX (not that great anyway), and since bootcamp costs money or is timebombed, I'd like to know how difficult it is to get it to work without those.

Ugh I feel unlucky, suspend to disk doesn't work for me either. Mind me asking which generation macbook you're running?

---

### Post by Breepee on 2007-04-19
> **ronocdh said:**
> 
Furthermore, I don't recommend you get rid of OS X. It is rock stable to have as a backup OS, and more importantly, it's necessary for firmware upgrades on your hardware.
In the end, I hope to use Ubuntu exclusively, it pretty solid too, and I can always install OSX for an update or another and the load Ubuntu again, not need to waste diskspace permanently.> 
As for power management, see posts above.
OK, thx, I missed it. Guess OSX will stay on a bit longer. I wonder what causes Ubuntu to suck up more juice.
> **mustang said:**
> Ugh I feel unlucky, suspend to disk doesn't work for me either. Mind me asking which generation macbook you're running?
1.1

---

### Post by FrancoNero on 2007-04-19
the problem i have is when i return from suspend, i dont have a keyboard and touchpad, so i can't login... bummer

---

### Post by wecannotbesaved on 2007-04-19
How do we get rid of the tap-touchpad-to-click thing?  It has been bugging me to an extreme. :( 

I've looked around in the usual places, mouse settings etc.  can't find it, is it even possible?

---

### Post by Seamyst on 2007-04-19
> **ronocdh said:**
> I won't have a chance to install until late tonight. Are you saying the GRUB kludge is no longer necessary? Do you triple boot or double?

Oh, no, sorry, I still had to install grub.  What I meant was, trying to install Edgy from the LiveCD gave me fatal grub install errors at 94% done (very annoying, that).  After the third time that happened I submitted a bug report and was automatically kept updated on additions to the bug, connecting it to other bug reports, etc.  This led me to understand it was a pretty major bug - which I later confirmed on the forums.  A temporary patch was sent out, but it didn't have any instructions and I had no clue what to do, so I basically ignored it.

Feisty, on the other hand, didn't give me the fatal grub install error.  I was able to install it completely, no problems, on the first try.  That's what I meant.

---

### Post by Chrisj303 on 2007-04-20
> **ronocdh said:**
> 

Also, Chrisj303, madwifi drivers may not work in C2D Books, but I've been using ndiswrapper for months now. Works on WEP networks fine, great range (reception is sometimes listed as better than in OS X, haven't tested that extensively, though).
!

Would you mind telling me ho you got it working, and what driver you used? I tried ndiswrapper with the NET5416 driver and all i get with ' ndiswrapper -l ' is "invalid driver!".
Lack of wireless is really getting me down, as i rely on this when i'm at home, and ubuntu without internet connection isn't much fun at all!

303

---

### Post by benanzo on 2007-04-20
I am working on a Feisty guide for the first gen (core duo) macbooks.  I don't dual or triple boot.  This is Ubuntu all-the-way.  I have full functionality (like I said) except for sound recording and spotty hibernation.  I can't understand the mic problem...everything is as it should be but no sounds are recording.  If anyone has any info, that would be great.

---

### Post by Chrisj303 on 2007-04-20
> **benanzo said:**
> I am working on a Feisty guide for the first gen (core duo) macbooks.  I don't dual or triple boot.  This is Ubuntu all-the-way.  I have full functionality (like I said) except for sound recording and spotty hibernation.  I can't understand the mic problem...everything is as it should be but no sounds are recording.  If anyone has any info, that would be great.

What are you going to do regarding firmware updates? - this can only be done with osx. During the OSX install - you can choose the 'customise' option, and uncheck everything - this reduces the install to around 2.5gb.

Obviously, it is your machine and you do whatever you like, but it really dosen't make sense to me. I'm just interested to know what the motivation is behind this. 

303

---

### Post by benanzo on 2007-04-20
I have windows and os x installed on the original 80gig disk that came with the macbook.  I bought my own ram and a 160gig drive when I got it and that is what ubuntu is installed on.  If I ever need windows or OS X, I'll spend 10 minutes changing the disk.  But I don't update the firmware because obviously Apple updates it for OS X, not Ubuntu.  A firmware update might break my system.  I have to be very careful.  If it works..it works.  I don't mess with it unless I see security issues in their changelog and even then I watch the mailing lists and forums to see how the update is affecting others before I run it.

---

### Post by Breepee on 2007-04-20
Indeed it works, so essentially firmware updates add nothing. Great someone will make a guide for beginners like me, but still, the shorter batterytime bothers me... 2hrs as opposed to 4-5 is just bad.

---

