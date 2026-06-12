---
title: "File system recommended for dual boot with XP"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by hito1 on 2007-06-27
Hi, there, I'm going to format my ubuntu partition to install feisty fawn, I'm currently using the ext3 file system, but, since I'll have the opportunity to choose again, I was wondering if others are better. 

Any suggestions or precautions? Speed is the most decisive factor to me.

Thanks a lot. :)

---

### Post by Scunizi on 2007-06-27
Ext3 is what you want to use if you need to exchange data between XP and Feisty.  Otherwise, if you're running SATA drives, I use ReiserFS..

---

### Post by Wynne G Oldman on 2007-06-27
> **Scunizi said:**
> Ext3 is what you want to use if you need to exchange data between XP and Feisty.  Otherwise, if you're running SATA drives, I use ReiserFS..Hi, I saw you post and wondered why you prefer ReiserFS to EXT3 for SATA drives? The reason I ask this is because I have SATA drives. Please be easy on me, I'm a newbie.;)

---

### Post by Scunizi on 2007-06-28
They are both a journaled file system.  ReiserFS is reported to be a little faster.  It also won't do an automatic check after "x" number of boots or reboots.  With my SATA's the automatic check took forever.

---

### Post by aquavitae on 2007-06-28
> **Scunizi said:**
> Ext3 is what you want to use if you need to exchange data between XP and Feisty. 

Why?  XP won't read ext3 file systems, so why is it better for data exchange?  I thought the only way to do it was through a FAT system (or since the new drivers, NTFS).

---

### Post by Nythain on 2007-06-28
there are windows drivers that allow read and write to ext3 filesystems... i forget what they are called but they do exist

---

### Post by speaker219 on 2007-06-28
> **aquavitae said:**
> Why?  XP won't read ext3 file systems, so why is it better for data exchange?  I thought the only way to do it was through a FAT system (or since the new drivers, NTFS).

Windows can read/write smoothly to ext2/ext3 file systems by downloading this:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Nigmah on 2007-06-28
[COLOR=DarkOrange][B]By default xp doesn't read ext3. You can get it to read and write to it(i believe it is beta or something though) 
but both xp and linux read fat32, the only downside of fat32 i know of(im sure hteres more that i don't know of though) Thats why i've got my external drive and my shared both having fat32 as their filesystem.
[/B][/COLOR]

---

### Post by speaker219 on 2007-06-28
> **Nigmah said:**
> [COLOR=DarkOrange][B]By default xp doesn't read ext3. You can get it to read and write to it(i believe it is beta or something though) 
but both xp and linux read fat32, the only downside of fat32 i know of(im sure hteres more that i don't know of though) Thats why i've got my external drive and my shared both having fat32 as their filesystem.
[/B][/COLOR]
Like i said, for ext2 and ext3 seamless support in windows:
[http://fs-driver.org/](http://fs-driver.org/)

---

### Post by aquavitae on 2007-06-28
I didn't know about ext support in xp - that's great! 

I can think of plenty of problems with fat32, e.g. you have to defragment it, can't use files larger than 2G, etc...

---

### Post by Scunizi on 2007-06-28
Bottom line is, you can't get it all right the first time.. Install, learn, have fun.  It's a whole different world here in linux land.  I made the conversion a little over a year ago and have enjoyed the switch.  That's not to say it wasn't painfull at times.  I am/was considered a power user in WinXX and still fix other people's machines.  Linux was very foreign to me and the learning curve was steep.  But the climb is good! :popcorn:

---

### Post by hito1 on 2007-06-28
> **Scunizi said:**
> Bottom line is, you can't get it all right the first time.. Install, learn, have fun.  It's a whole different world here in linux land.  I made the conversion a little over a year ago and have enjoyed the switch.  That's not to say it wasn't painfull at times.  I am/was considered a power user in WinXX and still fix other people's machines.  Linux was very foreign to me and the learning curve was steep.  But the climb is good! :popcorn:
I actually use Ubuntu for a quite time now. I'm still a newbie, though, and I think I'l be one for ever. I'm going to install Ubuntu feisty right now, after a long time with dapper and edgy and about 3 days with Kubuntu Feisty (I didn't like it much).

But yeah, I agree with everything you've said. :)

I'm sticking with ext3, btw, I'll experiment with other file systems when I have faster and newer hard drives.

---

