---
title: "Dammned dependencies, how do i sort this one?"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by phrilll on 2006-07-30
Hi, after suffereing a catastrophic windows corruption i took the extreme measure of formatting bill gates' sticky little fingerprints out of my hard drive and decided to dtart afresh with ubuntu. Seems to be going (slowly) well, but i have some issues...

I dont have internet on my ubuntu machine, uness someone can tell me how to share a mac's internet connection through ethernet to my laptop..

So i have been laboriously transeferring .deb packages via flash drive to install programs. trying to get mplayer running, i am thwarted because i need to install libggi2, to do such i must first have installed
libgii0
But to install libgii0 i need
libgii0-target-x
and to install libgii0-target-x i need libgii0. AAAAAAAAAHHHH!!!!

I am also having problems with blender - it's there, installed and so on, but nothing happens when i click. I ran it in terminal by typing blender, and was told:

Xlib: extension "GLX" missing on display ":0.0".
ERROR: Unable to open Blender window.

And a final one, anyone know how to reassign botton functions on a Wacom tablet pen?

Given that i know nothing about Linux and Ubuntu, i have no idea what to do. Any advice greatly appreciated!

Thanks

---

### Post by Stew2 on 2006-07-30
Hi, is there any way you could hook your laptop up to the internet for a while at least? Then you could install all these programs with synaptic and it would take care of the dependencies for you. Couldn't you just unhook your mac for a while and plug in your laptop to do the installs and updates?

Regards,
Stew2

---

### Post by Tomosaur on 2006-07-30
Bit of a sticky situation you've got yourself in there. I can understand your frustration definately - getting programs to work is often a nightmare, and without an internet connection, practically impossible.

I found this in a slashdot comment:
> 
Installs perfectly in Parallels (release candidate 2) running on a MacBook. Use the x86 Desktop edition, choose a Linux > "Debian" environment.

Only trick is getting a network connection via a MacBook's AirPort card. For that, choose "Host Only Networking" in the Parallels parameter screen (this has to be done as it defaults to a Bridged Ethernet port and emulates a Realtek NIC, which would require a cable to be plugged in).

Then go to Mac OS X's System Preferences > Sharing > Internet.
Select "Share connection from: AirPort"
Select "To computers using: eth2" (should be a bottom of list)

Make sure Ubuntu is using DHCP in its Networking config (it does by default), and has its default Ethernet port active. Now you should be able to open Ubuntu's pre-installed Firefox and check you've got a connection.


Dunno if that will help you, just thought I'd point it out.

You may also want to think about grabbing this and burning it to a DVD:

[Ubuntu main and restricted repositories](http://linuxtracker.org/torrents-details.php?id=2170)

I would definately try and get a shared connection going though. Life without internet while using linux is hard-going.

---

### Post by catlett on 2006-07-30
There are other ways to get the repositories. One way is to pay $35 for the repository DVDs or find a computer with internet access and download/burn the repository DVDs [http://www.ubuntuforums.org/showthread.php?t=224956](http://www.ubuntuforums.org/showthread.php?t=224956)
After you have access to the repositories you may want to refer to the Dapper Guide for instructions on how to install certain applications. [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)

---

### Post by phrilll on 2006-07-30
The plan was to hook it straight up, unfortunately my friend has lost the password for his connection, so i don't think it would work if i plugged his modem into my computer. 

"Installs perfectly in Parallels (release candidate 2) running on a MacBook. Use the x86 Desktop edition, choose a Linux > "Debian" environment.

Only trick is getting a network connection via a MacBook's AirPort card. For that, choose "Host Only Networking" in the Parallels parameter screen (this has to be done as it defaults to a Bridged Ethernet port and emulates a Realtek NIC, which would require a cable to be plugged in)."

Parallels? what's this? Its not a macbook but an imac G5 if that makes any difference, but i can't find a parallels parameter screen for love nor money. Still, persistence is the key to success....

---

### Post by Tomosaur on 2006-07-30
Unfortunately I don't own a mac of any variety, so I'm probably not the best person to be asking :P

I have heard about parallels though. I'm not entirely sure on the portability of programs between different types of macs, but I did find this:

[Parallels homepage](http://www.parallels.com/en/products/workstation/mac/)

Doesn't look like it's free though :S

---

### Post by kadymae on 2006-07-30
> **phrilll said:**
> 
I dont have internet on my ubuntu machine, uness someone can tell me how to share a mac's internet connection through ethernet to my laptop..


Do you have dialup or cable/DSL as your internet connection?

Because if you have cable/DSL, go and buy a router.  You'll be glad you did.

But according to my copy of the Missing Manual (OS 10.3) ...

1) If the "gateway" mac is asleep or off, there is no access with the other machine.

2) On the "gateway" mac, open up the Sharing panel of System Preferences, click the Internet tab, and click on Start

3) Next to Share Your Connection From, identify how your "gateway" Mac connects to the Internet.

4) Under To Computers Using, select how you connect your other computer(s) to the "gateway" mac.  (Note, you can't use wireless unless the "gateway" mac also has a wireless card installed.)

5) On your laptop open up the networking settings (I'm using Xubuntu, so I can't get specific about how to navigate to them on an Ubuntu machine) and where you choose how your laptop connects to the internet, choose the setting that specifies how the laptop connects to the "gateway" mac (wireless, ethernet, firewire, etc.). 

6) And I'm not sure exactly where you will find it in the networking settings, but choose DHCP wherever you find it.

Save and apply all settings.  You might even want to do a logout/login to force everything to reset.

This *should* work -- it's also how you would get a Windows Machine to share a connection -- but no gurantees.

Good luck.

---

