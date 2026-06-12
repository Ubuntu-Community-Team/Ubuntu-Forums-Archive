---
title: "Install Breezy when CD-ROM's dead?"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-02-17
Hi everyone,

A friend gave me his old Dell Latitude GenuineIntel 4.G 64 RAM with Win 98 SE on it.
Is it somehow possible to download Breezy and install it  even though the CD-ROM is dead?

---

### Post by kakashi on 2006-02-17
i think its possible to install it from a usb stick. no idea how though

---

### Post by mr_mop on 2006-02-17
Check out this thread.
[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

It is possible if you have a network connection. :) Just takes a while.
I did this with DOS instead of Windows as its quicker to install/setup.

---

### Post by xyz on 2006-02-17
Thanks guys!
The link's great! Being a noob, I'm sure it'll take me quite some time to get through this but I'll sure give it a try.
My friend wasn't sure but he thought 'Partition Magic' needs reinstall in Win98SE! I hope he was mistaken because....CD-ROM's busted!
Good day!

---

### Post by mr_mop on 2006-02-17
Unless you want to keep the Win98, then I'd say you don't need partition magic.
The Ubuntu installer will allow you to erase the disk and partition as you want.
Here's what I did.
1) Installed DOS 6 to a 500MB partition at the start of the disc. Try [http://www.freedos.org/](http://www.freedos.org/) if you don't have DOS
2) Followed the instructions in that thread, changing where it said about windows to DOS.
If you want to keep Windows, then you will need partition magic.

---

### Post by patrick295767 on 2006-02-17
I installed that too on a very old pc....
  
I warn you : with 64MB of RAM, it'll be very pain in the *** unless u use the XDMCP as a Server.
  Try lighter and faster distro ... This Breezy is very slow on 64MB ram old pc. 
You'll have to use DILLO as webexplorer
Openoffice will be very slow tooo.
  
Only citrix and XDMCP can be thought to be used with breezy.  
  
========
So, to do it,  I used an external USB CD reader ... with some tricks...
  
I'll try to figure out how...

---

### Post by Brunellus on 2006-02-17
[QUOTE=xyz]Hi everyone,

A friend gave me his old Dell Latitude GenuineIntel 4.G 64 RAM with Win 98 SE on it.
Is it somehow possible to download Breezy and install it  even though the CD-ROM is dead?[/QUOTE]
what you'd need to do is to install over a local network, via PXE:

I've used a combination of these two howtos:

[https://wiki.ubuntu.com/Installation/Netboot?highlight=%28netboot%29](https://wiki.ubuntu.com/Installation/Netboot?highlight=%28netboot%29)

[https://wiki.ubuntu.com/Installation/LocalNet](https://wiki.ubuntu.com/Installation/LocalNet)

If you have trouble setting up dhcpd-server, just uninstall it and use dnsmasq instead.  Different program, same job, but less fussy (IMO) to set up.  The latter link assumes dnsmasq as the DHCP server  (rather than dhcpd), and this is the method I used with some success.

I should note, however, that I really only put the ubuntu base system on the install target this way.  Knowing what I know now, I would have had to use IP forwarding to make the install target aware of the internet, and connect through the server to apt-get updated packages.  

Once you've put the base system on, I would recommend running an extremely minimal system, using fluxbox or openbox as your windowmanager, and maybe midnight commander to manage files.  Have a look at the package selections over at [DamnSmallLinux](http://www.damnsmalllinux.org) for an idea of what you can fit in 50 MB.

ioh.  and by the way, I like your user icon.

---

### Post by patrick295767 on 2006-02-17
U can try to make sthg via USB hdd : [http://www.ubuntuforums.org/showthread.php?t=101780&highlight=bootable+cd](http://www.ubuntuforums.org/showthread.php?t=101780&highlight=bootable+cd)

---

### Post by xyz on 2006-02-18
You guys are just great! Many thanks!
 
I've carefully read what you all wrote and followed the links.
I never imagined it would be that hard...I mean, being a noob, I'm going to have to work hard to understand all of this. 

I realise (as Patrik said) that 64 MB of RAM isn't much but I figured that, since Win98SE runs (slowly but it works!), Ubuntu would obviously run better because it is lighter. I could, for inst., do without OO. One does with what one has and can afford to get!

Just to make it a tad clearer, could one of you guys advise me **which of the solutions/links you indicated that would be the simplest to follow for a noob?**
So far I've found it quite difficult to get the hang of it just to get started.

One last thing: here in Switzerland, I use 'Cablecom' to connect to internet. The package comes with a CD that I use to get connected. I just have to click here and click there to install my connection. It's very easy; no knowledge required!
Since my CD-ROM's dead, how will I be able to get connected once? Note that my CD-ROM just died a few days ago; I was able to use it (and install using the Cablecom CD) last week.

Have a good weekend.

---

### Post by Kangaroo on 2006-02-18
For the people wanting to help, but who have no idea what "Cablecom" is.. 

Cablecom is a company supplying Internet via Cablemodem. The PC usually has be connected to the Cablemodem and be set up, to request an IP through DHCP. 

The Cablecom-CD supplied is just a bunch of Windows-programs (Antivirus, Firewall, etc.) supplied with the whole package you get, but it is absolutely not needed to get connected to the Internet.

---

### Post by Bartender on 2006-02-18
xyz -
Clearly, the **simplest** thing for you to do would be to borrow or scrounge a working CD drive and plug it into your system.
I dunno about your level of comfort within your PC's case or how many computer users you can turn to for help, but swapping a CD drive is just about the simplest thing one could possibly find to do within a computer case.  The PC will automatically recognize the drive on start-up

---

### Post by xyz on 2006-02-20
Thanks Bartender. I think you're right.
This is probably a stupid question but...do I need to look for an identical working CD drive (my dead one looks kind of like a drawer!) or any working CD drive that I would somehow plug into the Dell Latitude?

---

### Post by Kangaroo on 2006-02-22
Maybe supply a bit more info on your computer. 
Have you tried Dell Customer Support ?

---

### Post by pbaehr on 2006-02-22
[QUOTE=xyz]Thanks Bartender. I think you're right.
This is probably a stupid question but...do I need to look for an identical working CD drive (my dead one looks kind of like a drawer!) or any working CD drive that I would somehow plug into the Dell Latitude?[/QUOTE]

It's a little bit more specific since it's a laptop. You'll need to try to find one that specifically notes your laptop model in the compatibility list. I (very) quickly searched for Latitude parts and came up with this:

[http://www.priorityelectronics.com/laptop-cdrw/dell-latitude.htm](http://www.priorityelectronics.com/laptop-cdrw/dell-latitude.htm)

The top one's pretty cheap.

Whatever you get, just make sure it mentions your model number. Installing it will probably be even easier than installing one in a desktop since they pretty much slide in and out on most computers.

---

