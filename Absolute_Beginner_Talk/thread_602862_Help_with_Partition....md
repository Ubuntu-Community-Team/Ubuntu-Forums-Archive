---
title: "Help with Partition..."
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Ubun2User on 2007-11-04
[IMG]http://img87.imageshack.us/img87/7266/screenshotinstallzt7.png[/IMG]

What do I do to the above?  I can either go through this manually or I can do an auto but that reads that it will partition on the whole thing and I want to keep Vista on the computer.  Just want to run Ubuntu until I get used to it.

---

### Post by schauerlich on 2007-11-04
Which partition do you want to put Ubuntu on, the 10GB or the 240GB?

---

### Post by Tethylis on 2007-11-04
Just go do the partition thing manually. You need to make a root partiton and a swap partion. I don't know how big your hard drive is but you might have to resize your windows partition too.

---

### Post by Ubun2User on 2007-11-04
My HD is 250GB.  I want to allocate 80GB for Ubuntu.

---

### Post by schauerlich on 2007-11-04
Create a 79GB root partition and a 1 GB swap. Mount root as "/"  and swap as "swap" (both w/o quotes)

---

### Post by Pumalite on 2007-11-04
With Vista, use Vista partitioner and allocate space to ubuntu first. With XP you can use Gparted Live CD and resize XP partition (right click)
I would prepare partitions ahead of time with Gparted Live CD:
10 GB for'/'
2x RAM up to 1 GB for /swap
The rest for /home
I would then go 'Manual' and use the partitions already made. (more control; more secure)

---

### Post by Ubun2User on 2007-11-04
What is the Vista partitioner?  Do you know the program name?

---

### Post by Pumalite on 2007-11-04
If you use Vista, you first have to allocate space for Ubuntu from Vista. I think you find it in Administration. (sorry, never used Vista)

---

### Post by Ubun2User on 2007-11-04
Got it thanks!  Works great and I am now using Ubuntu.

---

### Post by Pumalite on 2007-11-04
You are welcome. Good luck.

---

