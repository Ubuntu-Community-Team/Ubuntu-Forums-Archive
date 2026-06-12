---
title: "trying to rescue data"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by morganpatrick on 2006-05-11
hello,

I'll make it quick. I'm trying to rescue data off of an ntfs partition that i resized and damaged. I already used ddrescue to get an img file of the partition but it won't mount because it can't find a primary boot sector. what do i do?

Secondly, I have an ext3 partition that reformatted accidentally and was wondering how easy it is to 'deformat' or make the wiped files accessible again, or if that data is just unretrievable.

NOTE: I'm rescuing a **seperate, secondary** hard drive so i shouldn't have to boot into a cd.

Thanks

---

### Post by Sef on 2006-05-11
This can read and write to NTFS files:

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

### Post by morganpatrick on 2006-05-11
Thanks, but that didn't help. Like I said I'm rescuing a seperate hard drive so I shoulnd't need a boot disk, and I did just boot up trinity and it was command-line and over my head. I've used ddrescue to get an img file I can't mount so maybe we can start there.

---

### Post by aysiu on 2006-05-11
You can try mounting the drive:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by morganpatrick on 2006-05-11
Thanks for the reply. I can't actually mount it because it is clipped -- that is to say, i repartitioned it down too far and clipped about 20g of data. So now I'm trying to bail out the remaining 80g but it won't mount because it can't find a primary boot sector. I damaged the filesystem.

---

### Post by aysiu on 2006-05-11
I don't know how you can see the files if you can't mount it.

I know you've tried *ddrescue*. Have you looked into *mondo*?

**Edit**: Never mind. *mondo* appears to be a backup "rescue" utility.

---

### Post by morganpatrick on 2006-05-12
I did try mondo and hit a dead end.

However, I'm now in knoppix, and it seems like this is supposed to be good for rescuing data, but I'm brand new to linux and dont really get ubuntu yet, much less knoppix. 

i can see all my partitions with qtparted right now, but i dont see any option for doing anything with my broken ntfs partition. it doesn't recognize it as ntfs, i have no idea how to restore the boot sector.

---

### Post by morganpatrick on 2006-05-12
by the way ddrescue worked, in a sense. it made me an img file. I just don't know how to restore the primary boot sector in order to mount it. the img file is a large fragment of an ntfs partition.

---

### Post by aysiu on 2006-05-12
[Recovering NTFS Boot Sector on NTFS Partitions](http://support.microsoft.com/?kbid=153973)

---

### Post by morganpatrick on 2006-05-12
Do I even need to add a primary boot sector to retreive data? shouldn't I be able to get files out of my .img file i created???  ](*,)

---

