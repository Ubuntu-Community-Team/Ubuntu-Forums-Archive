---
title: "Cisco Aironet 350 on Powerbook &quot;Lombard&quot; Ubuntu success story ;-)"
date: 2005-03-23
forum: Apple PPC Users
---

### Post by erkki70 on 2005-03-23
Hi everyone,

Currently trying to install a Cisco Aironet 350 wifi card on a Powerbook "Lombard" 333mhz/192Mb RAM/4GIGA HD, I thought I could share my experience with other users.

This thread might not be architecture and wifi card vendor specific and could also apply to i386 or others.

Previously, I've installed Ubuntu on the exactly the same hardware, ending up with a fully working box, except the wifi card which wasn't plugged in during install, and despite trying a lot of different things for almost a week (intensive googling!), config, tweaks, etc, I just couldn't get it to work. (yep, that's probably related to the fact I'm a newbie!)
So I decided to give it a second try with the card attached, as I read that Warty users reported that the card worked and was automagically detected.

I chose "install-powerpc" btw, with no special parameter.
Hoary ppc install goes smoothly (impressively easy and quick!), everything looks fine and eth0, eth1 and wifi0 are detected upon install when configuring network. 

I had to use eth1 as primary interface (I left eth0 unconfigured but plugged and wifi0 didn't seem to catch DHCP?), giving the right ESSID and WEP key it looks like it automatically get DHCP hooked, allowing me to keep going with the install. 

Due to HD size, this is a linux only box and I erased the HD with the partman tool on the CD. No prob, install goes.

Everything runs smoothly, and I reboot into the fresh Ubuntu :)

All again looks fine, just have an error on time syncing with ubuntu server, but airo messages are showing and the status and activity leds on the cards are both up, I assume that modules are then loaded and the card is recognized.

Install goes on, selecting and unpacking and finally setting up. 
So far so good, and it even fetches automatically some of  the updates.
Looking good but could it be so that it goes through eth0?

I finally get to see the GDM logon screen, signed in and that was it!
The Cisco Aironet 350 wifi card is up and running, without the need of any particular driver nor proprietary software, or tweak or configuration as everything is automagically handled by the installer.

I installed the 276 updates through this connection including the pcmcia-cs and 
after some minor error messages and a reboot:
Wow! :shock:
Still working!!!

So, if you're experiencing wifi card post-install problems, driver, settings or what so ever, don't give up and try a fresh install with your device attached, it might also work for you.

Thank U Ubuntu!
Default install looks to work really nicely, especially hardware detection and resulting installed box sticks to what's expected. 
After adding/removing packages to suit one's flavour, this distribution is a great great one! 
Keep on the good work!

---

### Post by orion_114 on 2005-04-09
Its allways good to see another satisfied ubuntu user ! :)

---

### Post by fortyfoxes on 2007-08-13
Hi, I’ve also got a Lombard (400Mhz), but try as i may I cannot get Ubuntu / Xubuntu installed. It is sticking at the “Retrieving choose-mirror” stage and Google is no help finding anyone with similar experience - I am trying to install the latest Xubuntu available for PowerPc - Dapper 6-06 .1

---

### Post by tcrroadie on 2007-08-13
Have you tried installing Feisty on your Mac?  If you have not yet, I would highly recommend trying Feisty.  Feisty Fawn has many updates and bug fixes to the kernel for PowerPC.  You can download Xubuntu 7.04 from the link below. 
[URL="http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/"]
Xubuntu 7.04 (Feisty Fawn) Downloads[/URL]

Also, please be sure to read the [PowerPC FAQ Wik]("https://wiki.ubuntu.com/PowerPCFAQ")i.

---

