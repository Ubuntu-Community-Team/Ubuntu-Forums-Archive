---
title: "Freeing up space on a windows XP disk"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by tarpon_bill on 2005-11-20
I have a windows XP box, two drives, but both are now used. I want to make space for a dual boot Ubuntu 5.10 partition.

First drive is 120 GB with a primary partition of 110GB and a second primary partition of 10GB. I want to reduce the first primary partition of drive C since it has 120 GB and only needs about 40 GB. The first drive also has a 10GB software partition that I want to stay as is.

I want the second drive, a 80 GB single partition backup drive to remain untouched.

gparted on the liveCD the right tool for the job? Can it read and write the NTFS partition and move the files contained within around to resize the partition?

How to proceed?

Ultimate goal, I want to insatall 5.10 into the freed up space on first drive. I am downloading the liveCD 5.10 now.

---

### Post by Kapre on 2005-11-20
[QUOTE=tarpon_bill]First drive is 120 GB with a primary partition of 110GB and a second primary partition of 10GB. I want to reduce the first primary partition of drive C since it has 120 GB and only needs about 40 GB. The first drive also has a 10GB software partition that I want to stay as is.

I want the second drive, a 80 GB single partition backup drive to remain untouched.[/quote]

tarpon_bill - First off, you must first make a backup of your partition and then defrag it at leadst 2 times. Then you use gparted and and partition the disk. For more info on installation with XP already loaded go to the wiki and look into [this thread]("https://wiki.ubuntu.com/Installation").

> gparted on the liveCD the right tool for the job? Can it read and write the NTFS partition and move the files contained within around to resize the partition?

How to proceed?

Ultimate goal, I want to insatall 5.10 into the freed up space on first drive. I am downloading the liveCD 5.10 now.

Just pop in the live Cd and use gparted.

K

---

### Post by aysiu on 2005-11-20
GParted is fine.
You can also [resize during the installation process](http://users.bigpond.net.au/hermanzone/p3.htm).

---

### Post by tarpon_bill on 2005-11-20
Thanks, I appreciate the help, will give it a try.

The liveCD runs fine on the system so it looks like it's a go.

---

### Post by tarpon_bill on 2005-11-20
OK ...  I am stumped. There are some files, one says it's immovable, and there is another that is at the high end of the main partition. This prevents the entire partition form being resized to a smaller size. Likely a feature of Windoze. Anyway around this -- make it so all the files are at the low end of the partition and it can then be shrunk?

---

### Post by Danielle on 2005-11-20
you can try using Dirms to move everything to the fornt of the partition. use the cmd - dirms c move lcn
if the partition isn't on c change c to the correct letter.

if you do it in safe mode it's best.

[http://www.dirms.com/](http://www.dirms.com/)

---

### Post by tarpon_bill on 2005-11-21
So far I have figured out to get rid of one of the unmovable files, you can temporarily turn off paging -- it's in the vitural memory settings, just set the size to zero.

But that leaves another unmovable file that seems to be put at the end of the windows XP partition to prevent resizing. I think it is the old updates that are to be used for rollback of changes ... more later.

UPDATE: May help others, but didn't fix my problem ... sigh.

Turn off the paging file
Turn off the hibernate function

Both of the above will eliminate a large unmovable block of files from the drive and may allow you to resize your partition. Unfortunately, in my case there is still a system file conviently placed by the OS near the end of the partition that stops me from getting a useful free disk area. It's almost as if MS wants the partition to NOT be resizable, I wonder why.

---

