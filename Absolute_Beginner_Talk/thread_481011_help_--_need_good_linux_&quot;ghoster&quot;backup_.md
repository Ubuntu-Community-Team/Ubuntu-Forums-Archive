---
title: "help -- need good linux &quot;ghoster&quot;/backup util."
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2007-06-22
I am needing to back up 10GB of data and Windows isn't doing the trick for me.
Why?  Because Windows filenames have a length limit of a certain number of characters.
So the copy (right-click process or other Explorer copy functions) cancels out and
stops when it reaches a single file that has too long of a filename.

The hard drive I am copying from has a corrupted Windows installation.  So what you 
read above is from taking out the HD and placing it into a slave on a second computer. 

Can anyone give me the name of their favorite backup utility that would exactly
(as in "exactly") copy all the files of an NTFS folder on this slave HD, onto
a FAT32 partition which I plan to create alongside with a beautiful Ubuntu 7.03 installation?

Thank you!!!

---

### Post by eentonig on 2007-06-22
I use rsync to bu my /home folder on a seperate HD.

---

### Post by Malibu Illusion on 2007-06-22
> **Average_Joe said:**
> Can anyone give me the name of their favorite backup utility that would exactly
(as in "exactly") copy all the files of an NTFS folder on this slave HD, onto
a FAT32 partition which I plan to create alongside with a beautiful Ubuntu 7.03 installation?

Yes, I'm sure they can.

---

### Post by Average_Joe on 2007-06-22
Only one vote so far for rsync / Grsync ... **_any others?_**
Remember this will be copying files from an NTFS partition which is located on a slave drive,
to the master HD where Ubuntu will be installed.

---

