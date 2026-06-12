---
title: "help me please"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by sparky1664 on 2008-02-18
hello everybody.  I just bought a referb pc, it's a ubuntu machine.  I successfully installed windows xp.  but after a couple of hours of usage it crashed and won't reboot.  the harddrive light stays on and no OS boots, can't get recovery console to work.  any help would be greatly appreciated, really.  p.s. the machine is an everex.

---

### Post by jan quark on 2008-02-18
if you have installed windows after ubuntu the linux grub loader was overwritten by windows and has to be restored

read this

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

---

### Post by Nxion on 2008-02-18
XP crashed or Ubuntu crashed ?

---

### Post by randy78 on 2008-02-18
What was wrong with Ubuntu?

If you haven't accumulated any really important data in XP, you can always just download the appropriate version of Ubuntu for your machine (We really need the details of the processor type, memory, etc... before we can make a recommendation)

You know, once you get Ubuntu running, you can run XP as a Virtual Machine (An Operating System inside of an Operating System!)

Let us know a bit more about your computer and we'll try to help ;)

---

### Post by sparky1664 on 2008-02-18
don't have access to the machine at the moment, nothing loads, i mean nothing.  ubuntu recovery dvd won't load.  what i remember is it only has 512 of ram and 1.3 g.  Dvd won't load with the windows cd.  nothing loads can't even get into the boot loader or the setup screen.  xp worked for fine until it came to the sp2, than nothing, tried re-installing ubuntu.

Technical Detail
Motherboard Model: VIA PC2500 (version: 1.0c)
Platform: Micro-ATX, 225mm x 190mm
Processor: VIA C7-D 1.5GHz
Memory: (2) DDRII slots supporting up to 2GB
CPU Type: VIA PC2500
North Bridge: VIA CN700
South Bridge: VIA VT8237R Plus
Graphics: UniChrome Pro LAN
Chipset: VIA VT6103 PHY
Audio Chipset: Realtek ALC655
Super I/O: ITE 8716F
BIOS Vendor: Award Memory (4MB Flash)
EPROM: Yes

---

### Post by randy78 on 2008-02-18
Try downloading DBAN (Cd and DVD Media) and burning it to disk, then insert the disk in the computer and restart...[http://dban.sourceforge.net/]("http://dban.sourceforge.net/")

Once it starts up, type:
quick

Then, just let it do its thing (will take a while and will give you a black screen with some text when it's finished)

Only do this if you do NOT have ANY important data on the drive, as it will send it into oblivion, and can never be recovered...
But...
Since it sounds like a fresh install of Ubuntu and XP, you should be OK doing it.

This will wipe everything off of your hard-drive and leave you with a clean slate to try once again.

512mb of RAM is definitely enough, as that was what I was running up until my memory upgrade last week.

---

### Post by sparky1664 on 2008-02-18
cheers, i'll try it.  will dban load if i'm having boot issues.  harddrive light stays on and nothing loads.

---

### Post by randy78 on 2008-02-18
> **sparky1664 said:**
> cheers, i'll try it.  will dban load if i'm having boot issues

It should...

If not, we might have to look at your BIOS settings and/or do a hard drive test to see if there is something else going on.

Let us know as soon as you find out!

---

### Post by sparky1664 on 2008-02-18
wilco.  hope i didn't cook the mobo.  it's a referb but it's only about three days out of the box.

---

### Post by randy78 on 2008-02-18
Not likely, but when it comes to electronics and especially computers, ANYTHING is possible ;)

Try wiping it and let's go from there.

---

### Post by sparky1664 on 2008-02-18
nothing happened, it acted the same way.  nothing booted, no setup no nothing.  the light on the dvd drive blinked like it should, but nothing and the harddrive light still stays on.

---

### Post by randy78 on 2008-02-18
Okay...

Enter your BIOS settings by pressing either ESC or F8 or F12 right when you turn the computer on (make sure to take out the CD/DVD that was in the CD drive)

You are going to be looking for the Boot Order...
You will want to make sure that it is set (for now) to boot from the CD/DVD drive first, then the hard drive second.

After that, try again and let us know.

Where did you get this machine from?

---

### Post by sparky1664 on 2008-02-18
wilco, wait one.  cheers

---

### Post by sparky1664 on 2008-02-18
nope no luck.  did i mention i'm not even getting a signal to my monitor.

---

### Post by sparky1664 on 2008-02-18
purchased from a retailer.  once it's out of the box the warranty is void.  not to mention changing the operating system.

---

### Post by randy78 on 2008-02-18
Okay...

Did you accidentally unplug anything?

Check all of your connections and cables for kinks, breaks and loose connections.

That's kind of a raw deal to get and I'm sorry to hear about your bad luck...

At this point, unfortunately, it DOES sound like a motherboard issue, especially since you aren't getting a signal to your monitor now.

You might want to make a new post in the Hardware section, detailing what we have tried and what the problems are.

They are a very knowledgeable bunch and will probably be able to pinpoint your EXACT issue ;)

Sorry I couldn't be of more assistance...

Good luck and if I were you, I'd at least try to contact the store and see if anything can be worked out...

Randy :popcorn:

---

### Post by sparky1664 on 2008-02-18
thx i appreciate the help.  i think my problem is i know just enough about puters to screw them up:lolflag:

---

### Post by e_james on 2008-02-18
It is an unfortunate fact of computer life that you put everything together and it works, and then, five minutes later it stops working. Many computer companies will run machines for hours or days before selling them, in order to minimise this problem. Most likely it's just one component and a suitable replacement will fix it.

---

