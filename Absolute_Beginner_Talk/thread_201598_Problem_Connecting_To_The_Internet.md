---
title: "Problem Connecting To The Internet"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by infin?ty on 2006-06-22
I have an ADSL modem and the network adapter is
RTL8139D PCI Fast Ethernet Adapter,(Realtek)

ubntu is not recognizing this (i tried using pppoeconf), it says try modconf but bash says modconf command doesnt exist.(i tried sudo modconf also even tht didnt exist)

I got the drivers to this card on a floppy, and there were drivers fro linux also(a C src file and a makefile), but wen i say make there are loads of errors in the C file itself and i am not able to correct them. So wat shld i do. Currently i am accessing internet thru windows and then to make any changes i have to go back to ubuntu its proving quite irritating.

In case any one is frm india, BSNL is my ISP, plz help me connect to the internet.

I tried ubuntu wiki also, but no help.

---

### Post by nalmeth on 2006-06-22
Have you seen this link?
[http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

It's rare that direct cable connection doesn't work, or that realtek ethernet doesn't work in general.

As a result, a lot of people don't know how to troubleshoot a direct connection
**looking around for someone else to draw attention to.. :-) )**

So I just link to there when it comes up.

Good luck with your connection

---

### Post by infin?ty on 2006-06-22
No, friend its not working, it just returns 'no such device found'. Do u have any idea asto why the modconf thing is not working.

---

### Post by infin?ty on 2006-06-22
comeon ppl please reply, or atleast tell me some links, please

---

### Post by neoflight on 2006-06-22
[QUOTE=infin?ty]comeon ppl please reply, or atleast tell me some links, please[/QUOTE]

is that a dial-up or a cable connection? 

whats your /etc/network/interfaces file looks like?
whats the result of ifconfig?

---

### Post by MaximB on 2006-06-22
sorry men...I've had the same problem but the "pppoeconf" worked fine to me
but then I had other problem - very rare one that even my ISP could not help me (in fact I think I helped them more :) )
but some good guy in the forum finally managed to help me out (after lots of attempts from other users).

but if you could finally connect and have another problem - maybe we/or I could help you out.

---

### Post by infin?ty on 2006-06-23
I tried the following commands, see if u can figure out wat problem i am having

**modprobe 8139too**

WARNING: Error installing mii (/lib/modules/2.6.12-9-386/kernel/drivers/net/mii.ko):operation not permitted

WARNING: Error installing 8139too (/lib/modules/2.6.12-9-386/kernel/drivers/net/8139too.ko):operation not permitted

**lspci**

0000:01:0a.0 Ehternet controller: unknown device 1904:8139 (rev 01)

**dmesg | grep eth**
no o/p

** lsmod | grep 8139**
no o/p

** dmesg | tail **

lists some bluetooth stuff, nothing conected to ethernet

** sudo insmod /lib/modules/2.6.12-9-386/kernel/drivers/net/8139too.ko** 

error inserting (the above path): -1 unknown symbol in module

I hope this will help to figure out wat problem i am having.

---

### Post by drtvasudevan on 2006-06-25
[QUOTE=infin?ty]I have an ADSL modem and the network adapter is
RTL8139D PCI Fast Ethernet Adapter,(Realtek)
In case any one is frm india, BSNL is my ISP, plz help me connect to the internet.

I tried ubuntu wiki also, but no help.[/QUOTE]
i am from india and on dataone
my network adapter is the same.
try this. it works for me.

 enter about:config in the Firefox address field, then ipv6 in the Firefox filter field. Then double click on the one & only line that is displayed to change the boolean value to True.
close and restart firefox.
That's it for IPv6 - then I can browse the web, & not before!

tv

---

### Post by infin?ty on 2006-06-25
> [I]enter about:config in the Firefox address field, then ipv6 in the Firefox filter field. Then double click on the one & only line that is displayed to change the boolean value to True.
close and restart firefox.
That's it for IPv6 - then I can browse the web, & not before![/I]


The problem with me frnd is tht my ethernet card is not getting detected by ubuntu 5.01, i am not able to connect only. I tried ur method but it dint workout.

---

### Post by drtvasudevan on 2006-06-25
strange.
i have the same network adaptor and there are no problems.
it works with windows i suppose!

sorry i cant help you there.

tv

---

### Post by drtvasudevan on 2006-06-26
see this if you have not already!
[http://www.fedoraforum.org/forum/showthread.php?t=87760&page=3&pp=15](http://www.fedoraforum.org/forum/showthread.php?t=87760&page=3&pp=15)
see the last post on that page and read through from begining.

also [http://forums.pcquest.com/forum/viewtopic.php?t=4474&sid=80ef024d038b37914942418afc224832](http://forums.pcquest.com/forum/viewtopic.php?t=4474&sid=80ef024d038b37914942418afc224832)
this d varient seems to have the problem.
mine is not.

tv

---

### Post by Apple 101 on 2006-06-26
1. Open another OS and find out the IRQ settings of your network card.
2. Reboot in Ubuntu and use this information when using the modprobe command.  You may also need to enter the information in a specific format in the modules.conf file, but I cannot remember how.

---

