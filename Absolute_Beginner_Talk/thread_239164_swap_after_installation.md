---
title: "swap after installation"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by hellfried on 2006-08-18
is it possible to create a swap partition after the installation of dapper? i did not create one during the actual installation. i have 1G of ram. would that mean i have to have a 2G swap partition?

---

### Post by meng on 2006-08-18
The 2:1 ratio is not a hard-and-fast rule. Probably safest to use another LiveCD distro like GParted to repartition your drive to create a swap drive. Then you just need to edit your /etc/fstab to point to the location of the swap drive.

---

### Post by taurus on 2006-08-18
Yes, you can create a swap and mount it at boot from /etc/fstab.  And no, you don't need to double your RAM for your swap!  That method was practice years ago...  Depending on what you do and how long you leave your computer running, swap of 512MB or 1GB for 1GB of RAM is plenty.

---

### Post by hellfried on 2006-08-18
> **meng said:**
> The 2:1 ratio is not a hard-and-fast rule. Probably safest to use another LiveCD distro like GParted to repartition your drive to create a swap drive. Then you just need to edit your /etc/fstab to point to the location of the swap drive.

i have always used gparted livecd to partition my hd. my next question is how do i point to the swap drive in fstab after i have created it?
below is how my fstab looks like currently.

---

### Post by taurus on 2006-08-18
Just add a line in your /etc/fstab that looks something like

```

/dev/sda5  swap  sw   none   0   0

```

---

### Post by hellfried on 2006-08-18
> **taurus said:**
> Just add a line in your /etc/fstab that looks something like

```

/dev/sda5  swap  sw   none   0   0

```

thanks will try it after i get some breakfast :D

---

### Post by meng on 2006-08-18
> **hellfried said:**
> thanks will try it after i get some breakfast :D
Never repartition your drive on an empty stomach!

---

### Post by hellfried on 2006-08-18
> **meng said:**
> Never repartition your drive on an empty stomach!

my exact sentiments! anyways things went without any hitch after i reformatted a 1G partition as linux-swap. this particular partition is found at the end of my dapper partition. i have edited my fstab file. should i expect some boost in my system performance now? so far i cannot feel the difference at all.

---

### Post by taurus on 2006-08-18
Since you have 1GB of RAM, I doubt if your system even uses the swap unless you have a bunch of apps running...  As always, you can use gkrellm to keep an eye on the RAM and swap.  It's a real handy little plugin.  ;)

---

### Post by hellfried on 2006-08-18
yikes all of a sudden synaptic does not work on my system. when i click on system > administration > synaptic package manager it asks for my password and then nothing! what is going on?

edited

found the answer. serves me right for not doing a search first. apparently something to do with the latest update of compiz.

---

### Post by hellfried on 2006-08-20
> **taurus said:**
> Yes, you can create a swap and mount it at boot from /etc/fstab.  And no, you don't need to double your RAM for your swap!  That method was practice years ago...  Depending on what you do and how long you leave your computer running, swap of 512MB or 1GB for 1GB of RAM is plenty.

i am just curious about your last statement; do u mean that if i leave my pc on 24/7 i have to have a bigger swap partition?

---

