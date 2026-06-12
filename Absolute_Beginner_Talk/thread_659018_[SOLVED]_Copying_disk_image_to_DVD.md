---
title: "[SOLVED] Copying disk image to DVD"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by xbhp13u on 2008-01-05
I have an image of my Win XP install created with Partimage.

Right now it is on a hard drive on my system, but I want to copy it to a DVD hopefully compressed. It is about 18 Gb.  

How can I get this onto one or two dvds?  I tried to archive through nautilus as a k7 compressed file, but it doesn't recognize my blank DVD.  I have created CDs through Nautilus before. 

Any suggestions on getting this to work or other ways of storing this image on disk instead of my hard drive?

Thanks

---

### Post by xbhp13u on 2008-01-05
Don't know where that k7 came from.:)

---

### Post by xbhp13u on 2008-01-05
Or can I just create a new image direct from partimage to the dvd?  How to mount the dvd in partimage?

---

### Post by xbhp13u on 2008-01-05
No one?

---

### Post by .nedberg on 2008-01-05
Those 18GB is probably compressed already. You could use WinRAR to split it into smaler files and burn to several DVDs (probably 5). I dont' know if 7zip will do it as I have not used that program.

---

### Post by Yoke &amp; Chung on 2008-01-05
I am not sure whether there is any "file splitter" in Linux, you can search around. If you still have the Windows partition, and do not mind re-imaging it, try Clonezilla. It will split your images into dvd writable sizes automatically.

---

### Post by Paulmd on 2008-01-05
> **xbhp13u said:**
> I have an image of my Win XP install created with Partimage.

Right now it is on a hard drive on my system, but I want to copy it to a DVD hopefully compressed. It is about 18 Gb.  

How can I get this onto one or two dvds?  I tried to archive through nautilus as a k7 compressed file, but it doesn't recognize my blank DVD.  I have created CDs through Nautilus before. 

Any suggestions on getting this to work or other ways of storing this image on disk instead of my hard drive?

Thanks

Partimage should have an option for automatically splitting the file. (the splitting part is toward the end)

[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

---

### Post by Sukarn on 2008-01-05
> **Yoke & Chung said:**
> I am not sure whether there is any "file splitter" in Linux, you can search around. If you still have the Windows partition, and do not mind re-imaging it, try Clonezilla. It will split your images into dvd writable sizes automatically.

I know hjsplit does a good job of splitting/joining files. Its available for Linux as well as Windows (dunno about Mac). It just does a binary split.

---

### Post by xbhp13u on 2008-01-07
the 18 gigs wasn't compressed.

I gave up and created a new image with partimage allowing partimage to split the file.  I was able to get it to burn to DVD that way.

Thanks for the comments..

I am having trouble now getting Partimage to find the files to restore.  I have posted that elsewhere on this forum.

---

