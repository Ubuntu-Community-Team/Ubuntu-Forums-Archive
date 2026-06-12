---
title: "Removed Windows - Let's Clean Up The Disk!"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by swheatley on 2007-05-07
Hi Everyone,

I have been using Feisty for over a month now on my laptop with no issues. Today I decided to blow away my Windows partition (backed up the last of the documents, but I've barely touched it in a month anyway, so did I really need them? :) ) Now that Windows is gone, I'd like to reclaim that empty space. However, the space was (obviously) at the beginning of the drive from my original Windows install. I wanted to shift all my partitions to the beginning of the disk so that I could extend my main partition to use the remaining space. However, I couldn't seem to figure out how to do this with either QtParted or GParted when I booted from the only handy LiveCD I had (a fairly recent Knoppix).

Does anybody have any ideas how to do this?  :confused: I would prefer not to leave it as a separate partition as I already have a fairly large partition that I'm using right now (30gig) and the remaining 40 gig wouldn't be quite enough for my home directory.

---

### Post by MikeDX on 2007-05-07
You should be able to run gparted either from a live cd or from with ubuntu itself, however, these programs do need root permissions, so from a terminal, try:

gksudo qtparted

This should bring up the main qtparted window, where you can select your main hd (probably /dev/hda), and resize your partitions as needed. dont forget to File->Commit when you are done!

---

### Post by rocknrolf77 on 2007-05-07
I think it's possible to resize your linux partition. Be careful with resizing partitions. Don't forget to backup :)

---

### Post by swheatley on 2007-05-07
Ok, so the dirty secret is that I'm not an absolute beginner. I've been using Linux off and on since 2001, but I'm really trying to make the effort to ditch Windows at home.

@MikeDX: I did run both front-ends to parted as su. It worked fine to delete the partition, but I don't seem to be able to move it.

---

### Post by MikeDX on 2007-05-08
> **swheatley said:**
> Ok, so the dirty secret is that I'm not an absolute beginner. I've been using Linux off and on since 2001, but I'm really trying to make the effort to ditch Windows at home.

:lolflag: 
> 
@MikeDX: I did run both front-ends to parted as su. It worked fine to delete the partition, but I don't seem to be able to move it.

I'd cheat

get a bootable cdrom with partition magic or whatnot..  then resize the partitions there. 

As for ditching windows, we successfully did that a few months ago however we did start with a clean install including partitioning..

Sadly though, we do still need windows for some things (not mission critical).. but the family shared pc comes in handy for that!

---

