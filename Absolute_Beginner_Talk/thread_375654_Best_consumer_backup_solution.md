---
title: "Best consumer backup solution?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Monsieur le Comte on 2007-03-04
I want to attach some sort of backup drive to my Ubuntu box and routinely back up a couple of gigs from various devices on my home network.

What would be my best option?  I would like to stay under $200 for the entire solution.  Lower cost of course is better.

The main ways I've been thinking of are:

Tape Drive
DVD recorder
Network Storage
Firewire/USB2 external HD

Tape drives are expensive though, and I'm worried somewhat about DVDs because they are so fragile and then there's plastic degradation which could render my data useless down the line.  Perhaps a USB2 or Firewire external drive would be the best solution?

If I went with a tape drive or a dvd recorder, what apps do I need to get?

---

### Post by og-emmet on 2007-03-04
> **Monsieur le Comte said:**
> I want to attach some sort of backup drive to my Ubuntu box and routinely back up a couple of gigs from various devices on my home network.

What would be my best option?  I would like to stay under $200 for the entire solution.  Lower cost of course is better.

The main ways I've been thinking of are:

Tape Drive
DVD recorder
Network Storage
Firewire/USB2 external HD

Tape drives are expensive though, and I'm worried somewhat about DVDs because they are so fragile and then there's plastic degradation which could render my data useless down the line.  Perhaps a USB2 or Firewire external drive would be the best solution?

If I went with a tape drive or a dvd recorder, what apps do I need to get?

On dvds: I wonder if using a rewritable disk instead of a write-once one might be better  since the recording layer is composed of a phase changing alloy and not a degradable dye. I'm guessing at least over a few years the RW should do better. Nothing is much easier than dvds for a fast and cheap solution.

On tape: If you already have a digital camcorder with USB or IEEE 1394 you could grab dvbackup and turn it into a tape drive with ~10G cartridges. More work than dvds but also two times the storage.

[http://dvbackup.sourceforge.net/](http://dvbackup.sourceforge.net/)

External HD: for $150 you can get either a 160G 2.5" or 500G 3.5" drive and cage. No removable media but drop dead simple. Think about buying the drive and cage (case) separate and save some money.

From what you've said I'd suggest looking into a DVD recorder and using DVD+RW disks since the format supports random write access. ~$50USD for the drive and ~$0.50USD per disk.

Bonne Chance

---

### Post by omrsafetyo on 2007-03-04
I have personally always manually written my own back-up scripts - which is fairly easy to do - in windows, linux, etc.  Especially considering you can simply tar -cvf entire folders, etc. of your choosing - and they will restore to the original location with tar -xvf - simple enough.  This is easiest with tape drives...  which is what I have always used - though external HDD would also be very simple.

with tape - you mount the tape drive, and then its simply **tar -cvf $TAPEPATH /folder/i/want/to/backup  **

---

