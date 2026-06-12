---
title: "VirtualBox Install Problems"
date: 2012-04-12
forum: Any Other OS
---

### Post by ken0069 on 2012-04-12
Linux Mint v12 x64 that was an upgrade from Ubuntu 10.10 about a month ago.  

I've been trying to install Virtualbox v 4.1.10 via the GDebi package installer off and on for a few days now and I'm not having very much luck as I keep getting  this error towards the end of the install.  

Error: Breaks existing package 'virtualbox-4.1' conflict: virtualbox-4.1 ( )

And before you tell me to install virtualbox from Synaptics, I did that but the latest version there is 4.1.6 and when I tried to install the add on support for USB drives it said that it wasn't compatible with the older 4.1.6 version??  

Ennywho, I've gone into Synaptics and uninstalled EVERYTHING Virtualbox and I've even tried to edit or delete the .VirtualBox folders in both the home and user directory to eliminate existing files as the problem to no avail.  

So I've been on a half dozen other forums trying to find a solution to this install problem but all those posts, one of which was over 85 pages, usually wind up off in left field and after reading for two + hours on one of those boards I decided to come home here and see if someone could help.  

So does anyone know why I'm getting this error and is there a way to delete those .VirtualBox folders if needed so that no OLD info is still there to make the install fail??

Thanks,

Ken

---

### Post by jonhoman on 2012-04-13
Hi Ken,

I've had a similar problem upgrading to VirtualBox 4.1.12 on LinuxMint 12 KDE. Here's what I did to get it to work:

1. Uninstall conflicting VirtualBox

sudo apt-get remove virtualbox-4.1

2. Download VirtualBox 4.1.12 for Ubuntu 11.10 (surprisingly the package for 12.04 does not install)

wget -c [http://download.virtualbox.org/virtualbox/4.1.12/virtualbox-4.1_4.1.12-77245~Ubuntu~oneiric_amd64.deb]("http://download.virtualbox.org/virtualbox/4.1.12/virtualbox-4.1_4.1.12-77245%7EUbuntu%7Eoneiric_amd64.deb")

3. Install package

sudo gdebi virtualbox-4.1_4.1.12-77245~Ubuntu~oneiric_amd64.deb

- Jon

---

### Post by ken0069 on 2012-04-13
Just ran that command line you posted and here is the output.

ken@Aluminum:~$ sudo apt-get remove virtualbox-4.1
[sudo] password for ken: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox-4.1 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
ken@Aluminum:~$ 

And this is how it's been since I uninstalled 4.1.6 the other day.  

Haven't tried the download/install deal from the terminal on 4.1.12 but will now to see if it works.

Oh, and thanks for the help!!

Ken

---

### Post by ken0069 on 2012-04-13
Well, there is joy in muddville today!  Got 4.1.12 installed plus the extension pack for USB 2.0 so now I'm going to install winders to see how that works.  

Thanks again for your help and as usual, this Ubuntu forum and it's members are the BEST support group for Linux on the internet!!!

---

### Post by ken0069 on 2012-04-13
Funny thing, tried to install an x64 Windows OS in Virtualbox but got errors stating that this computer didn't have an x64 processor??  Hummm, I have x64 Mint, x64 XP, x64 Vista and x64 7 installed on other drives in this box but can't install them in Virtualbox?  

Ennywho, I did get an x86 version to install though.  Weird, hey!;)

---

### Post by oboedad55 on 2012-04-13
> **ken0069 said:**
> Funny thing, tried to install an x64 Windows OS in Virtualbox but got errors stating that this computer didn't have an x64 processor??  Hummm, I have x64 Mint, x64 XP, x64 Vista and x64 7 installed on other drives in this box but can't install them in Virtualbox?  

Ennywho, I did get an x86 version to install though.  Weird, hey!;)

It depends on the processor you have. Google yours and see if it supports virtualization.

---

### Post by appalbarry on 2013-03-05
[jonhoman]("http://ubuntuforums.org/member.php?u=1612802") - Many thanks! Worked perfectly for me with Mint Release 13 (maya) 64-bit.  So simple!

---

