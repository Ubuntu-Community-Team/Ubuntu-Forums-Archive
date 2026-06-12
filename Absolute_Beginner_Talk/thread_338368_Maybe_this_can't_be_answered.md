---
title: "Maybe this can't be answered"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Bigguy2468 on 2007-01-14
I don't know if this is a question can be answered. I am currently typing this from the ubuntu Dapper Drake Live CD. It is the only CD so far that will boot up. I have tried the DVD for this same distro and every time that it gets to the point in the boot process where it says:

STARTING ENTERPRISE VOLUME MANAGEMENT SYSTEM...

...the system "freezes!" and that's that. Now some people might say, "well then why complain just use the you're using?" However, it would be interesting to know what the problem is. It seems the majority of the problem has to do with the DVD version of the distro, although the same DVD disc works fine on my desktop. I also had the same problem with the 64bit version although I didn't try the CD version of this disc only the DVD which had the same problem.

---

### Post by rbhigday on 2007-01-14
Is it possible to burn another DVD copy. Maybe the dvd disk is bad or the image was corrupted.

---

### Post by kebes on 2007-01-14
I don't know what the answer is, but when an install freezes you can sometimes get additional information by using "Ctrl+Alt+F1" (go from F1 through F12 ... or just use "Alt+F1" if you're in the beginning text part of the bootup). One of those background screens should have some kernel messages... possibly one of them has some error messages that will let you figure out why the system just froze. If you can get to a terminal in one of those background screens, you can also login to it and try to look at the log files (in "/var/log/" probably) and see if there's any hints there.

If you can't even switch through virtual consoles as I described above, then the system is really totally frozen. In that case there's not much you can do, exept try random things... At the initial bootup screen before hitting enter to "install from CD" you press F6 for "other options" and you can enter some kernel flags.

By playing around with flags you can sometimes figure out what went wrong. For instance if the kernel flag "all-generic-ide" suddenly fixes it (no longer freezes during install), then it's probably a problem with the motherboard IDE driver. If "irqpoll" fixes it then it's an IRQ issue, etc. There are lots of boot flags and sometimes one of them will work.


However, I have to ask: "If you have a LiveCD that works, why not just use that?!" :)

---

### Post by sailor2001 on 2007-01-14
how much ram do you have? also as someone suggested, if live cd boots, why not install from that?

---

### Post by Bigguy2468 on 2007-01-14
> **sailor2001 said:**
> how much ram do you have? also as someone suggested, if live cd boots, why not install from that?

1gig

---

### Post by Bigguy2468 on 2007-01-14
> **kebes said:**
> However, I have to ask: "If you have a LiveCD that works, why not just use that?!" :)

I knew that was going to come back as a question. I am happy to use the CD I have and install from that, it's just one of those things that "bug" me. You know, why in the world a DVD image would boot on my other machine and not on this laptop is beyond me. This laptop is brand new and I would think would work better than anything else I have, but obviously this is not the case. Anyhow, at least I have on that works now...yipee!!! :D

---

### Post by Ocxic on 2007-01-14
what about the alternate cd's/dvd's???

---

### Post by louieb on 2007-01-14
> **Bigguy2468 said:**
> ...However, it would be interesting to know what the problem is....
In your case I am 99% sure it is just a bad DVD burn. It just take a few scrambled bits in the wrong place to turn a CD/DVD into a coaster. Depending on where the bits are scrambled the disk might work. For example if you scramble up some bits in a help file or text file no problem. But if the scrambled bits are in the chunk of code that detects the amount of memory or hard drive type then probably not going to work.   
A couple of other reasons a CD/DVD fails to boot or partly boots.
Copies ISO to disk instead of burning as an image.
Boot order in BIOS not set to CD first.
BIOS incorrectly thinks CD is not boot able. 
And the hardest one to figure out the CD will boot on one computer but not another. Usually fixed as kebes pointed out by a boot flag. For example the first one I alway try is ide=nodma. Alto this could be a bad burn also. Its just the the scrambled bits  need to  execute on one computer but not the other due to different hardware on the two computers.

---

