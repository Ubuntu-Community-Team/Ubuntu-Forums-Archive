---
title: "Permission Question.."
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by nconceicao on 2007-08-13
I recently added my external HD to my Server.. and I now attempt to map to it from my laptop and try to copy data to it and it keeps saying I do not have permission to write "anyware on the drive", natually this was formated in Windows 2003.. is there a way to correct this so I can copy to and from it? I can't even create folders on it or ftp too it.. I was thinking of copying all the content from it to another drive and partition it using linux.. but is there an alternative??

Thank You

---

### Post by sparks0548 on 2007-08-13
Is this a Kubuntu or Ubuntu installation.  in Kubuntu there is a section in the System Panel that refers to how disk is mounted and what File System type there is.

Try these links for additional information:

[http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585)

[http://ubuntuforums.org/showthread.php?t=445387](http://ubuntuforums.org/showthread.php?t=445387)

[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)

---

### Post by bluenova on 2007-08-13
I'm guessing your drive is formatted in NTFS. You need to install '[ntfs-3g]("http://packages.ubuntu.com/feisty/otherosfs/ntfs-3g")' (from the universe rep) to be able to write to the drive.

---

