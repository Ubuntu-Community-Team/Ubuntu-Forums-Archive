---
title: "Ubuntu live cd ... can you format the HD?"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by dcmginc on 2006-11-22
I have this laptop that's in a real mess with problems and software. I've been searching for the last few days of ways to be able to get this laptop loaded so I could format the hard drive and then go about reinstalling everything. 

I found a site that gave me instructions on creating a Ubuntu Live CD. I downloaded the 700MB file... got it burned to a CD and put it in the computer... everything loaded up just fine without all the problems that I was having. Is there anyway to format the C drive on this computer now that I've got Ubuntu loaded off a CD? I did find one spot that showed the partitions... and in my excitement and clicking I think I deleted them, but I doubt that will solve my problems.

Any information is greatly appreciated since I'm very new to Linux.

Tim

---

### Post by richiewrt on 2006-11-22
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

just use this disk and you can delete partitions and start over and all kinds of wonderful stuff, then install whatever os you like.

---

### Post by CatKiller on 2006-11-22
> **dcmginc said:**
> I did find one spot that showed the partitions... and in my excitement and clicking I think I deleted them, but I doubt that will solve my problems.

Sure it will. If you've already deleted the partitions, you might as well install Ubuntu.

Welcome to the community.

:D

---

### Post by dcmginc on 2006-11-22
Ok... so I went ahead and downloaded that one richiewrt posted. It pretty much looks the same as what I have except it doesn't have all the bells and whistles. 

So I'm back where I was... In front of me right now is a screen that has 

Partition: unallocated
Filesystem: unallocated
Size: 18.63 GiB
Used -
Unused - 
Flags -

Is there a step that I'm missing? I tried to reboot the laptop without the CD and I'm still getting a bunch of crap trying to load.

Any other bits of help you guys can offer?

---

### Post by 56phil on 2006-11-22
Now that you have no partitions defined, you may as well click install and try Ubuntu like CatKiller said. It won't cost you anything but time and you may enjoy Ubuntu as much as I do. 

The install will create two partitions. One for swap, about twice the size of your RAM, and one for everything else. The install process will take about thirty minutes and you can surf the web at the same time. Welcome and enjoy.:)

---

### Post by dcmginc on 2006-11-22
I didn't see an install option.

---

### Post by CatKiller on 2006-11-22
> Is there a step that I'm missing?

Yes - installing an operating system!

The GParted cd that you've downloaded has the newest version of GParted on it, which will allow you to create partitions (now - otherwise you could have done other things with the existing ones).

The Ubuntu live cd has a slightly older version of the GParted partitioning tool on it. There are a handful of things that that version can't do, but that disk has the added ability of being able to run and/or install an operating system. Try it out for a while.

You've possibly still got a Windows boot-loader in the [MBR]("http://en.wikipedia.org/wiki/MBR") of your disk, but that will go as soon as you install an operating system on the disk.

So, you've wiped the disk. What was it you were **trying** to do, and maybe someone will be able to tell you how to do it.

EDIT: I'm slow tonight.

> I didn't see an install option.

It should be on the desktop when you've booted from the Ubuntu disk.

---

### Post by dcmginc on 2006-11-22
Ok... I just switched back over to the original CD with ubuntu on it and surprise surprise... that icon was right in front of me :)

I'm installing it now...

---

### Post by 56phil on 2006-11-22
Great! Be sure to tell us how it went.

---

### Post by dcmginc on 2006-11-22
> **56phil said:**
> Great! Be sure to tell us how it went.

Well rather then sitting and watching the progress meter I thought I'd go and do some other things around the house. When I came back quite some time later it told me I had to reboot. I clicked the button and waited... next thing I know there is a username box in front of me... "CRAP... what did I choose"?  haha... same thing for the password, but I finally remembered. Time for bed... its been a long day when I can't remember what I picked for my username and password hour(s) earlier.

Thanks for the help everyone!!

Tim

---

### Post by 56phil on 2006-11-22
Get some sleep ... if you can. I was running on two to four hours of sleep right after I discovered Ubuntu.

---

