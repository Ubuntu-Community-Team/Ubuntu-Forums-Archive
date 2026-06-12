---
title: "[SOLVED] Advice on Making a Small Partition on one Disc"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by Andavane on 2008-03-01
Hello,
My PC arrangement is listed below.
Am still fairly new to Ubuntu, and would like to make an ntfs partition on the disc where my ext3 Ubuntu is. The reason for needing a fat 32 partition on the Ubuntu drive is that I regularly share my files with a colleague who uses Vista, and with more colleagues when I go to India who are all using XP. My colleague may work on some of my files in Windows, and then I do more work on them.

The reason for my working files being on the windows disc is that that was the system I used first. Ubuntu was installed on a 2nd drive due to lack of space on the windows drive.

I understand I will need to use the gparted program, but am naturally very nervous about partitioning in any way, as I only ever used "Partition Magic" before.

Am happy to be pointed to a good "how-to", or to have it explained, but for me to understand it, it would have to be pretty simple, as I still don't understand much of the terminology used in the forums.

Apart from that, I am liking Ubuntu very much indeed. It is fast and stable, does what I want it to do, and I don't get the impression that programs are sneaking in by the back door and wreaking havoc.

Regards

John

~   ~   ~   ~   ~   ~   ~  ~

[B]PC: IBM Think-Centre A-50 : 40 Gb
(5 partitions on it)

Hard Drive 0) Windows XP-Pro
Hard Drive 1) Ubuntu 7.0.4 “Feisty Fawn”, : 110 Gb
(in the bay which used to be the CD drive)[/B]

---

### Post by spiderbatdad on 2008-03-01
Not sure gparted is designed for existing file systems, unless you run the gparted LiveCd. Qt parted on the Ubuntu livecd, I believe, is preferred for resizing existing partitions. Have you considered Installing Ubuntu on the entire disk and running windows in a Virtual environment through VMware Server, available in synaptic. That's the safest way IMO to run windows. If, the windows os gets corrupted, you can reinstall it without affecting your Linux install.

---

### Post by beardiggin on 2008-03-01
--edited--
I'm not sure I fully understand; do you have 2 disks, one with windows and one with Ubuntu?  If so you may not need to do any modification  of your partitions.

--end edit--
I am not sure about 7.04 but I know that Gusty can read and write the NTFS file system.  My system is a dual-booting XP/Ubuntu(7.10) Gusty.  I have been storing my documents only on the XP partition so that when/if I boot windows I can see the documents.

if you have 2 disks you should be able to find your Windows Disk under /media.
if you open up a terminal and type 

ls /media

you should get a list of directories.  one of those should be your windows system.  I'm guessing it will be something like /media/sda1 or maybe /media/hda1.

Hope this helps.

---

### Post by dcstar on 2008-03-01
> **Andavane said:**
> Hello,
My PC arrangement is listed below.
Am still fairly new to Ubuntu, and would like to make an ntfs partition on the disc where my ext3 Ubuntu is. The reason for needing a fat 32 partition on the Ubuntu drive is that I regularly share my files with a colleague who uses Vista, and with more colleagues when I go to India who are all using XP. My colleague may work on some of my files in Windows, and then I do more work on them.

The reason for my working files being on the windows disc is that that was the system I used first. Ubuntu was installed on a 2nd drive due to lack of space on the windows drive.
..........
~   ~   ~   ~   ~   ~   ~  ~

PC: IBM Think-Centre A-50 : 40 Gb
(5 partitions on it)

Hard Drive 0) Windows XP-Pro
Hard Drive 1) Ubuntu 7.0.4 “Feisty Fawn”, : 110 Gb
(in the bay which used to be the CD drive)

Install the **ntfs-3g** package, then the **pysdm** package and use that to mount the Windows drive partitions, then you can use them for your data.

---

### Post by Duck2006 on 2008-03-01
Some reading on partitioning your drives.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

As far as ubuntu reading win xp on a ntfs, follow dcstar post.

---

### Post by Andavane on 2008-03-02
Thank you very much for your responses. To add a little more detail, on the “Disc 0” there is drive C where the XP is installed, that is 20 Gb, Drive D with 4½ Gb partition which the manufactuers set to reinstall the XP, the  the remainder of the space is divided into 3 smaller partitions; on one of these partitions is  a folder of 750 Mb which copntains my important data. These are written to and backed up daily, usually now in Ubuntu but sometimes also in XP, for the rare occasion when there is a job I am currently unable to perform in Ubuntu. It was due to the limited remaining space which made me get another hard drive (in the CD bay) of 120 Gb on which Ubuntu is housed and running. During the installation I just selected “use the largest area of free space available”, knowing it would select that drive. So it all went well, but I didn't understand too well what I was doing.

There were problems last year with this (which turned out to be a faulty small fan in the hard drive itself: members helped me track down the problem as being hardware related) but as the fan has been replaced now, things are running very well.

So as there appears not to be a problem as such, I am reluctant to fiddle with it too much: “If it ain't broke don't fix it” as they say.

It is just the thought that the Ubuntu is running well on the added drive (“Disc 1”), and yet every time I want to do the smallest thing it has to “cross over”  to the “Disc 0”. For my problems experienced last year, a member suggested that the “crossing over” might be an issue, hence the feeling that it might be better to have the Ubuntu and all my data on the “Disc 1”, but if I put my data there, it will be invisible to Windows.

I may be entirely wrong in my idea to add a small Windows-readable partition into the large exisitng drive containing Ubuntu – or perhaps “shrink” the existing partition and make a small ntfs or fat32 partition for say 15 Gb for my data.

Regarding your kind replies:

from beardiggin:
> I am not sure about 7.04 but I know that Gusty can read and write the NTFS file system. 
Really? Interesting.

> My system is a dual-booting XP/Ubuntu(7.10) Gusty. I have been storing my documents only on >the XP partition so that when/if I boot windows I can see the documents.
I have been doing much the same.

> if you have 2 disks you should be able to find your Windows Disk under /media.
if you open up a terminal and type 
ls /media
you should get a list of directories. one of those should be your windows system. I'm guessing it will be something like /media/sda1 or maybe /media/hda1.
Hope this helps.
Indeed, and the terminal tip is very useful.

from dcstar/david:
> Install the ntfs-3g package, then the pysdm package and use that 
to mount the Windows drive partitions, then you can use them for your data.
Yes, David I see what you mean. I studied that in the synaptyic package manager, and it says:
“ntfs-3g is based on FUSE (userspace filesystem framework for Linux), thus

you will have to prepare fuse kernel module to be able to use it.”, so am a little thrown by that.
What is preparing a fuse kernel? is that the pysdm? I see that is a graphical storage manager.
Apart from that it looks like a good idea. However the data I use are on a vFat partition and Ubuntu seems well able to write to that.

Regards
John

---

