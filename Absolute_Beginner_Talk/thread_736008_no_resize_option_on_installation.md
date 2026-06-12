---
title: "no resize option on installation"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by mehtdosa11 on 2008-03-26
hi i've just seen this problem on the forum, and i have it myself. now i have partition magic on xp, having just put a new 250gb hard drive in my dell laptop [up from 60gb]
if i resize the main windows partition down to 50gb, should i leave the remainder as 'free space' or should i convert it to ext2 or 3?
this is my first post by the way, i'm glad to be on board.):P

---

### Post by satanic-yobbo on 2008-03-26
are you doing a fresh install of ubuntu from a live disk ?

---

### Post by housam on 2008-03-26
look at this guide :[[COLOR="Red"]_http://www.psychocats.net/ubuntu/installing_[/COLOR]]("http://www.psychocats.net/ubuntu/installing")

---

### Post by Khalis7 on 2008-03-26
> **mehtdosa11 said:**
> hi i've just seen this problem on the forum, and i have it myself. now i have partition magic on xp, having just put a new 250gb hard drive in my dell laptop [up from 60gb]
if i resize the main windows partition down to 50gb, should i leave the remainder as 'free space' or should i convert it to ext2 or 3?
this is my first post by the way, i'm glad to be on board.):P


If you would like 2 have fresh Ubuntu installation from livecd, I suggest you better format it to ext3 rather than ext2.  You see, ext2 in equivalent to fat32 and ext3 is equivalent to ntfs if i'm not mistaken and ext3 is more efficient when it comes to file storage process than what ext2 does.:KS

---

### Post by oedha on 2008-03-26
you will do on 250GB ? 
and plan to dual boot ?
i suggest
50 - ntfs - windows
the rest - ntfs - for winlin data
10 - ext3 - linux
1 - swap - swap
:)

---

