---
title: "Resizing existing partitions"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by lalji on 2006-09-13
I messed up the partition sizing during the original installation and need to fix it. Mine is a dual boot system with Windows XP and Ubuntu. I need to expand the XP partition (NTFS) and decrease the Ubuntu partition (ext3). Currently the existing partitions use up my entire 60GB hard drive (there is also of course a little swap partition). 

What tool can do this for me, or do I need more than one? I tried qtparted from Ubuntu and it recognizes no devices, telling me that I might not be root (I am - there's only one user). I tried qtparted from the system restore CD and it can resize the NTFS partition but not the ext3 partition. Any tips?

(I've only been using ubuntu for 2 days, so don't expect too much!)

---

### Post by xyz on 2006-09-13
Try this one for a nice clear explanation:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
A tool:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

 Documentation: [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by wieman01 on 2006-09-14
If you want to do it under Windows simply use Partition Magic. I personally think this is one of the best tools available. GParted comes second.

---

### Post by lalji on 2006-09-15
Thank you for your suggestions. Unfortunately, Partition Magic is a proprietary software and the free trials available (although tantalizingly suggestive) won't do the trick. 

GParted was initially promising (at least I got it to run!), but I realized that I can't achieve what I want from a hard drive based application and need to run a Live CD instead. While running the live cd the process failed (i.e. ejected to the command prompt without starting the GParted app) with the following error message:

Fatal Server Error: Caught signal 8

this came during part of the installation under the heading backtrace, after the following command: /lib/libc.so.6 (__libc_stat_man+0x9e)
There was also the message "X10:fatal IO error 104 (connection reset by peer)." 

I burned a new copy of Live CD and tried again, with the same result. I also tried booting as a lowmem computer - no difference. Also with some different options for screen depth and resolution - also didn't work.

Any ideas why GParted won't run?

My last ditch option might be to reinstall Ubuntu via the live CD and use the partition client that comes up then, but I'm not sure that it will expand the NTFS partition and decrease the ext3 partition as I need to do.

Thanks for your help.

---

### Post by xyz on 2006-09-15
How about Gparted Boot CD? No need for another Live CD,Partition Magic or anything else.
It did wonders for me. See what you think:
[http://digg.com/software/GParted_Live_CD,_like_Partition_Magic_for_free](http://digg.com/software/GParted_Live_CD,_like_Partition_Magic_for_free)

---

### Post by moore.bryan on 2006-09-15
> **xyz said:**
> How about Gparted Boot CD? No need for another Live CD,Partition Magic or anything else.
It did wonders for me. See what you think:
[http://digg.com/software/GParted_Live_CD,_like_Partition_Magic_for_free](http://digg.com/software/GParted_Live_CD,_like_Partition_Magic_for_free)
[I]i second the motion for the gparted livecd; it is amazing.
here's another link for it: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[/I]

---

### Post by lalji on 2006-09-15
Sorry for being unclear, but the problems I was describing (server error etc) happened when trying to use the GParted Live CD (from [http://gparted.sourceforge.net/livecd.php)](http://gparted.sourceforge.net/livecd.php)).

---

### Post by xyz on 2006-09-15
> **lalji said:**
> Sorry for being unclear, but the problems I was describing (server error etc) happened when trying to use the GParted Live CD (from [http://gparted.sourceforge.net/livecd.php)](http://gparted.sourceforge.net/livecd.php)).
Now I am not sure I understood you correctly. I do get an Error 404 when I click on your link.
Let me try to get this right: you're trying to get GParted Live CD,right?
I've been talking about GParted Boot CD!
We'll get there somehow!

---

### Post by lalji on 2006-09-15
here's what I've been using - it's the GParted live cd, not the boot. The link I originally pasted in acquired an end parenthesis which messed up the link.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Now, what's all this about a GParted boot CD? I haven't tried that one yet but would like to!

---

### Post by moore.bryan on 2006-09-15
*i put the livecd in at boot and it loads the program...*

---

### Post by lalji on 2006-09-17
I finally achieved what I intended - expanding sda1 (NTFS), shrinking sda2 (ext3) - and gparted was the main tool I used, but via the ubuntu live cd rather than the specifically gparted one which never worked for me. 

Unfortunately, I had to first delete the sda2 partition because (I found) it is not possible to move the beginning of a partition. After deleting sda2, I expanded sda1 to the desired size, then created a new sda2 partition on which to re-install ubuntu. Not pretty, but I got the result I needed.

Thanks all for your help.

---

### Post by xyz on 2006-09-17
Glad to see you got what you wanted!
Lots of ways to get to the same place, aren't there?
GParted Live, Gparteed Boot, Ubuntu Live ...and so on!
Happy going!

---

