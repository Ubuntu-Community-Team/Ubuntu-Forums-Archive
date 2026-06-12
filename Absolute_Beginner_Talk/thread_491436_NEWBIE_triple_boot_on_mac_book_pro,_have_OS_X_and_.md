---
title: "NEWBIE triple boot on mac book pro, have OS X and Windows Xp installed already"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by smirkus on 2007-07-03
Hey all, I have been doing research on this online, and have found a few great links, but before I screw up my fresh new 2007 MBP, I want to be sure that I get everything.

From these sites:
 [http://www.mactel-linux.org/wiki/Triple_Booting](http://www.mactel-linux.org/wiki/Triple_Booting)
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)
[http://refit.sourceforge.net/tripleboot/](http://refit.sourceforge.net/tripleboot/)

I have a feeling Kubuntu's installation is not different at all from Ubuntu's.

So, I am confused, because I think this guide and all the others I have come across assume you have a "temporary" version of windows installed that you can just scrap. I have a permanent NTFS partition version of windows I installed successfully with boot camp (And I can't make the partition smaller, because it is very small as it is). I thought it would be easy enough to make another partition with boot camp and then install the kubuntu OS CD to the new partition.... but it seems to actually do it properly requires much more that is over my head (boot camp can only handle 2 partitions supposedly).I have heard the suggestion of running Kubuntu with vmware or parallels, but those programs cost money :-(

Can anyone clarify for me if I can still install Kubuntu despite having Windows already on, that would be great. Or noob friendly info about creating another partition from OS X and being able to access all 3 OS's. Also, if anyone could provide/link to a more noob friendly MBP install guide, that would be amazing as well. Thanks for ANY help, as I really want to have this triple booted on my amazing laptop!

---

### Post by limbourg31 on 2007-07-03
are you a mac user then? if so i'm not sure about the partitioning scheme but its similar to PCs right? first how much hard disk space do you have? you might have to remove boot camp to have kubuntu on your hard drive... but if you want it through a virtual machine a free on is VirtualBox by InnoTek (not sure about the spelling :) GParted is a partioning editor which MIGHT work on a mac, its a LiveCD you can use to boot in and edit it.

---

### Post by annda on 2007-07-03
i wouldn't scrap boot camp just to try ubuntu. read more about it to make sure it can't handle more than 2 os's - it sounds ridiculous, but limitations are apple's second name (i'm a mac user too, so don't be too irritated). boot from the live cd to see if you really like linux.

my advice is google around for how to configure boot camp for another os. i can't help you with that because i have two separate machines, but many people here must have lin and osX on the same computer. install kubuntu WITHOUT grub and then configure boot camp accordingly.

---

