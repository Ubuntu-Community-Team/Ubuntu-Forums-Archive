---
title: "NTFS External Drive.  What to do?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by TMBridge on 2006-08-06
Hey all,

I have recently installed Ubuntu and I'm loving it.  I have tried linux in the past(Red Hat, Mandriva, and Fedora 5) and I just couldn't get into it.  With this last installation, I have decided that I am going to try to make the switch.

I have a External HDD that is of NTFS format.  I understand that Linux cannot write to this drive.  I wonder is there a way that I can change the file system without format (as its a 300gb drive with tons of goodies on it), or would it be possible to use windows to make back-ups of all the files on another windows (ntfs) drive, *then* format and change the filesystem of the external drive, and then finally put the back-ups back in the external drive?

Also, to which filesystem should I change it? FAT32?

Thanks for your help!

Tim Bridge

---

### Post by lamego on 2006-08-06
There is no way to convert from NTFS to FAT32 without loosing data, FAT32 is the best option.

---

### Post by daone on 2006-08-06
Thought I'd post a reply to your question though you probably already did somthing by now.

I was on [www.digg.com](www.digg.com) awhile ago and dugg this article on sourceforge that fully supports NTFS read/write in Linux.

The link is here:

[http://sourceforge.net/mailarchive/forum.php?thread_id=23836054&forum_id=2697](http://sourceforge.net/mailarchive/forum.php?thread_id=23836054&forum_id=2697)

I was going to try it myself, I'll post my results in the future if nobody else post anything about this.

---

### Post by orb9220 on 2006-08-06
That is not true I had a 120GB ntfs with 87gigs of stuff and defrag the hell out of it.

Then ran partition magic and converted ntfs to fat32 with everything just fine.

Been using it with ubuntu and all is there and accounted for.

---

### Post by Frank Golden on 2006-08-06
> **TMBridge said:**
> Hey all,

I have recently installed Ubuntu and I'm loving it.  I have tried linux in the past(Red Hat, Mandriva, and Fedora 5) and I just couldn't get into it.  With this last installation, I have decided that I am going to try to make the switch.

I have a External HDD that is of NTFS format.  I understand that Linux cannot write to this drive.  I wonder is there a way that I can change the file system without format (as its a 300gb drive with tons of goodies on it), or would it be possible to use windows to make back-ups of all the files on another windows (ntfs) drive, *then* format and change the filesystem of the external drive, and then finally put the back-ups back in the external drive?

Also, to which filesystem should I change it? FAT32?

Thanks for your help!

Tim Bridge
Linux cannot safely and/or reliably write to NTFS. There are 
some purported solutions out there to allow writes but use at your own risk. NTFS is complicated and the property of M$ (read closed source) any schemes to write to NTFS from Linux is the result of "reverse engineering". 

If you have a place to temporarilly store the data
to, then just copy it to the temporary storage device. Then
format your 300 GB drive to Fat32. You may/probably will not be able to format to Fat 32 using XP tools but if you have
Partition Magic or another third party partitioner you will be able to. Try using XP first by right clicking drive in My Computer and choosing "format". From the drop down see if Fat 32 is available. If not you have to use third party partitioner.
Don't know if linux's QParted will work, it's free and available
from Synaptic. Be aware that Fat 32 has a big limitation for some folks, you cannot have a single file of 4GB on it.
For instance if some of the "goodies" you refer to are video files greater than 4 GB you won't be able to copy them to your
Fat 32 drive. Fat 32 also fragments more readily than NTFS.

You could use Partition Magic to convert on the fly. But if any
single file is 4 GB or greater in size it will probably fail.
And if I know PM you will probably corrupt your drive.
That's why it is best to copy everything somewhere else for
safekeeping. Partition Magic works OK, but it is a powerful
program and can mess things up if you are not careful.

---

### Post by Aurdal on 2006-08-06
Are you going to use the external drive with any non Linux computer? If not. your best option (IMO) would be ext3 or reiserFS. If you still want to use the disk for a windows partition on your computer, there are tools to make windows recognize your ext3 disk. (I believe it was made for ext2 but from what I gather it works with ext3 as well.)

-Aurdal

---

### Post by lamego on 2006-08-06
```
That is not true I had a 120GB ntfs with 87gigs of stuff and defrag the hell out of it.

Then ran partition magic and converted ntfs to fat32 with everything just fine.

Been using it with ubuntu and all is there and accounted for.
```
Are you expecting people to buy Part Magic to do a one time partition conversion :) ?

