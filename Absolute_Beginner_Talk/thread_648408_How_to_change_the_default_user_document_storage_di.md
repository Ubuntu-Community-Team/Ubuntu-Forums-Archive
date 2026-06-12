---
title: "How to change the default user document storage directory?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by bettyhills on 2007-12-23
Reading up on the linux filesystem structure, I understand that user day-to-day operations are typically stored in a directory named /home/username.  Is that correct?

I would like to store almost everything of a document nature on a different (fat32) partition shared with WindowsXP.  Ubuntu 7.10 can see the mounted fat32 partition.  

Can someone tell me exactly, step-by-step how to do this using a symbolic link?  Or direct me to online instructions on how to create symbolic links?

Alternatively, is there **another way **to get similar results since  I only want (documents, music, data, video) "content" files on the shared partition, and prefer to have my linux-specific software and settings, etc. on the linux ext partition in /home/username?

TIA

---

### Post by erginemr on 2007-12-23
Hello,

Those settings are kept inside the file: 
```
~/.config/user-dirs.dirs
```
In other words, in the file "user-dirs.dirs" inside the hidden directory ".config".

Thus, you can first create the same directories in the fat 32 partition you have mentioned and edit this file to point to those directories. Say, if your fat 32 partition has been mounted in your "/media/hdb1" directory, then you can use something like the following line:
```
XDG_DOCUMENTS_DIR="/media/hdb1/Shared/Documents"
```
instead of
```
XDG_DOCUMENTS_DIR="$HOME/Documents"
```

---

### Post by erginemr on 2007-12-23
On a second thought, keeping this file intact and using symbolic links as you also suggested, is a very good idea. Then, all you need to do is to delete the original directory (say, Documents) in your home folder, create the same in your new partition and finally, create a symbolic link to it with the command:
```
ln -s <TARGET> <NEW LINK>
```
which, when exemplified, becomes:
```
ln -s /media/hdb1/Shared/Documents ~/Documents
```

---

### Post by jkblacker on 2007-12-23
You could put a job in your crontab that would copy all relevant file types (eg. *.odt, *.ogg) every hour, say. (This also has the added bonus that you have back-up copies stored, in case of data loss.) Would that be a suitable idea?

---

