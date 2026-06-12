---
title: "Best Ways To Decrease Boot Times?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-05-23
Inspired by the boot time poll thread, I decided to look into this further;

What are some ways to increase EDIT: DECREASE boot times? In "newb." language, if possible!

Another member posted this;
> tune2fs 1.40-WIP (14-Nov-2006)
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
        [-i interval[d|m|w]] [-j] [-J journal_options]
        [-l] [-s sparse_flag] [-m reserved_blocks_percent]
        [-o [^]mount_options[,...]] [-r reserved_blocks_count]
        [-u user] [-C mount_count] [-L volume_label] [-M last_mounted_dir]
        [-O [^]feature[,...]] [-T last_check_time] [-U UUID] device
tr@tr-desktop:~$ 


but I haven't the slightest idea what to do with it...
Being new, I hate to go in & start poking around for fear of really goofing things up!+

---

### Post by chamberlain2006 on 2007-05-23
May I ask why you would ever need to do this?

---

### Post by discmaster on 2007-05-23
> May I ask why you would ever need to do this?Well, you're askin' the wrong guy, because I am a "wet behind the ears" newbie! I just thought that it would be nice to decrease my boot times to 1/2 a minute, like many others are boasting.

I have a fairly "fast" pc, & 1 min. + seems excessive compared to other on here...

---

### Post by chamberlain2006 on 2007-05-23
Your post says you want to "increase" the boot time.  I'm not sure how you would do so.  You could google it, though.

---

### Post by discmaster on 2007-05-23
> Your post says you want to "increase" the boot time. I'm not sure how you would do so OOPS! Well that was a slip-up wasn't it! I'll work on changing the thread title! LOL :D

---

### Post by discmaster on 2007-05-24
What are good tweaks for a "newbie" to do to decrease boot time in Ubuntu 7.04? In doing research, I understand that attempting some of this can "break" things; is there a "safe" way to go about it for a new linux user? :)

---

### Post by lazyart on 2007-05-24
I keep my boot times low by leaving the machine running.

---

### Post by starcraft.man on 2007-05-24
> **lazyart said:**
> I keep my boot times low by leaving the machine running.

I agree, just don't reboot/turn off and you never have to wait for it to start up. If your running beryl though, I would make sure to switch to the Metacity window manager, Beryl has the odd problem of spontaneously freezing sometimes when I leave it doing something for more than an hour or so... not sure why, maybe its just me...

---

### Post by discmaster on 2007-05-24
I know a lot of folks run their pc's 24/7 these days, but I am from the "old school", I guess; I shut mine down at the end of the day. Having a boot time of over a minute seems excessive to me, esp. when I see some users are able to boot in 30 seconds!

I did find [this,]("http://doc.gwos.org/index.php/Speed_up_boot") but as with much of the info. found on the web, it is dated (4/06). I wasn't sure if I should try some of the tips there, since it is "older" info?

---

### Post by discmaster on 2007-05-24
Little help?

Can I use this to get started?
> sudo apt-get update sudo apt-get install sysv-rc-conf

Since I use T-bird mail, I removed all traces of evolution mail via. synaptic, in hope of trimming things down a bit, but as I said, since I am very new to "all things linux", I am leery to do too much without guidance.

I've already been thru a few messy installs/partitions, etc., & I am not anxious to relive all that again...

---

### Post by discmaster on 2007-05-24
> Since I use T-bird mail, I removed all traces of evolution mail via. synaptic, in hope of trimming things down a bit, but as I said, since I am very new to "all things linux", I am leery to do too much without guidance.

An update here - Don't do what I just did! Leave evo-mail as it is! I had to start another thread on how to recover, because after I removed this, the pc wouldn't boot!

All is well now, aftere re-installing evo-mail, but there were a few trepidatous moments!

Still working on a faster boot, though... :)

---

