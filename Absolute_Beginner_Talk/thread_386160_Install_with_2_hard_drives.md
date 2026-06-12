---
title: "Install with 2 hard drives"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by OldDog11 on 2007-03-16
I am building a new PC and planning to install Ubuntu, no dual booting, this
will be a completely windows free zone. This will be my first Ubuntu install
therefore would someone please advise me on partitioning. I am fitting two
brand new 160 Gb hard drives with the intention of putting the OS and all
programs onto drive 1 and all of my data etc onto drive 2.

I am considering partitioning drive 1 with / and /swap and making drive 2
/home but will this be wasting most of my drive 1, if so what else do you
suggest. I am not sure where the Ubuntu application software is  installed,
in / or /home? Also, should I put a /swap file onto drive 2 as well?

I had thought that keeping all of my data and personal files on a separate
drive was a good idea but now that large drives are common place is that a
sensible idea or would I be just as well off to put some of my data files
onto a separate partition on drive 1 with the rest on drive 2? I doubt if I
can have a /home on both drives therefore should I have e.g. a
/home/document, /home/music, /home/photos etc and not have a /home at all?
The other option could be to have a separate partition for each user, I am
aware that I can only have up to 4 partitions on each drive.

I have read that with large drives it's a good idea to create several
logical partitions /boot, /temp, /var, /usr etc but I believe in keeping
things simple, especially as I am trying to wean myself off of windows XP.
Are these extra partitions a good idea or are they just "going over the top"
I am finding the different way of working a little daunting at present but
I'm determined to get there so any help will be appreciated.

Thanks in advance

---

### Post by jbayone on 2007-03-16
I don't think you can set the home directory differently for different users. Not sure though.  I'd recommend using the second drive for /home and the first one for the root and swap.

---

### Post by OldDog11 on 2007-03-16
should I put /swap on the second drive as well as the first?

---

### Post by jbayone on 2007-03-16
Nah, I don't think you can have two swap partitions anyway.  Just use it on the first drive.

---

### Post by bodhi.zazen on 2007-03-16
You only need one swap, you may or may not get much performance increase by putting it on the second drive ...

Size if swap = ram X 2 , max 1 gb

If you have 1 + Gb ram you likely will not use swap at all :p

---

### Post by jbayone on 2007-03-16
Sorry, I checked it out and yes, you can have two swap partitions.

---

### Post by cavemanf16 on 2007-03-16
I too purchased 2 SATA 160GB drives to put Ubuntu on in my current system about 4 months ago. I still have approximately 120GB leftover on IDE drives in my system with WinXP and my favorite games, but I have successfully transitioned entirely to Ubuntu as my main "productivity" platform of choice. (I think if you give it 3-4 months of usage you'll also find it better than Windows.)

I have been fiddling with Linux since about 1998, and although it's true that having multiple partitions can be a good architectural/design choice at install time; I have found it to be not that big of a deal in Ubuntu and other modern Linux distro's. Here's the rundown of what I remember my system looking like when I installed:

Drive 1, /dev/sda:
10GB /boot (Maybe? I can't quite remember... maybe it was only 1-2GB for /boot)
2GB /swap (no, I didn't really need this much since I have 1GB of RAM, but I have the space on disk, so why not, just in case?)
rest of drive 1 for /

Drive 2, /dev/sdb:
160GB /home

That's it. I tried to keep it simple and leave plenty of space for all areas. For instance, I gave a HUGE amount of space to /boot (usually most forum posts only recommend 50-100MB) simply because I wanted to have enough space to drop a simplified linux kernel if things ever got really whacked on / and I needed to do heavy duty repairs. Although that was still overkill on my part since you can easily get bootable recovery CD's from anywhere on the 'net.

I gave such a huge amount of space for / because I wanted to be able to install a ridiculous amount of programs at any one time because I like to try all kinds of different programs out until I settle on one I like, and that can sometimes take me months of "playing" until I settle on just one program for a particular task.  I also didn't want to ever be bothered with running out of disk space for the main Ubuntu system and all the programs I use.

Lastly, I don't have a gigantic collection of mp3's or videos like some people do, so 160GB of space all for /home is more than enough for me.  My wife has her own iMac with a 500GB HDD, so I won't be running out of storage space anytime soon.  If you have a TON of media type files maybe it'd be more useful for you to setup a specific partition just for that on the second drive, and make a much smaller partition (40GB maybe?) on drive 1 instead.

Oh yeah, one last thing: make sure /home is ext3 (preferably), or jfs if you really have a reason to make it jfs.  Both are journaling filesystems, and that's a very good thing for keeping your data safer from disk and read/write software errors. I also made my / partition ext3 for data integrity sake.

Hope this helps.

---

### Post by OldDog11 on 2007-03-16
Where are the programs installed, in / or /home?

---

### Post by jbayone on 2007-03-16
/opt holds all the software that you've installed that isn't by default

---

### Post by bodhi.zazen on 2007-03-16
> **jbayone said:**
> Sorry, I checked it out and yes, you can have two swap partitions.

I never said you could not. As far as I now you can have more then two, but I do not know what the point would be.

You can also make a swap a file in / and not on a separate partition as well ...

I only mean OldDog11 only needs one swap partition, I do not see the need for one on each HD, which was the question asked :lolflag:

---

### Post by jbayone on 2007-03-16
I wasn't negating anything you said.  I had said earlier in the thread that you couldn't have more than one swap.

---

