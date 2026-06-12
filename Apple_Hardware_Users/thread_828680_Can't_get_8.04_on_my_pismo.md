---
title: "Can't get 8.04 on my pismo"
date: 2008-06-14
forum: Apple Hardware Users
---

### Post by iamdigitalman on 2008-06-14
I am starting to sound like a broken record here. Last year, I made a post about not being able to get 7.04 on it. 8.04 displays the EXACT SAME graphics bug, and the modelevel bit does not work in 8.04 at all. I went back and downloaded 6.10, and it works flawlessly, but I want something current.

Also, I tried installing it on an external 40gb drive in a USB enclosure. Upon getting to yaboot installation, it failed. I tried the same thing on my 20gb iPod over the firewire cable, and it failed in the exact same place. I then went and popped the hard drive internally, installed ubuntu, it succeeded, so I put it in the enclosure, and it shows up in the option key boot manager, I select it, and then press the -> button, and the screen goes black, and that is it.

I am going to return the enclosure since the connector popped off, and get a firewire enclosure, but I want to know if this will work.

I really do not see how powerpc can be an unsupported architecture when a lot of people will be dumping PPC equipment soon if they have not already.

---

### Post by stream303 on 2008-06-14
I'm not even sure if a Pismo can boot from a usb-drive.  The only external drives I'm familiar with that you can get to boot are firewire drives - which need manual editing of the /etc/yaboot.conf file after install. Perhaps this will help if you go firewire:

[http://ubuntuforums.org/showthread.php?t=314237](http://ubuntuforums.org/showthread.php?t=314237)

Running Dapper is a *great* diagnostic - I'd be sure to copy your /etc/yaboot.conf, and also your /etc/X11/xorg.conf file down for use with Hardy - maybe not so as a direct replacement, but for using valuable settings you can edit manually into Hardy's xorg.conf - it's a whole new ballgame now with the latest x server.

How much ram is installed?

In addition, the splash screen has been known to give trouble in certain models with Hardy, so what kernel parameters have you tried?  Have you tried using *nosplash*?

> I really do not see how powerpc can be an unsupported architecture when a lot of people will be dumping PPC equipment soon if they have not already.

Huh?  Did you mean that a glut of ppc boxes will be revived with Ubuntu, or that ppc support is a waste of effort?

---

### Post by joninkrakow on 2008-06-14
Pismos definitely cannot boot from USB, and I've had no luck with my internal Firewire getting it to even mount or recognize my external hard drive. In fact, if I forget and leave the hard drive plugged in, booting pauses, and won't continue, even if I unplug the drive. I have to reboot. 

However, I think that what I did to get Hardy to work was to upgrade it from Gutsy. I had to do the modelevel bit to get my Pismo to boot into 7.10, but upgrading it to 8.04 worked well.

You might find it best to actually start at 7.04, and upgrade from there. One trick I discovered before I learned the modelevel trick with 7.10, was at yaboot, after hitting "l" I would type in "old", and get the older kernel from 7.04 (if you hit the tab key at the second yaboot propt, you can see your options). That would boot. So, installing 7.04 gives you the older kernel as a fall-back.

-Jon

---

### Post by stream303 on 2008-06-14
> **joninkrakow said:**
> Pismos definitely cannot boot from USB, and I've had no luck with my internal Firewire getting it to even mount or recognize my external hard drive.

This may be a problem with older firmware.  Looks like the firmware update addresses this issue with firewire.  Check out:

[http://support.apple.com/kb/HT1395](http://support.apple.com/kb/HT1395)

Although to do the update, you have to have a working version of Mac-OS on the hard drive to actually perform it - it isn't possible to update from an OSX install CD.

**Standard warning** do NOT try to update the firmware from anything but a working hard-drive install of Mac-OS - in fact, don't even put in an OSX disk or OSX utility disk unless this has been performed first.

---

