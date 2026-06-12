---
title: "Check md5 sums in Ubuntu ?"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-07-01
In windows I used digest it , is there a Ubuntu or linux equivalant ?  Thanks ;)

---

### Post by Herman on 2006-07-01
We don't need any GUI application for doing md5sum tests in Ubuntu because it's so easy to just type the following command in a terminal,
```
md5sum filename
``` Where: filename is replaced with the exact name of the file you want verified
Where: the file to be verified is located in your /home/username folder.

It often takes a short time, depending on the size of the file. A few minutes is not uncommon.

A tip is to use 'Tab completion' to type the filename, to do that, just type the first two or three letters of the filename to be entered rather than typing it all. Then press your 'Tab' key and the rest of the filename for the file you want verified will be auto-completed. That saves time and typing errors.

If the file is inside another folder even inside a series of folders, then you will need to enter the directory path before the filename for the command to work. Otherwise, just copy the file out from where it is and paste in into the open in your /home/username directory (folder).
Regards, Herman :D

---

### Post by Drakkor on 2006-07-03
Thanks,Herman ! It works. :p

---

### Post by dgray_from_dc on 2006-07-18
Is there an equally easy way for recursively creating and/or verifying sums for entire directories?  I have a massive video and MP3 collection (nearly 30GB) which I have moved around a number of times from drive to drive as it has grown.  I have irrecoverably lost data a few times using windows and have become paranoid about data integrity.

---

### Post by kabus on 2006-07-18
> **dgray_from_dc said:**
> Is there an equally easy way for recursively creating and/or verifying sums for entire directories?

I'd use the 'find' command, which can recursively search for certain file types and execute a command on matching files. So to create checksums for every mp3 in my music collection I'd do:

```
find /mnt/hdb5/music_collection/ -name *.mp3 -exec md5sum '{}' \; >checksums
```

Check the 'find' man page for the details.

To verify you'd just have to type:

```
md5sum -c checksums
```

---

### Post by dgray_from_dc on 2006-12-10
I've found a way to recursively create and check MD5 sums.  Krusader integrates MD5deep, SHA1deep and various other programs into itself allowing you to create and verify checksums in an easy to use GUI.

---

