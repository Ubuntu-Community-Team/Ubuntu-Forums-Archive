---
title: "External Hard drive nightmare"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by Noremacam on 2006-01-10
I originally had a 160 gb NTFS external hard drive. I decided, I'd make it an ext3 drive, and just use some software I found online that allows you to mount ext3 partitions in windows. I created a partition that filled all but 100 mb of the drive in ext3. I made the other 100 mb fat, and put the windows software to mount ext3 partitions on that fat partition(should I take my drive to a friend's house, or whatever).

The whole idea was that I'd have the security and speed of ext3 without sacrificing compatibility with windows.

So I thought....

Well, the software didn't work. Ironically enough, windows couldn't even mount the fat partition! I even made that 100mb a fat16 partition just for the heck of it.

Well, that idea bit the dust. so I went back into linux and backed up my drive again to my linux partition, and reformated the entire drive in fat32. After doing so, I copied all my files back onto the external drive.

I boot back into windows, and it didn't find the partition. That was ok, I could manually assign a drive letter using the administrative tools that xp has. I go into the disk management console. It sees my drive, it sees my partition and recognizes it as fat32. It can tell me at the top that it has 46% free disk space. It knows that it's a primary partition. When I right click the partition, the option to mount the drive is thoughtfully grayed out with no explanation. I can't convert it into a dynamic disk either. The only option it gives me with the drive is to delete the partition, which is not an option.

As dumb as this sounds, how do I get windows to mount my fat32 partition so I can share files between it and ubuntu? Wasn't microsoft trying to patent fat32? Why can't they support their own filesystem? Help!

---

### Post by lha on 2006-01-10
What program did you use to partition and format your external hard drive? Atleast cfdisk and (linux's) fdisk don't produce fat partitions that are compatible with Windows' out of the box. After creating a fat partition with either of these programs, you have to dd the beginning of that partition with zeros to make it work. (Creators of these programs think this is a bug in DOS/Windows and therefore don't fix it.) It is recommended to use Windows' tools to partition and format fat/NTFS partitions.

---

### Post by Noremacam on 2006-01-10
I used Gparted(after unmounting the partition, to allow it to be modified).

Is there any way to fix the partition in windows, without losing all the data? Long story short; I don't have access to linux right now at the moment.

---

### Post by lha on 2006-01-10
Sorry, but I'm not familiar with dosfstools (GParted uses it to handle fat partitions) so there's no further advice I can give on making your partition accessible from Windows. If you have a fat partition or you are able to make one, you could use a live cd to copy your files to another partition which is accessible to Windows.

---

