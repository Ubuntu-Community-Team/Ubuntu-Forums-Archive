---
title: "/root/.trash - What's it for?"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by DOD1951 on 2006-09-23
There are a number of files in this location /root/.trash which get backed up when I backup root which are large. Are these files susposed to be there? Should they get deleted at sometime? 
/root/.Trash/backup.tar.bz2
/root/.Trash/backup.tgz
/root/.Trash/backup (copy).tar.bz2

---

### Post by jorn on 2006-09-23
I did't know there was a /root/.Trash/
Is it different from:
> /home/username/.Trash

---

### Post by DOD1951 on 2006-09-23
Am pretty new at this so not sure if i have this right.
When I go via the file browser and look at /root/.Trash and click on properties it says location of file is /root. When i was backup files using TAR the files above were written to the archive, however in the file browser the trash folder has an X against it saying there are zero items in folder.

Attached screenshot of what archive backed up.

---

### Post by DOD1951 on 2006-09-23
screenshot

---

### Post by jorn on 2006-09-23
If you open your terminal and type or paste:
> gksudo nautilus
you will be able to browse your root-trash-folder to see if it is identical with /home /username/.Trash
Be careful. You become root.

---

### Post by DOD1951 on 2006-09-23
This showed me what you see here and now I can see the files. Do you think its ok to delete them?
Thanks for taking the time to assist. 

Cheers,
 Dennis.

---

### Post by jorn on 2006-09-23
In the lower corner of your screen there is your trashfolder.
Is is safe to delete theese. If you do so are there still files left in /root/.Trash. If so I don't know if they are safe to delete. Maybe it's the same folder.

---

### Post by DOD1951 on 2006-09-23
Im not really sure how this has come about. I get the impression that the Garbage Bin is not in sync with /root/.trash for some reason. I decided to delete the files from /root/.trash as I recognized what they were. Interestingly the system asked if I wanted to permanently delete them from the Garbage Bin so there is obviously a connection somehow. Maybe have to go down as one of life's little mysteries. 
Thanks again for taken the time out to help.:D

---

### Post by aysiu on 2006-09-23
If you're logged in as root or browsing as root (using *gksudo nautilus*), anything you put in the trash will go to /root/.Trash

/root is the root equivalent of /home/username

Just as items you trash as a user will go to /home/username/.Trash, so will items you trash as root go to /root/.Trash

---

### Post by jorn on 2006-09-23
Pointing it out that way it sounds so simple.
Thank you. aysiu, for clearing up our little discussion.

---

### Post by DOD1951 on 2006-09-23
Thanks very much Aysiu that's interesting. So if I delete things when logged in as root I will have to take care of what is in the garbage bin but will have to be logged in as root to see that there is stuff in the garbage bin to empty. Learn something new every few minutes with this system. :)

---

### Post by aysiu on 2006-09-23
Technically you don't have to be logged in as root to *see* stuff in the garbage bin (you could just navigate to the /root/.Trash directory, but you *do* have to be logged in as root to empty that trash (or at least issue a *sudo* command to empty it).

---

### Post by xpod on 2006-09-23
> Thank you. aysiu, for clearing up our little discussio

As he does with SO many:D 
Good stuff

---

### Post by bulldog on 2006-09-23
Hmmmm..........I had some things to get rid of too in the root trash can.

Didn't know either it was there :D 

Have to clean better in the future.

Thanks Aysiu,to clear things for us.

---

