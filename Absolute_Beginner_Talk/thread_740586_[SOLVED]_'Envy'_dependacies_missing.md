---
title: "[SOLVED] 'Envy' dependacies missing"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Zralou on 2008-03-30
I downloaded 'Envy' to try and solve my ongoing problem with nvidia drivers, but after installing Envy, I try to run it and get the message, missing:

> build-essential,xserver-xorg-dev,pkg-config,dkms,fakeroot,devscripts,dh-make,debhelper,libstdc++5,dpkg-dev,dpatch


Where can I get this missing file/binary/whatever it is.

Sara Lou

---

### Post by mevets on 2008-03-30
it sounds like you installed the source packages. Im not at my ubuntu machine right now so I dont know if the binary is in the repos, but if you go to [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) and download the legacy envy you will get a deb with the binary.

---

### Post by anewguy on 2008-03-30
Try this in a terminal window:

sudo apt-get build-dep envy

---

### Post by Zralou on 2008-03-30
I downloaded the 'Envyng' because i'm running Hardy 8.04, it installed fine, put an icon on the taskbar and starts to run when I click the icon, but then it stops with the above message.

Sara Lou

---

### Post by Zralou on 2008-03-30
> **anewguy said:**
> Try this in a terminal window:

sudo apt-get build-dep envy

This is what I get:
> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to find a source package for envy

Sara Lou

---

### Post by anewguy on 2008-03-30
> **Zralou said:**
> I downloaded the 'Envyng' because i'm running Hardy 8.04, it installed fine, put an icon on the taskbar and starts to run when I click the icon, but then it stops with the above message.

Sara Lou

did you try  sudo apt-get build-dep envy


this will build the dependency list for the package envy, then let you know what it needs to download, how much space it will take, etc..

---

### Post by mevets on 2008-03-30
i guess if you must
```

sudo apt-get install build-essential xserver-xorg-dev pkg-config dkms fakeroot devscripts dh-make debhelper libstdc++5 dpkg-dev dpatch

```

---

### Post by anewguy on 2008-03-30
Sorry we crossed threads there.  Try copying the file list, then:

sudo apt-get install  <paste file list here>

---

### Post by Zralou on 2008-03-30
> **mevets said:**
> i guess if you must
```

sudo apt-get install build-essential xserver-xorg-dev pkg-config dkms fakeroot devscripts dh-make debhelper libstdc++5 dpkg-dev dpatch

```

Ok, that got it moving, thanks.  Envy couldn't detect my card tho'.....

Sara Lou

---

### Post by mevets on 2008-03-31
from here i really dont know what do to do, but what card do you have?

---

### Post by Zralou on 2008-03-31
Thanks for your help Mevets, I have the infamous Geforce 7050/Nforce 610 combo motherboard.

After it didn't recognise my card, I selected the 'manual' install and installed the lastest driver.  I managed to get the install completed with a successful boot into a GUI (something I haven't managed all weekend, see my other thread 'Hardy 8.04 + nvidia drivers'), but now i'm stuck with 640x480 resolution...

Sara Lou

---

### Post by PmDematagoda on 2008-03-31
Could you please reiterate on your problems and post any methods you tried to get the Nvidia driver to work and how they failed(if they did).

---

### Post by Zralou on 2008-03-31
If you have a lot of spare time on your hands, you can read my previous thread here:
[http://ubuntuforums.org/showthread.php?t=739127]("http://ubuntuforums.org/showthread.php?t=739127")

Sara Lou

---

### Post by PmDematagoda on 2008-03-31
All right, from your previous thread I can see that you are on a clean Hardy install and have not yet installed the Nvidia driver.

Now my question is, do you still have the driver file?

---

### Post by Zralou on 2008-03-31
> **PmDematagoda said:**
> All right, from your previous thread I can see that you are on a clean Hardy install and have not yet installed the Nvidia driver.

Now my question is, do you still have the driver file?

As of 12:30am last night after using 'Envy', I have the nvidia driver installed.  My problem now is, my screen resolution is stuck at 640x480 and I can't see half of whats on the screen to adjust anything in 'nvidia settings'.
I'm at work just now, so I can't try anything to fix the problem till I get home tonight.

I'm sure its something fairly simple, but I got too tired last night to complete it, and being novice to Linux, I didn't want to screw things up after finally getting somewhere.
As for still having the driver file, if you mean the nvidia driver file I downloaded, no I don't have it, but it only takes 20-30 seconds to download.

Sara Lou

---

### Post by PmDematagoda on 2008-03-31
Well, that doesn't matter.

Try this:-
1) Kill the X-Server with:-
```
sudo /etc/init.d/gdm stop
```

2) Reconfigure the X-Server with:-
```
sudo dpkg-reconfigure xserver-xorg
```
make sure that you select the proper options.

3) Restart the X-Server with:-
```
sudo /etc/init.d/gdm stop
```

See if that solves your problem.

---

### Post by Zralou on 2008-03-31
One thing I need to double check on those instructions, i'm running KDE not gnome, will they still work? (I noticed  the "gdm" command at the end, which is Gnome).

