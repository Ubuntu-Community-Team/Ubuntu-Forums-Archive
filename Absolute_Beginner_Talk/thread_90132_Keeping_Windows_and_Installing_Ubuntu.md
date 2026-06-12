---
title: "Keeping Windows and Installing Ubuntu"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by nijinsky on 2005-11-14
Hi All

Well this is my first post from Sunny Scotland.

I am going ti install Linux on my Thinkpad laptop and AMD 3000 desktop.
Ubuntu had excellent reviews and I've decvided to have a go.

I cant reformat my existing windows machines (too many bits of software that I cant be bothered reinstalling on them). Also my wife has some win apps she needs.

So my really simple Q? is........

Can I download ubuntu burn the CD and install onto a winXP machine without breaking windows. IE will the CD partition the disk for linux and still keep the XP section.


I bet this is in the FAQ, but I can see it. 

Cheers
Bob

---

### Post by frodon on 2005-11-14
Yes, installing ubuntu will not destroy your windows partition, on each boot you will be asked for booting windows or ubuntu.
All you need is to keep a bit of space to install linux, the install CD will allow you to create new partitions if it's needed.

---

### Post by brim4brim on 2005-11-14
If you have unallocated space it's incredibly simple to install linux with windows.  It'll just ask do you want to use the largest contigous free space or something like that and your good to go.

---

### Post by lreyes6 on 2005-11-14
I did it like this...
[LIST]
[*]install partition magic on windows
[*]resize one partition to leave at least 3 gb of free space (i don't like to have reduced spaces jeje)
[*]then on the free space you create a swap partition and a ext3 partition (i use a 1Gb swap)
[*]then u can install ubuntu with your cd/dvd
[*]just beware when the ubuntu installation asks for the partition configuration because here is where u chose manualy your ext3 partition... you have to mark it as a root ( / ) partition and you have to flag it bootable
[*] then the installer will ask for settin the grub on your MBR and will said that windows is installed on your machine and that will put it in the os loader
[/LIST]

uff i think i talk to much jajaja any questions? just ask

---

### Post by TeeAhr1 on 2005-11-14
Why hasn't anyone told this guy to BACK IT UP yet?  Seriously, all of it.  Anything you have that you can't reinstall from a disc.  ALL OF IT.  Partitioning is always risky, and even if you do everything right, stuff can be lost/corrupted...

---

### Post by mcduck on 2005-11-14
[QUOTE=TeeAhr1]Why hasn't anyone told this guy to BACK IT UP yet?  Seriously, all of it.  Anything you have that you can't reinstall from a disc.  ALL OF IT.  Partitioning is always risky, and even if you do everything right, stuff can be lost/corrupted...[/QUOTE]yes, make a backup of all important stuff, you should do that anyway as all hard drives break, sooner or later.. If you have anything you consider important, you should always have a copy of it in CD or something.

Then you can try to let Ubuntu installer to shrink your existing windows-partition, it can do that and it worked perfectly for me. Just run defrag in windows safe mode first.

---

### Post by JurB on 2005-11-14
It's best to defrag first to.

---

### Post by nijinsky on 2005-11-14
[QUOTE=mcduck]yes, make a backup of all important stuff, you should do that anyway as all hard drives break, sooner or later.. If you have anything you consider important, you should always have a copy of it in CD or something.

Then you can try to let Ubuntu installer to shrink your existing windows-partition, it can do that and it worked perfectly for me. Just run defrag in windows safe mode first.[/QUOTE]

I have all things backed up on 2 machines (software and license codes) and on 2 sets of DVD's in different locations. I was only wondering if it was ok. If there were normal breakages I'd reformat and start afresh.

I have about 800gb of data backed up and use about 50gb at any one time (these are 500mb 3D medical images). I just wanted to save a bit of hastle reinstalling the crucial ones.

Mind you it might be a good time to rationalise on the data. :-)


I'll just put the OS on my laptop for the time being and see how I get on (no images on that).


Cheers
Bob

---

### Post by TeeAhr1 on 2005-11-14
Well, let us know how it works out!  I'm about to do the same thing (after I figure out my wireless issues), hopefully if one of us runs into problems we can meet back here!

---

