---
title: "Shopping for a new hard drive"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-01-25
Well, I went and done it... I've downloaded so much crap off of the intraweb that my hard drive is maxed out. And since I'm a lazy bastard who would rather expand than start deleting, I'm doing just that.
[LIST=1]
[*]Is there any make, model, etc., that simply won't work with Ubuntu (Edgy, in my case)?
[*]Is there a make, model, etc., that anyone would heartily recommend?
[*]What do I need to do to install it?
[/LIST]
I thank you mightily in advance.

---

### Post by halitech on 2007-01-25
hard to make an honest recommendation without knowing are we talking IDE, SCSI, SATA, or flash drives? what someone might recommend for IDE may not get the same in SCSI or SATA.

---

### Post by ricardisimo on 2007-01-25
Fair enough. How do I find out what I've got right now? I'll use that as a starting point.

---

### Post by halitech on 2007-01-25
when it starts to boot, can you get into the BIOS? it should give us an indication of what you have. otherwise, you need to take the cover off and check that way.

---

### Post by ricardisimo on 2007-01-26
Here's my hard drive info:
```
hda: max request size: 128KiB
hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
hda: cache flushes supported
hda: hda1 hda2 < hda5 >
```
What's the pertinent info? UDMA? Thanks.

---

### Post by logos34 on 2007-01-26
This will give you more info:

In a terminal:
> sudo hdparm -i /dev/hda

You have the fastest pata drive (ata133), but with a small buffer (2MB)...Look for a new one with 8mb (or 16mb if its a big drive over 250gb)...Sata is not much faster than pata, despite its impressive sounding specs...Western Digital Caviar series are highly rated, and Seagate drives have a 5-year warranty, definitely something to consider...

A Chomsky reader!  Cool...

---

### Post by gn2 on 2007-01-26
For desktop PC's I always buy Samsung hard drives. Quiet, reliable and excellent build quality.

---

### Post by jvc26 on 2007-01-26
I've been using seagate or maxtor HDDs recently, both without issue.
Il

---

### Post by ricardisimo on 2007-01-26
I thank you all mightily for the tips. If I get a massive hd, I imagine I'm setting it as a slave, right? Is there a way to make the new drive the master and this current one the slave? Does that sound like an overly ambitious project? Actually, is there any benefit to doing that? I had assumed that there would be, but I really don't know.

---

### Post by taurus on 2007-01-26
I'd go with Seagate also because it's fast, cheap, and comes with 5-year warranty!

---

### Post by rocknrolf77 on 2007-01-26
Used to be a seagate fan until my seagate disks crashed after a couple of years. Now I have two samsung spinpoints. (160 and 400 gigs) They are very quiet. Seagate made a lot more noise. (For me at least) :guitar:

---

### Post by taurus on 2007-01-26
> **rocknrolf77 said:**
> Used to be a seagate fan until my seagate disks crashed after a couple of years. Now I have two samsung spinpoints. (160 and 400 gigs) They are very quiet. Seagate made a lot more noise. (For me at least) :guitar:

I've heard the customer service at Samsung sucks big time.

---

### Post by Lord Of The Dance on 2007-01-27
> **ricardisimo said:**
> I thank you all mightily for the tips. If I get a massive hd, I imagine I'm setting it as a slave, right? Is there a way to make the new drive the master and this current one the slave? Does that sound like an overly ambitious project? Actually, is there any benefit to doing that? I had assumed that there would be, but I really don't know.

Master and slave refer to the position of the hard drives when they are on a single ATA cable. The order makes no difference to performance. Its been a long time since I've installed a hard drive, but it is a fairly simple task, just make sure that the jumpers are in the correct position.

Edit: Do hard drives still use jumpers? Anyway, just make sure that master/slave positions are correct on the hard-drives

---

### Post by gn2 on 2007-01-28
> **taurus said:**
> I've heard the customer service at Samsung sucks big time.

Wouldn't know, my 80gb spinpoint is still going strong and it's been in use daily since May 2002.

I have other newer Samsungs, have fitted them in other peoples PC's and have yet to have a single problem.

---

