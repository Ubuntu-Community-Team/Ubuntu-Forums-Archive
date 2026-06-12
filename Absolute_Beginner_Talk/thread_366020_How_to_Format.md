---
title: "How to Format"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by insyted on 2007-02-20
FORMATTING
The purpose is to wipe the hard drive completely as if it came right out of the factory. The hard drive will be used for nothing more than backing up files. No OS will be installed onto it.


I don't understand the format features of Ubuntu.
For example, if insert a vista cd, the CD runs. There is an option to open command prompt.
I type in the regular "format c:" command. There is a warning about somethig mounted, and it asks if I want to force an unmant. (Can anybody explain this?)
Anyway, after I force the unmount, it goes directly to the typical format warning. I enter "y" to proceed with the format. 83 million years later, my hard drive is wiped. Unfortunately, as soon as it is wiped, Windows sets up a file system for installing Vista. This screws the whole point of the format up which is to wipe the disk clean.


With Ubuntu Live (The insaller cd which is actually the CD version of the OS). there is the gparted thing for partinioning and formatting. I used this to format my computer. I had to delete the current partitions. Then, create a new partition using all of my free space. Then I go to the format menu, and there are options for file system including ntfs, fat32, ext3, and more. I have to choose one of these, and then it proceeds with the format. In a few seconds, the computer is formatted. But it is actually not formatted because it sets up a file system. I'm having a hard time beleivig that the format is even legit.


#1: Why is it that using DOS from the vista cd, it takes 1046 million years to format my hard drive. Meanwhile doing it in Ubunut only takes a few seconds.

#2: Perhaps I should format from the terminal. Either way, does anybody know how to do this? I'd like to test it out. How can I format it completely without setting up any file system? DOS from the Vista CD is not able to do this as it sets up a file system as soon as the format ends. Ububtu desktop is not able to do this as it also sets up a file system along with the format.

---

### Post by Bachstelze on 2007-02-20
Formatting *is* creating a filesystem on a partition. I think I don't understand your problem. Do you want to format that partition or do you want not to ?

---

### Post by ashmew2 on 2007-02-20
> #1: Why is it that using DOS from the vista cd, it takes 1046 million years to format my hard drive. Meanwhile doing it in Ubunut only takes a few seconds.

Just showing that how much better UBuntu is than Vista or any other Operating System :P



> #2: Perhaps I should format from the terminal. Either way, does anybody know how to do this? I'd like to test it out. How can I format it completely without setting up any file system? DOS from the Vista CD is not able to do this as it sets up a file system as soon as the format ends. Ububtu desktop is not able to do this as it also sets up a file system along with the format.

I think , u shud be able to do that with gparted. When the partition table loads , just do right click and delete and right click and delete of every single thing and then Apply. I think that should do the trick.

Btw , If u want to use this HD for backing up files , how are u going to do so without a file system ?!?
And wat do u mean when u say "It does not get formatted as it sets up a file system"?

---

### Post by Vivix729 on 2007-02-20
I *THINK* in Windows, if you do not specify the /q attribute (for quick), a hard drive will be formatted using the long way, aka. each sector will be scanned for damages and corruption, rather than simply deleting the files and creating a new partition using the specified file system.

---

### Post by ashmew2 on 2007-02-20
Or the best way for hard drive options....First identify your manufacturer's name and then go to their website or something to find a utility , which i think , widely known as "Disc Manager" or "Disc Wizard". You should be able to burn that to a CD which will then boot the comp from the CD and give u options...
For example , I have a seagate hard drive so I use the Seagate Disc Wizard from [www.seagate.com/support](www.seagate.com/support) And in that , there is an option of something like "Fill Hard Drive with Zeros" . It pretty much restores the HD to its factory production stage..
:P

---

### Post by DivineOmega on 2007-02-20
> **insyted said:**
> FORMATTING
The purpose is to wipe the hard drive completely as if it came right out of the factory. The hard drive will be used for nothing more than backing up files. No OS will be installed onto it.

