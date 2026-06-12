---
title: "Trouble Shrinking Macintosh HD"
date: 2011-08-02
forum: Apple Hardware Users
---

### Post by megabenman on 2011-08-02
Hey everyone.
I'm having trouble shrinking my "Macintosh HD" partition.  It is 350GB.  It had about 250GB used but I cut that down to 100GB used.  Now, I'm trying to shrink that partition to 130GB.

Here are my results:

Using Gparted on Ubuntu Live CD: shows no progress bar and nothing ever happens.  If I stop it in the middle nothing happens to my partition.

Using Disk Utility on OS X Install DVD: progress bar freezes after 20 minutes.  DVD continues to make the scratching "being accessed sound" but nothing happens.  If I stop it in the middle nothing happens to my partition.

Using Disk Utility on actual OS X Partition (SL): works for a bit, then eventually goes to a black screen with only the cursor.  If I stop it into the middle, OS X will boot up fine but Disk Utility will tell me there are errors if I verify the disk, forcing me to repair it using the OS X install DVD.

Does anyone have a fix?  I'm guessing the problem is caused by me attempting to shrink the partition to smaller than the disk usage was a day ago, as I just recently deleted all the files.   Can anyone confirm?

---

### Post by pauljwells on 2011-08-03
Because you had a lot of data on the disk that is now deleted it is going to be very fragmented, with data left all over the disk. There is a disk defrag program called iDefrag from Coriolis software that can improve this but to be honest it is going to be much faster and safer to use something like Carbon Copy Cloner or Super Duper to make a bootable clone on an external USB drive, wipe the machine's disk and set up the partition scheme you want and clone back. You only need the usb drive and the new OSX partiton to be big enough to hold the data you have, it doesn't have to be exactly the same size as your original partiton. (ie it's not a direct bit for bit copy, the files are read from one and saved to the other, thus automatically defragmenting)

If that doesn't work, backup and reinstall - you do make regular backups, right? ;-) If you use time-machine you have the option during reinstall to restore from that.

HTH

---

### Post by megabenman on 2011-08-03
I have a 500GB external HDD that I used for time machine.   However I erased it and moved all files I want to access from my linux partition (movies, documents, etc).  It has about 300GB left.

So let me know if this will work:
1.  Use disk utility to shrink the partition on my external drive with the movies and documents (FAT32).
2.  Create a new partition for use with time machine (HFS+)
3.  Use timemachine to backup my now 100GB sized OS X Partition.
4.  Destroy OS X partition, remake one but smaller, reinstall from timemachine backup.

Will this work?  I have a 60GB Bootcamp partition located at the end of my partition table and I want to make sure that will still work, both standalone and with parallels.

EDIT: Disk Utility cannot resize FAT32 so I'll use gparted for that.

---

### Post by pauljwells on 2011-08-04
The external drive resize and time-machine plan should work but I'm not sure how well your bootcamp partition will survive. It might be ok but there has to be a risk that something might not work.
When you resize your external disk can you make another partiton so you can backup the bootcamp partiton too? Use Winclone.

---

### Post by conundrumx on 2011-08-04
You could also use SuperDuper! to do a (probably quicker) copy straight from the current OS to the external, then copy back again.

---

### Post by megabenman on 2011-08-04
> **pauljwells said:**
> The external drive resize and time-machine plan should work but I'm not sure how well your bootcamp partition will survive. It might be ok but there has to be a risk that something might not work.
When you resize your external disk can you make another partiton so you can backup the bootcamp partiton too? Use Winclone.

Well I think it all worked out, I made an NTFS partition instead of a FAT32 partition, installing NTFS-3G to give my mac NTFS write support.  My bootcamp partition is untouched and still boots in parallels.  Ubuntu installed perfectly as always :)

---

### Post by pauljwells on 2011-08-04
Good to know!

I'm not really clear exactly what you ended up doing though, where does the NTFS partition come into play?

Do a favour for future generations and write up exactly what you did. Post it back here. Others are likely to have the same question and you might like a reminder yourself one day too.

---

