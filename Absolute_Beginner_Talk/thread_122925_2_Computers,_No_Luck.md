---
title: "2 Computers, No Luck"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Invisible Wombat on 2006-01-28
I've tried the *live CD* on two different computers. I tried to install (dual-boot) using the  *install CD* on two different computers. both computers *Win XP Home, SP2* using *shipped CD Roms* I received in the mail yesterday. In each case I get to the point where *_Starting hotplug subsystem_* comes up and everything basically stops. Just hangs there. I tried unplugging all USB connections, still no go. Ideas??

---

### Post by Rackerz on 2006-01-28
Are you trying the same CD eachtime? If so try a different one. If not how many CD's did you order? Also are the machines identical?

Darren

---

### Post by Invisible Wombat on 2006-01-28
@ Rackerz

I recieved 5 CD roms each of Install and Live. Tried all on both computers. The only difference between the computers is one has a 160 gig HD and the other a 40 gig HD, otherwise, they're both Gateway Windows XP Home, SP2. They are networked. The Main computer (the one I want to dual-boot) has the following specs:

-Gateway DX200 S, Pentium 4, 1.93GHz, 160 Gig HD
-Windows XP Home, SP2
-Comcast High Speed Internet (Peachtree City, GA)
-NetGear CG814WG v2 modem/router
-Linksys Wireless G, 2.4 GHz 802.11g usb network adapter (on 2nd Computer)

---

### Post by Invisible Wombat on 2006-01-28
Anyone?

---

### Post by Invisible Wombat on 2006-01-28
Tried again with the *Live CD*. When it got to *Starting hotplug subsystem*, I pressed ctrl>c, still no luck.

---

### Post by Invisible Wombat on 2006-01-28
Last try to the forum before I give up alltogether. I really want to get this going,  but I'm totally stuck. Seeing all these success posts is getting me jealous. Please, Help. :(

---

### Post by BenTyreman on 2006-01-28
Have you tried booting with the option
```
ubuntu nodma
```
It got knoppix working for a friend with a Packard Bell with a similar problem. Alternatives are trying to disable acpi and apm. Pressing F3 or F4 should give you a list of things to try.

---

### Post by Invisible Wombat on 2006-01-28
[QUOTE=BenTyreman]Have you tried booting with the option
```
ubuntu nodma
```
It got knoppix working for a friend with a Packard Bell with a similar problem. Alternatives are trying to disable acpi and apm. Pressing F3 or F4 should give you a list of things to try.[/QUOTE]

I'll give it a shot. 

I did a google/yahoo/alta vista search "Ubuntu starting hotplug subsystem" and had no idea the extent of this. Hundreds upon hundreds of the same problem. Nobody seemd to have any real answers. I did find this though...
> 
"Installing: Guided installation takes care of anything for you. However I did have a problem with it stalling when loading the "hotplug subsystem"
I fixed this by entering GRUB at start up and editing the menu.lst file by adding irqpoll to this line
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/sda3 ro quiet splash *irqpoll* "

---

### Post by Invisible Wombat on 2006-01-29
I tried the Live CD on a friends' computer, no problem. He's not networked and is on DSL. I'm networked (two computers) and on Cable. Is this the problem?

---

### Post by kewl1uk on 2006-01-29
Perhaps if you try disconnecting the computer from the network and then trying the Live CD again you'll know whether it's possibly your hardware or possibly the network that's the problem?

---

### Post by phen on 2006-01-29
no, that shouldn't be a problem. do you want to try out the "irqpoll" thing? i never changed grub-setup on startup, but it should work by pressing esc ( or f5 i think) when grub starts. 

this problem might be a complex one, so you could try to disconnect you network, all usb-devices etc and see what happens! post any changes here!

hope you find a solution.. having such problems at such an early stage is sometimes a little disencouraging..

---

### Post by mgmiller on 2006-01-29
Another thing to try is in your BIOS, see if there is an entry regarding "legacy usb" support.  If it is there, try disabling it.  I now do this as a matter of course on every new machine I build for windows xp or linux and it seems to prevent lots of weird problems.

---

### Post by aysiu on 2006-01-29
I'm amazed nobody's mentioned the possibility that [the ShipIt CDs could be corrupted or otherwise not usable](http://www.ubuntuforums.org/showthread.php?t=113925). I would imagine they burn those ShipIt CDs at fast speeds in order to accommodate demand.

I would recommend downloading your own .ISO, doing a checksum to ensure disk image integrity, and then burning it at 4x or 8x. If you don't have a broadband connection/ CD burner... find a friend/relative who does.

---

### Post by Cesium on 2006-01-29
[QUOTE=aysiu]I would recommend downloading your own .ISO, doing a checksum to ensure disk image integrity, and then burning it at 4x or 8x. If you don't have a broadband connection/ CD burner... find a friend/relative who does.[/QUOTE]

I had problems installing Ubuntu when I burned the Ubuntu ISO a speed higher than 4x.  If you can download and burn the ISO somewhere at 4x, I would give that a shot.

---

### Post by aysiu on 2006-01-29
And don't forget to [do a checksum on the ISO](http://www.linuxiso.org/viewdoc.php/verifyiso.html) before burning it.

---

