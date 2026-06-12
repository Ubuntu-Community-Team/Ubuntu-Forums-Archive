---
title: "Wireless woes..."
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Aine Again on 2007-06-29
Afternoon, all.

I just replaced my Windows XP with Ubuntu 7.04. I am having trouble connecting to my wireless network. I know I need to tell you all the type of wireless card I am using, but I do not know it. How do I find that out? By accessing the BIOS?

Also: I am accessing the 'net with a wire, in case that helps.

---

### Post by Third Thoughts on 2007-06-29
The way to figure out what wireless card you've got, (and to figure out what hardware you've got in general) is open up the terminal and then type in the command lspci. Look for something about "Ethernet controller." You'll probably see two lines that have that phrase. One will be for your wired card the other for your wireless. Just go ahead and post them both. 

Just for your information lspci is shorthand for "list pci devices," so it lists all of the devices on your computer besides the core stuff like the motherboard, the cpu etc.

~Andrew S.

---

### Post by ugm6hr on 2007-06-29
In Ubuntu - open Terminal and type the following - then paste results here:
```
lspci
ifconfig
iwconfig
```

(Assuming you have a PCI / PCMCIA / internal wifi card)

---

### Post by tarek on 2007-06-29
IF you have bcm43xx follow this tutorial, it worked for me: [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")

---

### Post by Aine Again on 2007-06-29
Andrew,

Here it is.

> 
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)


---

### Post by ugm6hr on 2007-06-29
> **tarek said:**
> IF you have bcm43xx follow this tutorial, it worked for me: [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")

Are you psychic?

---

### Post by tarek on 2007-06-29
> **ugm6hr said:**
> Are you psychic?

lol

---

### Post by Third Thoughts on 2007-06-29
Alright Aine, the broadcom one is your wireless card, refer to the link that tarek posted above.

---

