---
title: "[SOLVED] Trying to install Xubuntu on a Windows Me."
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by dnbozss on 2007-08-01
Hi there, I'm VERY new to Linux.

I'm trying to dual boot Xubuntu on my Windows Me, but I'm having a few issues. I downloaded the ISO file, and then used a program and made a disc, but now, how do I boot from the disc on the Me? Do I have to use a floppy?

Thanks!

---

### Post by annda on 2007-08-01
you need to set the BIOS to boot from cd first. you can get to BIOS settings right after your computer boots - watch the screen closely, it will tell you to hit F2, F12 or DEL, or some other key. change boot order to boot from cd. if you have burned the iso according to instructions, you will see ubuntu soon.

---

### Post by the.phantom on 2007-08-01
you should be able to just burn the iso
and then put the cd in a cdrom and boot the computer
(it should boot from cd first)
if it doesn't boot
1. in windows right click on the disk and make sure it says ubuntu.iso
2. check your bios settings for boot priority !

NOTE how much memory do you have on your system now??
if not much then might have to try the alt version of xubuntu to install it

---

### Post by dnbozss on 2007-08-01
Um, it's called "xubuntu-7.04-desktop-i386.iso"....is that ok?

Will changing the BIOS affect my files at all? And how do I do it specifically? (Sorry, I've never really messed with OSs before.)

It has 30 gigs total, 15 gigs are taken. That's why I'm installing Xubuntu instead of Ubuntu. I heard it only takes 2-3 gigs to install....right?

---

### Post by Sayers on 2007-08-01
Xubuntu is good for hardware not harddrives.

---

### Post by skymera on 2007-08-01
i dont know about 2-3gb, seems a bit diddly.

but i know its fairly lighter weight than ubuntu

---

### Post by dnbozss on 2007-08-01
> **Sayers said:**
> Xubuntu is good for hardware not harddrives.

......I don't understand.....

---

### Post by dnbozss on 2007-08-01
God, I had it in the wrong frickin drive....I feel stupid.....

Anyway, I probably will need some more help, I've looked up partitioning and such, but I'm not completely sure of what to do.

Thanks for being willing to help!

---

### Post by dnbozss on 2007-08-01
Ok, here I am again.

So I put it in the right drive, and it booted to the Xubuntu start screen with all the options. I picked "Start or Install Ubuntu", and it went to the screen with the loading bar bouncing back and forth. After a few minutes, it changed to a progress bar (as in growing to the right). After it loaded all the way, it went to a screen where there were a bunch of screwed up pixels, then it changed to a black background, and an "X" cursor. After that, the cursor changed back into the standard windows cursor, and a bluish background. It pretty much just stayed at this screen forever.

What am I doing wrong?

---

### Post by bodhi.zazen on 2007-08-01
My guess would be too little RAM ...

You can try extending your memory by making a swap partition ...

Or you might want to look at a lighter Linux like Puppy or DSL on that box ...

---

### Post by dnbozss on 2007-08-01
I haven't done any partitioning yet, I thought that you could partition it when installing.

Too little RAM won't even let me start it up? That sucks.

How do I do swap?

---

### Post by annda on 2007-08-01
you are not doing anything wrong, it's probably an old video card that is causing trouble. try 'safe graphics mode' or whatever it's called when the cd starts. if this doesn't help, choose a vga option right for you - i believe the options are invoked by F4, but i don't have a live cd handy.

if none of the above works, you will need the alternate cd. by the way, what is your video card? and RAM?

---

### Post by mrbadboy3 on 2007-08-01
If he gets the Alternate he can't dualboot though can he? I used to have the Alternate because I downloaded it by accident but discarded it and downloaded the liveCD instead because I thought the other one couldn't dual-boot :\

---

### Post by bodhi.zazen on 2007-08-01
> **he who eats pie said:**
> I haven't done any partitioning yet, I thought that you could partition it when installing.

Too little RAM won't even let me start it up? That sucks.

How do I do swap?

> **annda said:**
> you are not doing anything wrong, it's probably an old video card that is causing trouble. try 'safe graphics mode' or whatever it's called when the cd starts. if this doesn't help, choose a vga option right for you - i believe the options are invoked by F4, but i don't have a live cd handy.

if none of the above works, you will need the alternate cd. by the way, what is your video card? and RAM?

If the (good) advice of annda fails ...

Try downloading the gparted cd and using it to do your partitioning .

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

Make a swap partition size = RAM X2 (256 Mb)

Make a 5-10 Gb partition for xubuntu (root or /), format it as ext3.

---

### Post by dnbozss on 2007-08-02
This is not my strong suit, so I'm just going to post everything under the My Computer properties.

Millennia RS 2110.
GenuineIntel
Intel(r) Celeron(tm) processor
128.0MB of RAM


Hope that has some useful information...

And I tried the 'safe graphics' thing...it didn't work.

---

### Post by ugm6hr on 2007-08-02
> **he who eats pie said:**
> This is not my strong suit, so I'm just going to post everything under the My Computer properties.

Millennia RS 2110.
GenuineIntel
Intel(r) Celeron(tm) processor
128.0MB of RAM


Hope that has some useful information...

And I tried the 'safe graphics' thing...it didn't work.

Look at the System Requirements here: [http://www.xubuntu.org/get#requirements](http://www.xubuntu.org/get#requirements)

As stated - your system is absolutely on the border of being capable of running the LiveCD.  If you have a shared memory allocation to your graphics card - it won't work.  A linux-swap may make it run, but you will not be able to install from the LiveCD.

If you want to try out the LiveCD before installing, look at the Gparted link from bodhi.zazen - and boot from that to create a linux-swap partition (around 256MB), then try again with the Xubuntu LiveCD (possibly with Safe Mode too).

Once you're convinced by how great it is (and how much better than Windows ME), use the AlternateCD to install.

---

### Post by dnbozss on 2007-08-02
But with the AlternateCD, I am unable to dual-boot, correct?

I tried it out on my XP, and loved it.

So even though the graphics card might not be able to handle the live CD, it would be able to handle just running xubuntu?

No doubt I will use Linux 10x more than ME, I just don't want to lose my ME for good. I don't have the backup disk to reinstall, so this is it.

But if worse comes to worse, I would readilly toss ME out the windows for Xubuntu. I just want to make sure that my comp can run it ok, or else I'll be stuck without ME or Linux.

---

### Post by annda on 2007-08-02
for all i know, alternate cd does nothing like voluntarily erasing the whole hdd and making dual boot impossible... but i haven't used it myself so here's the expert talking:
[http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm)

---

### Post by bodhi.zazen on 2007-08-02
> **he who eats pie said:**
> But with the AlternateCD, I am unable to dual-boot, correct?

Not sure where you got that idea. The alternate CD is how Ubuntu used to be installed, before the current desktop CD (an believe it or not used to be considered user friendly :lolflag: )

At any rate, you should be just fine as long as you understand partitioning and do not overwrite the wrong partition.

Still, partitioning and installing an OS is an undertaking and data loss is always possible.

You should back up important data, regardless of whether you choose to install Ubuntu or not ...

---

### Post by jgrabham on 2007-08-02
> **skymera said:**
> i dont know about 2-3gb, seems a bit diddly.

but i know its fairly lighter weight than ubuntu

Dont worry about that, I have xubuntu on my Laptop with a 2GB HDD!!

---

### Post by ugm6hr on 2007-08-02
> **he who eats pie said:**
> But with the AlternateCD, I am unable to dual-boot, correct?


Not true.  Just to be safe - use GParted to shrink Me partition to make room for Xubuntu, and create 2 additional primary partitions (at least 2GB ext3 for **/** and about 256MB for linux-swap).

Then use AlternateCD - just point the installer to the correctly created new partitions, and it won't write over Me.

This is not 100% safe, because resizing partitions always has some risk of data loss, but I've never had a problem with GParted.

---

### Post by dnbozss on 2007-08-02
Ok, I think I get how to make new partitions, but what do you mean by "2 additional primary partitions (at least 2GB ext3 for / and about 256MB for linux-swap)"? What would I type or do?

---

### Post by bodhi.zazen on 2007-08-02
> **he who eats pie said:**
> Ok, I think I get how to make new partitions, but what do you mean by "2 additional primary partitions (at least 2GB ext3 for / and about 256MB for linux-swap)"? What would I type or do?

LOL

In order to install Ubuntu you will need to :

1. resize (make smaller) your windows partition.

2. Make 2 additional partitions. 

1 = swap. Size = RAM X2, 1 Gb max format this partition as "linux-swap"

2 = / = the Ubuntu equivalent of C:\, the place you install Ubuntu. Size = 5 Gb (some claim to be able to do it in 2 Gb) format this partition as ext3

When you install, chose manual partitioning, mount the swap partition as swap. Mount the / partition as /

Install form alternate CD: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by dnbozss on 2007-08-03
Ok, I'm having issues. I downloaded the Alternate CD iso file, and created a CD with it the exact same way as the first one I tried, but it's not working. I am using a CD-RW though, as opposed to before I used a CD-R. My ME won't boot from it. I even erased it and burnt it again.

Can you not use a CD-RW or something? I was hoping to not keep using CD-Rs.

---

### Post by ugm6hr on 2007-08-04
> **he who eats pie said:**
> Can you not use a CD-RW or something? I was hoping to not keep using CD-Rs.

Rewritable media is not recommended, as far as I know.

---

### Post by dnbozss on 2007-08-04
Well, I still had a little trouble with it, but my Linux savvy friend helped me out and I'm now running Xubuntu! (And I got rid of ME all together.)

---

### Post by ugm6hr on 2007-08-05
> **he who eats pie said:**
> Well, I still had a little trouble with it, but my Linux savvy friend helped me out and I'm now running Xubuntu! (And I got rid of ME all together.)

Welcome to Xubuntu.  I think you are better off without ME - it's pretty useless!  If you have any problems - just ask here again.

---

### Post by heavenlybastard on 2007-11-25
hi guys bit confused,i have a gaming computer and yes its very powerfull but if lets say you install xubuntu linux on your pc will it over-ride windows and you'll just be able to use linux!!!OR can you switch back and forth when ever you want!!!please help!!!

---

### Post by ugm6hr on 2007-11-25
> **heavenlybastard said:**
> hi guys bit confused,i have a gaming computer and yes its very powerfull but if lets say you install xubuntu linux on your pc will it over-ride windows and you'll just be able to use linux!!!OR can you switch back and forth when ever you want!!!please help!!!

Using both is what is referred to as dual-boot.

There's plenty of info around about how to do it - including in this thread.

---

