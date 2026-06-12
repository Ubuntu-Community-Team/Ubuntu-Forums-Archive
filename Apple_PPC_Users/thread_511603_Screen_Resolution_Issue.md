---
title: "Screen Resolution Issue"
date: 2007-07-28
forum: Apple PPC Users
---

### Post by manzell on 2007-07-28
i've just installed Ubuntu 6.10 onto my Powerbook G4

My first issue is that my graphics resolution is limited to 800x600

Secondly, I'd like to enable to VGA out on my laptop.

------

I am pretty much a noob, and got confused between the ATI binary drivers vs xorg.conf editing and whatnot. Can someone give me a good starting point?

In reality, I just want the VGA out to work, since I'll be outputting to my TV at 800x600 anyhow.

Thanks!

---

### Post by manzell on 2007-07-28
here's my xorg.conf

```
Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
Driver "ati"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
```

It sounds like the "open source drivers" are the ones I want for this particular card. Where do I get them? Thanks!

---

### Post by stmiller on 2007-07-28
Check out the PowerPC FAQs for info on PowerPC and graphics drivers and enabling VGA-out. Basically in a nut shell, the drivers are already there (in the kernel) so you do not have to go out and fetch any from the web. (There's not any out there to fetch!)

Is this a 12", 15" or 17" Powerbook? And what exact model? ( [www.apple-history.com](www.apple-history.com) ) We need this info to help.


If it's a 12" Powerbook G4 with Nvidia, there's no VGA out due to lack of drivers from Nvidia for PowerPC Linux. And you must adjust your xorg.conf to say

Driver  "nv"

in the device section.

---

### Post by Sanchoclaus on 2007-07-28
I have a relatively similar problem, the windows in my ubuntu 7.04 emac, seem stretched, and the scroll bar on the right is barely visible.
I tried changing the resolution but System/Preferences/Screen resolution, has it fixed on 1024x768, I would like to changeit to 800x600
Does anyone know a command line to do this?
Many thanks

---

### Post by Sanchoclaus on 2007-07-28
One more thing the on-screen image seems to be shrinking in from the left and right side of the monitor.
How can I adjust the width of the screen?

---

### Post by manzell on 2007-07-28
> **stmiller said:**
> Is this a 12", 15" or 17" Powerbook? And what exact model? ( [www.apple-history.com](www.apple-history.com) ) We need this info to help.

It's the 15" titanium version. ATI Radeon 9000 (mobility m6 ly)

The version of the laptop is here: [http://www.apple-history.com/body.php?page=gallery&model=pg4_giga&performa=off&sort=date&order=ASC](http://www.apple-history.com/body.php?page=gallery&model=pg4_giga&performa=off&sort=date&order=ASC)

In short, it's the 2001 Powerbook G4 "Gigabit Ethernet" version. Not a lot of horsepower.

I should clarify, as well - I'm trying to enable the SVIDEO out as well as get a resolution that matches the screen dimensions (1152x768)

Thanks - let me know if you need any more information. I'll be checking the FAQ you mentioned as well.

**// EDIT //**

I reconfigured the x-server. All seems well with regards to screen resolution (1152x768 is working perfectly).  I still want to enable the s-video out (thanks)

---

### Post by stmiller on 2007-07-29
Okay great. I've got a similar machine: Powerbook G4 titanium 15". The s-video out should be possible. I think I've  got an s-video cable around somewhere. I'll try some things with my xorg.conf and see what happens.

---

### Post by stmiller on 2007-07-29
Ah, well it seems the program that would take care of svideo out for ATI cards is called atitvout but only works in x86 Linux, not powerpc. I found a note on the debian powerpc list which said atitvout uses x86 BIOS calls to work, so it cannot work in powerpc.

[http://packages.ubuntu.com/feisty/misc/atitvout](http://packages.ubuntu.com/feisty/misc/atitvout)

:(

---

