---
title: "Confused With Installation"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Joeb454 on 2007-12-03
Ok so I'm writing this from a Live CD, as I'm just about to partition the drive and install Ubuntu...despite the fact my laptop needs repairing, lol, either way I'll need to know how to sort these partitions out (pic included below)

Basically I want to know that the Recovery partition will be ok and accesible if I run the recovery DVD that came with my laptop.

[IMG]http://joeb.uk.googlepages.com/Screenshot--dev-sda-GParted.png[/IMG]

Any help would be appreciated

---

### Post by philinux on 2007-12-03
Edit - panicked

Make sure you mark it as not to format etc. 

Have you tested the recovery dvd's

---

### Post by Paqman on 2007-12-03
One problem you might have is that you can't have any more than 4 primary partitions on a drive. I don't know how may partition you were planning for Ubuntu, but you'll have to create an extended partition for them.

If you don't touch your recovery partition, there's no reason why it shouldn't work, AFAIK.

---

### Post by Joeb454 on 2007-12-03
Yeah I made the recovery disk the day I got the laptop why? I also have a generic Vista disc lying about somewhere if all else fails

--------------------------------------

And that's what I was thinking about the recovery partition. Will just use the 1 partition for Ubuntu I'm not bothered about having a separate /home partition atm, if I need to reinstall I'll just copy the content onto an external drive

---

### Post by jken146 on 2007-12-03
The Recovery partition will certainly be accessible if you leave it alone (there is NTFS read and write support) but I don't know anything about how Windows restore works so I can say no more than that really.

It looks like the best thing for you to do would be to shrink your Vista partition (I believe there is a tool for doing this in Vista) and then make your linux partitions in the freed-up space.  You will need at least:
-  a / partition
-  a swap partition

Give it a bit of thought before you jump in, and be careful not to accidentally format the wrong thing! (trust me, I've been there...)

---

### Post by philinux on 2007-12-03
Like the previous poster said - max primary partitions is 4 so you will have to use logical.

Ubuntu needs root and swap

---

### Post by Joeb454 on 2007-12-03
Well the plan is to shrink the Vista partition and install Ubuntu at the end of the disk, because I know Windows likes to be at the start because it thinks its all important :p

Well if it all goes tits up I can reinstall both systems anyway lol, be a pain in the *** but I could do it

---

### Post by Duck2006 on 2007-12-03
Partition your drive from in vista to give you the size you want for your ubuntu install. Then make then logical partitions.

---

### Post by Joeb454 on 2007-12-03
I'd rather use Gparted, purely because last time I tried to partition my Windows drive from Windows it completely killed the HDD

---

### Post by Duck2006 on 2007-12-03
> **Joeb454 said:**
> I'd rather use Gparted, purely because last time I tried to partition my Windows drive from Windows it completely killed the HDD

With vista if you may have errors after your install but there is only one way to find out then good luck hope it works well for you.

---

### Post by Joeb454 on 2007-12-03
Will post back after I've installed and let you know if I can still boot into Vista lol

---

### Post by philinux on 2007-12-03
Defrag and defrag agin

---

### Post by Joeb454 on 2007-12-04
Well I broke the MBR after I partitioned!! lol

Not installed Ubuntu yet because gparted took aaaages to shrink the drive (only shrunk by 20 GB!!! lol) but when I rebooted I got to find out what was on my Recovery partition, which is basically the repair options off the Vista install disk.

Anyway i can now boot into Vista, and I'll be installing ubuntu at some point today hopefully :)

---

