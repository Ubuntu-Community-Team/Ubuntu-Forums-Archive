---
title: "missing space on hard drive"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by actioncomics on 2007-03-13
I searched for this everywhere but could not find the answer.  If it is out there, if you could just point me in the right direction.

My problem is that after i have formated my hard drives to ext3 filesystem, the drive is missing space.  for example my hard drive is 150 GB but after formating it gparted says that there is about 2.5 GB of used space.  I have not put anything on the drive yet but something is using space.   anyone have any ideas?  thanks for any help.

ac

---

### Post by annda on 2007-03-13
what does

df -h

tell you? can you post the output here?

which partitions have missing space? your linux partitions?

---

### Post by overdrank on 2007-03-13
> **actioncomics said:**
> I searched for this everywhere but could not find the answer.  If it is out there, if you could just point me in the right direction.

My problem is that after i have formated my hard drives to ext3 filesystem, the drive is missing space.  for example my hard drive is 150 GB but after formating it gparted says that there is about 2.5 GB of used space.  I have not put anything on the drive yet but something is using space.   anyone have any ideas?  thanks for any help.

ac

Hi it has been my past that when you format the drive that it takes space to format the drive. So if you have a 80gb drive and format it to say ntfs you will only have about  78 to 79 gb free space. Hope this helps.

---

### Post by actioncomics on 2007-03-13
below is what df -h says.  i double checked gpart and it still says hdb1 has 2.5 used space but as you can see below this is only telling me 189M but at the same time it says that the size is 147 and available is 140.  now i am really confused.

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              20G  4.0G   15G  22% /
varrun                506M   80K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  172K  9.9M   2% /proc/bus/usb
udev                   10M  172K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-11-generic/volatile
/dev/hda3             131G   42G   83G  34% /home
/dev/sdb1             231G  219G   87M 100% /media/Comics/DCComicsII
/dev/sda1             231G  148G   72G  68% /media/Comics/DCComicsI
/dev/hdd              1.6G  1.6G     0 100% /media/cdrom1
/dev/hdb1             147G  189M  140G   1% /media/Comics/MarvelComics

ac

---

### Post by actioncomics on 2007-03-13
Paul, that was the first thing i thought of.  when i formatted in windows it would take up 8mb of space for formatting, but this is taking up 5% of the disk.  150GB disk that is about 6GB.  i just thought that was a little extreme.  if when formatting it is to take up that much space it is not a problem.  I am new at linux and just thought it was odd.

ac

---

### Post by actioncomics on 2007-03-13
i know i keep replying to my own message but is there a way to partition a drive and format it without using the gnome partitioner?

---

