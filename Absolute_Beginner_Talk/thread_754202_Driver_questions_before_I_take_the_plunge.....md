---
title: "Driver questions before I take the plunge...."
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by 124C41+ on 2008-04-13
I might be a little too cautious here but I think my paranoia is justified. 

I have been searching on the interwebs for around a day and a half now and have not been able to get a definitive answer for my question. 

I have heard people are having alot of troubles with the Radeon X1950 AGP version on Ubuntu. I have a  Radeon X1950 PCI-E. I have been able too boot into Ubuntu on a live CD with no troubles. IE. The background shows up as well as icons and also  the sample movies that are in the example folder play fine, I can also connect to my wireless network no problem.

Right now on windows I am using a 3rd party program called ATI tool for my driver, as well as for fan control, temperature monitering and clock control.

I have been told to use ATI Linux drivers from the official page. The Problem is that these drivers only go up to X1900 Series in the X86_64 Heading. [Here]("http://ati.amd.com/support/driver.html") My suspicions were confirmed by 1 or 2 threads on the forum here that these drivers did do not work for the X1950 AGP. I have not seen anything for the PCI-E version.  

What I am looking for is someone who can confirm that they are able to get 3D rendering, flash movies, fan and temp control in Ubuntu with my card using something other then the native drivers. 

Also any help on how drivers actually work in Ubuntu would be great as well.

 Any Help would be appreciated. Thanks

---

### Post by diablo75 on 2008-04-13
I think you'll be in good shape if you use Envy to install your ATI drivers for you.  It's very easy, all automated.

Here's the deb installer for Envy:  [http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb)

All you have to do is download and run that.  You might even download in run it while in a live environment to see if it correctly detects your video card.

A good list of compatible cards can be found here:

[http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL)

It is probably not a complete list, but the x1900 is listed in there.  Chances are the 1950 works with no issues as well.

Edit:  By the way, Flash is independent of your video card (doesn't matter what kind of card you're running to run flash).

Also... when you say "fan and temp control" to what extent do you mean?

---

### Post by 124C41+ on 2008-04-13
When I open it with the package installer it gives me the following message in the program in red text. "Error: Dependency is not satisfiable: module-assistant" and the "Install Package" button is grayed out. What now lol :P

This is in the Live CD version BTW.

Edit: I mean video card fan control. Fan control generally = temperature control.

---

### Post by 124C41+ on 2008-04-13
Bump

---

### Post by diablo75 on 2008-04-13
I've never heard of software that controlled the fan on your video card, but I suppose it could be done.  Why you would need to do that....well, hey.  I don't have a $500 video card to look at, but I guess the way they're going....  I've had software that could adjust the speed of the CPU fan, but it was subject to motherboard support for such a feature.

Anyway, I don't know about the fan thing.  Personally, I wouldn't worry about.  Stuff like that (fan speed regulation) is probably done entirely by the card itself.  Do you have an app that you are using right now in Windows that does what you are describing?

-------------

As far as that dependency error goes, it's got to do with the fact that the OS hasn't been installed yet.  So certain things in the Live environment are not enabled.  I suggested it as a "Maybe this will work" kind of suggestion, not a scientific method of any kind....

What you could do is just install Ubuntu along side windows as a dual-boot configuration.  Try it out for real, if all the hardware works to your satisfaction, then reinstall it again using the entire hard drive.  If you don't like it, you can use a GParted bootable CD to delete the Linux partitions and resize your windows partition back out to fill in the gap.

---

### Post by starcannon on 2008-04-13
Best advice for those nervous about taking the plunge is to do a wubi Ubuntu install from within windows, then if your less that pleased you can just use the windows uninstall feature in the control panel to get rid of it.

If I'm not mistaken wubi is included on the Ubuntu 7.10 Gutsy Gibbon Live CD, if I am mistaken then you can download wubi here [http://wubi-installer.org/]("http://wubi-installer.org/")

This is the method I used with my Dad when he was flirting with Ubuntu, after he found out he was only booting windows to use anyDVD and DVDshrink he went ahead and resized his windows partition and did a true dual boot setup. Anyway, its a great non destructive way to try Ubuntu as an install instead of a LiveCD.

---

### Post by 124C41+ on 2008-04-13
Im going to install it under a separate partition and run hardware tests. Thanks for your help guys.

---

### Post by Hendrixski on 2008-04-13
Just to put some perspective on this... drivers used to be a horrible problem on linux, so I every time I tried it I was like "screw this"  now... I've installed Linux on about 10 of my friends computers in the last few months and no driver problems.... and it's only going to get better.  So... don't worry about drivers, it'll all get squared away quickly

---

