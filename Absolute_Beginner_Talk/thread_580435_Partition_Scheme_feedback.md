---
title: "Partition Scheme feedback"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by tsgray on 2007-10-18
I know this has been asked many times before but I want to be certain I'm doing everything correctly before formating and installing 7.1. With the installation of gutsy I'm trying to move away from windows on a least one pc. Does anyone see any potential issues with this setup.....

HD 1 - 75GB (10,000 rpm)
10GB for /
1GB for /swap
64GB for /tmp - this will be used to play with other OS's in virtual box and temporary data storage

HD 2 - 300GB
300 for //home

Also any advantages to using one file system type over another. Thanks in advance for the guidance.

---

### Post by Pumalite on 2007-10-18
Looks OK. to me.

---

### Post by Duck2006 on 2007-10-18
All looks good but the 
> 64GB for /tmp - this will be used to play with other OS's in virtual box and temporary data storage

With the home may be you sould only use 30Gb and use the rest for data or even split it and use it for some other disc'o.

---

### Post by p_quarles on 2007-10-18
Depends on how much RAM the system has. Best practice is to use a swapfile twice as large as your total RAM. So, this is ideal if you have 512 MB.

---

### Post by tsgray on 2007-10-18
Thanks all for the quick responses. Keep them coming.

I currently have 1GB of ram but have another on the way I thought a 2 or 4GB swap was a bit of overkill

I forgot that /tmp is cleared out every 10 days if files aren't used (at least I know I read that somewhere) so I'll be changing that partiion to data.

---

### Post by Duck2006 on 2007-10-18
> I thought a 2 or 4GB swap was a bit of overkill

The swap partition does not need to be any bigger as with the amount of RAM you have the swap partition may net ever be used.

---

### Post by p_quarles on 2007-10-18
> **Duck2006 said:**
> The swap partition does not need to be any bigger as with the amount of RAM you have the swap partition may net ever be used.
That's very true for daily use, but when you do anything resource heavy you will be able to use it all. With 450 GB of hard drive space, it makes sense (to me) to allocate as much space as you might need.

---

### Post by Duck2006 on 2007-10-18
> **p_quarles said:**
> That's very true for daily use, but when you do anything resource heavy you will be able to use it all. With 450 GB of hard drive space, it makes sense (to me) to allocate as much space as you might need.

Thats true with all that space.

---

