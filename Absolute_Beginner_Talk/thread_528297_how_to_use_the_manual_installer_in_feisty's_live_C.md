---
title: "how to use the manual installer in feisty's live CD?"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-08-17
I need to use manual partition option during install and I need detailed instructions.

XP is already on this 80 GB hard drive, and I want to add Feisty.

Background story: I want to have a dual boot setup so option one, "Guided use of entire disk" is out. "Guided re-size" option does not come up, and "Guided use the largest length of contiguous space" gets an error message saying not enough space (because currently XP partition is taking up the whole drive.)

What install partition is asking now: I need to "specify a partition for the root system file (mount point "/") with a min size of 2 GB, and a swap partition of at least 256MB"

Note I would like to downsize ntfs to about 20GB, leaving me about 55GB for Ubuntu.

Here is what the partition menu in install says:
/dev/sda1 fat16 /media/sda1 41MB(size)/ 33MB(used)
/dev/sda2 ntfs /media/sda2  76264MB/8500MB
/dev/sda3 fat32 /media/sda3 3684MB/3200MB
free space 8MB

Earlier I thought I would try and shrink the XP partition before using the Feisty installer, by using gparted or qtparted, but couldn't get either one to be accepted. gparted said there was no proper video driver for the gui, and qtparted just wouldn't start at the command prompt. So I cannot take advantage of the "Guided use of the largest contiguous space option" as I cannot create any free space. 

That only leaves me with the manual option. Can someone tell me how to use it? Thanks!

---

### Post by MenZa on 2007-08-17
Well, you'd have to resize the NTFS drive *before* installing it. Try downlading the GParted LiveCD ([link](http://gparted.sourceforge.net/livecd.php))

---

### Post by swarup on 2007-08-17
> **MenZa said:**
> Well, you'd have to resize the NTFS drive *before* installing it. Try downlading the GParted LiveCD ([link](http://gparted.sourceforge.net/livecd.php))

Thank you for your concerned suggestion. The problem is that I already downloaded a GParted LiveCD for that very purpose earlier today, and I can't get it to work. GParted boots up, but then tells me the gui can't function, and I have to do "Forcevideo" with vesa. I did that at the appropriate prompts, but it would not accept it and so I could not use gparted. I tried it for around two hours earlier today, and couldn't get it to work. It's probably some real simple mistake-- but when you don't know what the mistake is, then it sure seems difficult!

---

### Post by annda on 2007-08-17
please defragment your XP drive AT LEAST ONCE before you attempt to resize the partition - windows just scatters fileparts all over the disk, which sometimes makes resizing impossible.

after that you should be able to choose "Guided use the largest length of contiguous space" option. if not, post back with the exact error message.

good luck!

---

### Post by swarup on 2007-08-17
> **annda said:**
> please defragment your XP drive AT LEAST ONCE before you attempt to resize the partition - windows just scatters fileparts all over the disk, which sometimes makes resizing impossible.

after that you should be able to choose "Guided use the largest length of contiguous space" option. if not, post back with the exact error message.

good luck!

Actually, I JUST did a format of the entire drive and reloaded XP. So I don't think that is the problem. What I found is that the "Guided use the largest length of contiguous space" option is only for if you have already shrunk the XP partition and you have free unallocated space you've thereby created. Then with this option the Feisty installer will see that space and use it.

So unfortunately, by this my problem is not solved.

---

### Post by annda on 2007-08-17
if you have a fresh install (meaning not much to lose), go for manual. **edit** the xp partition to shrink it and in the freed up space **add** one for swap (maybe 1GB) and one for feisty root (mounted as "/")

does that work for you?

---

### Post by mikewhatever on 2007-08-17
The following guide [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing) shows how to manually partition with pictures and explanations. It's already been suggested by oilchangeguy in post #2 of one of the other threads you started on the subject. [http://ubuntuforums.org/showthread.php?t=528100](http://ubuntuforums.org/showthread.php?t=528100)
Have you looked at it? If yes, which part do you not understand?

Another option I thought of is using gparted from Ubuntu cd before clicking the Install icon. You can find it under System>Administration>Gnome Partition Editor. Hope that gives you no video problems.

---

### Post by AlexenderReez on 2007-08-17
alternative you can have[ parted magic live cd]("http://news.softpedia.com/news/Parted-Magic-1-8-Available-Now-61073.shtml") to manage to partition :)

---

### Post by swarup on 2007-08-17
> **annda said:**
> if you have a fresh install (meaning not much to lose), go for manual. **edit** the xp partition to shrink it and in the freed up space **add** one for swap (maybe 1GB) and one for feisty root (mounted as "/")

does that work for you?

I do not know what you mean by "go for manual", and "edit the xp partition". What should I tool should I use to get it done. That is what I've struggling to get done all day.

GParted I can't get to run, qtparted I can't get to run, the Feisty CD doesn't offer an option to shrink the XP partition. How am I to "manually" get it done. Any ideas?

---

