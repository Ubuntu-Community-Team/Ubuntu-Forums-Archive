---
title: "New External HDD. What file system?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by pjones0404 on 2006-08-21
I have recently purchased a new 250 GB external HDD. i would like to use this w/ my ubuntu, win xp, and my mac. i was curious what would be the best file system to use so all os's can access it locally or over a network. 

i know that w/ NTFS i do not have native write access from linux nor OSX. i also am aware that there is a workaround but i am not to sure on how safe it is, and i would rather not risk losing all my data. I tried to format fat 32 since it is natively supported yb all but i can not create a partition larger than 32 GB in windows. can i format it ext3? can windows and OSX read/write to that file system? 

Any recommendation on what file system i should use that would allow me to connect it directly to all of these computers and also have read/write acces over a network. 


thanks. :)

---

### Post by meng on 2006-08-21
[http://www.fs-driver.org/](http://www.fs-driver.org/)
allows ext3 to be read/written from Windows. Unfortunately I do not know about OSX.

---

### Post by pjones0404 on 2006-08-22
thanks for the recommendation.

anyone else have any ideas on what would be the best way to accomplish this? i am really looking to share the drive via my ubuntu box.

i am new to linux and if i mess up ubuntu i would like to connect the hdd to xp as i fix ubuntu.

once again thanks.

---

### Post by oskar2000 on 2006-08-22
I have my external disk in 30gig pieces because I carry it around alot - it's only an 80gig though. I access my reiserfs disk with Yareg and Reiserfstools from windows - that might be an option. Mac probably supports both reiser and ext3, but I could be wrong.

---