Sara LOu

---

### Post by PmDematagoda on 2008-03-31
Hmm, since you have KDE, you will have to change:-
```
sudo /etc/init.d/gdm stop
```
to
```
sudo /etc/init.d/kdm stop
```

The command to restart the X-Server requires the same change as well.

---

### Post by Zralou on 2008-03-31
Ok, thats what I thought.  Also, the restart command, you have as "sudo /etc/init.d/gdm stop", is that right, or should that be "sudo /etc/init.d/gdm start"?.  Sorry for all the queries, but I am very novice at Linux so just like to make sure before I start entering code..

I will try this advice when I get home tonight (about 7pm EST), and post up the results.  Thanks for taking the time to help me with this, I really appreciate it.

Sara Lou

---

### Post by PmDematagoda on 2008-03-31
No no, I just said that the stop command was:-
```
sudo /etc/init.d/kdm stop
```

To restart the X-Server you need:-
```
sudo /etc/init.d/kdm start
```

---

### Post by stchman on 2008-03-31
> **Zralou said:**
> I downloaded 'Envy' to try and solve my ongoing problem with nvidia drivers, but after installing Envy, I try to run it and get the message, missing:



Where can I get this missing file/binary/whatever it is.

Sara Lou

You must enable all the repositories (main, universe, multiverse, and restricted).

---

### Post by anewguy on 2008-03-31
Just a brief background, if you don't already know.  You had to install the dependencies because Envy actually builds a kernel module, as you found.  Also, do you know much about a file called xorg.conf?  This file contains the configuration information for the x server, including resolutions.  The file itself is /etc/X11/xorg.conf.  You may want to check to be sure that your video card is marked for the appropriate driver (it may be using vesa at this time) and also check your resolutions.

You can look at a file called /var/log/Xorg.0.log to see if there is any information about it detecting your card, not finding the driver and defaulting back to vesa.  Depending on your system, there is probably more than one version of this file - cd to /var/log  and do a ls Xorg* to see them all.  Scanning these can help find errors not otherwise readily apparent.

Please post back when you are back home and copy the /etc/X11/xorg.conf file and post it back here if the previous suggestions have not helped.  Sometimes it is necessary to include the horizontal and vertical frequencies in the xorg.conf file for resolutions to work correctly. In that case, you need to either look in the manual for your monitor (they will be specified as ranges, example  vertical 30-120.  If you don't have a manual, try going to a website for the manufacturer and see if you can find them there.  It is best to have as much of this information as possible ahead of time so we can, hopefully, help you the best.

Good luck!   :)

---

### Post by Zralou on 2008-03-31
> **PmDematagoda said:**
> Well, that doesn't matter.

Try this:-
1) Kill the X-Server with:-
```
sudo /etc/init.d/gdm stop
```

2) Reconfigure the X-Server with:-
```
sudo dpkg-reconfigure xserver-xorg
```
make sure that you select the proper options.

3) Restart the X-Server with:-
```
sudo /etc/init.d/gdm stop
```

See if that solves your problem.

Ok, just got home and tried your suggestion, it gave me the option to configure my keyboard, then overwrote the xorg and threw me back to where I started at weekend, it restarted with 800x600 resolution and generic Vesa video drivers..................

Sara Lou

---

### Post by anewguy on 2008-03-31
According to another thread I was following - perhaps your old thread - it was mentioned that you do not run the dpkg-reconfigure of xserver-xorg when you are running hardy heron - a change from previous releases.  This may have something to do with why that is not working for you.  Does it ever get beyond the keyboard questions or does it just stop there?

Do you remember the name of the module created when you ran Envy?  I would assume either nv or nvidia - probably nvidia.  I would edit the xorg.conf file (remember you need to sudo to do that) and change the driver from "vesa"  to  "nvidia", save the file, then reboot and see if you at least get back to where you were with the resolution problems prior to the reconfigure of xserver-xorg.  When it does come up, check the log (/var/log/Xorg.0.log) for any messages in there).  If we can at least get you back to the correct nvidia driver, we can work on the resolutions from there.  As mentioned in my previous post, try to find the vertical and horizontal ranges for your monitor, as we may need them.

---

### Post by Zralou on 2008-03-31
I should have realised when it first popped up that i'd been down that road previously, it never goes any further than keyboard configuration, then drops back to ~$ prompt with the message it has overwritten the "possibly custom" xorg file.
After I realised where this was going, I made a note of the back-up file, so hopefully I can restore what I had previously.

:::edit::: forgot to say, I went and found the H+V frequencies online last night, so they are ready to be entered, and the module name is 'nvidia'.

Sara Lou

---

### Post by anewguy on 2008-03-31
> **Zralou said:**
> I should have realised when it first popped up that i'd been down that road previously, it never goes any further than keyboard configuration, then drops back to ~$ prompt with the message it has overwritten the "possibly custom" xorg file.
After I realised where this was going, I made a note of the back-up file, so hopefully I can restore what I had previously.

:::edit::: forgot to say, I went and found the H+V frequencies online last night, so they are ready to be entered, and the module name is 'nvidia'.

