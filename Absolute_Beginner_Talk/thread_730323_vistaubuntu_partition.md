---
title: "vista/ubuntu partition"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by jwalters on 2008-03-20
I recently purchased a new Dell with vista preinstalled. I went into windows and created a partition "F" about 1 gig size.

Now I want install ubuntu into the "f" partition, but am confused when the CD gets to the three choices. If I allow ubuntu to install I believe it will wipe out vista....if I do it manually I'm not sure how........

howto?

---

### Post by Nythain on 2008-03-20
did you actually create teh partition in windows or just shrink your windows partition, freeing up space???

if its just "free space" then you can tell ubuntu to do it Automatic USING FREE SPACE...

if you actually created a partition in windows, then you will probably have to re do it, since you are actually going to need at least two partitions out of that free space, at bare minimum a / partition and a SWAP partition...

---

### Post by gecko113 on 2008-03-20
Another way to do this is use Gparted which is on Ubuntu and its quick and easy way to partition and u can set up the allocated space to ext2 or ext3

---

### Post by Joe Dinmore on 2008-03-20
> **jwalters said:**
> I recently purchased a new Dell with vista preinstalled. I went into windows and created a partition "F" about 1 gig size.

howto?
 Note that you will need around 4 gigs minimum for Ubuntu

---

### Post by harpazo on 2008-03-20
For an easier solution that partitioning, you might try WUBI....

It installs Ubuntu in your Vista partition, but acts like a separate installation (including boot choices)

[http://wubi-installer.org/faq.php#requirements](http://wubi-installer.org/faq.php#requirements)

Harpazo

---

### Post by gecko113 on 2008-03-21
Ive done the same thing you have done but the only thing is that Vista killed itself cause it knew that Ubuntu is a better OS system then it so once that happened i went all linux :)

---

### Post by Nilanko Halder on 2008-03-21
Firstly u need to create 2 new parts of ur HDD.On the second last part, the main sys should be installed and the last part should be for SWAP.During installation, choose manual partitioning option, select the 2nd  
last part as root("/") and the last as "SWAP area" and that's it---u will not loose ur vista!:KS

---

