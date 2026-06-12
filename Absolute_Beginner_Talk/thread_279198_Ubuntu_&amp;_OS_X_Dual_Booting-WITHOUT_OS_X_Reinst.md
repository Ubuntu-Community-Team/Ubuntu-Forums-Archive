---
title: "Ubuntu &amp; OS X Dual Booting-WITHOUT OS X Reinstallation"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by iAndy on 2006-10-17
I'm getting real tired of not being able to afford a MBP, so I need to get Ubuntu onto my PowerBook...BUT...without reinstalling OS X.  Theres plenty of ways out there to get Linux onto the Mac along side OS X, but they all include reinstalling OS X, or just only using Linux and loosing OS X.

I know the linux community are always one for a good challenge, and I'm wanting to contribute something to the community of Ubuntu etc, so I thought I'd try and get Ubuntu onto my PowerBook G4 12" without reinstalling or otherwise screwing up OS X.  However...as with a community effort I need help!  I'm blogging everything I learn, hear and try on this project over at my blog at [andyjshaw.com,]("http://www.andyjshaw.com") you can read about this particular project directly [here]("http://homepage.mac.com/andyjshaw/iNet/ibuntu/index.html").

Anyone know how to do this?  Any helpful words or insights?  Post back here or on my site, I don't mind!  I'm totally open on this and really want to learn as much as I can!

---

### Post by linear on 2006-10-17
Have you seen this thread?

[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)

(Describes how to non-destructively shrink your OS X partition.)

---

### Post by iAndy on 2006-10-18
I hadn't!

Thanks for the heads up!...seems ideal!

It describes that you need to disable Journaling on your Mac drive if it is enabled, do you know what the journaling does and what I will lose by disabling it?

Thanks for the help!

---

### Post by iAndy on 2006-10-18
Scrap that journaling question!

Eventually got through the whole thread and it was all explained to me!

Had me going there for a sec with the Live CD, but I'm currently 12% shrinking my partition using parted!...all seems to be going well!...fingers crossed!

I've given 10Gb over to Ubuntu, which leaves me with 5Gb free for OS X!  (Yes, on my 100Gb hard drive I'm down to my last 15Gb and decided to dual boot!...logical!)

Thanks for the pointer to the thread!...learnt so much off it! (which is half the reason I'm doing this!!)

---

### Post by linear on 2006-10-18
If you haven't already, I'd suggest a search on your specific model in the [Apple PPC forum]("http://ubuntuforums.org/forumdisplay.php?f=133"). It's helpful to know about any tips or pitfalls before you go too far.

---

### Post by iAndy on 2006-10-18
> **linear said:**
> If you haven't already, I'd suggest a search on your specific model in the [Apple PPC forum]("http://ubuntuforums.org/forumdisplay.php?f=133"). It's helpful to know about any tips or pitfalls before you go too far.

Thanks!  Having a read now!

I am all done with the installation.  Dual-booting works a charm!

Just a few minor issues, the biggest one being the trackpad.  The trackpad works but is VERY VERY slow and unresponsive.  Scrolling across the screen takes a long time!  USB mice work fine, obviously, but the trackpad is a must...so I battle on!

I'm playing around with some drivers, but can't seemto get very far, htey are too long winded and complicated for a more simple user!

Know of any insights?!

---

### Post by linear on 2006-10-18
Nothing from personal experience. I don't have a PowerBook.

However, a quick search comes up with this: [http://www.ubuntuforums.org/showthread.php?t=270988](http://www.ubuntuforums.org/showthread.php?t=270988), which has some suggested edits to /etc/X11/xorg.conf.

(But instead of running the file browser as root, I would recommend running the _editor_ as root. Either **gksudo gedit**, or, if you don't mind the command line, open a terminal window and: **sudo nano /etc/X11/xorg.conf**.)

---

### Post by iAndy on 2006-10-20
Thanks for the guide link! It was perfectly simple and clear and worked without a single tiny hitch...thanks!

I do have some questions about the trackpad after doing this now.

My tracking speeds are must better now, thats great...however the sensitivity seems to have been decreased. As long as a keep my finger on the trackpad and keep it moving it is fine, if I stop for a brief second the trackpad will stop working and will no longer pick up my finger movin across it. I have to move my finger away and wait a brief second before it seems to wake up again and pick up my finger movements again. This is highly strange. It's almost as if it gets stuck...freezes for a few seconds, before unfreezing and carrying on again.

Before the trackpad didn't do this, it was just very slow, but picked up my finger fine every time.

Anyone know why it is doing this and have any suggestions?!

---

### Post by linear on 2006-10-20
Here's another resource to dig through:

[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

There are additional settings you could try.

---

### Post by iAndy on 2006-11-15
Thanks for the link.  Been slowly working through it, but come across a problem.

I haven't booted into Ubuntu on my mac for a week or so, and now I come to find that the boot loader, yaboot, or whatever it is, appears to have vanished, and therefore won't let me boot into Ubuntu.  

Before when I turned my Mac on, it would give me the BIOS looking screen of selecting l for linux or x for mac os x or c for CD ROM, before booting into Ubuntu by default.  Now it doesn't give me this at all...not even blinking before bootig up into OS X.  Has something happened to my open firmware where yaboot has vanished or for some reason has stopped working?

I can think of no large updates I have installed since I last used it.  I presume Ubuntu is still there and fine, just can't get to it!...any advice oh clever people of the community?

I've actually come to install Edgy, see how it runs on my PowerBook, to see what issues are there with it...but obviously found I can't boot into Dapper to start with suddenly!

---

### Post by linear on 2006-11-15
Did you, by any chance, use "Startup Disk" to select OS X for booting? Whether you did or not, try the fixes here: [https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot](https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot) (scroll down to the section headed: "**You lost the yaboot menu! Now what?**").

---

