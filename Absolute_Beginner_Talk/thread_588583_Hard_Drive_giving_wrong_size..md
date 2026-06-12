---
title: "Hard Drive giving wrong size."
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Drillbit on 2007-10-23
I installed 7.10 and I love it except for one problem - my hard drive says I only have 4.2 gigs left, even after I deleted gigs and gigs of stuff to make more room on there. 

I'm no good at these types of things. Your help would be appreciated.

---

### Post by Vansinnesvisan on 2007-10-23
Is the any data in the trash? You can check under Nautilus Go->Trash.

---

### Post by Drillbit on 2007-10-23
I've emptied the trash a few times and still says 4.2 gigs. Any ideas?

---

### Post by DarkDancer on 2007-10-23
This may sound dumb, and please forgive me if it does, but have you actually gone into the trash (left clicked on it) and made sure it was empty? I've seen Ubuntu say it was emptying the trash, and not really do it till you actually go into the can....

---

### Post by Sef on 2007-10-23
There is hidden trash too.  That may have data that needs to be cleared.

To access it, open the trash, then click on view, then go down to hidden files and check it.  Move any hidden files to trash, then empty it from there.

---

### Post by rudeboyskunk on 2007-10-23
Also, go ahead and go to a terminal and type "df", then post the results in this thread.

---

### Post by Vansinnesvisan on 2007-10-23
You could use the Disk Usage Analyzer to see what is using up the most space.

---

### Post by Drillbit on 2007-10-24
> **Sef said:**
> There is hidden trash too.  That may have data that needs to be cleared.

To access it, open the trash, then click on view, then go down to hidden files and check it.  Move any hidden files to trash, then empty it from there.

I emptied the trash and there was no hidden files. When I typed df in terminal here's what I got....

paul@paul-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            155519044   6676016 140943068   5% /
varrun                  484760       104    484656   1% /var/run
varlock                 484760         0    484760   0% /var/lock
udev                    484760        84    484676   1% /dev
devshm                  484760         0    484760   0% /dev/shm
lrm                     484760     34696    450064   8% /lib/modules/2.6.22-14-generic/volatile
paul@paul-desktop:~$ 


Thanks for your help with this everyone.

---

### Post by Drillbit on 2007-10-24
My aplogises. I didn't empty the .trash folder in the drive itself (it's a partician drive.) OK, back on track. Thanks for your help.

---

### Post by studo77 on 2007-10-25
YEA! You just helped me out.
I also removed a lot of stuffe on a partitioned drive. Thoought the trash included all trashed files, but no.
Going to trash via menu only goes for the main partition of Ubuntu, instead go to the folder/disk/partition -> show hidden files. And now you will see a .Trash folder. All the deleted files are in there.

Just gave me 16 gigs of free diskspace, nice.

---

