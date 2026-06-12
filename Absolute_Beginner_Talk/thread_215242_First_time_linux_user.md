---
title: "First time linux user"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Razer on 2006-07-13
Hi!

I've been interested in Linux for a while and finally decided that Ubuntu would suit my needs. I've read lots of installation guides and have also searched this forum but I still have a question about partitioning. Here is the scenario. I have 2 harddrives. One of them is 50gig and contains windows, the other is 160 gig and is my storage drive. What I want to do is to install Ubuntu on my 50gig which already has my windows on it. I know that if I use the first partition option during the Ubuntu install this will work but I also want to partition my second harddrive so that I can save a file in Ubuntu, switch to Windows, and Windows can see it and vice versa. I know about NTFS but was wondering if could be possible. If this doesn't work, then I want to have 100gig for windows and 60gig for Ubuntu. Please tell what program to use in order to partition my 2nd harddrive. Thanks for reading this extremely long post.

---

### Post by shanepardue on 2006-07-13
in regards to the ntfs question, that's not recommended..i would say don't do it..but that's just me..maybe fat32 windows partition is an option?

---

### Post by madmetal on 2006-07-13
its better to partition the 2nd hdd in fat32 so you can access your files from both os.
you can read and write files at fat32 hdds from both linux and windows.
after installing ubuntu you can use gparted in order to partition the second drive.

---

### Post by Razer on 2006-07-13
Thanks for the quick reply. I'll probably format the 2nd hdd as fat32 then. Another question: I just remembered that I have some programs such as VLC player and quicktime and I do not want to loose them. If I select the first partition option during the Ubuntu install will those files disappear or stay where they are?

---

### Post by maniacmusician on 2006-07-13
Is the first option something like "resize partition and use remaning free space"? if so, then those will not get deleted. There's also plenty of multimedia apps like that in Ubuntu as well, (including VLC), so you may find yourself not going back to windows :D there's not many programs that don't have a linux equivalent

---

### Post by muep on 2006-07-13
What do you mean by selecting the first partition thing?

Also, the programs and stuff are stored on your hard drive like any other files you might possibly have. When installing Ubuntu, you need to make a partition for it and format it. This means that if you remove a partition to make room for Ubuntu or format an existing partition for it, your files on that partition **will** be lost.

An easy solution is to move the important stuff to a partition that you are not going to format or erase. Another quite easy way is to resize an existing partition so that there will unpartitioned space for Ubuntu. Resizing is not supposed to destroy any of your data, but to be sure, taking backups is a good thing.

Taking backups at least of the most important stuff, preferably to an external drive that is disconnected from the computer during the install, adds a lot of safety to the install.

---

### Post by BigDave708 on 2006-07-13
It wouldn't be a good idea to partition your second hard drive with NTFS. Ubuntu can't write to NTFS partitions (but can sometimes read them). It would make more sense to format it with FAT32 as then it is just a simple case of mounting the second hard disk in Ubuntu.

---

### Post by djsroknrol on 2006-07-13
Hi Razer...

You want to search google for GParted live CD, boot with that and repartition your first drive drive with it...Like everyone else is saying, you should consider a fat 32 partition on the second drive for a shared directory for sharing files..you can read a NTSF partition but it's not advisable writing to them has not been reliable...

---

### Post by Razer on 2006-07-13
Thanks for all the replies. After reading the posts, I've formatted the 2nd hdd as Fat32. Also, I've partitioned the first harddrive with a section for ubuntu, swap space, window space, and the rest as Fat32. This forum is very helpful :-D

---

### Post by XPuntu on 2006-07-13
Here's another suggestion Razer.

There's a tutorial on psychocats that explains different ways to partition your drive. 

[http://www.psychocats.net/ubuntu/partitioning.html]("http://www.psychocats.net/ubuntu/partitioning.html")

One good tool mentioned is [FS-DRIVE]("http://www.fs-driver.org/") for Windows. This lets windows see Ext3 Partitions. Much better than using FAT32 with it's 4GB file size limit.

---

### Post by Razer on 2006-07-13
Hey

I've partitioned the harddrives and have installed Ubuntu successfully. I was really impressed with the quick install.

---

