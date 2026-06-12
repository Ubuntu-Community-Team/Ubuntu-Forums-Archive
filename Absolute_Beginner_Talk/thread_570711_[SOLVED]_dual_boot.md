---
title: "[SOLVED] dual boot?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by m005k on 2007-10-08
Does Ubuntu have a install choice for making a dual boot system?  I'm running windows XP. I have tried some live cds and would like to know how to make a dual boot before I start.

Mike

---

### Post by overdrank on 2007-10-08
> **m005k said:**
> Does Ubuntu have a install choice for making a dual boot system?  I'm running windows XP. I have tried some live cds and would like to know how to make a dual boot before I start.

Mike

Hi and this link may help
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Good luck!

---

### Post by Dr Small on 2007-10-08
When you run the installer, at the partioning section, you will be given the choice to:

1.) Install Ubuntu on the entire disc 
2.) To resize the XP partition to make a second partition for Ubuntu
3.) To manually setup the partitions

So yes, you can dual-boot.

Dr Small

---

### Post by bodhi.zazen on 2007-10-08
Why stop at dual booting ?

Soo many OS, Soo little time ...

---

### Post by Dr Small on 2007-10-08
yeah, that is why I have an entire hard drive dedicated to virtualbox :p

---

### Post by om1 on 2007-10-08
let us know if you need anymore help.... that should answer your question but if it doesn't let us know

---

### Post by bumanie on 2007-10-08
When i set up a dual boot $MS with ubuntu, I found it easier to partition the hard drive with an open source program called g-parted prior to using the live cd for an install. With g-parted I shrunk the windows partition and set up the swap file and formatted the rest of the hard drive to ubuntu's ext3 file system. 
G-parted can be obtained from this link: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) 
It is a live cd also, therefore it can be used on any pc that has the bios set to boot from cdrom. G-parted can partition most, if not all, known file types.

---

### Post by om1 on 2007-10-08
gpart is on the ubuntu live cd

---

### Post by bumanie on 2007-10-08
> **om1 said:**
> gpart is on the ubuntu live cd

I realise gparted is on the live cd. However, when one has never installed ubuntu before, some find it easier to prepare the hard drive in advance. Just an alternative method that gets the same result in the end.

---

### Post by rsambuca on 2007-10-08
> **bumanie said:**
> I realise gparted is on the live cd. However, when one has never installed ubuntu before, some find it easier to prepare the hard drive in advance. Just an alternative method that gets the same result in the end.

I think what om1 was referring to is that the actual gparted program is on the liveCD.  Thus you can prepare the hard drive in advance without downloading and burning another cd.  I believe it is under System - Administration, or someplace close to that.

---

