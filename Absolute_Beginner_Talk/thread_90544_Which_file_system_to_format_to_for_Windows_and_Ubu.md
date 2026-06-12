---
title: "Which file system to format to for Windows and Ubuntu?"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by dpack on 2005-11-15
Hi all! I'm new here, as this is my first post. To give everyone a little background, I am an advanced Windows user and have come up the ranks from MS-DOS to WinXP. I've never used any flavor of Linux. A friend of mine gave me an extra copy of an Ubuntu 5.10 disc he ordered so I'm ready to join the ranks of the Linux group. I temporarily dual-booted my Windows machine with Ubuntu and tried it out for two days. I figured a lot out on my own with help from reading these forums and other documentation. I believe I can switch to having Ubuntu as being my main OS and am ready to take the leap. However, there are some things that I do that require Windows that Ubuntu sticks it tongue out at me, so I need to continue dual-booting. I'm sure I'll be posting more with questions later but I have just one question I need addressed for now.

I have an external Maxtor 3000LE USB 2.0 hard drive. It is currently formatted NTFS. While I was playing with Ubuntu it could only read from the drive. Doing a properties on the disk showed root as the owner and my account only had read access. I believe I read somewhere that an NTFS partition can only be read from in Linux and it is not a good idea to enable NTFS writing in Ubuntu. But I don't want to reformat the drive to a Linux format either and lock Windows out from seeing it. I need to be able to work with the drive from either OS.

My question: What file system format can I format my external hard drive to that will give me full access to the drive and files (read, write, modify, and execute) with Windows XP and Ubuntu?

Thanks for the help!
David

---

### Post by BoyOfDestiny on 2005-11-15
[QUOTE=dpack]Hi all! I'm new here, as this is my first post. To give everyone a little background, I am an advanced Windows user and have come up the ranks from MS-DOS to WinXP. I've never used any flavor of Linux. A friend of mine gave me an extra copy of an Ubuntu 5.10 disc he ordered so I'm ready to join the ranks of the Linux group. I temporarily dual-booted my Windows machine with Ubuntu and tried it out for two days. I figured a lot out on my own with help from reading these forums and other documentation. I believe I can switch to having Ubuntu as being my main OS and am ready to take the leap. However, there are some things that I do that require Windows that Ubuntu sticks it tongue out at me, so I need to continue dual-booting. I'm sure I'll be posting more with questions later but I have just one question I need addressed for now.

I have an external Maxtor 3000LE USB 2.0 hard drive. It is currently formatted NTFS. While I was playing with Ubuntu it could only read from the drive. Doing a properties on the disk showed root as the owner and my account only had read access. I believe I read somewhere that an NTFS partition can only be read from in Linux and it is not a good idea to enable NTFS writing in Ubuntu. But I don't want to reformat the drive to a Linux format either and lock Windows out from seeing it. I need to be able to work with the drive from either OS.

My question: What file system format can I format my external hard drive to that will give me full access to the drive and files (read, write, modify, and execute) with Windows XP and Ubuntu?

Thanks for the help!
David[/QUOTE]

The answer my friend is sadly fat32. Depending on the size of that drive, I'd recommened to partition it. Make a chunk (or 2) fat32. If you are going to use linux more often make the remaining free space ext3 or reiserfs. 

I can assure you that windows (with 3rd party stuff) will let you see what's on there.

---

### Post by frodon on 2005-11-15
Fat32 is suppoted by both windows and linux, however it's not the better fomat for performance.
You could use ext3 which is a really good FS, stable and fast and there's now some drivers for windows : [http://www.osnews.com/story.php?news_id=11506](http://www.osnews.com/story.php?news_id=11506)

---

### Post by Pablo_Escobar on 2005-11-15
Frodon, as I see it FAT32 (with its limits, performance, etc) is a better choice than using ext drivers for Windows. (I've read thay can cause a data corruption).

Another thing - this is an USB drive, so it has to be portable, and not every PC it'll be connected to will have these drivers (dpack would have to carry around on seperate medium these drivers - bad idea).

IMHO as BoyOfDestiny suggested FAT32 is a way to go - no problems there.

---

### Post by frodon on 2005-11-15
I agree, but maybe we will have good windows driver for ext3 soon ... i hope so.

So dpack as Pablo_escobar said, FAT32 seems to fit to your needs, I also use FAT32 on 2 partitions (50Go and 70Go) and i never had problems with them. I think you have enough informations to make your choice now ;)

---

### Post by dpack on 2005-11-15
Thanks for the replies all! To address some of the items listed, this drive is only a 35GB drive. Reformatting it to be FAT32 will not be a problem at all. As far as performance, I don't run anything from this drive. I use it as backup. I drag and drop files to and from it uncompressed and unzipped - that's all. I just use it for storage. Performance is not an issue. Looks like FAT32 is the way to go!

One more question: After I change it to FAT32 and open the drive in Ubuntu, will root still be the owner locking my account out to being only read access? I don’t have Ubuntu installed at the moment to see is why I ask. If so, I’ll need the sudo command to give my account full access.

Thanks!
David

---

### Post by xmastree on 2005-11-15
[QUOTE=dpack]One more question: After I change it to FAT32 and open the drive in Ubuntu, will root still be the owner locking my account out to being only read access?[/QUOTE]
Read: [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

That tells you how to mount your FAT32 partition and allow all users to read/write to it.

---

### Post by frodon on 2005-11-15
To mount FAT partitions with user access : [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

EDIT : lol xmastree you're to fast for me !

---

### Post by Pablo_Escobar on 2005-11-15
With FAT32 You can anything (only root access etc). But the default setup is for every user to have read **and** write access. 
The read only problem is just the NTFS filetype.
No worries here, I have 3 FAT32 partitions and I access them with my deafult user with read, write, execute rights without any fuss :)
I'll change 2 of them to ext3 or Reiser when I'll have some time for disk space juggling :)

---

### Post by xmastree on 2005-11-15
[QUOTE=frodon]EDIT : lol xmastree you're to fast for me ![/QUOTE]Sorry... It's your thread and I jumped in... :rolleyes:

---

### Post by Wally68 on 2005-11-15
Just as a side note, as I haven't seen it mentioned in this thread, vfat doesn't support file permissions or ownership. It is stable and safe for sharing between windows and linux, but not the most secure. I really couldn't say what's better though. NTFS write support for linux is unstable and not recommended, and as mentioned earlier, ext3 support for windows is still unstable.

---

### Post by dpack on 2005-11-15
Thanks for the info! If what I am reading from Pablo_Escobar is correct I won't have to run those sudo commands. If I do then I got the link.

Thanks!
David

---

