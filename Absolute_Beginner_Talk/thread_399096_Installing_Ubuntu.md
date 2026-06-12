---
title: "Installing Ubuntu"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Wotching on 2007-04-01
I have a 250gb drive, partitioned into a 70gb NFTS (w/ windows installed on it), 130gb NFTS, and 30gb NFTS.  I went into Ubuntu install, and told it to install on the 30gb partition.  Now it says I have to pick 2 partitions, one for "/" root and one for swap.  How big, out of 30 gb, should each of those be?

---

### Post by BarfBag on 2007-04-01
Swap 1 GB, root the rest.

---

### Post by FakeOutdoorsman on 2007-04-01
Swap is usually 1.5 to 2 times the amount of RAM.  [Psychocats]("http://www.psychocats.net/ubuntu/index") has a great installation tutorial page that you should read first and also a section on partition planning.

[Installing Ubuntu]("http://www.psychocats.net/ubuntu/installing")
[Partitioning Windows and Ubuntu]("http://www.psychocats.net/ubuntu/partitioning")

Some people also make a seperate /home partition as well so it is easier to reinstall the OS or upgrade.

[Move /home to it&#8217;s own partition]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

---

### Post by Wotching on 2007-04-01
How big should that extra /Home partition be?

---

### Post by Maestro23 on 2007-04-01
> **Wotching said:**
> How big should that extra /Home partition be?

As big as you want.  This should be where all your personal files go (mp3, pics, vid files, etc...)

---

### Post by Wotching on 2007-04-01
Ahh, gotcha.  Well, then, how big does the rest of it have to be?  The "/" one.

---

### Post by FakeOutdoorsman on 2007-04-01
My "/" (excluding home, swap, media, and cdrom) takes up about 5 gigs right now, but mine may be bloated or small compared to others.  You would probably be safe with 9 gigs, but I'm guessing.  You really don't want to have root run out of space.

I think the Kubuntu installer requires a minimum root partition >2 GB.

In other words, I don't know.  Good question.

---

