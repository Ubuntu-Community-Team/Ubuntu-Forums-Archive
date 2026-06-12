---
title: "Really Newbie.."
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by Settler on 2006-02-16
Hello,

I would like to ask you how can I delete a directory from my computer desktop which wants 'root' privileges to be deleted...
I would like to ask the same thing for a file which is in the main file system.

And third for the time being..
How can I play music files that are in NTFS partitions..
Thanks a lot

---

### Post by aysiu on 2006-02-16
To delete a directory, do this: go to Applications > Accessories > Terminal and type ```
sudo rm -R /directory_name
``` Be **very** careful, though, that you don't remove a directory that will screw up your system if removed.

*sudo* means *with administrative privileges*
*rm* means *remove*
*-R* means *recursively* (so, for every directory within this directory)

You'll be asked for a password, use your user password.

For more details, see the third link of my signature.

To mount your NTFS partition, see the fourth link of my signature.

---

### Post by Settler on 2006-02-16
Thanks alot...
I just mounted NVIDIA driver for nvidia geforce 6600... But my max resolution is 1280x1024... Why can I not have a higher resolution?..If I can how can I???

---