As explained by a previous poster, formatting is the action of creating a new filesystem so the hard drive is ready to store data. If you want to use this drive for backing up files as you say, they you definitely need a file system to be present on it.

The type of file system you want depends on whether you will be backing up from Linux or Windows primarily.

---

### Post by ashmew2 on 2007-02-20
Totally Agree with DivineOmega

---

### Post by insyted on 2007-02-20
> **DivineOmega said:**
> As explained by a previous poster, formatting is the action of creating a new filesystem so the hard drive is ready to store data. If you want to use this drive for backing up files as you say, they you definitely need a file system to be present on it.

The type of file system you want depends on whether you will be backing up from Linux or Windows primarily.
Thanks for the info.
I just have 2 questions about this.

1. In the past, I have used the popular Windows 98 Startup flooy disk to format the computer, and do smartdrive. When it comes to formatting the computer, the DOS prompt appears, and I create a primary partition using all of my disk space. Then I proceed with the format normally. It never mentions anything about setting up any file system. does it set up a file system?

2. Regarding a present file system for backing up files. Cannot you backup files on a brand new hard drive from the manufacturer that you have never formatted? Say I just buy a hard drive, and hook it up. Being that it is empty, I could proceed to use it as a backup drive. Will this not work? Does it already come with some sort of file system?

When I did the format using Vista, it did not go the same way as I did it using the floppy Windows 98 Startup disk. For example, if my hard drive was a million bytes, the startup disk would format it, and tell my total disk space of a 100 million kb, and my total free space of a 100 million kb. Total used space is 0 kb.

When I do it with Vista CD, the format goes through, exactly the same way, except right before it ends in the same way the 98 floppy does, it does a file system setup routine. Then instead of 100 million kb free, I have little bit less than 100 million kb free. And a few thousand kb used.


UBUNTU TERMINAL QUESTION
I just want to format my drive to give me 100% free space with nothing on it.
Regarding Ubuntu. I have studied the tutorials for the terminal to move about the file system, but none of them seem to mention the most basic command line function which is to move from drive to drive. In DOS, I have to enter "c:" to go to the hard drive, "a:" to go the floppy drive, and "d:" to go to my CD drive.
In the guides I have reviewed online, I saw how to navigate the file system, and do "ls" and the other command that tells me where I am.

My question regarding Ubuntu is how I do I move from one drive to the next? If I want to go to the root directory of my CD Drive or the root directory of my hard drive. Furthermore, once I am in that directory, what command can I use to check the total, free, used disk space?

Also, as explained above, I do not know if it is formatting throroughly using the gdeparted. I want to make sure it does a thorough format, and clears everything out. Is a what seems to be a "quick format" like that capable of doing so?




> **ashmew2 said:**
> Or the best way for hard drive options....First identify your manufacturer's name and then go to their website or something to find a utility , which i think , widely known as "Disc Manager" or "Disc Wizard". You should be able to burn that to a CD which will then boot the comp from the CD and give u options...
For example , I have a seagate hard drive so I use the Seagate Disc Wizard from [www.seagate.com/support](www.seagate.com/support) And in that , there is an option of something like "Fill Hard Drive with Zeros" . It pretty much restores the HD to its factory production stage..
:P
Thank you!!
I use Seagate too. I will definitely look into that. Do you know if it will be able to work on non-seagate drives?

---

### Post by mcduck on 2007-02-20
1. That's because Win98 only understands FAT filesystem, no use asking what FS to use. The fact that it doesn't tell you it's setting up a file system is meaningless, it does it anyway. Like already mentioned, to store any data on a drive the drive must have a filesystem.

2. Hard drives usually have a file system when you buy one. If not, you must create one before you can use the drive.

What comes to moving to your drives, this works a bit differently in Linux. There is only one root, and everything else can be mounted into any directory inside root directory. Usually you'll find your other drives inside /media. (but if you want you could for example mount a new drive into a directory inside your home dir)

