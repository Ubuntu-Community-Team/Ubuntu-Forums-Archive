---
title: "Confused over different desktop install"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Fedz on 2006-09-30
Hi :)

Can anyone please enlighten me!

On my desktop I have only one partition that is:
Device: /dev/sda1 | Directory: / | Type: ext3

On my mates install it's (2 partitions):
Device: /dev/mapper/ubuntu-root | Directory: / | Type: ext3
Device: /dev/sda1 | Directory: /boot | Type: ext3

Both of us use Ubuntu as the only OS.

Tia

---

### Post by devils_casper on 2006-09-30
> Device: /dev/sda1 | Directory: /boot | Type: ext3

your mate created a separate partition /boot. whole filesystem under / (root) can be installed on separate partitions. 
i created a separate Home partition... this means, home folder under root is actually a separate partition.



casper

---

### Post by Fedz on 2006-09-30
Right Thanks :)

So it matters none that the filesystem is under root (like me) OR seperate (like his) ...

His system boots & operates identical too mine, so I'm assuming it doesn't matter.

Thanks again :)

---

### Post by David Corrales on 2006-09-30
I might add that one of the advantages of using a separate partition for home, is the ability to reinstall the operating system without touching your files/configurations.
Some people use different partitions for other things like /var, /tmp or /boot for example, depending on their needs.

---

### Post by easyease on 2006-09-30
a seperate home partition is useful in case you ever screw up your root (quite likely for a newbie) as it means you can do a fresh install of ubuntu 
but keep all your music and documents etc safe from harm. It means if you mess up root you can choose to use the same home partition again and not erase the data.

---

### Post by easyease on 2006-09-30
great minds......lol

---

### Post by devils_casper on 2006-09-30
only one more thing to add... if home partition runs out of space, you can attach new disk and mount home on that.....



casper

---

### Post by Fedz on 2006-10-01
Thanks for your input everyone - always appreciated :)

Too late for my install but, at least I managed to do his install better than mine :mrgreen:

---

### Post by petit.padavoine on 2006-10-01
It's not too late for your install, you can always repartition, and then let Ubuntu know about the changes by editing your /etc/fstab file.

---

