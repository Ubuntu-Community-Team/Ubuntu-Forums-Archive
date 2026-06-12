---
title: "[SOLVED] Resizing Ubuntu partition"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by -gabe-noob- on 2008-01-04
I've been playing around with gparted (not the wisest thing to do I know) and I freed up 30 gigs of space that I would like to add to my ubuntu partition which is now 94% full... can somebody help me

(if your wondering where 30 gigs of free space suddenly appeared, just know wine covers alll my needs for certain applications for a certain os)

---

### Post by Skidpad on 2008-01-04
You cannot resize a mounted partition, so an easy thing to do would be to download the GParted livecd, boot from it, and then resize.    By booting into the GParted livecd your Ubuntu partition will remain unmounted during boot, and then you can simply adjust the partition size from within the GParted GUI.

---

### Post by -gabe-noob- on 2008-01-04
a gparted live cd? But, how?

---

### Post by eternicode on 2008-01-04
o_0  [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Or, if you have the Ubuntu LiveCD, it also has GParted.

---

### Post by -gabe-noob- on 2008-01-04
yes I am an idiot and thannks, I'll mark this as solved

---

### Post by Skidpad on 2008-01-05
Right here: [GParted]("http://gparted.sourceforge.net/download.php")

You select the partition you want to resize, and then (been a while since I did mine, so I am going from memory here...) goto Partition>Resize, and you can drag it to whatever size you want.  

Check out the screenshots on the link I posted above.

---

### Post by bodhi.zazen on 2008-01-05
> **-gabe-noob- said:**
> a gparted live cd? But, how?

you can run gparted from your Ubuntu CD or the Gparted live cd :

GParted:
	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

---

### Post by Skidpad on 2008-01-05
No sweat!  Here's a link showing it in action: [Resize NTFS Partition]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

---

### Post by -gabe-noob- on 2008-01-05
While we are all here, anyone wanna point me to a guide for getting kiba dock on ubuntu 7.1 

Edit: at the forum staff guy, hows hardy heron shaping up? what type of functionality improvements is it on gutsy? I'm thinking of trying it.

---

