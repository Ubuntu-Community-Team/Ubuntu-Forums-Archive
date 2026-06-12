---
title: "retrieve files from windows D: when reformatting with linux?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by j_evenstar on 2007-05-08
hello, this is really my first time with the linux live cd. before anything else, my windows pc currently crashed and i decided to reformat it. however, it seems that my windows installer also crashed and keeps on hanging. now, i want to check if i reformat with linux, will my partitioned D: drive containing all my files be read by the new operating system? sorry for being such a noob about this..
thanks.

---

### Post by aysiu on 2007-05-08
Well, if you reformat it, your files will be gone, but you can use the live CD to retrieve the files *before* you reformat it.

Can you boot up the live CD, go to [a terminal](http://www.psychocats.net/ubuntu/terminal), and paste this command in: ```
sudo fdisk -l
``` and then paste the output back here in this thread?

---

### Post by j_evenstar on 2007-05-08
thanks for the quick response! here's the output: 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/hda2            3825        9963    49311517+   f  W95 Ext'd (LBA)
/dev/hda5            3825        9963    49311486    7  HPFS/NTFS
ubuntu@ubuntu:~$

i really didn't know where the terminal was!! anyway, if you meant retrieve the files before i reformat it, do you mean that i have to have an external storage? (flash drive, external hard drive). since i don't have such a large external storage device.. i just wish not to lose them even if i switch to linux ubuntu.

---

### Post by aysiu on 2007-05-08
Well, I kind of was hoping you'd have an external storage device. No iPod? Nothing? Can you email yourself files? Or they're too big?

It is possible to install Ubuntu and resize the existing Windows partition in the process, and the resizing process about 99.9% of the time is non-destructive, but there is the off chance that it might damage something, so if it's possible to rescue the files first *just in case*, you should try it.

Paste these commands into the terminal: ```
sudo mkdir /media/recovery1
sudo mkdir /media/recovery2
sudo mount -t ntfs /dev/hda1 /media/recovery1 -o nls=utf8,umask=0222
sudo mount -t ntfs /dev/hda5 /media/recovery2 -o nls=utf8,umask=0222
``` Then, if you're using Ubuntu, paste in ```
nautilus
``` If you're using Kubuntu, paste in ```
konqueror
``` If you're using Xubuntu, paste in ```
thunar
``` A file browser should open (like Windows Explorer, sort of). Press Control-L and type ```
/media
``` Then hit **Enter**. You should see two folders in there--*recovery1* and *recovery2*. If you enter those folders, you should see the contents of your Windows partitions. Then, it's up to you what you want to do from there (email the files to yourself, copy them somewhere, etc.).

If you want to resize the partition afterwards and install Ubuntu, this will walk you through that process:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Nythain on 2007-05-08
you could also just make sure not to reformat it during the ubuntu install, and actually create a mount point for it during the partitioning phase of the install...

---

### Post by aysiu on 2007-05-08
> **Nythain said:**
> you could also just make sure not to reformat it during the ubuntu install, and actually create a mount point for it during the partitioning phase of the install...
Well, that's the second part of my post, but it'd be nice to back up the essential files just in case the resizing process does something bad.

---

### Post by j_evenstar on 2007-05-08
thanks for your responses.can't believe im seeing my D: files..
so it's possible to reformat with ubuntu and still recover my windows partitions files.. i don't have the storage, and i won't be having it anytime soon, so ill just rely on that. but will the resizing of partitions not change the size of the files themselves? will all remain?  and i have another question.. can i save files if im using the live cd? uhm just wondering.. since im really such a newbie with ubuntu linux..

---

### Post by aysiu on 2007-05-08
Well, you're not really reformatting the whole drive.

What you're doing is resizing the existing partition (which currently takes up the whole drive) and then using the freed up space to make a new partition. That new partition is the one that will be reformatted to install Ubuntu.

Think about it this way: 

You have a big room full of junk, scattered throughout (Windows partition with data).

Then, you decide you want to put in a new room by dividing the room in two. Since everything's scattered about, you want to push it into a corner (defragment... though, you don't really have that luxury right now) so you have space for the new wall you're putting in. Once everything's in, you put in the new wall (reformat the new partition) and start putting more junk in the new room (installing Ubuntu on the reformatted partition).

You can get a better visual sense of it here:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by j_evenstar on 2007-05-08
thanks! i'll go through the sites you've mentioned, and ask again to confirm anything i'm doing..

---

