---
title: "OpenSuse specific installation"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by LinuxIsInnovation on 2007-12-23
Elucidating.. I have a 250GB HDD, and the partitions are like this:

 - 230GB ext3 Ubuntu Gutsy 64-bit
 - 2.3GB Grub
 - 4.6GB Swap

In my 230GB partition, about 16GB is free, and I want to make a separate partition out of it to install OpenSuse. I have tried Gparted, but it's trying to unmount the drive, which is not possible since it is the root mount-point partition. How do I install OpenSuse 10.3??

---

### Post by LaRoza on 2007-12-23
> **sayakb said:**
> Elucidating.. I have a 250GB HDD, and the partitions are like this:

 - 230GB ext3 Ubuntu Gutsy 64-bit
 - 2.3GB Grub
 - 4.6GB Swap

In my 230GB partition, about 16GB is free, and I want to make a separate partition out of it to install OpenSuse. I have tried Gparted, but it's trying to unmount the drive, which is not possible since it is the root mount-point partition. How do I install OpenSuse 10.3??

Use a live disk, see the link in my sig for the GParted Live CD.

I don't know if you have enough room, however. What is taking up 214 GB?

---

### Post by LinuxIsInnovation on 2007-12-23
And yes, I cannot afford to lose my data at this point. Please suggest a method that ensures 100% data protection.

---

### Post by LinuxIsInnovation on 2007-12-23
I have about 100GB of Audio Songs, 80GB Video songs, and 30-35GB of important data plus some more data.

---

### Post by LaRoza on 2007-12-23
> **sayakb said:**
> And yes, I cannot afford to lose my data at this point. Please suggest a method that ensures 100% data protection.

Back it up.

Don't alter the partition table without backing up, that would ensure 100% data protection (which means, don't install)

Any time you alter the partitions there is a risk. I have never experienced a loss, but a power problem, a hardware problem or a software issue could really bork the data.

> 
I have about 100GB of Audio Songs, 80GB Video songs, and 30-35GB of important data plus some more data. 

That is what I thought, just making sure I wasn't reading your numbers wrong.

I would suggest getting another hard disk so you can store data on one disk, and the OS's on the other.

---

### Post by LinuxIsInnovation on 2007-12-23
It's quite impossible for me to ged a USB hard-drive of 250GB at this point at my college. I have a laptop, so I cant get a standard HDD either..
How do I install OpenSuse though?

---

### Post by louieb on 2007-12-23
> **sayakb said:**
> ..impossible for me to ged a USB hard-drive of...How do I install OpenSuse though?
LaRosa's right. If you alter your partition table without backing up your data there is a chance you will loose some of your data - do you feel lucky.
He's also right about running GParted from a live CD. 

In your case - because your disk is so full - you stand an even greater chance of something going wrong.  

Given what you have said about your setup and the need to keep your data.  If it were mine I would not be altering the partition table on that PC until I had a way to backup the data.   Good Luck.

---

### Post by LinuxIsInnovation on 2007-12-23
Ok I'll try to arrange it somehow.. I dont seem to have any other alternatives :D
Thanx for replying.

---

