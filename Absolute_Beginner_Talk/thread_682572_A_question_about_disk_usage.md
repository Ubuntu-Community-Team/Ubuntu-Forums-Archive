---
title: "A question about disk usage"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Disparition on 2008-01-30
Hi, first of all. I'm totally new into the seemingly wonderful world of ubuntu, and I have few questions about my harddisk usage. Which confuses me a little bit. here it goes. 


I was running Vista before I installed ubuntu. It seems to run pretty fine, except a thing. I have a Seagate 80gb harddisk. But the disk usage thing shows the space as in following picture. As 70gb. (Has no partitions as far as I know)

[[IMG]http://img101.imageshack.us/img101/1774/disklb0.th.png[/IMG]](http://img101.imageshack.us/my.php?image=disklb0.png)

It isn't really a big deal, but If anyone could help me get full performance, I'd appreciate it.

---

### Post by p_quarles on 2008-01-30
It looks like it's working correctly. There is a bit of a difference between how hard drives are sold (1 gigabyte = 1 billion bytes) and how they are actually used by a computer. An 80 GB hard drive actually comes out to about 72 Gibibytes (or GiB), which is how the computer reads it.

Assuming you have at least 1 GB of RAM -- and this is a safe assumption given that you ran Vista on this machine -- the installer probably created a 2-3 GiB Swap partition. This is Linux equivalent of Windows's Virtual Memory.

---

### Post by Disparition on 2008-01-30
Ah, mister, thank you very much : )

---

### Post by hyper_ch on 2008-01-30
> **p_quarles said:**
> It looks like it's working correctly. There is a bit of a difference between how hard drives are sold (1 gigabyte = 1 billion bytes) and how they are actually used by a computer. An 80 GB hard drive actually comes out to about 72 Gibibytes (or GiB), which is how the computer reads it.


There was actually a court-case about this because the 80 GB was misleading to customers....

---

### Post by p_quarles on 2008-01-30
> **hyper_ch said:**
> There was actually a court-case about this because the 80 GB was misleading to customers....
Hadn't heard about that, but I'm not surprised. Advertising something on a scale which isn't native to modern computing (multiples of 10) does seem kind of bizarre.

---

### Post by bumanie on 2008-01-30
The problem is the way that disk manufacturers interpret 1mb and 1 gig etc. 1 mb = 1024 kb, 1gig = 1024 mb, the drive manufacturers round the 1024 down to 1000. Therefore an 80 g drive is measured by a manufacturer as 80x1000mb, but a 'true' gigabyte is 1024mb.
The reason for these non-base 10 numbers is due to the binary and hexadecimal number systems used in computing.

---

