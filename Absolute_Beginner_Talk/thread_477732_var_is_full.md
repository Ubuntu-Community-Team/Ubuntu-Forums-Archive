---
title: "/var is full"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by dmond on 2007-06-18
hi,

im recently installing ubuntu dapper drake and im a newbie but very much want to learn about ubuntu because im feed up with windows and im trying to covert to becoming a ubuntu savy. i know this is probably a simple question to ask but im having trouble with my /var. it says that /var is full and seems to be having trouble with the whole system.

my question is, how can i free up some space in /var and how can i avoid making the /var being full again.

any suggestions would be highly appreciated. thanx.

---

### Post by zvacet on 2007-06-18
```
sudo apt-get autoclean
```

---

### Post by Bachstelze on 2007-06-18
> **zvacet said:**
> ```
sudo apt-get autoclean
```

I don't hink that would be a good idea. On a standard (desktop) system, /var contains only log files, you can very well delete the old ones if they're not needed anymore.

---

### Post by Gavin77 on 2007-06-18
Maybe /var/cache/apt/archives is taking up a lot of space.
What zvacet said might help.

---

### Post by dmond on 2007-06-18
hi again.

@zvacet : sudo apt-get autoclean didn't do anything to my system but im trying sudo apt-get clean right now.

@HymnToLife : is alright to delete logs at /var/log? what are the files under the /var/log that needs to be retained?

@Gavin77 : yup. /var/cache/apt/archives is taking up a lot of space. but /var/cache/apt/pkgcache.bin and /var/cache/apt/srcpkgcache.bin is taking up more space. should i delete those files?

to all : thank you for taking the time for answering my questions. hope i can do the same in the future.

---

### Post by EagleRock on 2007-06-18
dmond,

pkgcache.bin and srcpkgcache.bin are simply cache files for the apt-get application.  You can delete them as long as you're not doing anything with apt-get at the time.  Note that they will be recreated when you run anything that uses apt-get (apt-get, aptitude, or the "Add/Remove..." link).

While cleaning up /var is a good short-term solution, it seems that your partition scheme seems to be a bit off from your needs.  How did you set up your system?  If you can provide the output of "df -k" and the contents of /etc/fstab, I can see how big your filesystems are and what can be done.  Depending on the filesystems you used in your installation, you might be able to resize partitions and get yourself more /var space.

---

### Post by Gavin77 on 2007-06-18
I don't know what those files are so I would advise against removing them.  On my system they're only around 10mb each anyway.

---

### Post by Bachstelze on 2007-06-18
> **dmond said:**
> 
@HymnToLife : is alright to delete logs at /var/log? what are the files under the /var/log that needs to be retained?

The old ones are gzipped, you an delete them, you shouldn't need to delete the current, not gzipped ones. How much space do you have on your /var partition ?

---

### Post by dmond on 2007-06-18
hi again,

please take note that im trying to revive a very very very old laptop thats why i resorted to this kind of partitioning. that is also why i cant paste the exact figures of the df of that laptop cause im using my second desktop to access the forum. anyway, here are roughly the partitions ive done to the laptop.

50.0 MB on /boot
1.0 GB on swap
1.0 GB on /var
3.9 GB on /
total harddisk is 6.0GB only.

@ EagleRock : you can resize the partitions without re-installing ubuntu? how?

@ Gavin77 : thanks. sudo apt-get clean seemed to have done the job.

@ HymnToLife : thanks. ive deleted some of the gzipped that have taken up big space.

---

### Post by EagleRock on 2007-06-18
> **dmond said:**
> hi again,

please take note that im trying to revive a very very very old laptop thats why i resorted to this kind of partitioning. that is also why i cant paste the exact figures of the df of that laptop cause im using my second desktop to access the forum. anyway, here are roughly the partitions ive done to the laptop.

50.0 MB on /boot
1.0 GB on swap
1.0 GB on /var
3.9 GB on /
total harddisk is 6.0GB only.

@ EagleRock : you can resize the partitions without re-installing ubuntu? how?

You can do so with the GNOME Partition Manager (gparted) very easily.  I would recommend booting into a LiveCD (which has gparted installed automatically) so you don't have to worry about drives being mounted.  You would simply enter gparted, unmount each partition on the drive (right click the row and select unmount, and then do your work.

If you're using a filesystem like ext2, ext3, or reiserfs (probably one of these three), you can resize the partitions easily.  If you wanted to kill some space on your root parition, you would simply shrink the root parition by taking space away from the front of the partition.  Then, you would be able to grow the /var parition accordingly.

Unfortunately, it seems that your drive is a bit too small to do so.  You might be a bit hard-pressed to keep /var less than full.  The boot and swap size you probably don't want to touch, so taking away from root would really be your only way to add space.

I'm not too up on making Ubuntu work with such a small space, so someone else would probably be better at helping you out.

Deleting those apt-get files will probably help, but you'd have to do it often (after updates and after application remove/installs), but that might get annoying to keep babysitting it.  You might want to try a reinstall and sticking to two partitions (/ and swap).  You would be able to have all your room available to where you need it, and you'd probably have to kill /var space less often.  However, that's a matter of personal preference.

---

### Post by Megatog615 on 2007-06-21
Call me crazy but I used to mount /var with a tmpfs filesystem :-). Probably not a good idea but it certainly saved space.

---

