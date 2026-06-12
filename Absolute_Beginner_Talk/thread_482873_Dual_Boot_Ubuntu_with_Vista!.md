---
title: "Dual Boot Ubuntu with Vista!"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Octarine on 2007-06-24
Right.
Im planning on Dual Booting Ubuntu 6.something with Windows Vista Premium

Im guna first Partion the Drive (only 80Gig) using Partionmagic into:

20Gigs: Vista + its programs
20Gigs: Ubuntu + its programs
40Gigs: Data (in FAT32)

From here, im stumped as to how to go about it. I think Im supposed to use Bootmagic in some way, but im
not too sure. I tried Ubuntu with Win XP once, and I ended up gettin a Grub error which blocked XP and Only let me run Linux from disk. So, what would be the best way to go about this please?

Id appreciate anyones input and/or experiences, etcetera..

Thanks!

---

### Post by foxmulder881 on 2007-06-24
If you already have Vista installed, just install Ubuntu and it'll automatically install GRUB and allow you to dual-boot on startup.

If nothing is installed currently, install Vista first and then Ubuntu (as described above).

---

### Post by sourjax on 2007-06-24
Well, I'm an extremely new user, but I am using Dual booting on Windows Vista Home, here's what I did.

1) I downloaded the ISO burned it to a disk using Roxio Easy Media Creator.
2) I then partitioned my disk using "Computer Management".
3) I then restarted my computer and followed the instructions.

Hope that helps.

---

### Post by Octarine on 2007-06-24
And what about partioning? I understand FAT32 is the format that both Linux and Windows can read from , but do you think I still need to partion?

---

### Post by mattg89 on 2007-06-24
I did something similar but with XP, so for you:

Install Vista first, on the whole hard drive
Burn an image of the CD
Use the Roxio to create the two other partitions, both can be FAT32, one can be reformatted in the install to ext3 (what linux uses)
Put the CD in and select the partition you want to install in (it shows you size and current format)
Ubuntu!

---

### Post by Octarine on 2007-06-24
Thanks for you help everyone, guess il see how it goes!!

---

### Post by Brightbelt on 2007-06-24
Octarine, I have a dual boot with Vista - the guys ar right about setting up partitions using Computer Management in VIsta first, but you'll also need a swap partition. 

This is a very small partition (1GB is plenty) that helps to facilitate the dual boot. I could be wrong but from what I undestand, this is critical to setting up a dual boot.

I hope this helps, ....Frank B.

---

### Post by mattg89 on 2007-06-24
> **Brightbelt said:**
> but you'll also need a swap partition. 

This is a very small partition (1GB is plenty) that helps to facilitate the dual boot. I could be wrong but from what I undestand, this is critical to setting up a dual boot.


You don't need to worry about this. The Ubuntu installer sorts it out automatically.

---

