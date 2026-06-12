---
title: "ubuntu 11.04 live cd won't boot on 2011 new  Macbook Pro 15'"
date: 2011-05-09
forum: Apple Hardware Users
---

### Post by dairyknight on 2011-05-09
I've got a new macbook pro 15' 2011 model and wanted to try ubuntu 11.04 on it. I had some experience with triple booting with my old macbook, so I thought this would be pretty straightforward. I downloaded refit, did a partition setup as:
1st Mac OS
2nd Free space for ubuntu
3rd bootcamped win7 x64

However, the 11.04 x64 live cd just wouldn't boot. It shows "cannot find a medium containing a live system", and bootstraped into Busybox, while the cd booted just fine with my old macbook.

Anyone occurred to the same problem?:confused:

---

### Post by joshuachoo on 2011-05-10
Have you tried holding down 'C' when booting your computer with the Ubuntu Live CD inserted? This allows your Mac to boot from the CD.

---

### Post by dairyknight on 2011-05-10
Well that's what I did... which didn't work.:confused:

---

### Post by samuaz on 2011-05-10
1. install refit on osx [http://refit.sourceforge.net/](http://refit.sourceforge.net/)
2. run refit partiton analyze in utilities folder
3. insert ubuntu cd and try again
4. if not work try the ISO for mac and efi [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by god7i11a on 2011-05-10
there is a whole nother thread on this elsewhere. i ran into this and did what was recommended, which is to boot 10.04.2 FIRST, then upgrade to 10.10, then upgrade to 11.04.

it turns out the upgrades are relatively easy, there's other stuff that one has to fight with. for example, i had to roll my own kernel to get network working.

---

### Post by calamaro_one on 2011-05-13
Hi i have the same issue, Macbook Pro 3,1, i have 3 partitions:

-OSX
-UBUNTU
-WIN

I've downloaded 11.04 natty amd64+mac, and also 10.04 amd64 as recommended, then i've burned these image in 2 cds with a pc because my cd drive on mac won't burn, but i can't boot into cd on my mac and i can't start installation. I press "C" during boot and i've also tried with refit.
Could someone help me to install ubuntu on my mac?

Thnaks

---

### Post by sabatier on 2011-05-15
This is what I did to get it to work:

1. Follow instructions at [http://ubuntuforums.org/showthread.php?t=1557326]("http://ubuntuforums.org/showthread.php?t=1557326")
2. Boot Ubuntu using both usb and cd

Ubuntu installs alright, but there's no wireless :-(

---

