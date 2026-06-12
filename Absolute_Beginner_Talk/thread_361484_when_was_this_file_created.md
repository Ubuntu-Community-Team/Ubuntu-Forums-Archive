---
title: "when was this file created?"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by kelbizzle on 2007-02-14
After right clicking a file I click properties. It shows when it was modified and accessed...although it doesn't show when it was created. Can I do this?

---

### Post by Jussi Kukkonen on 2007-02-14
Linux filesystems do not save the creation time, as far as I know.

---

### Post by kelbizzle on 2007-02-14
wow really. I better do some googling and find out why.

---

### Post by Yuzem on 2007-05-02
Did you find out why?
I'm very disappointed with this... :(

---

### Post by Tiede on 2007-05-02
Apparently, no one really, in the end, need the original creation date of a linux file. Therefore it has fallen in the "We don't need it, so we don't care" category.
The information you will find from the inode of a particular file are *atime, mtime and ctime* which are respectively: the *last access time* (last time the file was open to be **read**, the *modification time* (last time **the file was modified** in any shape of form; changed. appended, etc...) and the *change time* (last time the ***inode information*** for that file was modified (change of permissions, ownership, size, etc... of the file).
In a sense, it does make sense that the creation date of a file is not really needed. Even for backup purposes. So the devs do have a point. It's still, nonetheless, a fact as intriguing as it is interesting.

Hope I helped!!!

---

### Post by Yuzem on 2007-05-02
Then ctime is used instead of the creation date.
How can I get the ctime info?

---

### Post by Tiede on 2007-05-03
providing the option -l to *ls* should provide you with atime, mtime and ctime information (AFAIK).
For example:
```
ls -l ~/myfile
```
I want to point out though that ctime is **not** closely related to creation date. As one can observe, if a file is modified (changing it's mtime information), it's size is more than likely to change, thus also changing the ctime.
Furthermore, each time a file is renamed, the ctime is inevitably changed, and therefore the ctime may show a more recent date than the mtime - which is just fine if one thinks of it as *inode info change time*. Verily, if it was the creation time, we would have a logical error, since it is obviously impossible for the file to be modified before it is created! ;)

---

### Post by Yuzem on 2007-05-03
Thanks but I'm only getting one time:
```
ls -l asdfasfd
-rw-r--r-- 1 azd azd 9 2007-05-02 09:29 asdfasfd
```

---

### Post by Tiede on 2007-05-06
sorry. I forgot one argument. in my writing. **-l** only gives mtime (The modification time). To see the change time, the proper command is ```
ls -lc
```. --replace -lc with -lu for atime (access time).
Otherwise, you can use the **stat** command to view all three times...
It can be used as such: ```
stat /path/to/file 
```.
Sorry for the confusion.

---

### Post by Yuzem on 2007-05-07
That works...
Thanks!

---

### Post by carpetn on 2007-06-07
> **Tiede said:**
> Apparently, no one really, in the end, need the original creation date of a linux file. Therefore it has fallen in the "We don't need it, so we don't care" category.

In a sense, it does make sense that the creation date of a file is not really needed. Even for backup purposes. So the devs do have a point. It's still, nonetheless, a fact as intriguing as it is interesting.

Hope I helped!!!

I don't agree that date of creation is not an important bit of data. One can imagine legal situations in which it would be very important. Also for personal use. Say I take some notes in 2003 and add some in 2004. Then today it could be useful or even important for me to know that I started that file in 2003.

According to Nicholas Wells in _The Complete Guide to Linux System Administration_, "Linux maintains a set of timestamps for each file and directory that define when the file was created, when it was last modified, and when it was last accessed" (35). He also notes that the command "ll" in Red Hat Linux gives that information. 

Fedora Core 4 gives modified date, not creation date for "ll". Wells's book is based on FC2. Things may have changed since FC2 or he may have been mistaken. The key question is whether he was mistaken that the timestamp saves the date of creation. Also, whether this is different for Ubuntu.

Thanks.
carpetn

---

### Post by Cypher on 2007-06-07
> **carpetn said:**
> I don't agree that date of creation is not an important bit of data. One can imagine legal situations in which it would be very important. Also for personal use. Say I take some notes in 2003 and add some in 2004. Then today it could be useful or even important for me to know that I started that file in 2003.

According to Nicholas Wells in _The Complete Guide to Linux System Administration_, "Linux maintains a set of timestamps for each file and directory that define when the file was created, when it was last modified, and when it was last accessed" (35). He also notes that the command "ll" in Red Hat Linux gives that information. 

Fedora Core 4 gives modified date, not creation date for "ll". Wells's book is based on FC2. Things may have changed since FC2 or he may have been mistaken. The key question is whether he was mistaken that the timestamp saves the date of creation. Also, whether this is different for Ubuntu.

Thanks.
carpetn
Wells is mistaken and the command "ll" is nothing more than an alias to "ls -l" and not a separate command unto itself. If you intend to keep a file that contains chronological information, I think it is far more useful to put the date within that file as you make your entries as opposed to knowing that you started the file in one arbitrary day in a particular year.

I think the access time and modification time are a lot more important for various reasons. In all my playing with Linux both on a professional and personal level I've never had to worry about when a particular file was created.

I cared more about when I had touched it and even more important when I last modified it to know that it's recent and relevant enough..

---

### Post by Yuzem on 2007-06-07
I also think that it is important. For example with pictures that doesn't have any special info. If I want to retouch those pictures then how will I do to know the date that they were taken?
I could save that info in the filename but many applications like Picasa sort the pictures in function of the time stamps.
In Picasa creation date is there:
View > Sort Folder List by > Creation day, Name or Recent Changes.

The same applies to mp3 files, some players allow to sort the music by "added time" but if I tag the files or if I apply mp3gain I will change that info in a way that it will be no longer useful to me.

For files that I normally edit it is more useful the modification time stamp but for files that doesn't suppose to be changed (but eventually they will for one or another reason) the creation time is more useful.

I don't want (normally) to know when I changed the tag in an mp3 nor when I fix red eyes on a photo.

---

### Post by Cypher on 2007-06-08
As far as pictures goes, the creation date as well as a lot of other information from the digital camera is stored within the image's EXIF data. So any smart photo software will read that info instead of relying on some arbitrary file creation date.

---

### Post by Yuzem on 2007-06-08
Yes you are right but I said "with pictures that doesn't have any special info"
For example for pictures that were scanned. I don't know if modern scans saves EXIF data but old scans and old digital cameras doesn't.

Another example are pictures that are saved from the web,art sites, photography sites, etc...
I will prefer to have the time when I added those pictures to my collection.

---

