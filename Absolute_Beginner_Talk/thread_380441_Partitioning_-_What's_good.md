---
title: "Partitioning - What's good?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by quicksilver1234 on 2007-03-09
Hi All,
I'm installing Ubuntu Server. No dual boot. It's all Ubuntu. i want to make a web server. I used to have Redhat Linux on the box but I want to upgrade. 

It's asking me to partition the drive. What would you all recommend?
i found these pages as a tutorial.
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p2]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p2")

i have a 40 gig HD.
I was going to do...

[B]/boot  50 MB 
/swap 1GB
/ 5 GB
/var the rest of the hard disk[/B]

I don't know what these terms mean.
1) is 50 MB a good amount for boot?
2) What's swap for and is 1 GB on a 40 Gig drive a good amount?
3) Why would I set "/" (root?) with 5 GB. Is that overkill?
and lastly...
4)  When I poked around on a old copy of Red Hat Linux, I seem to remember other folders like /etc and /bin and /home. Where do they go?  Will the installer know to put everything else in the /var folder?
5) What's the term "hda5" term mean I've see go by? Does it mean anything?

---

### Post by etank on 2007-03-09
> 1) is 50 MB a good amount for boot?I normally let / take care of the boot stuff.
> 2) What's swap for and is 1 GB on a 40 Gig drive a good amount?
Swap is physical hard drive space that is used for when you do not have enough memory. The amount used here is normally 2 x physical ram.
> 3) Why would I set "/" (root?) with 5 GB. Is that overkill?
On a server /var is probably going to be most important to you. That is where your logs will go and also the default location for web sites if it is a web server.
> 4) When I poked around on a old copy of Red Hat Linux, I seem to remember other folders like /etc and /bin and /home. Where do they go? Will the installer know to put everything else in the /var folder?
If you do not make a separate partition for them then these will just be folders in the / partition which is fine.

This is a good link to look over [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning).

---

### Post by Gannin on 2007-03-09
Me, I like to keep it simple.  I would either just have two partitions, one for root and one for swap, or I'd have three partitions... one for root, one for home, and one for swap.

---

### Post by quicksilver1234 on 2007-03-09
I found this. 
[http://ubuntuforums.org/showthread.php?t=372333](http://ubuntuforums.org/showthread.php?t=372333)

> Well, it's true that you don't 'need' these partitions. Most people follow this scheme:
One partitiion for /
One partition for swap

Is that all I need to do is Boot (5 MB), Swap (1 GB) and / (rest) ?

---

### Post by quicksilver1234 on 2007-03-09
I don't need boot?

---

### Post by neji on 2007-03-09
Specifying boot is optional, if you don't specify a location for boot, it will install it to /, which is just fine.

---

### Post by quicksilver1234 on 2007-03-09
Finding more stuff...

[http://www.tldp.org/HOWTO/Partition/]("http://www.tldp.org/HOWTO/Partition/")

> If that 40g partition is clear of data, then delete it once you get to the partitioning stage. Make sure you are deleting the correct partition. You have backed up anything you don't want to lose, right? Once that partition is gone and you have 40g of free space, create a swap partition. I usually make mine 1.5 times the amount of system memory up to a 1 gig maximum partition size. Then create the rest of the free space as a single ext3 partition. This partition is the one you want to mount at /. What is "/" you ask? Think of the filesystem as a tree. / is it's root, as a matter of fact that's what it's called. / = root All other folders branch off of the root.

---

### Post by Patrick K on 2007-03-09
Here is my suggestion. 
1gb for swap
10gb for /home
the rest for /

Having a separate /home partition means all your configuration files are preserved if you have to reinstall. Most/all apps store these files in this directory and have it on it's own partition is a good idea. 

If you want, you can use some space for a data partition. In that case go with something like this:
1gb for swap
8gb for /home
15gb for /
16gb for data (you can name this anything you want)

If you collect a lot of music and/or video files make the data partition larger and the / and /home a bit smaller. I wouldn't go under 10gb for / and under 6gb for /home. Having data and /home partitions protect them on a reinstall.

---

