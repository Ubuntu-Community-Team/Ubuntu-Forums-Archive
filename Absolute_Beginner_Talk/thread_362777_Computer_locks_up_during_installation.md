---
title: "Computer locks up during installation"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Doctor Sneeze on 2007-02-16
Hello,

For the last few days I've been trying to install Ubuntu on my computer with no success.  Every time I try, the computer locks up.  I do not get any kind of error message, the computer simply stops responding, the cd drive is no longer reading and the hard drive is no longer active and the cursor doesn't move when I move my mouse.

I have tried with the regular iso of both 6.10 and 6.06 and the alternate for 6.06.  My computer processor is an AMD Athlon Thunderbird 1400 MHz.  I have 512 megabytes of ram and am attempting to install on a blank 12 gigabyte hard drive.

Thanks for your time.

---

### Post by Spr0k3t on 2007-02-16
At what point of the install does the system freeze?  Have you already partitioned your drive?

---

### Post by Doctor Sneeze on 2007-02-16
The lock up point isn't consistent.  It most frequently occurs past the 50% installed point, but it's happened early on and even once as soon as I clicked on the install icon.

I'm using the built in drive partitioning setup as I'm not really sure what I'm doing, and I don't think I have any software that will format the drives properly outside of that anyway.  The lock ups tend to occur after the drives are set up though.

---

### Post by shareMenaPeace on 2007-02-16
Make sure you burned the CD with lowest speed and when you successfull formated the drives you do not need todo this again just proceed with install.

---

### Post by Spr0k3t on 2007-02-16
I've had this happen to me a couple times with my testing.  I noticed it happens more often on blank drives than it does with drives that are partitioned.  This is what I would do.  Go back through the install, but instead of sticking with the defaults try setting the partition sizes.

For a 12GB drive, section off 10.999GB for root and home and the remaining as a swap drive.  Also, on boot, see if you can't disable the ACPI (or however you spell it).  Should be one of the function keys at the boot menu.

---

### Post by Doctor Sneeze on 2007-02-16
Doing the partitions manually and disabling ACPI don't seem to be helping.  I'll try burning a new CD tomorrow.

---

### Post by dtholen on 2007-02-16
I likewise experience this problem at the point where the install is attempting to partition the hard drive. I want to set up a dual boot but the install stops when attempting to set up the partitions. I suspect there problem is centered on partitioning difficulties and I can't progress beyond this point either.

---

### Post by panti19 on 2007-02-16
check the cd's integrity when it boots

---

### Post by Psyphre on 2007-02-16
I have this exact problem everytime I try to install ubuntu on my desktop. It will work... eventually. It took me over 20 times but it eventually installed. Oddly enough it works perfectly well on my laptop (using same cds).

---

### Post by dtholen on 2007-02-16
> **Psyphre said:**
> I have this exact problem everytime I try to install ubuntu on my desktop. It will work... eventually. It took me over 20 times but it eventually installed. Oddly enough it works perfectly well on my laptop (using same cds).

Are you saying that you attempted to install 20 times before you were successful? Does each attempt seem to advance further along the install process?

---

