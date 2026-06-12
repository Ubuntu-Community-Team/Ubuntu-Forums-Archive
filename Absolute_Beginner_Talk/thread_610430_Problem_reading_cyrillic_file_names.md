---
title: "Problem reading cyrillic file names"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by SunmanXII on 2007-11-12
Hello - 

I am having a really weird problem with a DVD my friend gave me. This DVD was burned on winidows XP. The DVD contained a bunch of folders with cyrillic names. Inside those folders were a lot of files - all with cyrillic names.

The first problem that I encountered was that Ubuntu could not read any of the file or folder names. They would all show up as a series of question marks. Of course if I copied and renamed them typing the cyrillic names in myself the file names could be read.

The scound problem that I encountered was the following. If I opened up the DVD with FIle Manager _it would not read files with the same lengths (i.e. with the same amount of question marks_. Thus, I could not see some of the folders. However if I looked at the dvd using the terminal all the folders would show up (but still as a series of question marks). When I tried to copy the directory from the DVD onto my hard drive using the terminal it gave me the following error for all the folders that had same lengths as another folder on the DVD 
```
"cp: will not create hard link `/path//???????' to directory `/path/???????'
```

Any ideas as to why this happens and how I could fix it?

Thank you!

---

### Post by mikewhatever on 2007-11-12
To solve it, you'll need to edit the line for cd-rom in /etc/fstab. I saw the trick on the Russian forum, but can't find the thread now. Luckily, I've written it down. First, back up your original fstab:
> sudo cp /etc/fstab /etc/fstab_backup

Now, open fstab for editing <gksudo gedit /etc/fstab>, and add **iocharset=utf8** to the cd-rom line. It seems that the default mounting option does not see Cyrillic characters. Below are examples of the cd-rom line from my fstab, first the original, then the edited.

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,**iocharset=utf8**     0       0

Hope it makes sense, cheers.

---

### Post by SunmanXII on 2007-11-12
> **mikewhatever said:**
> To solve it, you'll need to edit the line for cd-rom in /etc/fstab. I saw the trick on the Russian forum, but can't find the thread now. Luckily, I've written it down. First, back up your original fstab:


Now, open fstab for editing <gksudo gedit /etc/fstab>, and add **iocharset=utf8** to the cd-rom line. It seems that the default mounting option does not see Cyrillic characters. Below are examples of the cd-rom line from my fstab, first the original, then the edited.

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,**iocharset=utf8**     0       0

Hope it makes sense, cheers.

This worked like a charm.

Thank you SO MUCH! :):)

---

