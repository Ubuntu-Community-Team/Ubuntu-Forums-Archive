---
title: "Help with repartition"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by dalee on 2006-03-15
Hi,

I'm trying to repartion my harddrive (ext3) to free some extra space to play in. I've booted the Breezy Live cd and run gparted. At first it told me that it was unable to do the repartion because of disk activity. I finally figured out that the swap was being used. So I issued :sudo swapoff -a.

Now it runs, but it still won't do the repartition and I'm not getting any error this time to help me out.

I wonder, is this because when I originally did my install I just used one big partition instead of doing it right:rolleyes: . I really don't want to do a re-install because I've got things working just the way I want them to.

Thanks!
dalee

---

### Post by mlind on 2006-03-15
do you mean you have one big ext3 partition (that is the root?) and you want
to slice it a bit?

All I know that you shouldn't mount any partitions, definetly not the / (root) partition,
if it's one you're modifying.

I've done partitioning using Ubuntu's install CD, just going to Expert mode and
skipping to the part where wizard allows you to partition your drives.

---

### Post by dalee on 2006-03-15
Hi,

Yeah, it's one big ext3 partition. I just want to split it in half. 

When I right click on properties of hda in gparted it says that the drive isn't mounted. But, I'm sure that the Live CD is using the swap on the drive. Hence, the swapoff -a. I thought that, that should kill everything. Perhaps it's not?

I've even tried several other LiveCd's, PCLinuxOS, Slax, and even Madrivia. All behave the same.

dalee

---

### Post by mlind on 2006-03-16
I have no experience with liveCD's, but I've used Ubuntu install CD.
It has partition wizard (parted) too. Tried with that?

---

### Post by Sef on 2006-03-16
It seems that you need to have your drive mounted.  Not sure of the command offhand....will check and see if I can find it, unless someone else posts it first.

---

### Post by dalee on 2006-03-16
Hi,

Sorry, been doing that whole "work" thing. It really cuts into the important stuff sometimes;) .

I've not tried the install CD. Been thinking about it though. What worries me about doing that is I don't have a good feel for the partitioner on Ubuntu. Kinda silly I suppose, since I'm willing to give my drive a good whack with gparted:) .

Sef, from the reading I've done, and the first errors I got trying to use gparted, my understanding was that the drive had to be unmounted. But I readily admit that I might very well have it backwards.

Thanks!
dalee

---

### Post by plors on 2006-03-17
I advise you use the [gparted livecd]("http://gparted.sourceforge.net/livecd.php"). That way you don't have to worry about mounted partitions and/or swap at all.

---

### Post by dalee on 2006-03-17
Hi,

Thanks to all who helped me! I found the problem. There was a 50mb partition at the end of the drive that I didn't see until I resized the window!

I have no clue what it was doing there, or why it was made. But once I deleted it, gparted had no problem doing the resize.

So far everything seems to be ok. If I run into anything that gives me fits, I'll be back with more questions:mrgreen: !

You guys are great!
Thanks!
dalee

---

