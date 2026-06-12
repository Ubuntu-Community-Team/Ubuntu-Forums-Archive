---
title: "[SOLVED] amd64 w/winfast mobo hanging install"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Bob63 on 2007-07-11
Hi everyone,
I've looked through the boards and can't seem to get Ubuntu to install on this system. I've tried pretty much every combination of commands and still no joy. I really want to learn this!

I consider myself to have an intermediate level of experience, although it has all been on Windows systems (I don't count the eight months using Unix in an networked office environment, 'cause I was a "user", and had no chance to get involved under the hood.) I've experimented in the past with x86 Assembly language, used DOS, BASICA, VisualBASIC/VBA, and Windows 3.1, 95, 98&98SE, 2K, and XP. (My other machine is an old Compaq Presario running Win98, in fact.)

Here's what's happening on _this_ machine: Ubuntu install hangs at 66%, system is almost frozen. I get about 2 mouse clicks before it freezes completely. The partioner indicated that I have my hard drive partitioned into 20GB, 2GB, and 50GB.

Here's the system specs:
AMD Athlon 64 3400+ 2.2GHz
WinFast/Foxconn C51PVM06N2-6KRSH/6150BK8MC mobo
Western Digital WD800JB-00JJC0 80GB HD
Mitsumi FX400 quad-speed CDROM
Crucial 512MB 184-pin unbuffered DIMM DDR (PC3200)

This mobo has on-board nVidia GeForce 6150B + nForce 430.

The LiveCD will boot and run, although it will also lock up occasionally.

Like I said, I really want this to work, I use other open-source products on my other machine (i.e. Firefox and Thunderbird), and I like the idea. Plus Microsoft stopped supporting 98. If I can get this to work, I'm planning to upgrade that machine also.
I'm not adverse to typing, as long as I understand what I'm typing. I've even considered copying the files directly to the HD.

I'm going to go mow my yard while this latest attempt grinds.

P.S. This post is being done on Firefox during a LiveCD session, so everything basically works during Live....

---

### Post by gn2 on 2007-07-11
As you have determined that the hardware definitely works with Ubuntu, two things spring to mind:

1: Have you tried the alternate CD  text-based installer?

2: Are you using 64-bit version? (Maybe try 32-bit)

If you haven't read through Hermanzone (link in my sig) have a good read through, it's well worth it.

---

### Post by Bob63 on 2007-07-11
BTW, I'm trying to install 6.10 Edgy Eft, if that helps. Going and mowing sure didn't! On this last reboot, I used several command line options [noapic acpi=off nosmp nosplash] there was a great deal of output on the monitor. Is it possible to capture this in a file? The LiveCD session does recognize my floppy and my USB, so maybe....

I'll take a look at Hermanzone, and thanks.

---

### Post by gn2 on 2007-07-11
Perhaps try 7.04 instead of 6.10 ?

---

### Post by iver2435 on 2007-07-11
You might also want to try to include "noirqpoll" in your kernel boot options.

---

### Post by Bob63 on 2007-07-12
> **iver2435 said:**
> You might also want to try to include "noirqpoll" in your kernel boot options.

iver2435: I've tried noirqpoll, along with the usual suspects: noapic, apci=off, nolapic, nosmp,  irqpoll, noirqdebug, and nosplash....all equalling no joy. Are some of these boot options incompatible with each other?

---

### Post by Bob63 on 2007-07-13
Like everyone else who seems to have difficulty installing Ubuntu 6.10 Edgy Eft from the LiveCD, I downloaded and burned the .iso of the alternate install. Worked like a charm, installed in about 45 minutes, and I'm using 7.04 Feisty Fawn. Even the updates went smoothly. As of this moment, and unless something goes horribly wrong, I'm a very satisfied individual!

So I guess my next question would be, why is there such a problem installing from the LiveCD? Not just me, but I've seen a lot of problems on the forum.

---

### Post by masteryurez on 2007-07-14
THIS WOULD SOLVE YOUR NOAPIC PROBLEM!!

[http://ubuntuforums.org/showthread.php?t=500884&highlight=noapic](http://ubuntuforums.org/showthread.php?t=500884&highlight=noapic)

---

### Post by Bob63 on 2007-07-14
> **masteryurez said:**
> THIS WOULD SOLVE YOUR NOAPIC PROBLEM!!

[http://ubuntuforums.org/showthread.php?t=500884&highlight=noapic](http://ubuntuforums.org/showthread.php?t=500884&highlight=noapic)

Masteryurez,
Many thanks for your assistance; however, I was finally able to get Ubuntu to install....like this:
1. Turn off computer and all peripherals.
2. Disconnect all peripherals. (I only have one monitor and keyboard)
3. Open computer case, disconnect and remove CD-burner. (I only have one of these also)
4. Install CD-burner in old Windows98 PC.
5. Connect all peripherals to Windows98 PC.
6. Boot Windows98 PC and logon.
7. Go to Tucows and download a program to burn .iso images. Install program.
8. Go to Ubuntu website and download .iso image of the alternate Ubuntu installation for i386, burn this to a blank CD.
9.Log off, shutdown Windows98 PC, disconnect all peripherals, remove CD-burner from this machine and reinstall in the new machine.
10. Boot new machine, place new CD in drive, answer a few questions and Viola! 

I apologize if this sounds sarcastic, however, it worked and I am up and running. My next project will be upgrading that Windows98 computer that is (was) gathering dust in the corner.

Again, many thanks for your assistance, and I have made notes in case I run into this again.
Bob63

---

### Post by samb0057 on 2007-11-12
Got a 7/10 on UbuntuHCL.org, seemed to have a few problems: [www.ubuntuhcl.org/pub/reviews.php?product_id=332](www.ubuntuhcl.org/pub/reviews.php?product_id=332)

---

