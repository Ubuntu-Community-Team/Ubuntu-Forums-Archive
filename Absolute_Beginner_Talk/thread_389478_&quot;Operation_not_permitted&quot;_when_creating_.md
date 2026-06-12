---
title: "&quot;Operation not permitted&quot; when creating a link?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Phrawm48 on 2007-03-20
I have a FAT32 partition that I put "between" my Ubuntu Linux and Windows partitions to enable easy sharing of email profiles and other stuff between the two operating systems.

Most of the time it does what I want, but I'm now having trouble using either "ln" or Gnome to create a link to an HTML file on the FAT32 partition.

Gnome automatically mounts the FAT32 partition.  I can also mount it manually so I can access it via the command line with:

> sudo mount -t vfat /dev/hda8 /home/rbv/XFER -o iocharset=utf8,umask=000

I can then navigate to a sub-directory containing a bunch of HTML files, as follows:
> 
ric@ric-desktop:~/XFER/Tweener/Documentation_and_References/PNG-Definitive-Guide /html$ ls -l
total 1344
-rw-r--r-- 1 ric ric 24133 2003-07-20 11:22 biblio.html
...other files...
-rw-r--r-- 1 ric ric  1824 2003-07-19 22:22 cover.html
...other files...

What I now want to do is create a link named "index.html" to the file named "cover.html".  So I try the following "ln" command and receive an error message as follows:
> 
ric@ric-desktop:~/XFER/Tweener/Documentation_and_References/PNG-Definitive-Guide$ ln -s ./cover.html ./index.html
ln: creating symbolic link `./index.html' to `./cover.html': Operation not permitted

I've also tried prefacing the command with "sudo", but that doesn't change anything.

Note that I can create other sorts of files in this sub-directory, so I don't think it's a write permissions issue.  Also, if I move this stuff off of the FAT32 partition I can create the link.

Any ideas how I can create a link on this FAT 32 partition?  This seems like it should be so simple but I can't seem to do it...

Cheers & thanks,
Ric
SFO

---

### Post by lloyd_b on 2007-03-20
I'm afraid it is simple - you can't do it.  The "operation not permitted" is telling you that the filesystem type (FAT32) doesn't support symlinks. 

Lloyd B.

---

### Post by Phrawm48 on 2007-03-20
Alas.  Well, thanks for lettin' me know...

Cheers & thanks 'gain,
Ric
SFO

---

