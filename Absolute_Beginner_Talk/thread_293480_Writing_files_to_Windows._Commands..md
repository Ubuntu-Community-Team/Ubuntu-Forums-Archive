---
title: "Writing files to Windows. Commands."
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by pilgrim-online on 2006-11-05
I am having considerable problems trying to work out what commands to type into terminals.
Unless I can find one ready made for the job in hand I am lost as to what to try.
I am reluctant to experiment in case I disrupt something.

I have used the following web page to set up read and write access to my Windows partition from Ubuntu 6.06.
I have tried the test and it works.
[http://tinyurl.com/fqc8g](http://tinyurl.com/fqc8g)

With the test it placed an empty file on my [C:\] drive.
What I need is a command that will copy a file from my Home Folder in Ubuntu to My Documents in Windows.

I did try to do it by dragging and dropping, which would be my prefered option, but got a message saying that I did not have permission.

Can anyone provide a specific command for this operation?

Does anyone who uses 'fuse' know if drag and drop is possible, if so how do you set it up with permission?

Is there anywhere that basic commands are listed, with explanations, either on a website or within Ubuntu?

---

### Post by apjone on 2006-11-05
you need to build NTFS write into your kernal and then allow users to write to that filesystem. sorry forget how to do it but try searching the forum or google


> **pilgrim-online said:**
> I am having considerable problems trying to work out what commands to type into terminals.
Unless I can find one ready made for the job in hand I am lost as to what to try.
I am reluctant to experiment in case I disrupt something.

I have used the following web page to set up read and write access to my Windows partition from Ubuntu 6.06.
I have tried the test and it works.
[http://tinyurl.com/fqc8g](http://tinyurl.com/fqc8g)

With the test it placed an empty file on my [C:\] drive.
What I need is a command that will copy a file from my Home Folder in Ubuntu to My Documents in Windows.

I did try to do it by dragging and dropping, which would be my prefered option, but got a message saying that I did not have permission.

Can anyone provide a specific command for this operation?

Does anyone who uses 'fuse' know if drag and drop is possible, if so how do you set it up with permission?

Is there anywhere that basic commands are listed, with explanations, either on a website or within Ubuntu?

---

### Post by Theimon on 2006-11-05
Try the How-to from this page [http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)
It worked like a charm here. I no longer have NTFS disks but the time I did I could perform any action I wanted on my NTFS disks. I didn't get errors or dataloss so give it a try.

---

### Post by givré on 2006-11-06
> **apjone said:**
> you need to build NTFS write into your kernal and then allow users to write to that filesystem. sorry forget how to do it but try searching the forum or google
Damn not, the write support for NTFS of the kernel driver is really bad, and should not be use. You might rather use alternative like ntfsmount or ntf-3g.

---

### Post by pilgrim-online on 2006-11-06
Thanks for your replies but I do not think they will answer my questions.

The 'fuse' software is working, I can access/edit my Windows files but I have a problem with direction when I want to copy a file to Windows.

On the page I followed, the test instruction created a new file in Windows that did not previously exist either in Ubuntu or Windows.
What I am looking for is a direct way of copying an existing file from Ubuntu to Windows without having to use an external device like a Pen Drive as I do now.

I might try ntfs-3g at some time if I cannot sort it out with fuse, but I am still going to have the problem of not knowing what command to enter, or how to set up permission if I do not have it.

When I tried to drag and drop a file it did not say that it was not possible, only that I did not have permission.
Which comes back to my other point about needing a list of basic commands and their definitions.

Until a few weeks ago I had never used or even seen Linux, since then I have done a great deal, some of it with help from others, but very often I have read or been given instructions, most of which which have worked, without my having the faintest idea of what those commands are actually doing. 
If I had such a list I would at least have some idea of what I might try before I have to start asking others.

Not only is Linux a whole new type of OS to me, the terminology used is a whole new language, and while I never expect to learn a great deal of it, a grasp of the basics would be very useful.

---

### Post by Theimon on 2006-11-06
Well, I really have to say that if you easy access to your NTFS drives from bootup, try the ntfs-3g how-to. You can edit your fstab in such a way that, when properly installed, ntfs-3g will let you drag and drop files anyway you want. 
Just follow the steps mentioned in the first post over there.

---

### Post by pilgrim-online on 2006-11-06
Theimon,

You've talked me into it, I'll give it a try when I have the time.
Thanks.

---

### Post by Average Joe on 2006-11-06
Your NTFS Windows partition is probably mounted such that only root has write permissions.
You can give yourself write persmission to it by changing your /etc/fstab file. At the entry of your Windows partition, you should put the mount options
> defaults,locale=en_US.utf8,uid=1000,gid=1000,fmask=0133,dmask=0022
assuming that you want the locale en_US.utf8 and you have user id 1000 (which is the default for the first user created within Ubuntu).

And, as already mentioned earlier, the best NTFS driver for Linux is probably ntfs-3g. You can just install it from the (universe) repositories. I use it myself, and it works perfect.

---

### Post by pilgrim-online on 2006-11-07
I have installed ntfs-3g and no matter what I have tried I cannot mount the ntfs partitions.
I have followed the instructions on the Howto and cannot see what I am doing wrong.
I have written to **givre** to see what he makes of it, in the meantime the error message I get is:

[mntent]: line 8 in /etc/fstab is bad
[mntent]: line 10 in /etc/fstab is bad
mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab

and /etc/fstab reads:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1   *   /media/ntfs     ntfs-3g defaults,locale=en_GB.utf8   0       0
/dev/hda3       /media/ntfs     ntfs-3g defaults,locale=en_GB.utf8   0       0   
/dev/hda4       /media/fat32    W95 FAT32 [LBA]   defaults        0       0

I do not know why the error message shows Line 10 is bad as the FAT 32 partition is mounted?

---

### Post by taurus on 2006-11-07
> **pilgrim-online said:**
> I have installed ntfs-3g and no matter what I have tried I cannot mount the ntfs partitions.
I have followed the instructions on the Howto and cannot see what I am doing wrong.
I have written to **givre** to see what he makes of it, in the meantime the error message I get is:

[mntent]: line 8 in /etc/fstab is bad
[mntent]: line 10 in /etc/fstab is bad
mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab

and /etc/fstab reads:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1   *   /media/ntfs     ntfs-3g defaults,locale=en_GB.utf8   0       0
/dev/hda3       /media/ntfs     ntfs-3g defaults,locale=en_GB.utf8   0       0   
/dev/hda4       /media/fat32    W95 FAT32 [LBA]   defaults        0       0

I do not know why the error message shows Line 10 is bad as the FAT 32 partition is mounted?

Look at your /etc/fstab again!!!  How come there is a * in there, line 8???  And the last line doesn't even look right...  It should look something like

```

/dev/hda4   /media/fat32   vfat   defaults,umask=0000   0   0

```

---

### Post by smoker on 2006-11-07
hi, Pilgrim,

this link may help with your linux commands, there is also a link to the man pages at the end for more info,

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

hope this helps

---

### Post by pilgrim-online on 2006-11-07
**taurus,**

"Look at your /etc/fstab again!!! How come there is a * in there, line 8??? And the last line doesn't even look right... It should look something like 
Code:
/dev/hda4 /media/fat32 vfat defaults,umask=0000 0 0"

The only answer I can give you to the first part of your question is that I assumed it marked the Boot Partition.
As to the second part, that partition [/dev/hda4] is actually mounted and accessible.
Neither of these things explain why I cannot access /dev/hda3 my other NTFS Partition, yet that didn't appear in the error message?

My knowledge of this is not sufficient to understand it, so if there are even very basic mistakes I have no way of knowing.

**smoker,**

That's exactly the sort of thing I was looking for, as soon as I have the time I'll make a copy and study it, thanks.

---

### Post by givré on 2006-11-07
> **pilgrim-online said:**
> **taurus,**

"Look at your /etc/fstab again!!! How come there is a * in there, line 8??? And the last line doesn't even look right... It should look something like 
Code:
/dev/hda4 /media/fat32 vfat defaults,umask=0000 0 0"

The only answer I can give you to the first part of your question is that I assumed it marked the Boot Partition.
As to the second part, that partition [/dev/hda4] is actually mounted and accessible.
Neither of these things explain why I cannot access /dev/hda3 my other NTFS Partition, yet that didn't appear in the error message?

My knowledge of this is not sufficient to understand it, so if there are even very basic mistakes I have no way of knowing.

**smoker,**

That's exactly the sort of thing I was looking for, as soon as I have the time I'll make a copy and study it, thanks.
Ok man, i understand why you write it like that ;) .
The table that give you fdisk as nothing to do with how you shoud write your /etc/fstab. To know how to write it, and the command you can use, i recommand you to read the manual :
```
man mount
``` 
In fact, fdisk is a command line partitionner, so it has nothing to do with fstab. But we can use it, when you do `sudo fdsik -l`, just to know the partition of your HD(s) and their formats. If you want to know more :
```
man fdisk
```
But be carfull with fdisk, it's a real partitionner, that can erase everything if you don't take care ;)