---

### Post by Frank Golden on 2006-08-06
> **lamego said:**
> ```
That is not true I had a 120GB ntfs with 87gigs of stuff and defrag the hell out of it.

Then ran partition magic and converted ntfs to fat32 with everything just fine.

Been using it with ubuntu and all is there and accounted for.
```
Are you expecting people to buy Part Magic to do a one time partition conversion :) ?
I just had a thought. After copying your data to a safe place.
Use windows start>run>diskmgmt.msc and delete your 300 GB NTFS
partition. You will end up with 300 GB unallocated space.
Then boot into Ubuntu and install QParted from Synaptic.
Plug in your drive and use QParted to format to Fat32.
I don't think you can use QParted to directly convert from 
NTFS to Fat32 because of the write to NTFS thing in Linux.
Food for thought. Remember to back up your data.

---

### Post by TMBridge on 2006-08-06
Thanks for the help guys.

Let me get this straight.  From what I understand, I have two options.  

(1)I can "defrag the hell" out of my external drive and do an on-the-fly conversion to FAT32 and hope that all my files are intact, except  >4gb files which will be lost regardless.

(2)Copy files to another source and *try* format to FAT32 through windows.  If windows doesn't offer that ability, use a third party software to format to FAT32.  Then copy the files back if they didnt survive the transition.

Is this correct?

EDIT:  I've done some reading and I have found out about more FAT32 limitations.  I've read that not only is the file size limit 4GB, but the partition size limit is 32GB and the drive size limit is 137GB.  Is this true?

Thanks again, all.

---

### Post by orb9220 on 2006-08-06
My 120Gb is one partition. But as others have said if you have a need to have
windows access the drive then ntfs would be more robust. And there is a  linux app that can read and write to ntfs but forget it's name 3g something.

---

### Post by christhemonkey on 2006-08-06
My experience with writing to NTFS with linux has been good.
No corruption, no problems, just install the driver with [this howto]("http://www.ubuntuforums.org/showthread.php?t=217009") and i was set to go.

But still, it shouldnt be used on production machines as it is not 100%, but then again, no driver is!

---

### Post by anaconda on 2006-08-06
You could also resize your current ntfs partition, and create a ext3/fat32 partition to the free space, then move some data to the new partition, and resize again etc.... finally you have changed your ntfs partition to whatever you want.

