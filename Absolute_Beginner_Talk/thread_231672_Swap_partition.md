---
title: "Swap partition"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Kaloma on 2006-08-07
I hope this is a good place for this thread.

I am aware of several considerations for optimal (speed) placement of the swap partition(s).
[LIST]
[*]Place toward the outer tracks (on new drives)
[*]Place close to the data partitions that get the most use
[*]Place on a separate drive so that data and swap can be accessed concurrently
[/LIST]

My question: Is it worth placing the swap partition on a slower drive?

For example, my desktop machine has a 160GB 7200RPM SATA drive (Seagate) with 8ms access time.  I have a small HDD lying around with 8GB capacity (Western Digital), I don't know the RPMs or seek time, but the drive is much older (est. 5 years older than my primary disk).

Would is make sense to connect that drive to use for my swap partition(s), or is is better in this case to keep it on my faster disk?

Thanks in advance,
Matthew

P.S. I would find post the other specs on the old drive, but I have to dig it up first.  I'm at work right now.

---

### Post by eriefisher on 2006-08-07
Hey there.

How much memory do you have in the system? I don't think the slower drive will matter much because the swap will only be used when needed. Just being on a seperate drive should be more than enough.

eriefisher

---

### Post by Kaloma on 2006-08-07
Physical memory size is currently 1GB.

Matthew

---

### Post by eriefisher on 2006-08-07
Depending what you are doing, you might not even go into swap with 1 gig of memory. Monitor the usage and see how much your actually using.

eriefisher

---

### Post by steve.horsley on 2006-08-07
Nothing to do with swap speed, you moght find that having mixed IDE and SATA drives confuses GRUB. There have been lots of posts with booting troubles with mixwd drive tyoes.

---

### Post by KipBond on 2006-08-07
I'm pretty sure you will get much better performance just putting the swap partion on your SATA drive.  It's best to not ever use it, actually, so if you find that you are swapping a lot, then preferably buy some more RAM.  If that's not an option, then swapping to your fast SATA drive will be far more bearable than swapping to your old IDE drive.

---

