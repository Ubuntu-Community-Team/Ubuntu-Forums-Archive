---
title: "Edubuntu installation problem"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by gentoo_zach on 2007-06-01
Hello all,

I'm trying to install Edubuntu 7.04 on an old computer that I want to donate to a school.  It's an old IBM P3 with 384MB of PC100 RAM.  I've tried using the Desktop and the Server installation CDs.  Neither of them work at all.  They boot to the main screen where you can choose your selection.  Once I choose "install Edubuntu as a workstation" it goes to a blank screen with a blinking cursor in the top-left and never does anything else.

I've tried installing Gentoo Linux and other flavours and they work just fine.  Is there something I'm missing?

Thanks preemptively,
Zach

---

### Post by Crafty Kisses on 2007-06-01
Could be your RAM.

---

### Post by gentoo_zach on 2007-06-01
What part of the RAM, the amount or speed?  Has anyone else installed Edubuntu on a similar computer?

---

### Post by gentoo_zach on 2007-06-01
I guess this post really should have been in the installation forum, so if a moderator could move it for me, that would be appreciated.

---

### Post by bobplano on 2007-06-01
it should be the amount, all the numbers on the ubuntu page are RAM amounts

---

### Post by gentoo_zach on 2007-06-01
I thought that Edubuntu only required 256MB of RAM, and I have 384MB.

---

### Post by Crafty Kisses on 2007-06-01
> **gentoo_zach said:**
> I thought that Edubuntu only required 256MB of RAM, and I have 384MB.

It can be a number of things. Can you boot into verbose mode? Basically when you put the installer disc in and it's at the installer screen press:
```
Ctrl+Alt+F2
```

---

### Post by gentoo_zach on 2007-06-01
Now when I get to the installation screen and I start the process, it shows the "Loading Linux Kernel" box, goes to the blank screen with a blinking cursor momentarily, and then I lose the VGA signal.  There has to be a hardware problem with this computer.  It's just odd that it doesn't do it when I load in the test copy of Windows that I have.

Thanks for your help.

---

### Post by gentoo_zach on 2007-06-03
Well, I don't know why I didn't think of this before, but I just tried booting it and removing the "quiet" attribute from the end so I could see what was going on.  It starts going through what appears to be the kernel referencing the system hardware and it stops at this line:

```

[   87.086213] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2

```

That's the last thing I see and the cursor just sits there and blinks after that.

The only thing I can think of that might cause that problem is that I have the computer hooked into my KVM and it has a USB mouse with a PS/2 adapter on it. :confused:

---

### Post by pappapump on 2007-06-03
It would really help to know which Video card you are using, as well as if you are using shadowing in bios with the card and what interface it uses, pci, agp etc.

---

### Post by gentoo_zach on 2007-06-03
There is no video card (as in PCI, PCI-e, or AGP).  It is an older IBM NetVista 6579 with nothing added in except a NIC.  Here are the specs for that machine:

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-50706](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-50706)

It's just using the integrated Intel 815E video adapter.

---

### Post by gentoo_zach on 2007-06-03
Well, after taking this system off of my KVM and hooking everything (keyboard, VGA, mouse) up separately to it, I get this stopping point:

```

[   85.820266] ata1: port is slow to respond, please be patient (Status 0xd0)

```

I would assume that Edubuntu references drives in a similar fashion to other distros, and that ata1 is HDD0 considering it is on the primary IDE channel in master position.  Therefore, I would conclude that it is either a bad HDD or bad IDE channel.

---

