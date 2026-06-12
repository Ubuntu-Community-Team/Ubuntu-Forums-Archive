---
title: "a music player question..."
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by josh air balloon on 2007-10-30
I apologize if this has been answered before, but...

I was wondering why neither amarok nor rythmbox is reading my m4a music files.  I dual-booted vista and ubuntu today (im new to linux altogether, ive had it less than 24 hours, and have found everything else very easy to use, access, and understand besides this).  Ive tried to google the 2 error messages ive got are "error loading media, there is no available decoder" and something about "mpeg-4 aac decoder plug-in".

Yet when I look for the plug-in I cant find it.  Maybe I am just not looking in the right place?  Any help would be wonderful.

Also, is there a way I can transfer 2+ gigs of music from vista to ubuntu without having to burn it on to disks, or using a flash drive?

---

### Post by hyper_ch on 2007-10-30
are the m4a files stored on your vista partition and is the vista partition Read-Only?

---

### Post by ohmycar on 2007-10-30
What I was able to do was actually drag and drop my songs from my vista partition to my ubuntu desktop. When I looked at the "computer" page in ubuntu, I could access the partition that had vista installed in it and I just navigated through it to find my songs and dragged them over to my ubuntu desktop. :)

---

### Post by josh air balloon on 2007-10-30
Im sure they are in my vista partition, but im new, so how exactly do i acces my vista partion from ubuntu?

---

### Post by mali2297 on 2007-10-30
Try installing the **ubuntu-restricted-extras** package, from [Community Docs]("https://help.ubuntu.com/community/RestrictedFormats"):
> 
Synaptic
    * Go to Applications &#8594; Add/Remove...
    * Set Show: to All available applications
    *  Search for ubuntu-restricted-extras and install it. 


Note however that you won't be able to play encrypted .m4p files, like ones bought from Itunes music store.

---

### Post by mali2297 on 2007-10-30
> **josh air balloon said:**
> Im sure they are in my vista partition, but im new, so how exactly do i acces my vista partion from ubuntu?

Check here:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by zvacet on 2007-10-30
**synaptic<search box>type mpeg-4 aac decoder** and install them all.

---

