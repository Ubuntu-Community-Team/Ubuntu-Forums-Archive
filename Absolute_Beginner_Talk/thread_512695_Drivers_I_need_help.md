---
title: "Drivers??? I need help"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Antikythera on 2007-07-29
I just built a computer and I put Feisty Fawn (Ubuntu 7.04) on it, my problem is that I can't find Drivers for it any where. Part of my problem might be that I don't really have a clue about what I should be looking for. If you need the specs for the comp let me know and I'll post them. Thanks!!!

---

### Post by Jimmyfj on 2007-07-29
Specs for your graphics card would be a good start

---

### Post by mikewhatever on 2007-07-29
A lot of drivers are pre-loaded in Ubuntu and get installed during its installation. Does something not work on your newly installed Feisty? From the fact that you do not know what to look for, it seems you do not need additional drivers.

---

### Post by Antikythera on 2007-07-29
> **Jimmyfj said:**
> Specs for your graphics card would be a good start
 It's a 3Dfx 5500 PCI 64MB SDRAM Voodoo5 32 BIT Color. 


> **mikewhatever said:**
> A lot of drivers are pre-loaded in Ubuntu and get installed during its installation. Does something not work on your newly installed Feisty? From the fact that you do not know what to look for, it seems you do not need additional drivers.

I can not get the computer to recognize a wired internet connection, it asks for information about a modem but i don't use a modem. I also can't install the cd that came with the mother board. So far those are the biggest problems that I have come across.

---

### Post by Jimmyfj on 2007-07-29
This is what I've been able to find so far - I'll see if there more:

[http://www.linuxlinks.com/Reviews/Hardware/](http://www.linuxlinks.com/Reviews/Hardware/)

---

### Post by Antikythera on 2007-07-29
thanks for the help

---

### Post by jimbob on 2007-07-29
I don't think you want to install the CD that came with the M/B.  It's probably for Microsoft only.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by ugm6hr on 2007-07-30
> **Antikythera said:**
> I just built a computer and I put Feisty Fawn (Ubuntu 7.04) on it, my problem is that I can't find Drivers for it any where. Part of my problem might be that I don't really have a clue about what I should be looking for. If you need the specs for the comp let me know and I'll post them. Thanks!!!

Errrmmm... If you've managed to put Fiesty on already - the drivers have already been recognised.  Some hardware does have "Restricted Drivers" - but most works with all functions without any additional drivers.  I wouldn't bother with the mobo CD - is there something on the mobo that doesn't work?

I see your other post mentions that your ethernet doesn't seem to work.  As default - you need to have the ethernet plugged in at boot-up.  And it shouldn't need any settings to be changed at all.

This will confirm the hardware recognised - the ethernet will be Ethernet / Network controller.
```
lspci -nn
```

This will tell you what your IP is, if it's connected:
```
ifconfig
```

Another idea - perhaps try Wicd (see my signature) - it allows ethernet roaming / static IP and DHCP - which might solve the problem.

---

