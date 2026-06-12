---
title: "Can't create ethernet interface (?!)"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Kuma_Pageworks on 2006-09-06
I've heard about Ubuntu, and I went to check it out when I inherited my wife's laptop (IBM Thinkpad A20e) when we upgraded her this weekend. I downloaded 6.06 and installed it. I really, really like it. It's shiny and groovy.

However.

Networking has been a nightmare. And since much of getting other software packages depends on networking, my love of Ubuntu (and Linux) is coming to a standstill. I'm hoping that someone can point me in a helpful direction and break this total stonewall that I've hit.

At first, I was trying to set up the wireless card. I'm not totally naive, so I figured that this wasn't going to be a piece of cake. After re-installing (twice), and going through all of the online troubleshooting docs (some of which were inaccurate in themselves), I wasn't getting anywhere. Linux saw the card, the card saw my wifi at home, I had the WEP key ... but I couldn't get the card to pick up an IP address to save my life. I think I need to install ndiswrapper to make my card work correctly - but without a network connection, that's not so easy. The only other directions I saw had things like recompiling the kernel in it. Screw that for now - I've only been at this two days.

Ok, so take a step back. I decided that I was better off just screwing the wireless and getting the ethernet up and running. Plug directly into my wireless router (which has an ethernet port), download the software I wanted and chill for a couple of days while I figure out what the hell I need to do to get the wireless working.

So I get out the cable and plug in.

Nothing. Not only is there nothing really going on with the ethernet (minimal activity lights on both ends), but I went into the network properties and there's no interface for the ethernet port. At all. All I have is an interface for the modem. 

So I do a little research and I find that I can add an interface. The only thing is ... in the control panel for the networking interfaces, there's NO little button to 'add'. All of the online docs show a screenshot with it there. But I have no button. No way to fix up the ethernet port. I'm dead in the water.

I did some commands, and while Ubuntu recognizes the ethernet port, when I do lshw it says 'available to root only'.  It's a built-in Intel Ethernet Pro 100 port, if that helps.

Where do I go next? ](*,)

---

### Post by amohanty on 2006-09-06
can you post the output of 
**ifconfig**

AM

---

### Post by Kuma_Pageworks on 2006-09-06
ifconfig comes up with 'lo' and 'sit0' - no entry for eth0.

Actually, I just rebooted and now there's just the entry for lo.

lsmod | grep e100 comes up with two entries: e100 and mii 5888 1 e100

---

### Post by bodhi.zazen on 2006-09-06
> **Kuma_Pageworks said:**
> ifconfig comes up with 'lo' and 'sit0' - no entry for eth0.

In a terminal:
```
sudo nano /etc/network/interfaces
```
Add or edit your eth0 line to look like this:
```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```

Exit Type Ctrl-X, type "Y' to save edit.

Now:
```
sudo ifup eth0
```

viola', no?

---

### Post by amo-ej1 on 2006-09-06
To verify that the interface got detected properly you can also do a 
```

dmesg | grep eth

```
That should show the device driver being loaded (and detecting the nics). And 
```

ifconfig eth0

```
should also show the interface (with a down status). ifconfig lists only interfaces that have the UP flag set by default.

---

### Post by Kuma_Pageworks on 2006-09-06
No - and there's something a bit more sinister.

I'm getting a message during boot-up that something's up with the 'eeprom', then getting LAN adapter boot messages on startup.  Going into BIOS, I see that the MAC address of the Internal LAN is 'Not Applicable'.

I think maybe the EEPROM got scragged.

Um.  Uh oh.

---

### Post by Kuma_Pageworks on 2006-09-06
Great - now I just have to figure out a way to get the boot floppy to become a boot CD to update the firmware.

---

### Post by amo-ej1 on 2006-09-06
care to paste the message ?

---

### Post by Kuma_Pageworks on 2006-09-06
"PXE-E05: The LAN adapter's configuration is corrupted or has not been initialized. The Boot Agent cannot continue."

There's also no MAC Address listed in the BIOS for the LAN adapter.  I'm pretty sure the card is hosed.  I'm trying to create a boot CD with the firmware utility on it ... not much success there, either.  But it's an improvement.

---

### Post by bodhi.zazen on 2006-09-06
OMG, I have never had a problem of this magnitude with editing /etc/network/interfaces as I advised.

I am so sorry.

Suggest you boot to the live CD, mount, and edit /etc/network/interfaces.

Re-boot and perhaps someone else can help you.

---

### Post by amohanty on 2006-09-06
Bodhi, I am quite certain that editing /etc/network/interfaces did not cause the problem :)

> Great - now I just have to figure out a way to get the boot floppy to become a boot CD to update the firmware.

Assuming you have the firmware ona CD

Hit [www.bootdisk.de](www.bootdisk.de)
Download a Win98 SE boot disk
Boot with it enabling CD
cd to the CD drive
Run firmware

HTH
AM

---

### Post by bodhi.zazen on 2006-09-06
Thanks amohanty. I can't see it either, but I feel bad. Worse because I do not know how to help.

---

### Post by Haim on 2006-09-07
It may be the problem we are having over at this thread  (not that theres much on it!)

[http://www.ubuntuforums.org/showthread.php?t=251217&highlight=eeprom](http://www.ubuntuforums.org/showthread.php?t=251217&highlight=eeprom)

I've also got an intel mini-pci card.  Says the eeprom is corrupted so won't load it.  Works when booting into windows, suggestion is that windows doesn't check the checksum with the eeprom.  Linux kernal does.  There is a patch around to ignore but suggestion is one should really fix it, and its nots intel but the manufactorer or seller or someone who has stuffed it.

So if you have any clues on rewriting the eeprom I'd love to hear them, supposedly ethtools can do it and maybe the other (older) kernal driver (name escapes me, not e100), also theres something we've found from intel but not sure it'll sort my hardware.

Enough blab.

---

