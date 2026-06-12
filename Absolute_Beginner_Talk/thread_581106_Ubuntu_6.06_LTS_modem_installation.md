---
title: "Ubuntu 6.06 LTS modem installation"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by death__machine on 2007-10-19
Hi guys,
I had come to these forums sometime back for help in installation for Ubuntu 7.04 which i couldnt install cuz of ATI drivers.
Anyways i tried running the live cd of 6.06 LTS and it worked!! So i plan to install it, i do have a slight problem though, ubuntu didnt detect my modem in the live mode.
So i downloaded some drivers from [http://eciadsl.flashtux.org/download.php](http://eciadsl.flashtux.org/download.php). My modem is listed, but i dont understand how to install the modem, even with the given instructions([http://eciadsl.flashtux.org/tutorial.php](http://eciadsl.flashtux.org/tutorial.php)) cuz some part of it is in some other language. Can anyone help me with this? 
I have downloaded this file _eciadsl-usermode_0.12-1_i386.deb_ .
I was thinking of pasting this file on a flash disk and connecting the flash disk after installation of ubuntu.
Should i try this? And if anyone has used these drivers i would appreciate the help.
The live version of ubuntu was awesome!!
thanks guys

---

### Post by 001100 on 2007-10-19
use 7.10 more devices use a torrent to download. and yes use the restricted driver mananger to enalibe your ati card. 7.10 works a lot better with devices in my case.

---

### Post by death__machine on 2007-10-19
The tutorial page mentioned to download an rpm file, will the installation of the rpm file be different from the .deb file that i downloaded? Are they just different formats?

And i also downloaded the synchronization file mentioned in the tutorial.
I will post here after installation of ubuntu
Wish me luck!!

---

### Post by death__machine on 2007-10-19
> **001100 said:**
> use 7.10 more devices use a torrent to download. and yes use the restricted driver mananger to enalibe your ati card. 7.10 works a lot better with devices in my case.

You mean to say that 7.10 may have a chance of working since 7.04 didnt work on my system?
And how do i use the restricted driver manager?

---

### Post by death__machine on 2007-10-19
I have started downloading 7.10 just to check if my modem works , or if even my pc can make it thru live mode. Will post when i have burnt the cd and have checked it.

---

### Post by death__machine on 2007-10-19
Hey guys, i tried ubuntu 7.10 on my system, the live cd worked. So the only problem that i have right now is to get my modem working. I havent installed ubuntu yet but i will as soon  as i get info on installing the modem. Can anyone one help me on that?
System Configuration:
Dell Inspiron 6400
Intel Core 2 duo 2.0 Ghz
2 GB ram  667 mhz
ATI MOBILITY RADEON X1400 128MB
120 GB HDD
Alcatel lucent Cellpipe USB20a

---

### Post by death__machine on 2007-10-19
Hi i tried to install the usb modem, thru settings and stuff but i couldnt :(. The wireless adapter of my notebook works in ubuntu (i wish i had taken a wireless router instead of the usb modem). I really dont know how to get internet working. And is there a way to remove free space from the partition of windows that i am using and create a new partition thru that free space?

---

### Post by death__machine on 2007-10-20
bump

---

### Post by death__machine on 2007-10-21
bump

---

### Post by podunk on 2007-10-21
First - do you have any important data on your notebook? If so, there is always a chance of data loss when you play with your partition. I'd strongly suggest you back up the important stuff.

Shrinking the windows partition. Is this XP? If yes I think you'll find that using the drive manager in the windows control panel the easiest and safest  way to go. It will present information to you in a way you're familiar with. Using the control panel utility shrink the windows partition and format the new partition fat 32 - it'll be easy to spot that way when you get to the ubuntu install.:)

Versions. Are you new to Linux? If so installing the latest and greatest can sometimes be a problem. The latest and greatest will usually support more hardware than older versions, but older version have had lots of fixes applied, there are a lot of work arounds to problems here on the forums, and a very large pool of users experienced in the older version.

7.10 is 3 days old here - folks will find lots of little bugs and quirks to work around. 

Devices. I doubt very seriously that you'll be able to get your modem to run when you're using the live CD. Installing things into the virtual ram disk gets complex quickly. I'd suggest you go ahead and install to your hard drive then give the modem a go.

Getting a stock install of 6.06 won't take but an hour or so. You'll need to burn the *Ubuntu* deb package to a CD while in Windows then post back and one of us will help you from there.

A comment about Windows devices in general. Things that the manufacturer doesn't offer Linux support for sometimes just can't be made to work at all in Linux. Printers and modems in particular are problems. If you're thinking about making the switch to Linux permanent you might want to consider buying hardware that comes with native Linux drivers. It'll avoid having to fidget around with stuff every time you upgrade versions.

---

### Post by death__machine on 2007-10-21
Thanks a lot. I will try partitioning, i already have the Ubuntu 6.06 burnt on a cd. I will post after installing ubuntu successfully. Thanks man

---

### Post by death__machine on 2007-10-24
Hi i was about to install ubuntu 6.06 but, I kinda got confused at this one point.
Umm i rezized my windows partition from 109 gb to 89 gb so i got 20 gb free and I utilized 15 gb for /root and 2 gb for /swap. So i come at this point where four partitions are listed, / , /swap ,and the other two which are supposed to be windows and mediadirect partitons started with /media. So i was worried if doing this would make windows not function or something. Is that true?
That is the  q i have, whether the address of the windows partition should start with /media or something else?

---

### Post by death__machine on 2007-10-24
Installed Ubuntu successfully!! :D . 
All i need now is help on installing my modem. I tried installing the .deb file which i have mentioned before but it gave an error saying incorrect architecture i386 and i have no idea what that means.
Can anyone help me with the modem?

---

### Post by death__machine on 2007-10-24
bump

---

### Post by death__machine on 2007-10-24
bump

---

