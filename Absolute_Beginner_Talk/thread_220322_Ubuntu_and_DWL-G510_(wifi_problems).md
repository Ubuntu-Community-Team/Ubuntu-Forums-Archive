---
title: "Ubuntu and DWL-G510 (wifi problems)"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Falcon X on 2006-07-21
I'm a new user to Ubuntu (I've used Fedora Core in the past).  This is my first time trying to setup a wireless card in linux, so I'm going through a bit of a learning curve.

Unfortunately, it doesn't look like Drapper Drake recognized my wireless card.  As the subject says, it's a DWL-G510 and it's working with the nForce2 chipset.  From what I've read Ubuntu should automatically install and configure my wireless card so I'm having troubles finding a walkthrough/tutorial.

Any help would be greatly appreciated!

---

### Post by orb9220 on 2006-07-21
Well if you have a dwl-510 rev B1 card yes that is supported in ubuntu.

That is what I'm using which I believe is based on the Aethros chipset.
But if you have first series 510 that may not be supported.

Check the wireless forum and search with the term 510 and see what popups.
You may have to configure with ndiswrapper program which is a workaround for linux unsupported cards.

Sorry couldn't be more help.

---

### Post by Falcon X on 2006-07-21
From what I've been looking at, yes, I think I need to use the ndiswrapper utility.  I am pretty sure I have the first rev of the DWL-G510 so it's based on a different chipset than yours.

---

### Post by KingBahamut on 2006-07-21
[http://doc.gwos.org/index.php/D-LinkWireless](http://doc.gwos.org/index.php/D-LinkWireless)

---

### Post by Falcon X on 2006-07-22
It seems I should use the madwifi drivers.  The installation instructions require the downloading and installation of these drives.  I thought they came with Dappper Drake?

---

### Post by richbarna on 2006-07-22
> **Falcon X said:**
> It seems I should use the madwifi drivers.  The installation instructions require the downloading and installation of these drives.  I thought they came with Dappper Drake?

[http://madwifi.org/wiki/Compatibility#DWLG510](http://madwifi.org/wiki/Compatibility#DWLG510)

Check out the mad wifi link in my sig.
|
|
v

---

### Post by orb9220 on 2006-07-22
A chunk from another place:

Madwifi is mostly made for atheros chipsets, so rev. B of this card should work flawlessly in ubuntu since madwifi is installed by default. But for the Rev.A with a marvell chipset, you will need ndiswrapper. I've read somewhere that ver 1.5 is working rock solid with this card, and 1.1 or 1.4 could end in kernel panicking. This was an old post on a forum, so now just use the latest version, 1.13, and it should work perfectly. For installation, you have 3 ways: install the old ndiswrapper-utils 1.1 deb package for ubuntu(not recommended), compile the latest 1.13 version or finally you can also build the 1.13 to get a deb package then install it with dpkg.

The latest way is my preference, since you can easily and cleanly uninstall ndiswrapper when an error happened, using dpkg -P. Here is a simple way to do that: [http://ubuntuforums.org/showthread.php?t=104539](http://ubuntuforums.org/showthread.php?t=104539)

All is there, even a noob will understand. The only thing that is not mentionned: first, before following this HowTo, go under synaptic package management and add other repositories like in this guide here: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto).

After you are done with the ndiswrapper installation, follow the last install tips on the ndiswrapper site to get your windows drivers to work.

Example:

ndiswrapper -i name_of_the_windows_driver_file.inf
to select your windows driver
modprobe ndiswrapper to load the ndiswrapper module. You should see now you wifi card in the network tool, under system tab.

Run in a term  lspci which will confirm your card chipset.
Then go to the wireless forums here and post and read the answers are probablly there.

Good Luck

---

### Post by Falcon X on 2006-07-22
Thanks!  After opening up my box, I confirmed that by card is a Rev. A card (marvell chipset).  I will definitely try your recommendations.

---

### Post by Falcon X on 2006-07-22
Okay, so I have begun the process.  The one thing that's not explained and what you said I would have problems with is the packages.  I am curious what packages I need as I am stuck at the *fakeroot debian/rules...* commands.

---

### Post by Falcon X on 2006-07-23
Ignore the previous post.  I grabbed the wrong version of ndiswrapper.

However, I have successfully done through the installation process of ndiswrapper and attempted to load the driver.  Everytime I load the driver I do *dmesg* to check whether it was succesful, and it says that it could not talk to the hardware.  I am using the drivers that ndiswrapper suggest and have also tried the 2000 and win98 varients.  I'm a bit confused at this point in time.  Any advice would be great!

---

### Post by orb9220 on 2006-07-23
Well sorry No since I have never gone thru the process myself.

But what you could do is outline the steps you have done and post in the wireless forum so the wireless guru's might spot the problem.

Also try google with 3 term searches like: g510 marvel ndiswrapper or g510 ndiswrapper madwifi etc... I find using 3 and 4 term search can help pinpoint info to help,

---

