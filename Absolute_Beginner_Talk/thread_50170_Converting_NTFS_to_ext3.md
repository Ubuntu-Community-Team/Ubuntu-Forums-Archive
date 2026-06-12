---
title: "Converting NTFS to ext3?"
date: 2005-07-19
forum: Absolute Beginner Talk
---

### Post by Phixion on 2005-07-19
Hi there, I installed Linux on my main HDD, but I still have lots of data on my other 2 HDDs which are NTFS. Is there anyway I can convert these to Linux without losing the data? Or will I need to backup the data on em and format? If so, what program should I be using to format them?

At the moment I can read my NTFS drives, will that allow me to burn the stuff from them onto DVD? Or will I need to boot into windows to do that?

Cheers.

---

### Post by Kyral on 2005-07-19
There is currently no way to convert a partition from NTFS to ext2/3 without losing the data. You are going to have to backup and reformat. You should reformat them in FAT32 so that both Windows and Linux will have read/write access to them.

As for the DVD burning question....I don't know for sure. It SHOULD work, but I have never tried it :D

---

### Post by dave9191 on 2005-07-19
I dont know of any programs that convert from NTFS to ext3. I guess you will have to backup and format. 

You can use mke2fs to format the drive. To find out more about this type 'man mke2fs' into a terminal. 

If you can read the ntfs partion you will be able to burn the data from in in linux. 

Dave

---

### Post by Phixion on 2005-07-19
Thanks for the replies, whats the difference between ext2 and ext3? which should i go for?

---

### Post by dave9191 on 2005-07-19
ext3 is more recent, Im not totally sure about the differences ( i used to know them ). Im sure that you can find some stuff about it on google. But I always use ext3. 

Dave

---

### Post by Phixion on 2005-07-19
OK cheers guys.

---

