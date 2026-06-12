---
title: "Forgive a newbie..."
date: 2008-10-21
forum: Apple Hardware Users
---

### Post by stevenrasnick on 2008-10-21
Hello all, this is my first post, so go easy on me, willya?

I've been interested in running Linux ever since I first heard about it. The only problem was that, at the time, I was about fifteen years old, didn't have my own computer, and the family wouldn't allow me to install it on our house machine. (A Dell Inspiron desktop, if you're wondering.)

Fast forward (almost) four years later, and now I have a MacBook. My specs are, in case you guys need them:

2.4 GHz Intel Core 2 Duo
250 GB HDD
2 GB 667 MHz DDR2 SDRAM
Mac OS X v10.5.5

Using System Profiler, this is what was read as my "Model Identifier":

*Model Identifier:	MacBook4,1*

I have no idea why a comma is there and not a dot. I just copied/pasted that in.

I was backing up with Time Machine to a LaCie 500 GB external HDD, but I decided with all the stuff (I keep a lot of movies in my iTunes Library) on my MacBook's hard disk, using Time Machine wouldn't be worth only 2 backups. So, I finally decided to take the plunge. I could always buy a bigger external disk for Time Machine later.

First thing's first, I had to download the ISO disk image. After that was done, I burned the ISO to a blank CD-R using the Finder, oops! Wasted a disc... FTFD FTW!

Okay, so I looked at the documentation, and I found BurnIsoHowto. Great guide I had no idea what I was doing (obviously).

So I open up Disk Utility and burn the ISO to a blank CD-R. Open the Ubuntu installation disc (using the Finder) I just created and voila! There are a bunch of files on it, and not just Ubuntu8.10.iso.

I booted from that disc and "Hell Yeah!" The Ubuntu splash/install/live/whatever screen appears. Going good so far. I choose to run the "integrity check", and the disc was good to go.

I then boot into the "live CD" version, just to get familiar with the interface. It all looks swell so I hit "install" and start the installation process. I was going to install Ubuntu on my LaCie disk.

(I had to reformat the LaCie disk during installation, which I was anticipating.)

The installation is done and it asks me to restart the computer, so I do. When the computer boots, it boots into Mac OS X. Okay, I restart and hold Option key...

Only Macintosh HD is visible!?

How do I boot into Ubuntu? I know I've written a lot, but I just wanted to give you guys the rundown plus some background info.

Thanks for any and all assistance.

PS - I originally wanted to dual boot Mac OS X and Ubuntu on the internal HD, but I ended up screwing up and futzing up my whole Mac OS X installation. Prior to this I was using Carbon Copy Cloner for bootable backups (something Time Machine is strangely missing.) So I reinstalled Mac OS X from scratch and used my CCC backup as my Migration Assistant drive. I was up and running OS X in no time. That's when I decided to install Ubuntu on the external LaCie drive.

PPS - End of post. For serious this time. :)

---

### Post by kosumi68 on 2008-10-21
steven,

very nice post, and it seems to miss one step that is important. As you might know, there are two partition schemes at work here: GPT and MBR. As you will find in the first couple of posts in the sticky thread at the top of the page, you might need to use refit to synchronize the two tables.

Good luck!

---

### Post by stevenrasnick on 2008-10-21
Haha, that settles it then... I sometimes get impatient when stuff doesn't "just work".

I guess that's what I get for being a Mac user.

:rolleyes:

---

### Post by fballem on 2008-10-21
> **stevenrasnick said:**
> Haha, that settles it then... I sometimes get impatient when stuff doesn't "just work".

I guess that's what I get for being a Mac user.

:rolleyes:

You will need some patience - Linux is not Mac/OS or Windows. There is a learning curve.

Good luck, and welcome

---

### Post by cyberdork33 on 2008-10-21
> **stevenrasnick said:**
> Using System Profiler, this is what was read as my "Model Identifier":

*Model Identifier:	MacBook4,1*

I have no idea why a comma is there and not a dot. I just copied/pasted that in.that is normal.

> **stevenrasnick said:**
> I was going to install Ubuntu on my LaCie disk.

Can't do that. See the FAQ about installing to an external drive.

---

### Post by jwhendy on 2008-10-23
I agree with the rEFIt suggestion. Once installed you will have a boot choice each time you start up. There is also a partition tool at that menu. To partition for OS X and Linux (at least in my case) it was necessary to get the GPT (NOT MBR) tables correct, then use the rEFIt tool to sync the two.

One common mistake is to use fdisk or cfdisk to edit the MBR (typical method for PCs). This is a waste of time, as (at least for me), syncing from rEFIt will always write the GPT (unchanged with (c)fdisk) to the MBR, thereby ruining your hard work.

If this makes sense or if you are having troubles getting the partition scheme to work, give a holler and I'd be happy to share what I know. I also was successful in mounting my OS X drive on the Linux side, which is nice.

-John

---

### Post by cyberdork33 on 2008-10-23
parted is the only FOSS tool that can edit GPT. Try gparted and / or parted.

---

### Post by jwhendy on 2008-10-23
You can also use gpt from an OS X terminal. The only difficulty is that you need to boot from a disk other than the drive you are partitioning. The commands are fairly simple. To create a partition:

gpt add -b [beginning] -i [index] -s [size] -t [type] rdisk#

beginning = starting location
index = where in the partition order (2-4 for logical partitions)
size = size in SECTORS. (SECTORS * 512)/(1024^3) = Gigabytes
type = linux in this case
rdisk# = your HD (probably rdisk0)

From a Mac OS X terminal, type 'man gpt' for more info. This is how I partitioned my drive. Since you used CCC (as did I), you can just boot into the disk image you made on an external drive and do it from there.


-John

---

