---
title: "Can I do this? w/ my ext drive"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by ZeldaFan on 2007-09-13
I have Ubuntu Feisty Fawn set up on my laptop occupying my entire hard drive. I also have a 160 GB external hard drive. Before I used to daul boot in my laptop between ubuntu and windows vista. But now I was wondering my external HD from its current FAT32 file system to ntfs (or whatever is best with Vista) to install vista on it. The external drive connects to my computer through the USB interface by the way. Can I do that? And if I can how would I handle loading into the operating system and installing programs?

---

### Post by rivalarrival on 2007-09-13
Yes, you can do it (from what I've read, at least...)

You'd have to set the boot order in BIOS to optical drive > USB > Internal Hard drive.

Drop in your vista disk and it SHOULD be a fairly typical installation. I've never messed around with Vista, but XP's installer always saw my USB flash drives. 

Loading programs should be the same as well... 

If I were going to do that (with XP - I don't know vista) I would shrink my internal drive's partition by a couple gig, create a new NTFS partition, and use it for my windows swap file - USB is pretty slow, in my experience.

---

### Post by ZeldaFan on 2007-09-14
Thanks for the reply.
I was really think about doing this and while I have a general idea as to how to do this. I'm not so sure as to the specifics. How do I reformat my external HD to ntfs? And after that, are there any guides out there as to what to do? I can probably figure out changing my bios boot order, but I'm not sure about the swap file. I'd probably just boot into a live CD, resize my current internal HD partition, make a new partition as NTFS, but then what? How do I make windows take that as my swap partition? I have both xp and vista, as I have vista as an upgrade, so I'll install xp first.

---

