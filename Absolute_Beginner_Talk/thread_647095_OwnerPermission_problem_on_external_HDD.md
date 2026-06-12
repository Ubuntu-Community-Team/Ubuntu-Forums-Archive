---
title: "Owner/Permission problem on external HDD"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Tytal on 2007-12-21
In a similar vein to [this thread]("http://ubuntuforums.org/showthread.php?t=647024") (and a few others), I have a problem with my external HDD. I've read a number of similar threads, but those users all seemed to have trouble mounting their drives; I just can't delete anything.

Unlike that user, I can see and access all my files, I just can't save anything new to the drive or delete anything from it. When I check the file permissions, it says user "unknown" and I can't seem to choose a new owner or assign a new group.

I'm running Gutsy/7.1 and now I'm terribly confused. Things seemed to be working okay until I went up to Gutsy.

Cheers,
Michael

---

### Post by jken146 on 2007-12-22
Have you tried changing the permissions of the files on the drive, or of the mountpoint for the drive?  What filesystem is the drive formatted in?

---

### Post by raffytaffy on 2007-12-22
Try this dosfsck -a /dev/sdc1  ( replace sdc1 with proper drive )

The following file system problems can be corrected using this program:

    * FAT contains invalid cluster numbers.
    * Directories with a large number of bad entries (probably corrupt). The directory can be dropped.
    * Files . and .. are non-directories.
    * Directories . and .. in root directory. They are dropped.
    * Bad file names. They can be renamed.
    * Duplicate directory entries. They can be dropped or renamed.
    * Directory . does not point to parent directory. The start pointer is adjusted.
    * File contains bad or free clusters. The file is truncated etc

---

### Post by jken146 on 2007-12-22
Isn't dosfsck just for FAT filesystems?

---

### Post by raffytaffy on 2007-12-22
Sorry, I thought your external was FAT

---

### Post by raffytaffy on 2007-12-22
Well you can always try
sudo chown -R user /dev/hda#  ( again replace hda with proper drive
sudo chmod 777 /dev/hda#

Then reboot and see if it mounts correct,.

---