### Post by FakeOutdoorsman on 2007-08-21
I just decreased my Feisty boot time from 38 seconds to 33 seconds with just a few changes.  I don't leave my computer on 24/7 for multiple reasons and got tired of waiting.  First of all, I started with [Bootchart]("http://www.bootchart.org/"), which will watch your boot and create a nice graphic of the result.

```

sudo aptitude install bootchart

```

Or you can install via Synaptic.  After you boot you can find the Bootchart results in /var/log/bootchart.  You can see a bunch of examples at the [Bootchart - show off your boot speed!]("http://ubuntuforums.org/showthread.php?t=241604") thread.

With my new boot graphic I noticed that usplash was taking awhile.  It's the nice Ubuntu logo and loading bar that shows up while your computer loads.  I didn't need that so I removed it:

1. Make a backup of your GRUB configuration:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

```

2. Edit out "splash" from the kernel line (you might have to remove "silent" too):
```

gksudo gedit /boot/grub/menu.lst

```

3. Reboot!

There's a start.  I've made some [other changes]("http://ubuntuforums.org/showpost.php?p=1715900&postcount=2"), but I'm running a lightweight custom Ubuntu install that cut out some bloat and loads in 33 seconds.  Not lightning fast, but fast enough for me.

---

### Post by defenestratos on 2007-08-22
> **lazyart said:**
> I keep my boot times low by leaving the machine running. 

That is not very energy efficient, especially for us users who don't compute all day.

---

### Post by WakkiTabakki on 2007-08-22
This applies to Feisty...

Using the bootchart app, you can find out which process thats taking the time at start-up  (once you've booted there'll be a png-image of the boot process in /var/log/bootchart). I noticed that s40networking sits and blocks the process for about 30 secs or so. Probably waiting for a time-out. Since this is on a laptop w/ wireless, and a password is required to get access, so that process will *always* timeout, so why start it!?!
1. Disable the network at boot
```
mv /etc/rcS.d/S40networking /etc/rcS.d/DISABLED_S40networking
```

2. Instruct the boot process to do what it can in parallel
In the file /etc/init.d/rc change the line
```
Concurrency=none
```
to
```
Concurrency=shell
```


I'm not sure, but I think thats all I've done and now my laptop takes 30 secs flat from grub to GDM!

Some more info on tweaking, and quite possibly wrecking, your system :o
[http://www.xsol.se/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/](http://www.xsol.se/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/)

Good luck
/N

---

### Post by kakao on 2007-09-15
> **WakkiTabakki said:**
> Some more info on tweaking, and quite possibly wrecking, your system :o
[http://www.xsol.se/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/](http://www.xsol.se/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/)


An update on the link as I just found out. It's now here:
[http://www.xlntsolution.com/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/](http://www.xlntsolution.com/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/)

Another good one is this:
[http://www.fooishbar.org/blog//tech/ubuntu/fastBootMiniBoF-2004-12-09-13-45.html](http://www.fooishbar.org/blog//tech/ubuntu/fastBootMiniBoF-2004-12-09-13-45.html)

Cheers.

---

### Post by Kopachris on 2008-03-27
Sorry to dig up this thread, it was the result of a google search, but I was thinking of putting a small computer (no case, just mboard, cpu, ram, floppy, hd, and cd) in my locker at school.  Since I only have 5 minutes to get to class (about 2 minutes is needed for me to get between classes), I could use a laptop battery as a power source, but it would still need to boot very quickly.  I take it I should install Damn Small Linux for a starter, but I still would like it to boot in about the same amount of time as my printer (about 10 sec) so I can do stuff between classes, like make a to do list.  Appearances is not a limiting factor, btw.  I'd have the IDE HD have the OS on it, then connect a USB hard drive (I have a 120GB one with X-Plane on it) at the end of each day to upload my data.  If there really was no other way, I could just put LFS on it, and save everything to a floppy.  I'd quickly run out of floppy disks, though.  An alternative: How long do you think it would take Damn Small to boot from a 256MB flash drive?

On a semi-related note: I could put a mATX motherboard with a floppy in my toaster and run LFS from a floppy disk on it. :D

---

