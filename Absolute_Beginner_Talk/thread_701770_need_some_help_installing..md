---
title: "need some help installing."
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Vandorin on 2008-02-19
I've decided to install Ubuntu on my spare drive in my computer, I formatted the drive, and it is ntfs but when I click "install" and go through the steps, when I get to the end, there are only 2 options, instead of many. I was just wondering what option I would choose, if I choose the first one, which was use ALL of the hard drive, would that allow me to dualboot, and just install it on the one hard drive i formatted, and when I try to partition the hard drive, it keeps giving me an error. Does anyone know what to do?

---

### Post by teamkiller87 on 2008-02-19
If you have a spare drive then yes you can choose to install Gutsy using ALL the space. As for the erroe, off the top of my head I would have to say that the formatting is the problem. Linux works on ext3 format, not ntfs, so you should choose to format it like this. Also before actually formatting the ext3 you need to create a swap partition. If this doesn't ring bell... let us now.

---

### Post by Vandorin on 2008-02-19
it does not ring a bell, so I have to change my ntfs drive on the formatted drive to ext3?

---

### Post by teamkiller87 on 2008-02-19
Well, first you should set up your swap partition. It usually needs to be 1.5-2 times more than you RAM... or so do most users say from what I've heard. So, to break it down... 1GB of RAM -> 1.5GB-2GB swap. I, however have a 512MB swap partition with 1Gb of RAM and haven't experienced any trouble. Anyway, after choosing how big you want your swap partition to be you should see a drop-down list of formatting types. Choose swap. After doing this, the remainder of your HDD should be formatted using ext3. This will be the actual partition your Ubuntu will be installed on.

---

### Post by Vandorin on 2008-02-19
ok Im pretty sure I have it figured out, and right now its installing, so it's either going to format my whole computer, and install in there, or on the drive I partitioned. thanks!

---

### Post by teamkiller87 on 2008-02-19
You're welcome... Good luck!

---

