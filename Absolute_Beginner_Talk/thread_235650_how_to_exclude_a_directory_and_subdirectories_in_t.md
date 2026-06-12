---
title: "how to exclude a directory and subdirectories in tar"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by utab on 2006-08-13
Dear all,

I would like to exclude a directory and subfolders in a tar archieve. I found that I have to use exclude but how to use

For example I would like to do sth like 

tar cvpjf backup.tar.bz2 / --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys --exclude=/home/utab/xp

I want /home/utab/xp to be excluded with all subdirectories but could not do for now.

Regards,

---

