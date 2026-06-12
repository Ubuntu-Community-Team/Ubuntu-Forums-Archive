---
title: "Unable to veiw my other hard drives"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by matty24v on 2007-12-31
Since installing Ubuntu on my computer I have been unable to view the contents of my other hard drives will in windows XP any ideas

---

### Post by The Tronyx on 2007-12-31
> **matty24v said:**
> Since installing Ubuntu on my computer I have been unable to view the contents of my other hard drives will in windows XP any ideas

Hello matty24v.  Could you please open your terminal and type:

> 
sudo fdisk -l

That will display any drives detected by your machine.  Also what file system are these drives, NTFS, FAT32, etc?  And lastly, how large are these drives?  I anticipate we can find them and mount them after you run that command but it helps to know just what we are looking for. :)

---

### Post by matty24v on 2007-12-31
I can see them fine will running Ubuntu its when im in windows xp that i cant see them

---

### Post by The Tronyx on 2007-12-31
> **matty24v said:**
> I can see them fine will running Ubuntu its when im in windows xp that i cant see them
WIndows doesn't like to interact with EXT partitions.  If you want to view linux partitions from windows, you'll need to install this, [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by matty24v on 2007-12-31
Fantastic this has worked a treat

---

