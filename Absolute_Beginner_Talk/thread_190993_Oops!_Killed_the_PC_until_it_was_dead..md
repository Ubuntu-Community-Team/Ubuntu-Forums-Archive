---
title: "Oops! Killed the PC until it was dead."
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by ianwpc on 2006-06-06
I'm an Apple user, so bear with me.

I recently aquired a PC. I installed Windows 2000 on a partition and left the rest of the drive free. Cuz I wanted to try Linux...

So tonight I install Ubuntu 5.10 on the free space. Everything goes great, and I'm thinking this is actually do-able for an end user like me. System restarts after a successful install. Boot loader appears (it just works), select Ubuntu, and I'm watching the system display it's startup messages. I'm excited, anticipating future freedom from the Evil Overlord of Cupertino and the Powers That Be in Redmond. And then it hangs. Does nothing. For a while. So I reach down and hit reset.

And then the laughter died. Along with the PC. The BIOS now reads INVALID BOOT DISKETTE. Booting from the Windows 2000 CD-ROM gets me "no drive detected". Booting from the Ubuntu CD-ROM gets me a hang at "Detecting network hardware". Glorious.

I'd like to cut my losses. Loss, actually. I would like my PC to see it's drive again. Any ideas?

Thanks in advance for any responses. And putting up with my writing.

Ian

---

### Post by rcarring on 2006-06-06
Boot with a 98 boot disk.

Run fdisk /mbr

Reboot

Run fdisk

If it says no drives found, your hard disk has died.

Research the drive manufacturers site see if they have a diags floppy you can download and use.

Its possible a low level format may recover the disk but if its less than 4Gb I would seriously consider getting a cheap 20Gb off ebay.

---

### Post by u.b.u.n.t.u on 2006-06-06
When you start your PC enter BIOS. See if that can detect your HDD.

---

### Post by Ptero-4 on 2006-06-07
How new is that box? If it's post-2002 x86 PC or a x86 Mac. Odds are you got one of the OS nazi suicidal computers that get sold nowadays. If that's the case, you won't be able to install non-M$ OS's on it. All you can do is return it for a refund and get yourself a PPC Mac or a pre-2001 x86 PC.

---

### Post by ianwpc on 2006-06-07
And the tears turned to joy...

Thanks for the suggestions. And the quick responses, wow.

I decided to remove the network adapter to see if the Ubuntu CD-ROM would make it past the hang (reserve judgment, I was at loose ends). Power off, remove card, power on and voila! Greeted by boot loader. Windows partition recognized. Install completes. I'm posting from it *right now*.

So far, so much better. No more candy-coated proprietary everthing or legacy-clunk with extra advertising. As an added bonus, I have established my credentials as a mega-noob.

Closure is such a rare thing in life...

---