Sara Lou

If the backup file isn't correct, try looking at some of the old log files for Xorg in /var/log.  I don't off the top of my head remember the exact sequence they use for naming/rotating the logs, but an ls /var/log/Xorg* should show them.  One of the older log files (check the date/time) may show the driver name when it at least worked with the nvidia driver.

I've got to run for a little while, but I'll be back later.  I really think that once the correct driver is specified and runs, it will just be a matter of specifying the frequencies and the valid resolutions in xorg.conf.  I had a similar problem a long time ago with a different driver but it had the same symptoms and fixed it via those things.  I have to admit my luck with Envy, or the directly downloaded nvidia drivers, hasn't been as good.  I have an old (but new to me! :) ) PNY Verto GeForce 6600GT I was trying to get working and along the way I got suggestions I would be better off going back to a clean install of Ubuntu and starting again.  Only problem is something happened to my BIOS along the way and now I can't access my hard drives at all - I'm running with the LiveCD.  I have a different motherboard (newer than what I've got now but still used - but new to me!  :)  ) on the way and a new power supply to support it.  Then I can go back and start again too.  So you see, while trying to help you here, and reading the other replies from others helping you, I'm hoping it will help me help myself.  I can help you through some parts, then it will rely on others if those things don't work for you.  :)


EDIT===  The syntax (you'll have to put your frequencies here) for the rates is:

    HorizSync     31-101
    VertRefresh    60-160

They go in the monitor section of xorg.conf.  change those, specify the nvidia driver in place of the vesa driver, then reboot and see what happens.  It may take some tweaking of the various resolutions for each color depth in xorg.conf to get one that works for you.  At any rate, I really do need to go, I'll  be back later.

---

### Post by anewguy on 2008-03-31
I also found some other posts that may help you.  Keep in mind the xserver-org reconfigure thing if you see it as some of the posts may pre-hardy heron:

[http://ubuntuforums.org/showthread.php?t=715247&highlight=Geforce+7050](http://ubuntuforums.org/showthread.php?t=715247&highlight=Geforce+7050)

---

### Post by Zralou on 2008-03-31
I found that link a couple of days ago, but using that method I couldn't boot into a GUI, i've tried just about every opion there is.  My other thread about the nvidia driver problem is now 8 pages long.

Sara Lou

---

### Post by anewguy on 2008-03-31
I really am suspicious of the newest release of the nvidia driver by nvidia - this is the same driver package that Envy picks up and compiles.  I think there is a bug in it when it comes to recognizing/configuring a lot of the cards.  As an example, for my old GeForce 6600GT envy said it need the package, compiled it, then promptly changed my device type to "amd", which the xserver turned around and said no devices found.  I tried "nv" and "nvidia", but had no luck - I could never get into a GUI (the GUI was there, but the screen was all messed up so you couldn't tell what it was supposed to be).  I wish I could find somewhere that has the nvidia driver releases archived, as I would sure like to try one a few releases back.  I had several pages on a couple of different posts I made on this problem and never got a solution either.

---

### Post by anewguy on 2008-03-31
I will assume you've made the changes to xorg.conf by now.  Now is the time to look at the newest /var/log/Xorg.0.log file.  Check to be sure the driver was found, and that it wasn't overridden by vesa later in the listing.  Also check down in the listing and you'll find the various resolutions it thinks it can support and at what rates.  Post all of that back here and we'll go from there.  :)

---

### Post by Zralou on 2008-03-31
Sorry I haven't replied sooner, i've been going through all this on the other thread I have going.  I've posted all the outputs from the various logs and files there.
I gotta go to bed now, will be continuing this tomorrow night, thanks for your help, I really appreciate it.

Other thread is here:
[http://ubuntuforums.org/showthread.php?t=739127](http://ubuntuforums.org/showthread.php?t=739127)

Sara Lou

---

### Post by anewguy on 2008-03-31
I think they are leading you in the right direction in your other post.  Remove the nvidia-auto -select  line, then modify the monitor and screen sections as described by monraaf - just be sure the frequencies match your monitor's range.  Also, if you have the documentation for your monitor or access to it online, check and see if it lists the various resolutions it supports and at what frequencies.  If a resolution is specified that isn't support, you can either get an unreadable screen or get a default screen - which will be low resolution.

I'll try to keep an eye on the other post as well as this one.

BTW, early in the other post someone mentions that you can't get restricted drivers in KDE.  I think you already know, but they are there - the management is just different than that in Gnome.  I was running KDE and tried the restricted drivers - I just can't remember now how to tell you how to get to them (something like system, then settings or some such thing - it opens a window on which is either restricted manager or there is an advanced tab that gets you there - sorry I can't remember right now!  ).  :)

---

### Post by Zralou on 2008-04-01
Just a quick note to finalise this thread.
Thanks to everyone who contributed with their time, effort and patience, I really appreciate it.  You guys are great.

Monraaf nailed it with his solution, card is installed and working, monitor is running at 1064x768 resolution, everything is good.

Thanks to everyone.
Sara Lou

---

