---
title: "howto: copy a complete hard drive"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2006-04-09
Hi:

I want to copy all the files from one of my hard drives to another. I don't want to use cloning software or anything like that - I just want to copy all the files and folders.

How do I do this?

Thanks.

GM

---

### Post by ubernoob on 2006-04-09
do you mean like copy in an ordinary way?
sudo cp -r /media/disk1 /media/disk2

---

### Post by catlett on 2006-04-09
If I'm understanding right you just want to transfer your folders and files and not an operating system on the drive.
If all you want to do is transfer files and folders you can use a dvd or cd (depending on the size of your files and what kind of disk writer you have). But this assumes the hard drive you are copying to is already installed and is being run by an operating system.
For example if you have  2 computers. And you want all the files and folders from computer 1 to be moved to computer two. If computer 1 has a cd writer you just put a cd in and write all your files and folders to the cd. Then put the cd in computer 2 and copy all the files from the cd to a your hard drive. 

If you want to upgrade your hard drive from a 10gb to a 60gb and you want the files and folders to transfer to the new drive this will not work. Because you can't just copy the operating system over as a file. I can't really tell what you mean by copy folders without  ghosting software so I don't know if this is helpful.If this is off the mark, post a little more info about what your doing.
Also these days flash drives hold as much software as cds. You might want to use a USB flash drive to do the transfer. Regards

---

### Post by catlett on 2006-04-09
[QUOTE=ubernoob]do you mean like copy in an ordinary way?
sudo cp -r /media/disk1 /media/disk2[/QUOTE]
Is that command comparable to cloning a drive? Can you move a partition with an operating system that way? For example if I want to move a system that's on hdb2 to hda4  can I do it by the -r command followed by the original destination and the destination I want it to go to? Does this just copy or does it copy and erase the source destination? Sorry to cut in and ask questions but I want to move an install from my second drive to my 1st drive so I can put in a bigger 2nd drive. At the moment I was just going to partition and reinstall but if I could move it to another partition in the 1st that would be great.

---

### Post by aysiu on 2006-04-09
[QUOTE=catlett]At the moment I was just going to partition and reinstall but if I could move it to another partition in the 1st that would be great.[/QUOTE] You want a live CD and PartImage.

---

### Post by ubernoob on 2006-04-09
[QUOTE=catlett]Is that command comparable to cloning a drive? Can you move a partition with an operating system that way? For example if I want to move a system that's on hdb2 to hda4  can I do it by the -r command followed by the original destination and the destination I want it to go to? Does this just copy or does it copy and erase the source destination? Sorry to cut in and ask questions but I want to move an install from my second drive to my 1st drive so I can put in a bigger 2nd drive. At the moment I was just going to partition and reinstall but if I could move it to another partition in the 1st that would be great.[/QUOTE]

No, it will only copy the files. But the "-r" is recursive, so you also copy all the subfolders.

---

### Post by catlett on 2006-04-09
I don't mean to take over the thread but I wanted to say thank you.

---

### Post by mlind on 2006-04-09
does that cp command preserve file permissions and owners too?
I thought "cloning" wasn't possbile with cp. I've done it using tar tho.

---

### Post by GMachine_24 on 2006-04-09
Hi:

My apologies for not being more specific.

I want to copy a hard drive that only has data files on it - no operating system. So I just want to copy all the files and folders "as is" -  which I assume means I can do so using this command:

sudo cp -r /media/disk1 /media/disk2

Where disk1 is the hard drive with the data - in this case a 160GB drive - that is going to be copied to disk disk2 - in this case also a 160GB drive (blank and new and to be partitioned with one partition, as is disk1, and formatted).

Thanks and don't worry about taking over the thread - the more the ... better....

GM

---

### Post by ubernoob on 2006-04-09
the cp does in a certain way preserve file permission. At least if you copy directly to another disk with same filesystem. But if you want to store it on a cd, you have to use tar. I think that cp does not preserve links the way it should either. So it is not a good idea for a file system. There is another command for that, but i can't remember what it is. (never used it)

in your case GMachine_24:


sudo cp -r /media/disk1 /media/disk2

will do fine. but you need to format disk2 before copying.

---

### Post by GMachine_24 on 2006-04-09
Thanks again to everyone.

I guess I just want to add that the only reason I am doing this is because I have 60 GB of music files on this one hard drive that have taken me years to collect - and although I have "backed up" the files using .tgz it seems . . . somewhat iffy to me how well those files will be preserved since I had to create a gigantic .tgz file to begin with and then had to split it into like . . . whatever 35 or 40 smaller 1.5GB zipped files because of the Linux upper file size limit of <2GB and expecting to be able to cut and then paste all those back together without some major you-know-what seems, as I said, iffy at best.

GM

---

### Post by ubernoob on 2006-04-09
I understand. Good luck with the copying :) Although linux doesn't have a limit on 2 GB. At lest not ext2,ext3,reiserfs and xfs. fat32, but thats not linux ;)

---

### Post by GMachine_24 on 2006-04-23
Hi:

I know Linux doesn't have a 2GB "limit" but according to the Ubuntu Wiki files above this size might not meet ISO 9660 standards . . . and might not be able to be restored...

You can read about it on this page

[https://wiki.ubuntu.com/BackupYourSystem?highlight=%28up%29%7C%28back%29#head-10cc310ec3b4dfbb1a70901c6a36bba71fad1955](https://wiki.ubuntu.com/BackupYourSystem?highlight=%28up%29%7C%28back%29#head-10cc310ec3b4dfbb1a70901c6a36bba71fad1955)

If this is not true I'd like to know because having 40 split files seems a little insane.

---

### Post by GMachine_24 on 2006-04-26
Hi:

I thought I should post how I ended up copying the hard drive as perhaps it will be useful information for others.

First, I ended up doing it on an FC4 system. Which shouldn't really matter but in the interest of full disclosure.

I used the "rsync" utility to copy drive 1 to drive 2 on the same computer. It was simple and efficient; in future updates rsync will only copy what has changed - i.e. an incremental backup.

The code is simple:

rsync -avz /music1 --force --ignore-errors /musicbackup

/music1 is the directory/mount point for the original music drive; /musicbackup is the directory/mount point for the backup drive.

when you're ready to do your second back up of the same hard drive, you use the same code, rsync figures which files are new/changed and copies only those.

rsync is useful for lots of other reasons - if you want to copy over a network you can easily encrypt using ssh and there are many other features of rsync.

this site has a lot of helpful information [http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)

This article (again) [http://www.linuxjournal.com/article/8590](http://www.linuxjournal.com/article/8590) has basic information for building a terrabyte backup system - the author uses FC4 but the same thing can be done easily with Ubuntu.

Happy back ups.

---

### Post by 3G-Buntu on 2006-05-15
Thaks for the info!

---

### Post by patrick295767 on 2006-05-15
That can maybe help : [http://patrick295767.sitesled.com/data/backup_your_harddisk.htm](http://patrick295767.sitesled.com/data/backup_your_harddisk.htm)
  
Greetings !
  
Patrick

---

### Post by GMachine_24 on 2006-05-27
The link in the previous post is dead - at least for the several times I have attempted to connect to whatever Web site that is . . . 



GM

---

