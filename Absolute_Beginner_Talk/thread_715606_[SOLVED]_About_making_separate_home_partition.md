---
title: "[SOLVED] About making separate home partition"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Wikzo on 2008-03-05
Hey,

I am going to install Ubuntu 7.10 on my new Znote 3215W laptop in a few weeks. I have read about making a separate home partition, but I am unsure of how to do it. I have found some guides, but they all seem too complicated for me using the alternative installer CD and that kind of stuff.

Is there any way to make the partition using Gparted in the live mode of Ubuntu? I know how to make partitions, but I don't know how to tell my system "This is a partition for the home partition".

My coming laptop has a 80 HDD. I am thinking of doing this:

/root = 10-15 GB
/swap = 1-2 GB
/home = 60-70 GB

---

### Post by logos34 on 2008-03-05
Here's a[ step-by-step]("http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html") for Feisty install with separate /home.  (live cd)

Nothing's changed in Gutsy.

---

### Post by oedha on 2008-03-05
you can use gparted livecd from [http://gparted.sourceforge.net](http://gparted.sourceforge.net)
or
boot from livecd and focus on step 4 ( partition step )
choose manual....and you can set your partition just like what you wanted......( including assignment as something )

---

### Post by Wikzo on 2008-03-05
Thank you. This picture was all I needed to know.

[img]http://www.easy-ubuntu-linux.com/images/install-new-partition-mount-pts.png[/img]

Two things:

- Does it matter which order I make my partitions in?
Like **/swap, /root and /home** or the opposite **/home, /root and /swap**?

- If/when I want to install a new Ubuntu version (let's say 8.04), how do I install it over my old one and keeping the home partition?

---

### Post by logos34 on 2008-03-05
in any order you like.


> "[Identify your /home partition. Set its mount point as '/home' and make sure that Format is not ticked.]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion?highlight=%28upgrade%29")"

---

### Post by indytim on 2008-03-05
As Logo34 mentioned, it doesn't matter.  A lot of people like to keep the less "volitile" partitions at the front (like /swap).  This might make it a bit easier once you get into growth and start re-sizing things (like your /home).

IndyTim

---

### Post by saguinus on 2008-03-05
The SWAP partition should be as much as the amount of your RAM i think.
If your RAM is 2GB or more, you need a smaller than 2GB swap partition.


sag

---

### Post by zvacet on 2008-03-05
I prefer to install in this order** root home swap** but like others say you can do it anyway you like it.

---

