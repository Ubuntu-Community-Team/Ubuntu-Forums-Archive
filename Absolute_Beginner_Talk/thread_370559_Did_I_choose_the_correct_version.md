---
title: "Did I choose the correct version?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by majkball on 2007-02-25
I just installed Ubuntu 6.10 on a P3@600Mhz with 394MB Ram... well and everything seems to work. I even managed to share a printer through it to my wireless WinXP Laptop. But the problem is that it seems to be going slow, and the CPU is at 100% load when I am sitting at the machine.

Should I reconsider installing a lower version of Ubuntu? Would that speed up my system?

I will use my Ubuntu machine as a print-server, internet-gateway and eventually simulate database/web-server in my LAN.

BTW... does anyone know how to make use of a 200GB harddrive in an old system like this (IDE33), cause the bios tells me the slave disk is on 136GB... it would be fun to make use of the whole capacity.

---

### Post by bmathis on 2007-02-25
I would try Xubuntu, it has a lighter desktop and requires less system resources. Another option would be to install fluxbox, but its not as easy as Xubuntu.

For the hard drive, a OS GB is different than a manufacturer GB. 200GB might not be 200GB when you get it home.

---

### Post by kairu0 on 2007-02-25
I would definitely consider a lighter version of Ubuntu, such as fluxbuntu or maybe even xubuntu. Your CPU and memory specs are low for Gnome these days.

As for the hard disk, you've probably hit the BIOS limitation. If you have already flashed the BIOS to the most recent version, then you probably won't get around it.

---

### Post by rusty4r on 2007-02-25
Someone with more experience might say different but I don't think that what version you have is going to matter. Maybe your software updater is running look at system monitor and see what is running so feverishly.

What brand of hard drive is it? My seagate 160Gb came with a disk to let the bios see the whole disk.

well I see you already have better answers I type to slow

---

### Post by majkball on 2007-02-25
Thanks for the quick answer.

I checked at the Ubuntu distribution-page and must agree that Xubuntu seems to be a better choice for me. Fluxbuntu seemed to be lightweight aswell, but maybe I should choose Xubuntu anyway, since my linux knowledge is limited... or nearly null. :D

Is Xubuntu also well supported... will I be allowed to continue posting my questions regarding Xubuntu here or should i rather look for something like xubuntuforums.org

I suppose a BitTorrent client will work on an Xubuntu installation aswell?

And which version should I choose of Xubuntu? 6.06 or 6.10... or any other?

---

### Post by louieb on 2007-02-25
I have Dapper 6.06.1 running on a P2-400 348meg ram. Sure it not as fast as the P4 but it fast enough for me. xUbuntu   may be a bit faster on mine but I just like the Gnome desktop.

The P2 has a 30 gig hard drive limit in BIOS. I could get a BIOS flash to fix it. But I am to lazy to get on the internet and get the flash and make the disk. I am also to cheep to spend the 30 bucks to buy the upgrade. The PC not worth much if any more than that. You just have to find the mother board type and BIOS type. Just Google BIOS upgrade there are some programs (windows) that can get the BIOS information for you.

BTW good going on getting Ubuntu to share its printer with XP.  I found it was easier to let and old laptop running XP to be the print server on my home network.

---

### Post by RedSquirrel on 2007-02-25
> **majkball said:**
> I just installed Ubuntu 6.10 on a P3@600Mhz with 394MB Ram... well and everything seems to work. I even managed to share a printer through it to my wireless WinXP Laptop. But the problem is that it seems to be going slow, and the CPU is at 100% load when I am sitting at the machine.


What are you using to determine the CPU load? It shouldn't be 100% all the time, that's for sure.


>  Should I reconsider installing a lower version of Ubuntu? Would that speed up my system?
Xubuntu would definitely be better for your specs. I have Xubuntu installed on an AMD Duron 600 MHz with 320 MB RAM (specs slightly less than yours) and it runs smooth as silk. 

Running Fluxbox is another option. You could install it on top of what you already have or you could install it on top of Xubuntu. You could also try Fluxbuntu, or use a command line install to get only the packages you want/need.

EDIT: at the moment, I have Fluxbox installed on top of Xubuntu, and after I login I'm only using 58 MB of RAM. Not bad, eh? I could make it lower, but that's good enough for now.

---

### Post by PurplePenguin on 2007-02-25
That machine should be fast enough to not have 100% CPU load, especially if it's just sitting there.  What kinds of applications are you running when you see this happen?

There was / is a bug in Nautilus that caused CPU load to hit 100%.  Maybe you should look into exactly where the problem is.  You can add a gnome System Monitor applet to your task bar which shows the CPU load, if you notice it's at 100, click it and you'll get to see exactly which programs are causing the problems.

Re: your hard drive, it's true that if it says 200GB on the box, that's not what you'll get.  But you won't get a mere 130GB, you should get some number that's quite a bit higher than that.  Sounds like it's more a BIOS problem relating to your relatively old motherboard.

---

### Post by hilltop_yodeler on 2007-03-31
> **majkball said:**
> 

Is Xubuntu also well supported... will I be allowed to continue posting my questions regarding Xubuntu here or should i rather look for something like xubuntuforums.org

Xubuntu is WELL supported.  You can ask questions here on the Ubuntu Forum.

> **majkball said:**
> And which version should I choose of Xubuntu? 6.06 or 6.10... or any other?
One of my machines is pretty similar in specs to yours and I am currently running Xubuntu 6.10 "Edgy" on it, and it runs great!  I tried running the latest Feisty release as a live-cd and it would not configure X properly, so the graphical interface was useless.  Perhaps if I knew more about configuring X, it would not be an issue.  Anyway, 6.10 runs great.

---

