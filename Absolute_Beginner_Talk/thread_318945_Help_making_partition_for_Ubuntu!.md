---
title: "Help making partition for Ubuntu!"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by punkdanne on 2006-12-14
Hi!
This is my very first post at ubuntuforums, and i'm looking for help on making a partition for ubuntu on one of my drives.

the drive i want to partition has a c: partition and a d: partition. in the c: windows is installed, and in the d: i have all my installed games. c: is primary and d: logical. 

I want to make a partition out of the free space on d:, not messing up my windows installation. I want it to be able to play games, and i've never tried ubuntu before ;)  but i want to so bad! but i can't get it working! I've tried some with partition magic and the ubuntu install cd without sucess. 

Partition magic says "This partition crosses the 1024 cylinder boundary, and may not be bootable". does that mean i can't have linux installed there ? 

I would also like som help in how many partition, what types and how big (swap-disks, root etc)

Thanks in advance for any help :)

---

### Post by FryerFox on 2006-12-14
If you use the LiveCD, you should be able to run GParted from the System->Administration menu. Right-clicking on an NTFS partition will allow you to resize it without destroying the data. Now, I can't guarantee that everything will go smoothly and the data will remain intact, but I have done this many times and have never had a problem. I have also not heard of credible stories of data corruption other than people accidentally deleting the wrong partitions, etc.

If this step completes successfully, then you should be able to install to the free space on that drive with the installer (desktop icon).

I would suggest that you make sure that you have at least 10GB or space available for Linux, so you can install any programs you want without worrying about space (350GB is better).

I don't know about the 1024 cylinder thing... Does anyone else have information about it?

Of course, if you have the option of putting in an extra drive, then that would offer some extra peace of mind, since this is your first time :)

Hope this helps - good luck.

---

### Post by moshuptrail on 2006-12-14
Definitely use the Gparted Live CD.

BUT, before you start, run scandisk and defrag from Windows on both C & D.
Then run defrag again.

This makes re-sizing faster and less likely to mess up.

If you have enough space, you might be able shrink D enough to make 3 partions for Ubuntu.
/            - system, needs 3-5G
swap     - swap, not more than 1G
/home    - all the rest

Lastly, if you feel really good, you could try copying all the stuff from D to /home (after you get Ubuntu running) and then convert D to FAT32.  Then copy the files back.  Now D (known to Ubuntu as /media/hda2) will be shareble, read/write space for both Ubuntu and Windows.

---

### Post by Sef on 2006-12-14
Get [GParted]("http://gparted.sourceforge.net/livecd.php").

Swap should be double your ram, but after a gig of ram it don't usually make much difference unless you do heavy gaming or movie making.

---

### Post by FryerFox on 2006-12-14
> **Sef said:**
> Get [GParted]("http://gparted.sourceforge.net/livecd.php").

No need to get it - it's already on the LiveCD

---

### Post by Sef on 2006-12-14
> No need to get it - it's already on the LiveCD

I know, but I prefer to use the GParted LIve CD.  It's more updated than the one on Edgy.

---

### Post by punkdanne on 2006-12-15
Thanks for all the help!
> **moshuptrail said:**
> Definitely use the Gparted Live CD.

BUT, before you start, run scandisk and defrag from Windows on both C & D.
Then run defrag again.

This makes re-sizing faster and less likely to mess up.

If you have enough space, you might be able shrink D enough to make 3 partions for Ubuntu.
/            - system, needs 3-5G
swap     - swap, not more than 1G
/home    - all the rest

Lastly, if you feel really good, you could try copying all the stuff from D to /home (after you get Ubuntu running) and then convert D to FAT32.  Then copy the files back.  Now D (known to Ubuntu as /media/hda2) will be shareble, read/write space for both Ubuntu and Windows.

Right now i'm thinking of formatting all d:, and install ubuntu on it. what exactly does the / and /home partitions do ?

---

### Post by hyper_ch on 2006-12-15
Well, Linux does not have "drive letters" as windows has... so there is no "c: / d: / e: ..." drive.

Linux instead uses a root dir "/" and you can setup different things into different folders.

Normally you have a folder "/boot" with your kernel, a folder "/home" which actually has all the user data and documents a folder "/etc" containg a lot of application configuration files and some other stuff... you have the "/usr" folder normally containing the binaries of the installed applications....

So in this scenary it it sort of appealing to have all data (movies, mp3s, office documtens, browser settings, emails, ......) in your "/home/USERNAME" dir and put it on a seperate partition... this means if you reinstall linux again, you can then set to use the /home partition again and you don't need to put everything back in there as it won't be touched...

In windows you don't have by default those options. There are some programs that let you alter the c:\document and settings folder to some other partition... but as far as I know (without special win distro) you can do that only AFTER the installation... by default it will make it on c:\...

Linux offers you to do that during installation :)

---

### Post by hyper_ch on 2006-12-15
[http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html](http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html)

[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by punkdanne on 2006-12-15
CRAP! the installer crashed! will i ever be able of installing ubuntu :p
gonna have to reburn the cd i guess.. 
Now I told the installer to take all d:, and automatically partition it correctly.:(

---

### Post by punkdanne on 2006-12-15
And damn! windows wont start now either! "the operating system cannot be started"

---

### Post by ddtrust on 2006-12-15
> **punkdanne said:**
> And damn! windows wont start now either! "the operating system cannot be started"


If you chose the automated partitioning during ubuntu install, it probably deleted all existing partions on the disk drive. I personally prefer to do the partitioning manually, 'cause I think it's safer way to do it. I think you should first gather some information about linux partiotioning system through google ("linux partitions") and then try to partition manually.

---

