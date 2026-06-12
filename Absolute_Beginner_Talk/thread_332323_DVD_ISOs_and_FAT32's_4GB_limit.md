---
title: "DVD ISOs and FAT32's 4GB limit"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by feap on 2007-01-05
I have a HDD formatted with FAT32 and would like to save DVD ISOs on it. But there's a 4GB limit on FAT32 partitions. Any way to circumvent this? Repartitioning/reformatting is not an option.

The only (partial) solution I've come up with is to zip it up in two so the parts are less than 4GB, but this makes mounting the ISO directly impossible.

---

### Post by macogw on 2007-01-05
Nope, no way arround it that I know.  That's why NTFS exists, but its a small pain to use NTFS in Linux.

---

### Post by crispy_420 on 2007-01-05
I would advise against NTFS use with linux. The drivers/software for read/write are in alpha stage and are very buggy. Some people claim they are perfectly stable but they are not. Just search the forums here for horror stories. That is what happens when you reverse engineer since Microsoft won't help.

I would use ext3 as your file system. If you need windows access, there are far more stable drivers to read/write for windows and ext3. And if this is for external drive it will work too. 

Are you doing DVD backups? If so is there an option to save as files (VIDEO_TS & AUDIO_TS) instead of iso. So as a windows user Nero can burn it as a DVD.

Just my thoughts, it never hurts to get more opinions.

---

### Post by rev_b on 2007-01-05
I found the most efficient way to get data shared between windows and linux isn't using FAT32 (way too old and limited FS), but to format a ext2 or ext3 partition and using a driver to make windows read and write to linux FS

Here: [http://www.fs-driver.org/](http://www.fs-driver.org/)

The beauty of open-standards is that you can make a working driver knowing the full FS specs. Problem with "proprietary" NTFS Linux support is that there's too much guessing involved...

---

### Post by crispy_420 on 2007-01-05
exactly

---

### Post by feap on 2007-01-05
Well, as I said, reformatting in non-FAT32 is out of the question. But I hadn't thought about "extracting" the vobs from the ISO, I'll try to figure out how to do that. Thanks!

edit: Hmm, it should be as easy as copying the VOBs from the mounted ISO to another dir. I believe Xine can read VOBs directly just like an ISO.

---

### Post by orb9220 on 2007-01-05
I use dvdshrink under wine and save as files to hardrive then you end up with the standard video_ts folder with vobs 1 gig ea in size. 

Any DVD program that saves dvd movie as folders to hard drive should work.

---

### Post by crispy_420 on 2007-01-06
Reading vobs is ok put it will limit you to a few chapters of a DVD and not the whole movie. What you'll want is a program than can read an entire directory (eg VIDEO_TS) or the ifo file. Either way you watch the whole dvd. I'm not sure what program in linux (windows = PowerDVD) will do this, but maybe someone else can will in that detail as I have yet to try.

As far as a DVD player in linux, I like VLC. Just my preference though. I use to use xine and switched to vlc, no real reason, just a change for me.

Why is reformat/partition not an option for you?

---

### Post by orb9220 on 2007-01-06
> Reading vobs is ok put it will limit you to a few chapters of a DVD and not the whole movie.

This is not true.

I am confused by what you said all dvd movies are a video_ts folder with vobs. A DVD Movie will have all the 1gig vobs it needs to cover the movie and all the extra's.

If you look At uncompressed vobs of the main movie you will see that they are 1024mb this is the standard for dvd's.

DVD shrink copies the whole DVD without any changes. or you can reauthor and just grab the movie without all the extra's.

> What you'll want is a program than can read an entire directory (eg VIDEO_TS) or the ifo file

vlc or Totem as most the others will let you drop a video_ts folder dragging from nautilus and the whole movie will play.

Hope this has cleared up a few issue's

---

### Post by maestrobwh1 on 2008-06-11
I "used" to have windows on my PC... and when I did, I used NTFS-3g and I never had an issue writing and reading to the partition; however, lacking a means to check/fix it properly from Linux, it never felt wholly comfortable.  I created a partition in NTFS of about 8 GB and used to write my iso files to it before burning them.

There is a windows driver to read/write to/from EXT2 and EXT3 called ifsdrive, and you may want to consider creating a partition that is EXT3 for storage and do your read/write to that partition from each OS.

I have always had a "storage" partition.

I do see some issues.  I have a WD 500 GB usb drive and it is fat32, so I have to make sure my dvd isos are set to be created at 3.9 GB if I want to save them there.  Kind of a pain in the butt, but I do swap the drive out to other computers that are not mine and have an MS OS on them.  I need the drive to be readable from anything and fat32 is the only "universal" filesystem.  Stinks.

---