I would format it to ext3 and install this to windows..
[http://www.fs-driver.org/](http://www.fs-driver.org/)
however with removable disks there is a small problem with it. (in windows..) windows doesnt free the drive letter after removing the disk... not a big problem, but the workaround is here
[http://www.fs-driver.org/relnotes.html](http://www.fs-driver.org/relnotes.html)

And you wouldn't have to worry with the 4GB limit, or the bigger problem, that fat32 doesnt understand access rights.. eg. linux asks you if you want to execute or open the .pdf-file you just doublecliced..(because all files have all rights rwx, and x means that they are executables. (in windows .exe))

---

### Post by Aurdal on 2006-08-06
The 32 GB limit is limited to Windows XP/NT and only goes for mormatting. If you format a disk > 32 GB with other software Win XP/NT will still be able to use it.

---

### Post by Frank Golden on 2006-08-06
> **TMBridge said:**
> Thanks for the help guys.

Let me get this straight.  From what I understand, I have two options.  

(1)I can "defrag the hell" out of my external drive and do an on-the-fly conversion to FAT32 and hope that all my files are intact, except  >4gb files which will be lost regardless.

(2)Copy files to another source and *try* format to FAT32 through windows.  If windows doesn't offer that ability, use a third party software to format to FAT32.  Then copy the files back if they didnt survive the transition.

Is this correct?

EDIT:  I've done some reading and I have found out about more FAT32 limitations.  I've read that not only is the file size limit 4GB, but the partition size limit is 32GB and the drive size limit is 137GB.  Is this true?

Thanks again, all.
Here is some info from M$ about Fat 32 limitations

[http://support.microsoft.com/kb/184006/en-us](http://support.microsoft.com/kb/184006/en-us)

How much data etc do you have on the 300 GB drive?
You could create a large ext3 partition using QParted
in Linux and download and install the following free software to XP

[http://www.fs-driver.org/](http://www.fs-driver.org/)

that will let you assign a drive letter and access read/write
from XP. Of course you will have full access from Linux. I use this software on my dual boot. It places a control in your
control panel that shows your ext3 partition(s)and lets you assign drive letters to them. They then show up in My Computer as drives.
I normally leave my Ubuntu install without a drive letter unless I really need to access it from XP. And then I am careful not to 
change anything.

---

### Post by TMBridge on 2006-08-06
Thanks for all the help guys.  This is a great community.  

So right now I have:

-40gb internal slave hdd
   Partiton 1 (40GB) -> Linux (ext3)
-80gb internal master hdd
   Partiton 1 (10GB) -> Windows XP (ntfs)
   Partiton 2 (70GB) -> Storage (ntfs)
-300gb external hdd
   Partition 1 (297.8GB) -> Storage (ntfs)

This is what I've decided to do:

Step 1: 
I cleaned up my external drive and got rid of all data thats not valuable.  I have 80GB remaining without MP3s (110 with MP3s but I they are safely stored on my MP3 player and can be transfered over via gnomad later).

Step 2:
Store the 80GB of data on various other locales (i.e. Laptop/Friends computer)

Step 3:
Format the external drive with an ext3 filesystem.

Step 4:
Install driver from fs-driver.org onto windows systems that are storing my data.

Step 5: 
Copy data from windows systems back to the external drive.

...and thats it!

Before I actually go through with this, if anyone with more experience in this type of thing could give me a "sounds good!" or any tips, it would be greatly appreciated.

Thanks again all!

---

### Post by Frank Golden on 2006-08-06
> **TMBridge said:**
> Thanks for all the help guys.  This is a great community.  

So right now I have:

-40gb internal slave hdd
   Partiton 1 (40GB) -> Linux (ext3)
-80gb internal master hdd
   Partiton 1 (10GB) -> Windows XP (ntfs)
   Partiton 2 (70GB) -> Storage (ntfs)
-300gb external hdd
   Partition 1 (297.8GB) -> Storage (ntfs)

This is what I've decided to do:

Step 1: 
I cleaned up my external drive and got rid of all data thats not valuable.  I have 80GB remaining without MP3s (110 with MP3s but I they are safely stored on my MP3 player and can be transfered over via gnomad later).

Step 2:
Store the 80GB of data on various other locales (i.e. Laptop/Friends computer)

Step 3:
Format the external drive with an ext3 filesystem.

Step 4:
Install driver from fs-driver.org onto windows systems that are storing my data.

Step 5: 
Copy data from windows systems back to the external drive.

...and thats it!

Before I actually go through with this, if anyone with more experience in this type of thing could give me a "sounds good!" or any tips, it would be greatly appreciated.

Thanks again all!
Install the ext3 driver on your XP also. That way if you need 
access to the ext3 storage drive from XP you will have it. Read/Write. Looks good on paper as the engineer said.:)

---

### Post by TMBridge on 2006-08-06
Thanks.  One more question.  Last one, I promise!

Should I format the external drive in windows or in linux.  And which program should I use for both cases?

---

### Post by Frank Golden on 2006-08-06
> **TMBridge said:**
> Thanks.  One more question.  Last one, I promise!

Should I format the external drive in windows or in linux.  And which program should I use for both cases?
Unless you have a copy of Partition Magic on your XP install
I would use QParted in Ubuntu. I think you have to delete
your NTFS on your external drive first using Windows  diskmgmt.msc. If you don't I think
you will get a can't write error from QParted because it is trying to write to a NTFS drive. Try to convert with QParted from Linux first. On the other hand if you have PM on your XP
install you can convert on the fly from XP. There is risk of data
loss with any method that's why you backup your stuff. Please
feel free to ask questions. Don't do anything unless you are comfortable. The simple solution of using XP's built in disk
management utility to convert to ext3 doesn't exist. As a matter
of fact a drive that has been formatted by XP to NTFS mostly
can't be converted back to Fat 32 using XP alone. Most third 
party partitioners will have no problems. PM will format a bunch
of different filesystems. As will QParted in Ubuntu.

---

### Post by TMBridge on 2006-08-06
thanks.  as a matter of fact, I do have PM on my windows install.  I will try the method that uses that.  Should I still delete my
NTFS on my external drive first using Windows diskmgmt.msc?  Or just leave it with the data on it (backed up of course)?

---

### Post by Frank Golden on 2006-08-06
Correction: I have been referencing a Linux partition tool QParted
it is really QTparted. I just checked, it is available in Ubuntu synaptics.
Install, plug in your drive and start program. Enjoy.

---

### Post by Frank Golden on 2006-08-06
> **TMBridge said:**
> thanks.  as a matter of fact, I do have PM on my windows install.  I will try the method that uses that.  Should I still delete my
NTFS on my external drive first using Windows diskmgmt.msc?  Or just leave it with the data on it (backed up of course)?
What the heck. Try converting with data on it first. If you succeed
it will save you some time. I have had PM truly mess things up in the past.
Be forwarned. Worst case you will wipe all the data on drive. That's why
you backup. I never tried to convert to ext3 on fly. Done Fat32 ok, though.
Defrag first. Don't defrag if you have .iso or other image type files however. It is not recomended. I have had disk defragger freeze while
trying to defrag .iso, .ccd, .mdf image files.

---

### Post by anaconda on 2006-08-07
> **TMBridge said:**
> Thanks for all the help guys.  This is a great community.  

Step 3:
Format the external drive with an ext3 filesystem.

Step 4:
Install driver from fs-driver.org onto windows systems that are storing my data.

Step 5: 
Copy data from windows systems back to the external drive.

...and thats it!

Before I actually go through with this, if anyone with more experience in this type of thing could give me a "sounds good!" or any tips, it would be greatly appreciated.

Thanks again all!

Sounds good!  :)
Fs-driver is wery good, and I havent had any problems with it, BUT when you copy 80GB of stuff to your ext3 hd it would be better to do it from linux. (native enviroment, and it can read from ntfs partitions without problems..)

And read this carefully, if you want automatic driver letter assigning & removing in windows.  (the problem is that windows dont free the drive letter when you unplug the ext3-usb-hdd..)
---------------------------------------
 Note that there is another workaround for the mentioned USB drive issue: you may modify the type of any Ext2/Ext3 partition on your USB drives. Linux Ext2/Ext3 partitions usually have as type 83 (hex). You may set the type of them to 7 (hex) for example with the Linux fdisk tool (using its t-command). The partition type of 7 (hex) - usually used on NTFS partitions - causes Windows to create and remove drive letters for a plugged or an unplugged USB drive itself.
Since Windows doesn't check the type of a partition while determining the file system, everything works well.
Linux does not check the types of partitions either. 
---------------------------------------

---

