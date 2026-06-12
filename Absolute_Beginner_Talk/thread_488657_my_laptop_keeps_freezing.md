---
title: "my laptop keeps freezing"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by mikehipson on 2007-06-30
Hi, i installed ubuntu last week, and i have been running into all kinds of problems.  The latest one is that my laptop just freezes while I'm on the internet.  Even when I only have like one or two pages open.  Also, update manager was running both times that it froze.

Help?

Mike

---

### Post by overdrank on 2007-06-30
> **mikehipson said:**
> Hi, i installed ubuntu last week, and i have been running into all kinds of problems.  The latest one is that my laptop just freezes while I'm on the internet.  Even when I only have like one or two pages open.  Also, update manager was running both times that it froze.

Help?

Mike

HI how much ram does the system have an have you ran a memory test?

---

### Post by csinner on 2007-07-02
I'm experiencing the SAME problem. My laptop just randomly freezes. I don't know if update manager was running when this happened. My system has 2 GB of memory but I don't know how to run a memory test.

Tell me anything you need me to try.

Also, because I thought maybe it was just the Ubuntu distro, I tried DLing the OpenSuse internet installer, and that froze while downloading all the packages (~2.2 GB). The installer made it about an hour before freezing.

Any help at all would be MUCH appreciated.

Thanks and much love,
~C

EDIT:
I'm running an MDG VisionBook XL 2007 model.
2 Gigs of ram, 160 GB hard drive (5400 RPM I think), Intel Graphics Media Accelerator 950. Intel Dual-core x86 architecture (unsure what speed, but probably 1.6 or 1.7 GHz).

Any other advice you need, just message and I'll post ASAP

---

### Post by thierce on 2007-07-02
I had that problem with my plain old desktop PC and after exchanging all components it turned out that the mainboard was defect... My condensator splashed and after buying a new MB everything went well.

---

### Post by csinner on 2007-07-02
F***

This is a brand spanking new laptop too. I bought it this past wednesday, and received it on thursday.

MDG never takes my complaints seriously. If I bring this to them, they won't find the problem. Just tell me that all Linux distros have issues (Just like when they kept blaming Kazaa all those years ago and then found out my BIOS was defective, and replaced my MB).

Any ideas of how to isolate the exact problem (if it truly is a hardware defect)?

---

### Post by ruza on 2007-07-02
When it freezes can you move the mouse? 
Do you have restricted drivers?
If yes try removing drivers and editing xorg.conf to change your resolution.

---

### Post by Yettie on 2007-07-02
I'm having trouble with my laptop randomly freezing as well. I'm fairly certain that it was caused by the last system update (an upgrade of Linux- restricted-modules), because I didn't have any problems before then.
I wonder whether there is any way of uninstalling updates.

---

### Post by rillip on 2007-07-02
System freeze is almost always hardware.  The reason being, even when it's software, the OS will interupt processes at a very low level and switch to provide core services.  Even when I had something go catastrophically wrong in Linux, I could still move my mouse, type one character, etc.  It was too slow to do anything with, but I could do it.  The other scenario is that the software crashes the OS, in which case you get an error screen, much like Window's BSOD.

Now having said that, is there a way to isolate it?  Yes.  Is it easy?  No.  On a laptop it will be a major pain in the butt and will void any sort of warranty you have, which kind of defeats the purpose.  You would have to find a way to cause the freeze on demand.  I.e. it always freezes if I run this series of programs, or leave it running for at least this long, etc.  Then you'd have to have a known good computer.  Then you very systematically exchange components.  The only thing I would leave is the motherboard.  Then, at the end, if you've flip flopped and are having the issue still, it's the mobo.  With a laptop, it could be the powersupply too.

The easiest defect checks to make are on the hard drive (done automatically by Linux at boot, called fsck) or Ram errors.  When you first boot, you will see an option in the Grub menu list giving "memtest 86+" or something to that effect.  Run that for a few scans (takes several hours, best to just do it overnight).  If it comes up with errors, indicates motherboard or ram errors.  Impossible to tell which without switching RAM, because the memory controller could be the issue, and it's built in to the mobo.

A lot of system locks are heat related.  You might want to get a temperature monitoring device/program to check the CPU/Sys temp as well.

If you're seeing the laptop freezing and think it is the upgraded restricted modules, try booting into a different kernel from the grub menu list, you probably got an incompatible one.

Hope this helps.

---

### Post by csinner on 2007-07-02
With my particular issue, I mean total system lock-down. No mouse movement, no typing possible (therefore no keyboard shortcuts available).

The monitor stays on the same screen, stuck until i force a reboot.

I'll try to see if I have that memtest thing in my GRUB menu. However, voiding my warranty is not something I want to do.

I DO have a restricted driver though. For my network card. What makes a driver 'restricted' and why would this cause problems?

Any help at all is very much appreciated.. I wanna start using my laptop.

~CSinner

---

### Post by Yettie on 2007-07-02
Rillip, thank you for your quick reply. I have been struggling to get back on-line with my system crashing before I can even login.
I have had an automatic fsck since the problem started and no errors showed up.
I wondered about temperature but several checks using 'acpi -t' seemed OK.
I tried booting into a different kernel but that didn't help either.

I have found the restricted modules in Synaptic and it shows that they have been updated. However I am puzzled that when I look in 'Restricted Drivers Manager' it says that my system does not require restricted drivers. Does this mean that I could try uninstalling them. I know that I have an ATI graphics card.

---

### Post by mikehipson on 2007-07-04
well, my laptop normally freezes when im using an open office application.  the mouse still moves around but is unable to click on most things.  actually, usually i can still click on the last thing that was clicked on when the computer froze.  but, yeah the keyboard doesn't work, and i actually have to physically turn off the computer to get anywhere.

I'm doing the memtest 86 thing right now.  I started it yesterday, and its been doing the memory test for over 27 hours now..... it seems to be running normally, but when is it going to be finished???  I know its supposed to take a long time, but this seems to be a really really long time.  How do I know how much time is left?

Mike

---

### Post by mikehipson on 2007-07-04
My sister just gave me an idea about freezing.  She was wondering how much RAM ubuntu needs to run properly.  Since it uses like 4 gigs of hard drive, how much RAM does it need to run without freezing so easily?  My laptop has 512 MB, is that enough?

Mike

---

### Post by csinner on 2007-07-08
Well I have a full 2 gigabytes of RAM, and my comp still freezes. However I believe that my problem is that my wi-fi card is on a restricted driver. Is there any way to get around this?? or to find a better driver?

---

