---
title: "need to move home folder to another partition."
date: 2012-03-08
forum: Asus Ubuntu Support (CLOSED)
---

### Post by pog12156 on 2012-03-08
i followed this guide[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving") as accuratly as i could and while it does end up working for reasons that i dont know i lose all control of the speaker volume. The volume slider refuses to move and the sound that comes out is barely audable, like i have to press my ears against the speaker to hear it. i reinstalled ununtu again and attempted it with the same results.

this is on an asus K52F laptop and the partition im trying to move the home folder to is formated in ntfs.

so does anybody know what would cause that? im too scared to try it again.

---

### Post by wyliecoyoteuk on 2012-03-08
I assume that you are trying to share your home system between windows and Linux.
Not really a good idea.
You might get better results using

[http://www.diskinternals.com/linux-reader/]("http://www.diskinternals.com/linux-reader/")to share it from the dark side.

Your home folder doesn't just hold your data, it also holds all of your program settings, including those for your sound system.
NTFS doesn't support the same file permissions as Linux filesystems do, and symlinks won't work.
Linux is also case sensitive, whereas NTFS and windows aren't. That might sound minor, but it is frequently a pain in the behind.

:D

---

### Post by wyliecoyoteuk on 2012-03-08
You can see all the hidden files and folders by going to the view menu and clicking "show hidden files"

---

### Post by wyliecoyoteuk on 2012-03-08
deleted

---

### Post by pog12156 on 2012-03-08
ah i see. hmm well is it possible just to move some of the sub folders? like music, pictures, videos, and documents.

---