---

### Post by Bachstelze on 2007-02-20
I don't know exactly how Win works but the fact is : to store anything on a drive, you *absolutely* needs a filesystem. I wonder where you got that idea of "no filesystem" from but it doesn't make any sense.

Also, what you need to know about Linux file structure - and Unix-like systems in general - is that there is no such thing as drive letters. You ahve your filesystem with the / directory and everything will be in it, including any additional drives. Drives in Unix are *mounted* in a directory of the filesystem. Say I have a partition mounted on / - that acts as the root filesystem - and I have another partition I want to use. In windows, I would assign it another drive letter, so I would access the files as for example E:\foobar.txt. In Unix, I mount it into a directory, that means that if I mount my partition in /mnt/data, I would access my file as /mnt/data/foobar.txt.

---

### Post by DivineOmega on 2007-02-20
> **insyted said:**
> Thanks for the info.
I just have 2 questions about this.

1. In the past, I have used the popular Windows 98 Startup flooy disk to format the computer, and do smartdrive. When it comes to formatting the computer, the DOS prompt appears, and I create a primary partition using all of my disk space. Then I proceed with the format normally. It never mentions anything about setting up any file system. does it set up a file system?

Although I have not used the 98 start up disk for a year or two, I believe it simply changes the partition table, and creates a new unformatted partition (i.e. blank space - with no filesystem). This is useless for any practical purpose, as no files can be stored on a partition that does not contain a filesystem.

> 2. Regarding a present file system for backing up files. Cannot you backup files on a brand new hard drive from the manufacturer that you have never formatted? Say I just buy a hard drive, and hook it up. Being that it is empty, I could proceed to use it as a backup drive. Will this not work? Does it already come with some sort of file system?

No, you can not put files on a drive without valid partition table and file system.  An 'empty' drive from the manufacturer does not have a file system and thus the computer has no way of knowing how to store the files. 

Formatting a partition on the drive sets up the partition so that files can be written to and read from it. The specific filesystem used determines how this occurs and which operating systems can access it.

> UBUNTU TERMINAL QUESTION

...

My question regarding Ubuntu is how I do I move from one drive to the next?

In Ubuntu, different drives and partitions are mounted in the /media/ directory.

e.g. Your CD-ROM drive will be  located at /media/cdrom0/
To list all the mounted drives and partitions you can use the command: '/media/' and then 'ls'. Then you can change to the root of that drive or partition using a command in the format '/media/cdrom0/' for example.

---

### Post by Patrick K on 2007-02-20
Free space is space that has not been formatted. It is empty of anything. No OS on the planet can use it like that. Each OS uses a file system and a drive has to have a file system on it for the OS to use it. Formatting is the process of installing that file system on the drive. 

