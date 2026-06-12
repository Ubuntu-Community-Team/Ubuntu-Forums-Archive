---
title: "File Manager"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Curulin on 2006-11-15
a) I have a MP3 player with 256mb storage and usually I can put 4-5 albums on it.
Now with Ubuntu I have problems.
I used XNC to delete all the old files and to copy new MP3s on it. After one album, about 40mb, it said the device was full.

Why?

b) Since XNC looks a bit hard to handle, I decided to install Nautilus.
I'm a complete Linux newbie, I have installed all my software so far with "add package" and Automatix.
Nautilus is part of neither.
I downloaded and unpacked Nautilus, now how do I install it?

---

### Post by doh224 on 2006-11-15
hi I think I can help you with b 
what is the name of the file?

-doh

---

### Post by george29 on 2006-11-15
If you're using Ubuntu then correct me if i'm wrong but Nautilus is the default file manager. so you should be using it anyway?

when you deleted the files on your mp3 player, did you check to make sure that you deleted the files from .trash as well. It could be that you deleted the files, this moves them to .trash but doesn't actually free up the space until they are deleted from .trash too.

George

---

### Post by EndianX on 2006-11-15
> when you deleted the files on your mp3 player, did you check to make sure that you deleted the files from .trash as well.

That is almost certainly the problem.  I had the same thing happen a while back and found that the files were not actually deleted, but rather moved to a hidden directory.  Set Nautilus to allow you to see hidden files, or use command line and delete the trash folder.

---