---

### Post by taurus on 2006-11-07
> **pilgrim-online said:**
> **taurus,**

"Look at your /etc/fstab again!!! How come there is a * in there, line 8??? And the last line doesn't even look right... It should look something like 
Code:
/dev/hda4 /media/fat32 vfat defaults,umask=0000 0 0"

The only answer I can give you to the first part of your question is that I assumed it marked the Boot Partition.
 
In fdisk, yes but not in /etc/fstab.  Therefore, you need to remove that * from line 8.  Also, why do you have two different partitions, /dev/hda1 & /dev/hda3, mount to the same mount point, /media/ntfs???

Maybe mount the first one to /media/ntfs_1 and the second one to /media/ntfs_3...

> As to the second part, that partition [/dev/hda4] is actually mounted and accessible.
Neither of these things explain why I cannot access /dev/hda3 my other NTFS Partition, yet that didn't appear in the error message?

My knowledge of this is not sufficient to understand it, so if there are even very basic mistakes I have no way of knowing.

So, you can modify your /etc/fstab as I told you or you can leave it the way it is right now.  It's up to you but I think there is a big problem with your /etc/fstab.

1.  There shouldn't be any * in line 8.
2.  You can mount two different drives to the same mount point but you won't be able to access the first partition since the second one is mounted on top of the first one.
3.  Modify the last line of your /etc/fstab about your fat32.

It's up to you if you want to make those changes...

---

### Post by pilgrim-online on 2006-11-08
To start with everything is now working as it should.
I edited Lines 8+10 and got a different error message.
I then altered Line 9 and it got sorted.

etc/fstab now reads:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/ntfs     ntfs-3g defaults,locale=en_GB.utf8   0       0
/dev/hda3       /media/windows     ntfs-3g defaults,locale=en_GB.utf8   0       0   
/dev/hda4       /media/fat32    vfat    defaults        0       0


I apologise if my lack of understanding caused frustration but like the name of this board suggests, where Linux is concerned I am an Absolute Beginner.

Thank you all for your help.

---

### Post by givré on 2006-11-08
> **pilgrim-online said:**
> 
I apologise if my lack of understanding caused frustration
You don't have to, you where all like you at the beginning. ;)

---

### Post by taurus on 2006-11-08
Actually, I would make the last line in /etc/fstab to look like this so I, as a regular user, can read and write to it!!!

```
/dev/hda4   /media/fat32   vfat   defaults,umask=000  0  0
```

---

