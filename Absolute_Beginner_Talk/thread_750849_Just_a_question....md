---
title: "Just a question..."
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by The_LP on 2008-04-09
I just heard about Ubuntu in a presentation in my PC hardware class, and was interested in trying it out. I heard about this beta, where I could install it on my Windows PC to try it out. As I was going through the installation, I had some questions as to what happens when it installs. It won't mess with my previous hard drive partitions will it? Does the installer just make a new partition to install to? I just want to be extra careful, because my hard drive has ALL of my important school stuff, and I don't want to lose any of it. Please get back to me soon, so I can complete the installation without worries!

---

### Post by Crafty Kisses on 2008-04-09
First off, are you talking about Wubi?

---

### Post by The_LP on 2008-04-09
Yes sir!

---

### Post by Boelcke on 2008-04-09
When you install Ubuntu on your hard drive, it does make new partitions.  If you're installing it on a Windows machine, certainly there will be some resizing of the existing partition (which probably fills the entire drive), which, one must admit, does involve a certain amount of risk.

I have installed Ubuntu on several machines to Dual Boot with Windows, and it works great.

However, since you're so new to it, I'd recommend first just using the LiveCD.  Download the latest Ubuntu version, and boot your computer with it in the drive.  It will boot and run off the disk without messing with ANYTHING on your hard drive.  This is a great, low-risk way to check it out.

[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

Get desktop edition, 7.10.

---

### Post by akiratheoni on 2008-04-09
> **Boelcke said:**
> When you install Ubuntu on your hard drive, it does make new partitions.  If you're installing it on a Windows machine, certainly there will be some resizing of the existing partition (which probably fills the entire drive), which, one must admit, does involve a certain amount of risk.

I have installed Ubuntu on several machines to Dual Boot with Windows, and it works great.

However, since you're so new to it, I'd recommend first just using the LiveCD.  Download the latest Ubuntu version, and boot your computer with it in the drive.  It will boot and run off the disk without messing with ANYTHING on your hard drive.  This is a great, low-risk way to check it out.

[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

Get desktop edition, 7.10.

If he's talking about Wubi (I think he stated that earlier), then it won't create any extra partitions.

---

### Post by The_LP on 2008-04-09
If I'm using Wubi does that change anything? I would imagine that it would be smart enough to not take up the rest of my whole hard drive, but I've been wrong many many times when it comes to guessing.

---

### Post by The_LP on 2008-04-09
> **akiratheoni said:**
> If he's talking about Wubi (I think he stated that earlier), then it won't create any extra partitions.

So... does that mean I should be good to finish the installation without worrying about it formatting my hard drive, or does that mean it will in fact, screw me over by formatting my existing main partition on which it is installed?

---

### Post by Boelcke on 2008-04-09
Ah, sorry, I wasn't thinking of Wubi.  Disregard my post.

Of course, if you're comfortable downloading Ubuntu and burning a CD of it, that is a good option for checking it out.  Choices, choices...

Welcome to Ubuntu.

---

### Post by The_LP on 2008-04-09
> **Boelcke said:**
> Ah, sorry, I wasn't thinking of Wubi.  Disregard my post.

Of course, if you're comfortable downloading Ubuntu and burning a CD of it, that is a good option for checking it out.  Choices, choices...

Welcome to Ubuntu.

I'm not comfortable with that, as I need my current Windows partition for backing up all my files before completely switching to Ubuntu. I just need to know if using Wubi to try the new beta will format my current Windows partition, or if it sets aside some space to let me try it out.

---

### Post by The_LP on 2008-04-09
partition #1 of Loopback (loop2) as ext3
 partition #1 of /host/ubuntu/disks/swap.disk as swap

Those are the partitions it talks about, but I forgot which ones it went through at the beginning and what the descriptions were.

---

### Post by KCormier on 2008-04-09
By default, wubi should create a disk image file on your windows partition to install itself to!  So it lives entirely in a file on your windows partition!

-Kevin

---

### Post by The_LP on 2008-04-09
> **KCormier said:**
> By default, wubi should create a disk image file on your windows partition to install itself to!  So it lives entirely in a file on your windows partition!

-Kevin

That's good to hear... because I would cry if it killed my Windows partition.

---

### Post by Saint Angeles on 2008-04-09
even you you DO repartition your drive, ubuntu can read NTFS drives... so you could just transfer your files from windows to linux.

you can't do that the other way around.

---