With W98 you should have been given a choice between using large partitions and smaller partitions (I don't recall the exact terminology).   The larger option installs the FAT32 file system, the smaller, the FAT16 file system. I don't think fdisk explicitly mentions FAT32 of FAT16. 

As delivered from the mfg, the drive is unusable. It must be formatted with a file system. The mfg has no idea what OS the drive will be used for. With some partitioning apps, you have a choice of what file system to install. GParted and many others can format to various file systems. MS' fdisk can only format to Windows supported file systems. A drive without a file system installed on it is pretty much a paperweight, although it has the potential to be usable. 

You need to explore the Linux file system. In it, there are no separate drives, as such. Everything is a file, including the various HDDs on the system. That said, by opening the directory where the various drives are mounted you can access the drives. But, as far as Linux is concerned the drives are just files in a directory that are stored in the file system under the / (root) directory. 

If you have a Seagate drive installed on you system, you can use Seagate's formatting utility to format other brand drives. It will squawk about, it but will work. I used it to format my second drive, a Maxtor. I actually like Seagate format utility since it will format to many different file systems and, at least for FAT32, allow setting the cluster size. Many don't allow setting this, and it can have a big influence on space usage and drive performance. (For instance, for a partition used for storing large file, like movies or music, a large cluster size will improve performance.)  The downside is it will not allow changes to any partition without reformatting the entire disk, which, of course, wipes the entire drive. GParted is a much better choice for making changes to partitions. 

For exchanging data between Linux and Windows, FAT32 is quite usable since both can read and write to it. I don't use NTFS but understand there are beta programs for Linux that allow writing to it. Linux doesn't natively do this (although it can read NTFS). Also, I have heard there are Windows utilities that allow reading and writing to Linux's EXT3 file system. 

There are a great number of differences between Linux and Windows. Coming from Windows, as I did, can be very confusing. After a while you start to get a feel for it and it becomes less confusing. Although, I suspect, it is much like Quantum Theory: no one on the planet has a complete and total, gut level understanding of it. Maybe Linus T.

---

### Post by ashmew2 on 2007-02-21
HI , yes ive used that Seagate disc wizard on a samsung hard drive and quick filled zeros on the hard drive , although it said "NOT A SEAGATE DRIVE" but it zeroed it out no problem.
Btw , if there's no OS installed and only a file system on your whole hard drive how are u going to transfer files from your data to it ?

---

### Post by DivineOmega on 2007-02-21
> **ashmew2 said:**
> HI , yes ive used that Seagate disc wizard on a samsung hard drive and quick filled zeros on the hard drive , although it said "NOT A SEAGATE DRIVE" but it zeroed it out no problem.
Btw , if there's no OS installed and only a file system on your whole hard drive how are u going to transfer files from your data to it ?

Providing you have an operating system on one hard drive, it will be able to access any other hard drives in the system and thus be able to transfer files on to it.

---

### Post by Patrick K on 2007-02-21
> **DivineOmega said:**
> Providing you have an operating system on one hard drive, it will be able to access any other hard drives in the system and thus be able to transfer files on to it.
Provided it can read and write to the file system on the other drive.

---

### Post by ashmew2 on 2007-02-21
oops , silly me hehe
Thanks for the corrections :D

Btw has the thread starter sorted out his worries yet or not ?

---

### Post by Patrick K on 2007-02-22
> Btw has the thread starter sorted out his worries yet or not ?

Who knows. He hasn't posted back.

---

### Post by RickBryan on 2007-02-22
> **Patrick K said:**
>  
There are a great number of differences between Linux and Windows. Coming from Windows, as I did, can be very confusing. After a while you start to get a feel for it and it becomes less confusing. Although, I suspect, it is much like Quantum Theory: no one on the planet has a complete and total, gut level understanding of it. Maybe Linus T.

This is an excellent post; very thoughtful and insightful for new users.  I've also found some of the Linux concepts that don't have direct Windows counterparts are the biggest stumbling block to going forward with Ubuntu.  Understanding the reasoning (and naming convention) behind the *nix directory structure proved most difficult, along with drive and partition naming ('hda,' 'hda,' 'sdb,' etc.)  Once I got a handle on that, along with the concept of "mounting," which isn't something Windows users are used to, things became somewhat easier.  For whatever reason it took me weeks to figure out "sudo" stood for "superuser do," and that "make install" wasn't actually creating (making) an install file, but installing a file which was already created (made).  Seemingly minor issues have been the most frustrating, so when Windows users take the time to explain technical cross-platform issues in a verbose manner it's very much appreciated.  

Thanks again.

---

### Post by Patrick K on 2007-02-22
Glad to help. I'm just a baby in the Linux world.

---

### Post by 3rdalbum on 2007-02-22
> **RickBryan said:**
> Once I got a handle on that, along with the concept of "mounting," which isn't something Windows users are used to, things became somewhat easier.

Although Windows users aren't aware of "mounting", it is still done on Windows. Without mounting a drive, virtually no applications are aware of its existence.

---

