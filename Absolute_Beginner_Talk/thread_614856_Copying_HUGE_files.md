---
title: "Copying HUGE files"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by siege911 on 2007-11-16
I've been doing some video editing on my Ubuntu box and ran out of HDD space. So I got an external 500GB drive for some extra space.

Now I'm trying to copy over 50+GB of video files that I may need later so I can't delete them now. Problem is when I try to copy and paste via Gnome, it copies about 4GB and then shuts down all of the windows and stops.

I've tried typing this into the Terminal:
```
cp -a /home/siege911/Videos/wedding/* /media/BACKUP/video/wedding
```

This was what I gathered from reading some info online about copying via the terminal. Anyways, it worked for a little bit. Probably got around 5-6GB, then said:
```
File size limit exceeded (core dumped)
```

I have 3 video files that are at least 7-8GB each. I can transfer the others one at a time, but how do copy these ones over?

---

### Post by kellemes on 2007-11-16
It's formatted FAT32? This can't handle files larger as 4Gb..
You need to format ext3 or NTFS or some other fileformat that's able to handle large files..

---

### Post by Inxsible on 2007-11-16
if your external drive is FAT32 it cannot handle files greater than 4GB. You will have to format it to EXT3 or NTFS

---

### Post by alwiap on 2007-11-16
just a thought if you don't want to reformat the drive, you could also cut the files in half using a video editing software so its < 4 GB; and then transfer the videos

---

