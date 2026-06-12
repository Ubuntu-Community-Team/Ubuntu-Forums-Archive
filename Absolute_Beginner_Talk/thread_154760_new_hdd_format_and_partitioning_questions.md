---
title: "new hdd format and partitioning questions"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by sldonmtns on 2006-04-03
I just bought a new 300gb seagate drive (IDE)
The total drive space is: 297.46gb
Total free space w/ NTFS: 279.39gb
So, NTFS is only taking up 73.18 mb

Now I partioned the drive to ext3 w/ gparted live cd,
and the total free space is: 274.95gb
So, ext3 is taking up: 4.51gb

When I mounted the drive in ubuntu the total free space dropped to 261.0gb

Is it normal for ext3 to take up so much more room than ntfs?

Also, why does the space drop almost 15gb when the drive is mounted?

Thanks

---

### Post by az on 2006-04-03
By default, when you format an ext partition, 5 percent is reserved for the super user.  That way, if you run out of disk space, you don't leave your system unbootable.

Also, there are different ways of reporting disk space.  Some report k as 1000 bytes while others report 1024 bytes.

---

### Post by sldonmtns on 2006-04-04
Is there any way to change the 5% left for user? I am using this drive just for storing files (no systemfiles), so it would not matter if I filled the drive up, right?

Also, all the free space specs were taken from gparted, so they were not reported differently.

I also want to make sure it's normal for ext3 to take up 4 and half gigs on a 300gb drive, before I start moving my files over to this drive.

---

### Post by Randomskk on 2006-04-04
When you install Ubuntu, a second partition - the swap partition - is also made, and this is like the windows pagefile, but it has it's own partition, and this will take up some space.

---

### Post by sldonmtns on 2006-04-04
I know about the swap partition, but that's only for the drive ubuntu is installed onto. I just made one partition for the whole drive, because this drive is just for storing media files, etc.

---

