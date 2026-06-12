---
title: "Help Installng Ubuntu"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Blood Red Sandman on 2006-10-15
First of all, I am Linux n00b. After reading what is coming up in the Micro$oft's new Windows Vista EULA, I figured "Stuff This, I am Migrating to Linux"

Anyways, I have downloaded Ubuntu Destop 6.06. I have managed to get it to load into my computer's Ram. However I can not get my mouse to work under the GUI. First I thought it was some thinking that it was some thing to do with my wireless mouse. However i having the simulare problems with a normal PS2 mouse. 
(BTW, I think the keyboard is not reponding either under the GUI as I just had the screen saver turn on, and the only way to get out of it was to reboot the PC)

What am I doing wrong?

Secondly, my exposure to linux is rather small. If there any sort of online step by step reference that I can use actually **INSTALL** Ubuntu? Lot of the references that I found Eg. The offical Ubuntu Desktop Guide starts off with the basic foundation for linux and ubuntu, and then the next chaper is written as if I have all ready finished installing the OS and I now what to do some thing with it.

---

### Post by steve.horsley on 2006-10-15
The mouse/keyboard issue is going to be a problem for the live install CD. I would suggest that you try the "alternate" installer CD - it runs in text mode instead. The questions are identical for a basic install, but the "alternate" installer has more options if you want them.

Make sure you back up everything first. There is always a slim chance of some error scrambling your hard disk.

Here is a set of screenshots of a live CD install. As I say, the questions from the text-mode installer are pretty-much the same.

[http://easylinux.wordpress.com/2006/04/30/ubuntu-dapper-drake-beta-installation-from-live-cd/](http://easylinux.wordpress.com/2006/04/30/ubuntu-dapper-drake-beta-installation-from-live-cd/)

---

### Post by Blood Red Sandman on 2006-10-15
okay, I will give that a shot then.
I will just call it the night and wait for my off peak bandwidth to kick in before I get this new ISO.

Thank you

FYI, I am installing this on my other PC which I normally abuse any ways. :twisted:

---

### Post by ReaderRat on 2006-10-15
> Secondly, my exposure to linux is rather small. If there any sort of online step by step reference that I can use actually INSTALL Ubuntu? Lot of the references that I found Eg. The offical Ubuntu Desktop Guide starts off with the basic foundation for linux and ubuntu, and then the next chaper is written as if I have all ready finished installing the OS and I now what to do some thing with it.
For Instalation Help:
Install Ubuntu - Graphical (with pictures)
          [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Install Ubuntu - Text based (Alternate CD)(with pictures)
          [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Blood Red Sandman on 2006-10-15
I will give another shot at this later tonight after work.

Thank you.

---

### Post by Blood Red Sandman on 2006-10-16
okay, I can not be this stupid :-k 

Is the any reason why I normal PS2 Keyboard and Mouse will not work after the first menu?

With either Desktop i368 or Alternate i368, my PS2 & Corded keyboard and mouse become unresponsive after the first menu.

What am I doing wrong ](*,)
Is there some thing that i should be setting in my Motherboard's Bios ?


Computer Specs are as follows :- [SIZE="1"]
AMD ATHLON XP 1700
1x 512Mb @ FSB 400 Ram Hynix Chipset
MSI MS-6390 Motherboard
Leadtech nVidia GeForce FX-5700 256Mb / Dual Display / VIVO
Seagate 80Gb with 8Mb Cache ATA Hard Drive
Seagate 80Gb with 8Mb Cache ATA Hard Drive
Sony 1.44 Mb Floppy Drive
Creative Sound Blaster Audigy ZS
Logitech Z-640 5.1 Speakers
LG DVD Rom
Cooler Master Extreme Power 430 Power Supply[/SIZE]

---

### Post by Blood Red Sandman on 2006-10-16
BIOS was right. 
Plug and Play Bios was turned off. So I now got my mouse and keyboard working :KS 


Now lets see how the rest of this goes like. :-D

---

### Post by aktiwers on 2006-10-16
Good Luck - and Welcome to the dark side :)

---

### Post by buckethead27 on 2006-10-16
Good luck! Let us know.

---

### Post by Blood Red Sandman on 2006-10-16
The Dark Side is when I install Linux on my main rig.

However your timing is amazing as I am about to hit the [Restart Now] button

---

### Post by Fryingpan on 2006-10-16
I am attempting an install of Ubuntu but I think my lack of RAM is causing it to hang and stall. Downloading the "alternate" .iso right now. Any traps to look out for when installing that?

(I am trying it out on an old desktop - not my main machine. Not yet!)

---

### Post by Blood Red Sandman on 2006-10-16
Okay, every thing looks nice. However how do i get Firefox to connect to the internet. 

My connection is Optusnet ADSL connected via a Netgear DG834G v2 router.
I am using the onboard network card on my MSI motherboard.

Also, my second hard drive is NTFS. And it as some linux apps that I would like to install. How can I got about mounting my other hard drive?

I am also not getting any sound from my Creative Sound Blaster Audigy ZS sound card.

---

### Post by _duncan_ on 2006-10-16
Mounting NTFS and FAT32 partitions are covered in the System Documentation. While running Ubuntu, try this:

1. System > Help > System Documention.
2. Choose 'Ubuntu Dekstop Guide'.
3. Click on the arrow beside 'Configuring Your System' to expand the menu.
4. Choose 'Partitions and Booting'.
5. Read sections 4.2.2 and 4.2.3.

It may be worthwhile to browse through the whole documentation when you have time. Enjoy!

P.S. Sorry, I can't help with your DSL net connection problems. Still on dial-up. :)

---

### Post by steve.horsley on 2006-10-16
> **Blood Red Sandman said:**
> Okay, every thing looks nice. However how do i get Firefox to connect to the internet. 

My connection is Optusnet ADSL connected via a Netgear DG834G v2 router.
I am using the onboard network card on my MSI motherboard.

Are you using Ethernet and DHCP? If so, then it should just work. If using something else. I think we need to know what. For starters, can you post what happens when you do the command **ipconfig /all** in Windows?  Also, from Linux, the output of the commands **ifconfig**. 
> 
Also, my second hard drive is NTFS. And it as some linux apps that I would like to install. How can I got about mounting my other hard drive?

See this guide...
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)
> 
I am also not getting any sound from my Creative Sound Blaster Audigy ZS sound card.
Make sure it hasn't selected your on-board sound as the default. System->Preferences->Sound, default sound card.

