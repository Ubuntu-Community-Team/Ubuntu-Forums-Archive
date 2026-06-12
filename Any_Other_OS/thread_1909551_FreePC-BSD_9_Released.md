---
title: "Free/PC-BSD 9 Released"
date: 2012-01-15
forum: Any Other OS
---

### Post by Double.J on 2012-01-15
Hi all, 

For any interested, FreeBSD 9.0 final released Thurday, followed by PC-BSD 9.0, Isotope Friday.

I was a bit caught out by the speed of the follow up release, so only have a base install of free 9 at the moment. But can confirm I had no issues with the installer using zfs.

The immediate follow up of PC-BSD Isotope has meant I've been playing with this over the weekend; not much change from RC3, No bugs for me as yet - checked out the LXDE and KDE desktops so far, not tried gnome 2 or XFCE yet. 

Just wondering how others have got on?

---

### Post by sffvba[e0rt on 2012-01-15
I was tempted to try PC-BSD 9 but I see there is an issue with Intel Graphics and 3D acceleration (that should be sorted out by 9.1) so I guess I will wait.


404

---

### Post by the8thstar on 2012-01-23
I'm currently downloading it and hoping it will run smoothly in Virtualbox.

I'll post again to keep you guys updated.

---

### Post by Double.J on 2012-01-24
how'd you get on the8thstar? I first tried PC-BSD in a Vbox from a CD and got real graphics issues with KDE, had to use VMWare.. did finish my install of free and added KDE and gnome to test, but have since overwritten.

Let us know how you got on :)

---

### Post by the8thstar on 2012-01-24
Well, I downloaded the VBox image with guest additions installed. 

I chose KDE 4.7. as my desktop environment.

The system reports several random problems with KWin crashing and desktop effects can't be enabled. 

I failed at reinstalling guest additions from the ISO because there is no executable for BSD (only Windows, Solaris and Linux). Bummer! 

Also, I would like to replace GDM with KDM but I have no idea how.

---

### Post by wolfen69 on 2012-01-24
I *would* give it a go, but there is no guest additions for vbox. Weird.

---

### Post by TransitMan on 2012-01-24
> **wolfen69 said:**
> I *would* give it a go, but there is no guest additions for vbox. Weird.

Huh? What??
I found the vbox file and installed it in my VirtualBox without any problems.

Here's the link to the downloads page - [http://www.pcbsd.org/index.php?option=com_zoo&view=item&Itemid=98](http://www.pcbsd.org/index.php?option=com_zoo&view=item&Itemid=98)
Scroll down and you'll see several installation downloads available.

---

### Post by the8thstar on 2012-01-25
> **TransitMan said:**
> Huh? What??
I found the vbox file and installed it in my VirtualBox without any problems.

Here's the link to the downloads page - [http://www.pcbsd.org/index.php?option=com_zoo&view=item&Itemid=98](http://www.pcbsd.org/index.php?option=com_zoo&view=item&Itemid=98)
Scroll down and you'll see several installation downloads available.

Do you have any issues with desktop effects in Gnome and KDE?

---

### Post by TransitMan on 2012-01-25
> **the8thstar said:**
> Do you have any issues with desktop effects in Gnome and KDE?

Not that I've noticed, when I get around to playing with it.  :popcorn:

I am wanting to learn the ins and outs of BSD and figured I'd get my feet wet by installing this latest from PC-BSD. :guitar:

---

### Post by jackdale on 2012-01-26
I've been a fan of PC-BSD since 7.1 for a variety of reasons.  Since 8.2, the installer has been more than impressive.  I am particularly impressed with the installer in 9.0.  I briefly list a couple of reasons below:

Choice of installing PC-BSD (desktop) or FreeBSD (server)

Choice of officially supported desktop environments (GNOME (2), KDE, XFCE, LXDE, etc)  You can also choose to install multiple DEs at first install.

There are a large number of "unsupported" DEs that you can also install (including OpenBox).

If installing in a virtual machine, you can install VMWare or VirtualBox guest additions as a default package.  Also can install drivers by default (eg NVidia)

Can install compiz as standard

Choice of shell (eg csh, bash, sh, etc)

You can choose what packages you include for each DE (eg choose not to install KOffice :D, etc)

Multiple users and groups can be set-up at installation.

All this saves a lot of mucking around after installation.

(Some of these features have been present before 9.0, but the package now is fabulous!)

And now the PBI package manager is a lot more mature and has most of the kinds of packages that we would expect in a modern distro (although a few are not quite bleeding edge given the lag for porting).

And then what a solid system.  No deal-breaker bugs.  Thoroughly tested prior to release.  Released a few months late to ensure this (mainly because of problems with FreeBSD release schedule).

I think PC-BSD is now at a level where it can really start to compete with the bigger linux distros for the desktop market.

---

### Post by Double.J on 2012-01-26
I agree the improvement of the bpi in this release, as well as the choice of DE's (same as official Buntus) is excellent.

(for thos unaware pbi's is the key feature of PC over free - they are binaries like .deb's that massively speed up installation over the source based install of free's ports)

The only problem I had with the installer was that I used GPT - whilst officially supporting it, it would seem the installer can only handle GPT if it's re-writing the partition table. I had to use gpated to create a fat32 partition for the installer to use as it couldn't *see* 150GB of free space on the drive, and then when it did install, didn't configure the bootloader correctly, so I had to chainload to it manually... still I'd ratheer it did that than write over my current set up by default ;)

---

### Post by wolfen69 on 2012-01-26
> **TransitMan said:**
> Huh? What??
I found the vbox file and installed it in my VirtualBox without any problems.

Here's the link to the downloads page - [http://www.pcbsd.org/index.php?option=com_zoo&view=item&Itemid=98](http://www.pcbsd.org/index.php?option=com_zoo&view=item&Itemid=98)
Scroll down and you'll see several installation downloads available.

Thanks, I'll check it out.

---

