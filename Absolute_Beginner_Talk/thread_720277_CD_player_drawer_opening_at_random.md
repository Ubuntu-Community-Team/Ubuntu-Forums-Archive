---
title: "CD player drawer opening at random"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by st0nes on 2008-03-10
Hi all,  A problem has begun on my antiquated system over the last couple of days: the cd drawer opens and closes irritatingly every few seconds.  This begins as soon I boot the machine, before I have any applications running.  Is there something in Ubuntu which is perhaps polling the cd player and causing this to happen?  And if so can I disable it?

---

### Post by NightwishFan on 2008-03-10
That is an odd problem. :confused:

Open a terminal when the drawer is closed and type:
eject

See if any error messages come up. If none while its open type:
eject -t

---

### Post by zxscooby on 2008-03-10
place your cup in the cd tray ,that will keep it from opening and closing and you will have a place to hold your beer.

---

### Post by st0nes on 2008-03-10
Hi NightwishFan,  eject opens the drawer, eject -t closes it again.  Of course, now that I'm discussing the problem, it has stopped.

---

### Post by NightwishFan on 2008-03-10
Ah ok. I was really looking for some sort of error message such as "Drive in use" Normally if my drive is messed up it will tell me why when I try to eject from the terminal. Glad you got that sorted.

-Kazuma

---

### Post by st0nes on 2008-03-10
Spoke too soon; it's started again.

---

### Post by NightwishFan on 2008-03-10
:(

I am really at a loss with that. Perhaps try to reboot.
or
EDIT: Try to use a cd such as music and see if it pops it out while you try to play (its in use)

---

### Post by pbpersson on 2008-03-10
I just had that problem with a brand new CD drive.

When I powered up the computer, the drive would open

I would close it, and it would open again

It would never stay closed

It was because I had switched the faceplate when I installed the drive, took off the white one and replaced it with a black one so my computer would appear very stylish

It turned out that the faceplate was not quite COMPLETELY on the drive so when the drawer would close it could not quite close all the way.  It was perhaps 0.5mm from closing so it would pop open again

I pressed down on the faceplate around the drawer and although I could not perceive any change, I apparently move the faceplate that extra 0.5mm so the drawer would close properly and stay closed

Perhaps this might also help you in your mission of taming your wild CD drive  :)

---

### Post by UBUSNAFU on 2008-03-10
I also have one of these very special CD drives. In my case it is definitely a fault with the drive itself as it happens when I power it up on the bench with just a power supply and no computer attached. You might want to try that or try booting with a live CD from another distro. That will at least eliminate Ubuntu as being the cause.

---

### Post by st0nes on 2008-03-10
I have tried the reboot -- no change.  The drive works in the saense that I can play a CD in the short interval before it ejects again.

---

### Post by st0nes on 2008-03-10
Thanks, I tried that -- no luck.

---

### Post by st0nes on 2008-03-10
Thanks.  I'm fairly sure ubuntu isn't the cause; I've been using ubuntu on this machine for a couple of years now and this has just reared its head over the last couple of days.  Does anyone know of some means of temporarily disabling the drive without ripping it out of the box?

---

### Post by Victormd on 2008-03-12
Does this happen only when in Ubuntu or does it also happen before the boot menu?
Have you tried disabling it in the BIOS?

---

### Post by pbpersson on 2008-03-12
Go inside the computer and unplug the power cable from the back of the drive

---

