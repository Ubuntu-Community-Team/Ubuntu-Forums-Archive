---
title: "Best way to Partition Dual Boot? (noobie)"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by den.saunders on 2006-12-20
Hi all,

I am very new to the Ubuntu world, and for that matter Linux in general, but so far I like what I see. :) 

I  have long been meaning to experiment with Linux, and I've finally found the time to start.

After strugling to properly partition my HD for the "/" and "swap" sections I finally did it. And then after hours of struggling to get my reolution 1280*800, I finally got it.

Now I am wondering...the best way to keep my Linux-Windows shared community happy. I will need to keep windows for some design software, and  am curious to know how I should go about best utalizing the two on the same 80gb HD. 

I currently have;

hda1:~65gb, NTFS housing winxp, and all files
hda3:~2.5gb, ext2 housing ubuntu, and home files for ubuntu?.
I think hda2 was taken by Page File Memory on Windows (about 1gb)
And the rest is unused.

Now it sees with hda1, I can see the files but not edit or save, correct? This is because it is NTFS?

Also, my "swap" volume that I allowed during installation, what does it do? And where is it?

Thanks in Advance, I hope I haven't asked too much!

---

### Post by bulldog on 2006-12-20
If you type in your terminal ```
sudo fdisk -l (l as in like)
``` you see all your current partitions.
The swap is the same thing as windows page file.
Your ubuntu partition is rather small,2,5GB isn't that much,so take care you won't run out of space.
A better choice would be making it about 10-15GB.

Welcome to Ubuntu :D

---

### Post by den.saunders on 2006-12-20
Yes, yes it is, hense why I feel I should change the partitions :)

I just found this which id also helpful...
[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

---

### Post by den.saunders on 2006-12-20
Yes, yes it is, hense why I feel I should change the partitions :)

I just found this which is also helpful...
[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

Using Ext for the shared section instead of FAT32, seems like a good idea, any opinions?

---

### Post by Dusty545 on 2006-12-20
I'd argue against using ext2 or ext3 for the shared section as Windows will chuck a wobbly over reading it.  FAT32 ain't pretty but it's pretty well supported with Ubuntu.

Much as I hate to advocate use of my setup to anybody, I'm stuck with the 80GB HDD in my laptop and have things this way:

dev/hda1 - Windows (c:) NTFS - ~25GB
dev/hda2 - Shared (d:) FAT32 - ~20GB
dev/hda3 - Ubuntu / ext3 - 15GB
dev/hda4 - swap linux swap - 2GB

The remaining space I keep aside for testing some other distros/BSD/Solaris/etc.  I'm changing this to make a bigger shared area as everything else I've tried is a major nawse and once I've built a new desktop then I'm going to reformat with just Ubuntu and a swap file..

---

### Post by Sef on 2006-12-20
> Using Ext for the shared section instead of FAT32, seems like a good idea, any opinions?


Using ext2 or ext3 would be a good move.   Both Windows and Linux can read and write to them with no problems.

---

### Post by Dr. Nick on 2006-12-22
> **Sef said:**
> Using ext2 or ext3 would be a good move.   Both Windows and Linux can read and write to them with no problems.

If I am not mistaken it takes special software to read/write from ext* in windows, Fat32 can be done natively with both. I have a shared Fat32 setup which I loathe since you can not write files bigger then 4gb to a Fat32.

I am curently searrching out the best method to make my shared ext3 and get good support in windows.

---

### Post by Dr. Nick on 2006-12-22
Bingo!!!

I saw this site in the past and found it again
[http://fs-driver.org/index.html](http://fs-driver.org/index.html)

It will install on windows and allow you to set drive letters to your linux ext2/3 partitions from windows so that you can access it from "My Computer" just like any other drive.

It appears to fully support read/write aswell. I am not positive it doesnt corrupt ext partitions since mine install is messed up, but it mentions no risk. I think since ext is a open file system it should be pretty stable.

I am using it to backup some files from ubuntu (instead of just using  a live cd) since i goofed my install, it seems to work just fine to backup to a external usb drive.

---

