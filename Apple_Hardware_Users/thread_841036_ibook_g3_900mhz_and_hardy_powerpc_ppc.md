---
title: "ibook g3 900mhz and hardy powerpc ppc"
date: 2008-06-26
forum: Apple Hardware Users
---

### Post by luke.is.very.handsome on 2008-06-26
So i got the .iso for the livecd, won't load, got the alternate cd .iso and loaded it, went through the install, using the default, using the linux-powerpc, using expert and expert-powerpc, trying anything i could think of to get it to work.

The install runs through just fine in all those cases of alternate cds, but it won't load after a reboot, it blanks on the load of X i would presume, and won't give me a chance to flip to a tty and try from there.  I can't get a command line at all after that.

I put in a rescue disc and loaded it, went in to nano and checked my xorg.conf and it looks ok.

Thinking that hardy will just not run on it, I installed the server .iso for it and it runs great, updates, upgrades, all and all.  So i "apt-get install ubuntu-desktop", "apt-get install xubuntu-desktop", "apt-get kubuntu-desktop", and I end right back where I started.  No screen to use to do anything with the machine after the reboot.  I even let it sit over night thinking it might just be taking ages, I've also stared at it for about 3-4 hours while watching a couple movies waiting for it.  Nothing.

I know people have got hardy to install on their ppc machines, I just am wondering if this is never going to work since ppc got dumped.  YDL 5.01, 5.02, and 6 don't load their cds, neither does gentoo 2006.1 and 2007.  I did find that fedora 9 loads and installs just fine and also boots, but I'd rather use ubuntu for the machine since I am more partial to it.

The exact error that I can see is, fine install, when I load a gui on to the machine, it won't load, it says its Loading or some junk and then blanks and thats all I get, yaboot carries through fine, its just the spot right before X would come up and I would see the ubuntu splash screen.

It has about 768 of ram, a 40gb hard drive, a combo drive, and whatever video card these come with, i believe an ATI mobility.

Any help with this would be appreciated, hit me back.  Thanks!

---

### Post by stream303 on 2008-06-26
Good news is that you are real close to success - but due to the hardware, you'll have to manually enter some values in /etc/X11/xorg.conf.  Hopefully just one session of sudo nano /etc/X11/xorg.conf might do it! :)

I'd double check the following by perusing the threads for ibooks xorg.conf, but I think in your case changing the values to something close to this in the Monitor section of xorg.conf should get you up and running:

[b]HorizSync  28-70
VertRefresh  58-62[/b]

And you may also have to force it to use the ATI radeon in the Device section of xorg.conf:

**Driver  "radeon"**

You may also have to disable glx and/or dri by adding a section to the end of xorg.conf.  Check these two faqs for some ideas:

[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

and

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

Although the above is based on an iMac, but should help out.

Hardy (and all modern distros using xorg 7.3) are starting to leave xorg.conf pretty bare, so here's what it might look like on Hardy for you:

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync  28-70
        VertRefresh  58-62
EndSection
```

(Maybe just using a VertRefresh of 60 might do it..)

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver  "radeon"
EndSection
```

Just doublecheck those frequencies, and see if this gets you a bit further...

---

### Post by luke.is.very.handsome on 2008-06-27
So ok, from the alternate cd, I still get a broken machine.

From the server cd and then running apt-get install ubuntu-desktop, i miraculously get the login screen,  so I type in my username and password, and i get a brown screen with nothing to click on but the brown screen.  Its like the window manager doesn't want to start now.  So I push my ctrl-alt-f1 and look at the xorg.conf file and copy what it has on to the alternate cd machine, still doesn't load.

What is my difference between the two that causes it to not even bring up the login, and why on earth would the window manager not load after gdm starts up.  If those are the right terms to use there.

Alternate 8.04 PPC CD.
perfect installation
yaboot boots up right
says, logging in (text)
goes to a blank screen and sits.

Server 8.04 PPC CD.
perfect installation
yaboot boots up right
says, logging in (text)
brings up the login gui
goes to a brown screen and sits.

xorg.conf are the same on both machines, which are both the same makes, models, and builds, probably even close in serial numbers.

Both are still iBook G3 640mb ATI 40gb macs.

The xorg.conf info doesn't seem to change anything really on the computer.
Any guess now what to do?

---

### Post by stream303 on 2008-06-28
Sounds like the date-bug that shows up on some G3's where the pram battery is starting to go, and once past gdm, gnome chokes on the bad date:

[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

Once that's sorted, keep this handy as well:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by luke.is.very.handsome on 2008-06-29
Well, it did look really promising that it was the datebug, but I checked my date in both openfirmware and in the install and both of them are correct.  I reset them anyway to what the current is, so they are now both a few seconds off of the real time and nothing changed with the loading.

I reinstalled and that didn't change anything either, just in case the install before was done when openfirmware had a wrong date, if it did.

I went and got the netinst cd of debian etch 40r3.  It installs and loads gnome perfectly.  I'm so screaming confused what is wrong with this computer and the ubuntu hardy install.  Either way, I'd like to fix it and figure it out, I really want the edubuntu hardy to work on here so I can lock the machine down for a user.  Only let em have firefox, openoffice, sound, and internet access.

---

### Post by luke.is.very.handsome on 2008-06-29
forgot to mention that I have not tried this on another ibook g3 900mhz, I have quite the plethora to my disposal, so its not likely that after a third or fourth machine that the pram would be bad on all of them.

---

### Post by stream303 on 2008-06-29
In some cases, the pram battery doesn't have to be bad - the date just gets reset to something weird upon install, and the application of the date bug fix cures that from there on out.  It's good that this isn't really a problem on your systems.

(I had this issue on a relatively new G4 iBook, and once the date bug was fixed, everything was fine.)


If Debian Etch loads, thats great.  It has worked well for me too, as I also run Lenny-Testing since I want to be a bit more up to date.  I'll bet that the older Ubuntu Dapper won't exhibit this problem, so that's worth a shot since Etch and Dapper are closer relatives.

However, once we get into Debian Lenny-Testing, or later releases of Ubuntu, I've had problems show up in both that are similar.

I forgot which Ubuntu you are trying to install, so maybe something a little bit older, but perhaps not as old as Etch, such as Feisty 7.04, or Gutsy 7.10 might be a good starting point.

---

