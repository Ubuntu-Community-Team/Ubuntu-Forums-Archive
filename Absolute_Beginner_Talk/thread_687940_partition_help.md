---
title: "partition help"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by sneakmonkey on 2008-02-04
Hello, I'm still relatively new to linux but I think I'm getting the hang of it but I have a question regarding partitions. During the installation I blindly set up my partitions without thinking ahead and fudged them up.

I'm using Gparted to try and fix it and I wanted to ask if I could possibly add the unallocated space to hda7 partition because I simply just don't have enough space available.

[IMG]http://i227.photobucket.com/albums/dd79/sterkadoo/Untitled.jpg[/IMG]

Heres a screenshot just to show what my partition setup looks like currently.

---

### Post by logos34 on 2008-02-04
You'll need the Gparted Live CD:
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by oedha on 2008-02-04
you still have 49gig as unallocated.....
can you right click on hda7 and choose move or resize ?
or...you can delete one of your swap to be added do hda7.....
you only need 1 swap and it about 1.5-twice of your ram size

but,....i suggest you not to do anything with hda1 since it was a warning flag there

---

### Post by sneakmonkey on 2008-02-04
Ahh, il have to give that a try when i get hold of a cd burner, thanks a bunch :)

---

### Post by sneakmonkey on 2008-02-04
> **oedha said:**
> you still have 49gig as unallocated.....
can you right click on hda7 and choose move or resize ?
or...you can delete one of your swap to be added do hda7.....
you only need 1 swap and it about 1.5-twice of your ram size

but,....i suggest you not to do anything with hda1 since it was a warning flag there

yeah, hda1 is my windows partition i dont want to touch that

but it wont let me resize or move hda7 and im guessing because they are in use

so maybe if i can resize it running off of a different partition or just try the live cd thing

---

### Post by logos34 on 2008-02-04
> **sneakmonkey said:**
> Ahh, il have to give that a try when i get hold of a cd burner, thanks a bunch :)

what about the LiveUSB version?

---

### Post by Boelcke on 2008-02-04
Yes, when you boot from the GParted live cd, you'll be able to modify those partitions.  Kill all those swaps, make hd7 larger, and then re-make a swap at the end.  I usually do 2x my memory, on the hope that one day I'll add some.

---

### Post by sneakmonkey on 2008-02-04
> **logos34 said:**
> what about the LiveUSB version?

ohh, i missed that.

il give that a try now, heh thanks again

---

### Post by sneakmonkey on 2008-02-04
i wasnt sure if i should post another thread for this but it seemed like a small question
about the live usb thing, i have no idea how to do this even with the instructions, im just stumped.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

-either download this file in the directory where you have downloaded the iso file,
untar it (tar -xjf set_usb.sh.tar.bz2), become root and run it (sh set_usb.sh)

I can follow maybe 15% of that, the rest im clueless on what to do

---

### Post by logos34 on 2008-02-04
Download the gparted live cd .iso ([gparted-livecd-0.3.4-11.iso  ~52 MB]("http://download.tuxfamily.org/gpartedlive/"))

into you /home dir or desktop

then download [this file ]("http://gparted.sourceforge.net/livecd/set_usb.sh.tar.bz2")

then open a terminal and run 

**tar -xjf** set_usb.sh.tar.bz2  
(results in file 'set_usb.sh')

OR 

right-click on the file and 'extract'

then run command as root:

**sudo sh set_usb.sh**

---

### Post by sneakmonkey on 2008-02-04
> **logos34 said:**
> Download the gparted live cd .iso ([gparted-livecd-0.3.4-11.iso  ~52 MB]("http://download.tuxfamily.org/gpartedlive/"))

into you /home dir or desktop

then download [this file ]("http://gparted.sourceforge.net/livecd/set_usb.sh.tar.bz2")

then open a terminal and run 

**tar -xjf** set_usb.sh.tar.bz2  
(results in file 'set_usb.sh')

OR 

right-click on the file and 'extract'

then run command as root:

**sudo sh set_usb.sh**

ok i have both the iso and the other thing on my desktop, and i think i did everything right (the other file now reads as "set_usb.sh" like you said)

is something supposed to happen or do i just boot off of my flash drive?

---

### Post by bodhi.zazen on 2008-02-05
I think this is getting more complicated then it needs to be.

You can not resize a partition if it is in use or mounted, thus you need to boot a live CD.

You can boot the Ubuntu desktop (live cd) and run gparted from there.

In general, swap = RAM X 2 , max 1 Gb or max = RAM on Laptops if you use sleep or suspend.

---

### Post by logos34 on 2008-02-05
> **bodhi.zazen said:**
> I think this is getting more complicated then it needs to be.

You can not resize a partition if it is in use or mounted, thus you need to boot a live CD.

You can boot the Ubuntu desktop (live cd) and run gparted from there.

In general, swap = RAM X 2 , max 1 Gb or max = RAM on Laptops if you use sleep or suspend.

Yes, but the problem is that the version of Gparted on the ubuntu live cd won't resize partitions from the left border/to the left.  At least that's my experience with primary partitions

---

### Post by bodhi.zazen on 2008-02-05
> **logos34 said:**
> Yes, but the problem is that the version of Gparted on the ubuntu live cd won't resize partitions from the left border/to the left.  At least that's my experience with primary partitions

It will as of 7.10. Earlier versions will not work.

---

### Post by logos34 on 2008-02-05
> **bodhi.zazen said:**
> It will as of 7.10. Earlier versions will not work.

yep, you're right--they finally updated gparted to version 0.3.3.  I would have sworn it was still using 0.2.6.  How did that slip by me?  

sneakmonkey,

sorry for wasting your time.  You could have just used gparted on the ubuntu live cd after all.

---

