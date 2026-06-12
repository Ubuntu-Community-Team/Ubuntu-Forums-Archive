---
title: "anyway to speed up kubuntu?"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-26
Running dapper kubuntu with latest version of kde whenever i start an app or click to open a file it's painfully slow..It took 45 secs just to open a folder..
The machine specs are 2.0ghz celeron with 512 megs of memory

---

### Post by muep on 2006-06-26
According to your machine's specs it seems that something is broken. Even my old Celeron 600 MHz with 128 MBs of ram can beat that.

I don't know the solution to the problem,but anyway.

Good luck solving it. Somebody will probably help :)

---

### Post by nalmeth on 2006-06-26
What kind of video card do you have?

---

### Post by acht on 2006-06-26
[QUOTE=nalmeth]What kind of video card do you have?[/QUOTE]

i really dont think a video card has anything to do with it.  i would just see if a reinstall fixes anything or even try xubuntu.  you might even want to get 1 gb of ram. do you have a swap file?

---

### Post by coolclassic on 2006-06-26
Have you dma switched on on your hard drive?

sudo hdparm /dev/hd?

to check

---

### Post by nalmeth on 2006-06-26
Installing NVIDIA (for example) drivers might make things faster *if *the problem lies with X
As said, this is unusal performance for those specs.

---

### Post by WADemosthenes on 2006-06-26
If you're going to re-install, which I do often :P, might as well try something: # hdparm -d1 -c1 -m16 /dev/hda from: [http://www.zdnet.com.au/insight/hardware/soa/_Speed_up_Linux_with_hdparm/0,39023759,39179216,00.htm](http://www.zdnet.com.au/insight/hardware/soa/_Speed_up_Linux_with_hdparm/0,39023759,39179216,00.htm).  Enables dma, multcount, and IO suport.  All speed up the hard drive, but are risky as I understand.

PS, xubuntu on my pentium II 365 mhz laptop doesn't take that long to open a folder, I rather think there is something quite wrong with your machine, I would re-install, but I'm a noob and re-install everytime anything goes wrong :D.

---

### Post by lime4x4 on 2006-06-26
dma is enabled i have a 1.4 gig swap file
the drive was partitoned like this
partition1 gigs
partition2 1kb
partition31.4 gig swap file 
don't ask me why i have 1kb partition cause i don't know...lol
Also i installed ubuntu on another hard drive within this computer and that is really fast..And have already installed kubuntu 5 times always with the same results

---

