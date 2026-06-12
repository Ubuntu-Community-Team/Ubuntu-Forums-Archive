---
title: "[SOLVED] Gutsy, doing fresh install, got separate Home, need some help."
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-11-04
Ok got to stage 4 in manual bit here's a screenshot do I select format sda1 which is root?
sda3 is my home partition.

Then what. Never done this before.

---

### Post by celticbhoy on 2007-11-04
Are you dual-booting, or are you putting onto pc as the only OS

---

### Post by philinux on 2007-11-04
Dual boot. sdb is my windows disk.

---

### Post by celticbhoy on 2007-11-04
I would select to format both sda partitions just to make sure both clean

---

### Post by philinux on 2007-11-04
sda1 is root sda3 is my home I don't want to format this and sda5 is swap and the option is greyed out anyway.

---

### Post by celticbhoy on 2007-11-04
Sorry just re-read subject line, was thinking of first install, would just format root - sda1

---

### Post by philinux on 2007-11-04
I upgraded and few things amiss thats why fresh install.

Now error even if tick box or not.

---

### Post by celticbhoy on 2007-11-04
If I remember right, in the step previous to your question you have to define a pertition for root. I also take it that as your home partition is sda3 if you dont format or repartion this all your data is safe. so if a mistake is made in selection or definition of sda1 your data will be safe.

---

### Post by philinux on 2007-11-04
Nope,

previous step asks about guided - 2 options or manual. I selected manual. Nothing about root.

Have you got to mount sda1 or something.

---

### Post by detgar on 2007-11-04
> **philinux said:**
> I upgraded and few things amiss thats why fresh install.

Now error even if tick box or not.

You need to click the edit button for your root and home partitions and change "/media/sd??" to "/" and "/home" respectively. Check the format box on / and uncheck it on /home.

---

### Post by celticbhoy on 2007-11-04
This guide should help

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I think you need to select sda1 and edit its use

---

### Post by philinux on 2007-11-04
Cheers detgar,

Just clicked the edit to see what gives. Here's a screenshot how it looks now. Looks ok to me what pitfalls are there when I get to next stage after clicking forward?

Sorry for being cautious but I dont what to cock it up.

---

### Post by celticbhoy on 2007-11-04
There should be no pitfalls as data is on sda3

---

### Post by philinux on 2007-11-05
Sorted - well couple of irks but nothing much.

---

