---
title: "Will Windows destroy my Ubuntu partition?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by escape_goat on 2007-05-22
Hi all, _absolute_ beginner here.  ;)  

I decided a bit back I wanted to try Ubuntu, and because my hard drive was woefully small, I bought a new one.  I wanted to have the option to also boot Windows because I have, in the past, played some online games and would like to have the option in the future.  So I have a completely fresh install of both Ubuntu and Windows on my HD.

Naturally when I booted my fresh XP install,  it found all sorts of new hardware, including "Generic Volume".  I'm assuming this is my Ubuntu partition.  I always hit cancel for fear that it will try to format my Ubuntu partition or otherwise screw it up.  But that leaves me seeing the prompt every time I load windows, and I'd rather not.  Also I've had issues where I close it and it just pops up again, so it's an annoyance.

If I were to follow the "Found new hardware" prompts until it was satisfied there were no drivers to install for it, (and so didn't ask me again), would I risk having my ubuntu partition messed up somehow?  Or does Windows have any permissions to write to an Ubuntu partition?

---

### Post by Ferrat on 2007-05-22
There shouldn't be any risk, as long as you don't format or temper with the data windows won't touch it =)

---

### Post by steevols on 2007-05-22
I think what's happening is Windows is seeing the Generic Volume (generically speaking) for the first time on your install. Therefore, it has to install the .inf for it so the Windows Disk Manager can see it. Go ahead and click "Next...", there is next to no chance of it harming Ubuntu.

---

### Post by brennydoogles on 2007-05-22
> **escape_goat said:**
> Hi all, _absolute_ beginner here.  ;)  

I decided a bit back I wanted to try Ubuntu, and because my hard drive was woefully small, I bought a new one.  I wanted to have the option to also boot Windows because I have, in the past, played some online games and would like to have the option in the future.  So I have a completely fresh install of both Ubuntu and Windows on my HD.

Naturally when I booted my fresh XP install,  it found all sorts of new hardware, including "Generic Volume".  I'm assuming this is my Ubuntu partition.  I always hit cancel for fear that it will try to format my Ubuntu partition or otherwise screw it up.  But that leaves me seeing the prompt every time I load windows, and I'd rather not.  Also I've had issues where I close it and it just pops up again, so it's an annoyance.

If I were to follow the "Found new hardware" prompts until it was satisfied there were no drivers to install for it, (and so didn't ask me again), would I risk having my ubuntu partition messed up somehow?  Or does Windows have any permissions to write to an Ubuntu partition?

By default Ubuntu uses an EXT3 filesystem. Luckily for us, windows doesn't even know that EXT3 exists unless you install a special program. What is most likely popping up is windows seeing the new piece of hardware (the second hard drive you bought) and wanting to know what it is. Your Ubuntu will be fine!!

---

### Post by crusti on 2007-07-18
I have the same issue with an XP/Debian install.
First I installed XP and left a nice chunk of space for linux as free space. After the XP install was complete I installed Linux. Rebooting into XP causes the following:

The softrware you are installing for this hardware:

Generic Volume

has not passed Windows Logo testing to verify its compatibility with Windows XP...etc.

I tried STOP, but it will try again, and it will always try twice whenever I restart the computer.
I tried disabling Plug And Play, and this did end the message, but it also meant I could not use my usb flash drive. FAIL. So after reinstating Plug And Play and rebooting, the next time it appeared I clicked "Continue Anyway" and went through a brief few screens. Rebooted. Same thing, asked me about the "software" I was allegedly trying to install.

Thinking it might actually need some software, I installed the ext2fsd-0.31a.exe driver and set it to start automatically. Rebooted. Same problem, still wants to talk about this Generic Volume.

So this has really got me messed up. It'd be fine for my admin account, but even my regular user account is pestered with the desire to install, and to enter the admin id and password to deal with the Generic Volume.

I'm sorry you've read this in the hopes of finding an answer. If I find one, I'll post the solution. But if you know how to deal with this, please do post a reply...

Thanks, 

Crusti

hda
C: 4.8 GB
E: 1.3 GB
hdc
D: 10 GB
F: 15 GB
linux (hdc4)
13 GB

P600/384MB/Compaq Deskpro EN

XP Professional, Debian "testing" net install

---

### Post by crusti on 2007-07-18
Well, here's the story.

Immediately after installing the ext2fsd-0.31a.exe, I set it to start automatically (because it tried to register to do just that) and then needed a reboot. Upon reboot, I once again logged into my admin account and the driver was activated, and then it prompted me again about the Generic Volume thing as before.

So this time I clicked on Continue Anyway, and it finished its process. But here's the kicker.
I rebooted, and logged into my admin account, and there was no more Generic Volume message!

Furthermore, I logged into my usual user account and there was no message there either.

One last reboot for confirmation, and there was no Generic Volume message in my admin account. So it seems to have worked.

Just to make sure my USB still worked, I plugged in a USB drive to my USB 1.1 port. It continued to give me the error that it could not be stopped. It had been doing this prior to installing linux I believe (but I'm not sure.)

At least I no longer have that annoying message popping up twice every time I log in.

One problem down, one to go.

Crusti

---

### Post by crusti on 2007-07-18
Ok that was kinda silly.
PC Tools Antivirus was keeping my USB flash drive from ejecting.

crusti

---