---

### Post by Blood Red Sandman on 2006-10-16
_duncan_
  Will look into that after I knock off from work.

> **steve.horsley said:**
> Are you using Ethernet and DHCP? If so, then it should just work. If using something else. I think we need to know what. For starters, can you post what happens when you do the command **ipconfig /all** in Windows?  Also, from Linux, the output of the commands **ifconfig**. 

This is the IPconfig from my windows PC :-

[SIZE="1"]Windows IP Configuration
        Host Name . . . . . . . . . . . . : pzychobitch
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Broadcast
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:
        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet NIC
        Physical Address. . . . . . . . . : 00-20-ED-6E-AC-B3
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.2
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DHCP Server . . . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 192.168.0.1
        Lease Obtained. . . . . . . . . . : Tuesday, 17 October 2006 7:40:11 AM
        Lease Expires . . . . . . . . . . : Wednesday, 18 October 2006 7:40:11 AM[/SIZE]

Will look into the rest after work and I am in the process of getting ready for work.

---

### Post by Blood Red Sandman on 2006-10-16
Now that I am at work, I relised that I can get my hands on my sister's BF's old motherboard which is a Gigabyte GA-7N400 Pro 2 ver 1. He recently got a new AMD64x2 Rig.

* Firstly, this motherboard is better and newer than my MSI
* Still as has 3 months more warranty 
* And finally, all the ram slots work on it. My MSI motherboard had a little problem one night which involved smoke come out of one of the DIMMS slots. :-# 

Is ubuntu an operating system where I can swap and change motherboard with little side effects. Or it is going to be best if I reinstall the OS again?

---

### Post by Blood Red Sandman on 2006-10-17
OH YEAH! I love this OS! 

For the first time 8 years, I have been able to change my Motherboard and still have a working OS on it. 

Not sure what was the go last night with getting onto the internet. However tonight I can get on. 

I have also managed to get my Logitech Cordless Keyboard and Mouse working too.

---

### Post by Blood Red Sandman on 2006-10-17
> **steve.horsley said:**
> See this guide...
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

I go into System --> Admistration --> Disk.
I can see the other drive, however under Storage Properties, it's telling me that the drive is unknown, and that there aren't know partitions in the disk.

Strange. As I don't remember formating this one. As last night, it ubuntu was at least detecting the drive.


> **steve.horsley said:**
> Make sure it hasn't selected your on-board sound as the default. System->Preferences->Sound, default sound card. It is. However still no sound.

[EDIT] Found the problem as it was pointing all the sound toward the digital out put.[/EDIT]

---

### Post by steve.horsley on 2006-10-17
> **Blood Red Sandman said:**
> OH YEAH! I love this OS! 


I'm glad you're off to a good start. Enjoy.

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) should prove helpful.

---

