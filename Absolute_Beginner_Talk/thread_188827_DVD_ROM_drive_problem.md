---
title: "DVD ROM drive problem"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by learning on 2006-06-04
o.k., I have a cdrw drive as primary that works fine.  The DVD drive, I have set as slave.  system seems to recognize it in file manager.  However, it will not mount anything.  Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


I'm guessing it should be listed in there somewhere?  What should I do?
One more caveat:  I am not 100% sure dvd drive works anyway, pulled it from an old computer that was sitting in closet last 3 years.  So, if it is not a configuration problem, and I should just go buy a new one, will any brand work or are there compatablility problems with some types?

Thanks!

---

### Post by Perfect Storm on 2006-06-04
Exactly the same trouble I have, I havn't figure it out how to solve it. I've reported the bug back in beta and I have seen other with same problems.

---

### Post by learning on 2006-06-04
Thanks for letting me know it isn't just me!

So it is some sort of os problem, most likely?  New one would not change anything?

---

### Post by Perfect Storm on 2006-06-04
Do you know which brand you have? So we can compare?

I have Liteon DVD-rom LTD163

and

PHILIPS DVD+RW-D128

One with similar problem : [http://ubuntuforums.org/showthread.php?t=168444](http://ubuntuforums.org/showthread.php?t=168444)

---

### Post by learning on 2006-06-04
My primary CD-RW drive is an HP CD-Writer Plus (came stock in hp pavilion xt953, which is mostly what the computer I am using at home is)

I am not sure of the DVD ROM drive.  It came out of an E-Machines E 550.

---

### Post by cyracks on 2006-06-04
To see if cd-rom is recognized during the boot
```

dmesg |grep hd

``` and than check 
```

cat /proc/ide/hdX/model

``` where X depends on the results from the first command.

btw: I think that almost all cd/dvd rom drives are supported under linux.

---

### Post by learning on 2006-06-04
Here is output:

jason@jason-desktop:~$ dmesg dmesg |grep hd
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294675.642000]     ide0: BM-DMA at 0x10a0-0x10a7, BIOS settings: hda:DMA, hdb:pio
[4294675.642000]     ide1: BM-DMA at 0x10a8-0x10af, BIOS settings: hdc:pio, hdd:pio
[4294675.906000] hda: SAMSUNG SV3002H, ATA DISK drive
[4294676.884000] hdc: CR-48X5TE, ATAPI CD/DVD-ROM drive
[4294677.598000] hdd: SAMSUNG DVD-ROM SD-608, ATAPI CD/DVD-ROM drive
[4294677.666000] hda: max request size: 128KiB
[4294677.695000] hda: 58711968 sectors (30060 MB), CHS=58246/16/63, UDMA(66)
[4294677.696000] hda: cache flushes supported
[4294677.697000]  hda: hda1 hda2 hda3
[4294677.729000] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[4294677.735000] hdd: ATAPI 32X DVD-ROM drive, 512kB Cache, DMA
[4294698.475000] Adding 2008116k swap on /dev/hda3.  Priority:-1 extents:1 across:2008116k
[4294698.632000] EXT3 FS on hda1, internal journal
[4294704.112000] EXT3 FS on hda2, internal journal
[4383804.659000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
jason@jason-desktop:~$ cat /proc/ide/hdd/model
SAMSUNG DVD-ROM SD-608

Must be a Samsung SD-608!

So, I guess my problem is: it is recognized properly and just won't mount anything.  Not even audio cd's.

Is that pretty much your problem, Artificial Intelligence?
From the thread you posted, it looked like the other person (I thought) said they could play some audio.

---

### Post by learning on 2006-06-04
I am wondering, given the outputs...

Shouldn't the dvd drive be in fstab, like the cd drive?
Could I add a line for it?
Anyone know what such a line should look like?

Something like:

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

except it should be hdd and then whatver dvd drive info is?

---

### Post by cyracks on 2006-06-04
[quote=learning]
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
[/quote] Create /media/cdrom1 and then insert into /etc/fstab

```

/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0

``` and then 
```

sudo mount /dev/hdd

```

---

### Post by learning on 2006-06-04
How do I Create /media/cdrom1?

I edited fstab as you suggested but here is my output:

jason@jason-desktop:~$ sudo mount /dev/hdd
mount: mount point /media/cdrom1 does not exist
jason@jason-desktop:~$ sudo mount /dev/hdd
mount: mount point /media/cdrom1 does not exist
jason@jason-desktop:~$


Then... soundjuicer came up and it recognized the cd, and got the tracklisting!
It even played for about 4 seconds.  But when I minimized the window to post that it worked it locked up. (got not responding error and had to force quit)

Looks like progress though!

But, should it be cdrom1 I am trying to create?  It is a dvd drive.

---

### Post by uzi09 on 2006-06-04
/media/cdrom1
is just a directory:

```

sudo mkdir /media/cdrom1

```

although this should probably be there, or perhaps another cdromX
where X can be anything
cdrom, cdrom0, cdrom1, cdrom2
depending on how many cdroms u have and how the os sets it up

---

### Post by learning on 2006-06-04
Now it seems to be working fine, as far as playing c.d.'s goes!

But still does nothing with a dvd :(

could someone with a working dvd rom post their fstab output?  doesn't the udf,iso9660 paramter just set it for cd's?

---

### Post by cyracks on 2006-06-04
[quote=learning]How do I Create /media/cdrom1?

But, should it be cdrom1 I am trying to create?  It is a dvd drive.
[/quote]
```

sudo mkdir /media/cdrom1

```
It doesn't matter what is the name of the directory you can choose the name you wish.

---

### Post by cyracks on 2006-06-04
This is my line for DVD/RW

/dev/hdc   /media/cdrom0    udf,iso9660 user,noauto     0       0

---

### Post by learning on 2006-06-04
well, i guess it's iso for both...

At least it plays c.d.'s now!  That's more than it was doing.  I think I'll go up to the store and buy a linux mag with a data dvd in it and see if it will read that.  Right now all I have here are movie dvd's to test with.

---

### Post by cyracks on 2006-06-04
To be able to play DVD movies you have to install **libdvdcss2,**** libdvdnav4 **and[B] libdvdread3
[/B]
**Edit:** Don't know how outdated the document is but for more info check *[http://ubuntuguide.org/]("http://ubuntuguide.org/")*

---

### Post by learning on 2006-06-04
Back from store!

I had the libraries installed already (just double-checked).

When I try to mount the dvd (one from magazine or a movie), it tells me no medium found. 
It will mount/play c.d.'s though.

I guess it is just a bug, as A.I. suggested.

I'm farther along than was though!

If anyone has any other ideas for me to try, I'm willing!

Thanks!

---

### Post by cyracks on 2006-06-05
How old is you DVD drive ? Do you try to mount DVD-(+) disk while DVD drive only supports +(-) disks ?

---

### Post by learning on 2006-06-05
The DVD drive is about 6 years old I think.  I don't understand what you mean by + (-) or (-)+ discs.

I have used it to play store bought dvd's (movies) in the past in other computer.  It could be drive is bad, but if it were, it doesn't make sense (to me) that it would play c.d.'s and not dvd's.  Could it be a bad drive and still play c.d.'s?

---

### Post by cyracks on 2006-06-05
If you could play the same movie on an old computer with the same DVD then probably dvd rom is bad. Try to test it in windows if you can.

---

### Post by Kid G on 2006-06-06
My DVD drive won't mount on the desktop but I can access the drive when I browse to /media/cdrom0. My DVD-RW drive does mount on the desktop though. Neither drive shows up when  I use *sudo fdisk -l* in the terminal? :???:

---

### Post by learning on 2006-06-16
Just so you know what happened (I hate when I read posts and don't know if problem got fixed or not)...

I didn't have a windows machine around I could stick the old dvd rom drive in, but I kind of guessed from all we did, iand what it was doing, it was just broken.

So, I bought a new dvd rw drive = Lite On model: SHW-160P6S10C for $49.99 from Wal-Mart.

Plugged it in, set it as master and set old cdrw drive as slave.  Removed old dvd rom drive and threw back in closet until I can test it.  Everything automounts to desktop.

Turned on computer and everything now works great!

---

### Post by acronymsical on 2007-09-09
I had a similar problem with a LITEON DVD-ROM LTD163. I switched it with my other DVD (RW) drive within the same computer, and set the appropriate master/slave switches on each. The Lite-on is now set as the slave and works fine. Perhaps there is a weak point in the circuitry that drives the cable.

---

