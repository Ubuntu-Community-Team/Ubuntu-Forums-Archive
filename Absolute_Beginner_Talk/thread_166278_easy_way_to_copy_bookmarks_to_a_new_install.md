---
title: "easy way to copy bookmarks to a new install?"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by legolas on 2006-04-26
I had to reinstall Ubuntu onto a new drive.  I had to do it from scratch because for some reason I could not get the boot to install after installing from a backup.  After trying a number of times, (and accidentally erasing my Windows XP boot loader too](*,) ), I just did it the hard way( which only took 30 min ) I need to put in all my bookmarks, but I was wondering if I could just copy a specific folder from my old Ubuntu to my new Ubuntu.  Or if anybody has any other clever ways to get my bookmarks in from my other Ubuntu, without having to do them one by one.  Come on guys, hit me with your outstanding knowlege of the Linux system!:-D

---

### Post by Nikusan on 2006-04-26
[QUOTE=legolas]I had to reinstall Ubuntu onto a new drive.  I had to do it from scratch because for some reason I could not get the boot to install after installing from a backup.  After trying a number of times, (and accidentally erasing my Windows XP boot loader too](*,) ), I just did it the hard way( which only took 30 min ) I need to put in all my bookmarks, but I was wondering if I could just copy a specific folder from my old Ubuntu to my new Ubuntu.  Or if anybody has any other clever ways to get my bookmarks in from my other Ubuntu, without having to do them one by one.  Come on guys, hit me with your outstanding knowlege of the Linux system!:-D[/QUOTE]

copy the directory ~/.mozilla from your old install to your new one. This works equally well for any other program who's settings you want to retain (gaim for example).

---

### Post by manicka on 2006-04-26
[QUOTE=Nikusan]copy the directory ~/.mozilla from your old install to your new one. This works equally well for any other program who's settings you want to retain (gaim for example).[/QUOTE]

Yes, this is the best way as it will also retain all your extensions, themes etc

---

### Post by Nikusan on 2006-04-26
[QUOTE=manicka]Yes, this is the best way as it will also retain all your extensions, themes etc[/QUOTE]

Now that I think about it, the best advice is probably to copy your whole home directory. Doing that will keep all the settings from all the applications you used in the old install.

---

### Post by Sef on 2006-04-26
What I do to save my booksmarks in firefox is this with firefox open -- Bookmarks > Manage Bookmarks > File > Export > Save in /home and then back up the data on the home partition.  To install them,  same until File > import > /home and click on the bookmarks file.

---

### Post by TeeAhr1 on 2006-04-26
...and that, folks, is why you make /home its own partition.  Which, yeah, I didn't do either the first time.  Whaddaya do...

---

### Post by legolas on 2006-04-27
Wow!  Excellent ideas guys!  Thanks.  
TeeAhr1, you mention making /home in its own partition, how would you do that?  Do you do that when you are setting up the partions in the very beginning of set-up?  How does linux know to put the home stuff in that partition when it is installing itself?

---

### Post by steve.horsley on 2006-04-27
[QUOTE=legolas]Wow!  Excellent ideas guys!  Thanks.  
TeeAhr1, you mention making /home in its own partition, how would you do that?  Do you do that when you are setting up the partions in the very beginning of set-up?  How does linux know to put the home stuff in that partition when it is installing itself?[/QUOTE]

Yes, you make an extra partition. This involves manual partitioning of course, and having to decide what size to allocate to each partition. I suggest that if ou have enugh disk space, you allocate two partitions of 5-15 Gig, to hold two root filesystems - your main one and an experimental one. Allocate a 2 gig swap, and the rest as a home partition. In the partitioner, you then specify which partition will be / and which partition will be /home. Just don't install on the wrong one. The installer will want to format the / partition before installing of course. Don't tell it to format /home.

---

### Post by timsch75 on 2006-04-27
If you do not have a home partition yet, you don't need to reinstall your system.  Just create a partition, copy /home (current) to the new partition (cp -a) and edit /etc/fstab to let your system know where to find your new home directory

---

