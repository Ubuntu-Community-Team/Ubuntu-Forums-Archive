---
title: "Now i've done it"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by jonwatts on 2007-11-10
So I inherited this Dell laptop and it already had Ubuntu on it, but a really old version.  So I downloaded 7.10 and after quite a bit of difficulty, managed to get all the way through the install process.  However, I discovered that the installer’s partitioner had partitioned the disk so that the old system was taking up half of the memory.  Figuring that the answer to this was to re-partition and therefore re-intall, I went about the task of manual partitioning, which I finally got through, but I think I have now severely screwed something up.  I created a “/” (2 gigs) and a swap (500 MBs), but not a /home, so didn’t end up with access to it.  Upon trying to redo the manual partition function again, the computer froze so many times that I took a break.  Now, returning to this project, I see that the computer freezes in the installed OS when I open the Add applications program.  The computer freezes when I open the install program from the boot CD.  I downloaded a new copy of 7.10, and the computer can’t even read the CD.  Everything is moving soooooo slowly, I have now spent hours sitting in front of it and waiting to see if it is going to give me any options at all.  

Oh.  Man.  What do you think?  Have I turned this computer into trash by hitting the “off” button one too many times while it was frozen in installation?  Did I get greedy and end up with nothing at all?  

Feeling awful, stupid, and awfully stupid
jon

---

### Post by TadH on 2007-11-10
since u cant reinstall from the liuve cd try this
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
its an install for no cd and this time just use the whole hd and dont partition good luck

---

### Post by jonwatts on 2007-11-10
so i actually can boot up from the first installation CD and everything seems to work, except that the computer takes over 20 minutes to open the "install" function, then freezes after the second step.  This is why I suspect that, along with the other problems, there may be something wrong with the hardware and not the installer.  After all, it worked perfectly a few days ago from this same CD.

---

### Post by taurus on 2007-11-10
What's the spec of that Dell laptop?

---

### Post by jonwatts on 2007-11-10
gosh, i don't even know how to figure that out.  if it involves booting it up and looking, i'll be back in a few hours. :)

---

### Post by Joakim Stokland on 2007-11-10
Is it an old computer? You say you used 2gigs for / and 500MB for swap. Does that mean that your hard drive has only got 2,5GB, or is that the amount you wanted to use? 

Ubuntu 7.10 System Requirements:
Ubuntu is available for PC, 64-Bit and Mac architectures. At least 256 MB of RAM is required to run the desktop install CD. Install requires at least 4 GB of disk space. 

Can you match that? If not, 7.10 is a no-go. You should stick with an older version on that laptop if you haven't got sufficient space on your hard drive.

For more information, see [http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition](http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition) and [http://www.ubuntu.org](http://www.ubuntu.org).

Good luck!
Joakim Stokland

---

### Post by jonwatts on 2007-11-10
Ok:  I had to put a bright lamp over it and speak sternly, but here is the information that I gleaned:
Dell Latitude C640
BIOS Version: A05
Mobile Pentium 4  2.00 GHz/1.20 GHz
HD: 20005 MB

is that it?

---

### Post by xtang on 2007-11-10
Your laptop specs are absolutely fine, the problem is something else.

---

### Post by jonwatts on 2007-11-10
Thanks Joakim!  (i knew a fellow from Cape Verde with that name)
But I installed 7.10 on it already, and everything worked fine except for the partitioning.  I used 2 gigs because I didn't know any better.  If I had it to do again, of course, I would use 4 gigs for "/", .5 for the swap and the rest for "/home", right?
I'm learning!  I'm just afraid my curve may not have been quick enough to keep me from turning this thing into garbage.

---

### Post by Duck2006 on 2007-11-10
> I would use 4 gigs for "/", .5 for the swap and the rest for "/home", right?

That sould work ok.

---

### Post by jonwatts on 2007-11-10
> **xtang said:**
> Your laptop specs are absolutely fine, the problem is something else.

the specs are fine meaning that there couldn't be a problem with the hardware, or meaning that the system should be able to handle installing 7.10?  

Is there a way that I can re-partition (or re-format!) the HD from recovery mode?

---

### Post by Joakim Stokland on 2007-11-10
Yeah, that should be fine, but 5 for the swap? Do you mean 5GB? You don't need more than about 500MB for swapping. The swap partition is rarely used, as a matter of fact, unless you have a very small amount of RAM.

Also, if you have the opportunity, you may want to expand your /-partition, as your installation may grow as you install more software and save stuff.
Anyway, I would recommend you pay close attention to how much free space you have got. I read somewhere about someone who got "locked out" from the system (not being able to login) because of an overfilled hard drive. As far as I can recall, this was on 7.04. It is possible that this problem won't occur in 7.10 though...

Joakim

---

### Post by jonwatts on 2007-11-10
Thats great advice, thanks.  I will expand the "/".  and I was trying to write .5, as in one half a gig, as in 500 MBs for the swap, yes.

what do you think about re-formatting from recover mode?

---

### Post by TadH on 2007-11-10
reformatting from recover mode shoukld work fine. Good luck friend

---

### Post by Joakim Stokland on 2007-11-10
Well, I don't think you will be able to change the size of the partition you're running from, so you'll have to do it from the live CD. If you use the live CD, you can start gparted to make changes to your partitions. With gparted you can change the size of partitions without formatting. If you format you will have to reinstall you know :) If you start recovery mode, you still boot from the hard drive, and you will be running from the partition you would want to change. So I think the live CD is the only way to go...

Joakim

---

### Post by Duck2006 on 2007-11-10
Or use the live CD of gparted or pmagic

---

### Post by jonwatts on 2007-11-10
> **TadH said:**
> reformatting from recover mode shoukld work fine. Good luck friend

thanks!  how do I do it?

---

### Post by Joakim Stokland on 2007-11-10
I would recommend using a gparted live CD. It is easy to use, and very powerful. 
You can download it from [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/). Burn it to a CD, and boot the computer with the disc inserted.

This guide is easy to follow, and explains exactly what you need to do:
[http://gparted-livecd.tuxfamily.org/larry/tips/gfs.htm](http://gparted-livecd.tuxfamily.org/larry/tips/gfs.htm)

Good luck!
Joakim

---

### Post by Duck2006 on 2007-11-10
> **Joakim Stokland said:**
> This guide is easy to follow, and explains exactly what you need to do:
[http://gparted-livecd.tuxfamily.org/larry/tips/gfs.htm](http://gparted-livecd.tuxfamily.org/larry/tips/gfs.htm)
Joakim

Nice guide

---