### Post by slayerboy on 2007-03-13
You could use something like Ultimate Boot CD ([www.utlimatebootcd.com](www.utlimatebootcd.com)[http://www.utlimatebootcd.com]("http://www.utlimatebootcd.com/")) that has tons of utilities to do just what you need.

If you really just want to wipe out everything on the drive and start from scratch, write zeros to the drive multiple times to completely wipe the drive, then you should be able to use Gpart when you install Ubuntu.

I had a problem that looked like a bad drive, but I wrote zeros to the drive 3x (took about a day or two) and it cleared all problems up and the drive is fine.  I think I used Autoclave from the Ultimate Boot CD, it has the option to write zeros multiple times. Usually one pass works, but in this case, there could be issues with the partition table, so I would do it 2-3 times IMHO.

---

### Post by actioncomics on 2007-03-13
thanks i will give that a try and see what happens.

ac

---

### Post by slayerboy on 2007-03-13
Also, you could test the drive to make sure it doesn't have any bad sectors or anything like that.  Most of the time you can look at two 100GB drives and one might show 99.5GB and another might say 98GB.  2-3GB differences from what it says on the packaging of the drive isn't that uncommon, but anything above that there's either something causing problems with the partition table or there's a problem with the drive itself.

How old is the drive?  I should have mentioned for you to do a test on the drive using the ultimate boot cd first, just to make sure the drive is fine, then write zeros.  If the test says you have problems, then you have problems and writing zeros won't really help.  But, like I said, it seemed to help my issues with the corrupt partition table that I had, luckily.

---

### Post by Songwind on 2007-03-13
You might just be a victim of "marketing math."

In terms of labelling, most drive manufacturers say that 1Gb = 1,000,000,000 bytes.

However, an actual GB = 1024X1024X1024 bytes, so right there you "lose" space when your OS tells you what size it actually is.

A certain % of your drive will be dedicated to partition tables and file tables after formatting.

---

### Post by actioncomics on 2007-03-13
yea i took into consideration that the drive may not be what the manufacturer said.  one thing i forgot to mention earlier is that i tried this on 2 other 250GB drives with the same result.  in fact it really screwed me up because i had one drive as NTFS (full) and the other i was using to transfer files to so that i can convert to ext3 filesystem.  both of those drives had about 11GB of space used up with nothing on them.  so i had to find another place to put 11GB of data.  anyways i think i will try to ultimate boot cd first and write the 0s to it.  to see what happens.  thanks for the help.  I will let you know what happens.

ac

---

### Post by flyingbrass on 2007-03-13
Hard drives are advertised with a capacity expressed in base 10.  Computers don't work that way.  See [http://en.wikipedia.org/wiki/Kilobyte](http://en.wikipedia.org/wiki/Kilobyte)

That's why your 160 GB drive's true capacity is actually somewhere around 149 GB.

By default, mkfs reserves 5% of the space when creating an ext3 filesystem.  The amount of reserved space can be adjusted using tune2fs.

---

### Post by euler_fan on 2007-03-13
One other thing I have found, and this may be more an FYI in this case than helpful, is that on my flash drive I had had some large folders which consumed 90% of the drive, and when I thought I deleted them, it actually just hid them on the drive.

It was really bothering me until I looked at the hidden folders and realized "hey, why is all this stuff I deleted still here?" Once I deleted the hidden files I got my drive back.

Again, might not be something you run into, but it can happen.

---

### Post by actioncomics on 2007-03-14
> By default, mkfs reserves 5% of the space when creating an ext3 filesystem. The amount of reserved space can be adjusted using tune2fs.

that was what i was looking for.  when i switched my 3 drives (all at different times) over to ext3 filesystem they all consistently loss the same amount of space (by percentage that is).  

My next question would be what will happen if i adjust the space reserved down.  what is the lowest i can go to maximize my freespace?

dc

---

### Post by arron on 2007-03-14
> **actioncomics said:**
> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              20G  4.0G   15G  22% /
...
/dev/hda3             131G   42G   83G  34% /home


Used space is just that, the space used.  It looks to me you have about 150 gigs used of your hard drive, hda1 + hda3 = 20 + 131 = 151 gigs.  it looks like you made a HUGE /home directory partition.  This can be done for many reasons, but most are ok with their hard drive just with /.

Remember hda is one physial drive, hdb another, then the numbers hda# is the partition number.

---

### Post by arron on 2007-03-14
> **actioncomics said:**
> that was what i was looking for.  when i switched my 3 drives (all at different times) over to ext3 filesystem they all consistently loss the same amount of space (by percentage that is).  

My next question would be what will happen if i adjust the space reserved down.  what is the lowest i can go to maximize my freespace?

dc

Unless you have a specific reason for doing it don't.  There is a specific reason that the partitioner makes this space.  As I understand it, this is where the data is stored for where the file data an be found on the rest of the drive.  Unless you have a specific reason to alter this, don't.  This space has been reserved for all partition types from way back when.  5% of a 10 gig drive is not a lot. 5% of 150gig is a bit more, but still a small percent.

Don't worry about small potatoes like this, if you are that tight for space on a 150 gig drive, then you need another drive.  The headaches for a small gain like this, and potential future problems are not worth the gain IMHO.

---

### Post by actioncomics on 2007-03-14
after alot of hunting i think i have finally found the answer (now that i know what to look for).  Keep in mind that the 3 extra drives are used strictly as storage and nothing more.  once i put the data on there it does not move or change.  I might add things but i don't remove them.  It would seem that some of the space is saved for "root" access.  so that if i fill up a drive, root would still have space to work with temporary files.  Keeping that in mind I would not mess with my main OS drive but I could theoretically change my data drives since they would not need root access.  Also keeping in mind that on every drive i would need some space for journaling to take place on the drive.

Thanks for everyones patience on this issue, for some reason that was just bugging me and i needed to figure out where the "used space" was.  below are the links that i have found to help answer this.

[http://ubuntuforums.org/showthread.php?t=215177]("http://ubuntuforums.org/showthread.php?t=215177")
[http://boncey.org/2006_11_18_reclaiming_ext3_disk_space]("http://boncey.org/2006_11_18_reclaiming_ext3_disk_space")

ac

---

