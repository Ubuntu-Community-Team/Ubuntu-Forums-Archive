---
title: "Linux and Windows sharing the same partition ... possible?"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by sim085 on 2006-08-02
Hello,

Now that I played a little with Ubuntu, I am planning to format my computer again and and install Ubuntu again, and Windows XP.

I planned to do this as follows; Divide my hard-disk in 3 partitions.  One partition is for Ubuntu, the other one is for Windows XP and the third one is just a data partition.

This means that both Ubuntu and Windows would have access to this partition to put files in it.

Now is this even possible; that Ubuntu and Windows can share the same partition? Or if a partiton is for one OS then it will not be recognized by the other one?  

I am new to the Operating System environment, and therefore I am still experimenting.

Thanks for any comments,

regards,
Sim085

---

### Post by fourchannel on 2006-08-02
Sorta...

Here's the catch. There are 2 prominent filesystems for windows. FAT32 and NTFS. FAT32 is what windows 95/98 used, and NTFS is what XP and Windows Server 2003 and soforth use.

NFTS has shady write support in linux, yet it is the filesystem of choice for XP.

Both XP and Linux can read/write to FAT32 with no problems *except* that FAT32 does not support file permissions--so your data is not as well protected. For a single user PC this is a trivial concern.

The question then... How do I create at FAT32 partition?
There is a thread about sharing files between XP and Linux that may be what you are looking for. [http://ubuntuforums.org/showthread.php?t=203524&highlight=create+fat32](http://ubuntuforums.org/showthread.php?t=203524&highlight=create+fat32)

---

### Post by coffeecat on 2006-08-02
A shared data partition is an excellent idea. The easiest way is to format it as fat32, because Linux cannot (reliably) write to Windows XP's ntfs and Windows can only read/write the Linux filesystem ext3 if you install a special app. Install Windows first and then Ubuntu. Ubuntu should pick up the presence of the fat32 partition during install and add a line to /etc/fstab for it to be mounted at bootup. Or at least it will if you choose the custom partition option during the install. If you don't get such a line and an icon doesn't appear on your desktop, just post back and someone will tell you what to add to fstab.

One hint - I don't know what partitioning software you are using, but if it can add partition labels (Gparted can't - BIG omission devs :( ) choose a label like 'Shared_Data' or whatever you like. Then the desktop icon will have a sensible label. Better than /media/hda5 or whatever.

Another thing. You'll need four partitions. Don't forget that Linux uses a swap partition. Windows uses a swap file. Rule of thumb is 2x your RAM.

---

### Post by coffeecat on 2006-08-02
Afterthought. As I said you'll need 4 partitions. Don't make them all primary because if you need another partition in the future you are stymied. Windows **must** go on a primary partition. Your data partition, the Linux root and the swap partition can all be logical ones. That's what I'd do.

---

### Post by andb on 2006-08-02
I'd suggest you put your data on an ext2/3 partition. Lets hope you'll use ubuntu more often :) Windows can access ext2 just fine, rememebr its an open source format. Find great win XP driveres for ext2 access at: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

NTFS has major overhead, Ive seen 20% of my space wasted to it own housekeeping. ext2/3 are self defragging, vfat is ancient really not the best solution

So, if you make it ext3, you can still read it, but windows wont do journaling, or recording what will be happening. However, it will acces the files just fine. 

Swap space. Windows rule of thumb in 1985 was 2x memory. Most of the time windows in now 0.5x. Try setting it equal (at most) or half. once you are running, use the command "top" to see how much of that swap space is used. Ive never used over 20mb from my swap file! A freind mentioned thta linux can use an actual file as swap, could easily be on vfat(wouldnt work ext2/3 because windows would access the swap file before the ext driver is loaded) , and then you caould acutally use the same partition for both linux and windows swap, freeing up lots of space! If you have over 512mb memory, ubuntu really isnt going to use swap space. My typical load at any time is skype, ekiga, gaim, amule, azureus, quod libet, lots of swiftfox browsers, watching a movie in xine or vlc, often burning with gnomebaker, all at the same time, never over 20 mb swap and Ive only 512mb ram.

Most likely partition scheme:

1) .5g swap
2) 10g windows (or whatever value you want)
3) 10g ubuntu
4) rest to data

After you have used your system a while, look into mounting /root /boot /usr /var /tmp all on different partions. It can make for a more stable system, when your temp fills, it wont crash the system...

to learn more: [http://learnlinux.tsf.org.za/](http://learnlinux.tsf.org.za/)
go to linux courses, start with fundamentals

---

### Post by Frank Golden on 2006-08-02
> **sim085 said:**
> Hello,

Now that I played a little with Ubuntu, I am planning to format my computer again and and install Ubuntu again, and Windows XP.

I planned to do this as follows; Divide my hard-disk in 3 partitions.  One partition is for Ubuntu, the other one is for Windows XP and the third one is just a data partition.

This means that both Ubuntu and Windows would have access to this partition to put files in it.

Now is this even possible; that Ubuntu and Windows can share the same partition? Or if a partiton is for one OS then it will not be recognized by the other one?  

I am new to the Operating System environment, and therefore I am still experimenting.

Thanks for any comments,

regards,
Sim085

Hi sim085,

   Check this out



[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)



This is a comprehensive guide to dual booting Ubuntu/XP.

You need to download the Alternate CD for the fine control

over the install it gives you. I was not able initially

to get my Fat32 partition to automount after the install but

the author has a whole section(s) devoted to doing just that.

Read it carefully and print the sections that are relavent.

Start with a clean HD and install XP first. This guide walks

you through step by step the process of using the built in

partiioning tool on your Alternate CD to shrink XP to smaller

partition, create a Fat32 shared partition and finally install

Ubuntu on the remaining free space.



Another plan might be if you have access to Partition Magic

in XP use that to shrink your XP partition. Then create an

appropriately sized Fat32 partition for shared data and leave

the rest of the drive unallocated. You will need about 4-6GB

of unallocated space. You can use the DesktopCD and install

from the installer icon once the CD finishes booting.

When you get to the partitioner section choose the option

to install to the largest free space. Ubuntu will automatically

partition the unallocated space to ext3 for the OS and ext2

for swap and install itself. The big drawback to Fat32 is 

this filesystem won't allow single files greater than 4GB like DVD images etc.



I presently have XP on a ~20GB NTFS partition at start of my 120GB HDD, a second 3GB NTFS partition for XP pagefile, a third 44GB

NTFS with large XP programs and data and music files (wma), a fourth

24GB Fat32 extended partition to share between OS's and finally

18GB ext3/ext2 Ubuntu install. The Ubuntu partitions are logical

drives of the fourth extended partition. I have my NTFS & Fat32

partitions (except the small pagefile) automount at bootup.

I have icons on desktop and can access them. I can't change

my NTFS ones which is good (keeps from messing up XP). I have

full read/write priveleges to the Fat32 shared partition.

See screen shot link
[http://i30.photobucket.com/albums/c338/fjgold/Screenshot-2.png](http://i30.photobucket.com/albums/c338/fjgold/Screenshot-2.png)
Of course these are just suggestions there are many ways to do what
you want to do.

---

### Post by stoft on 2006-08-02
I recommend using a good partitioning program when setting up your partitions. E.g. if you do decide to use fat32 as one of the partitions, Windows won't let you create a fat32 that's larger than 32GB even though it has no problems handling partitions that are much larger. An example of a good partitioning program is GNU Parted/QT Parted which you can find on e.g. SysrescCD ([www.sysresccd.org)](www.sysresccd.org)), the swiss-army knife of system rescue. Burn it out on a CD, boot CD, partition.

Before you go ahead I recommend you read more about the restrictions of each type of filesystem. Taking fat32 as an example, the max file size is 4GB. If you foresee having files larger than that then maybe you should consider another alternative.

Comparison of filesystems: [http://en.wikipedia.org/wiki/Comparison_of_file_systems#Comparison](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Comparison)

---

### Post by Frank Golden on 2006-08-02
I have my copy of SysRescueCD on a 1GB Cruzer Titanium USB flash
stick. My laptop will boot from just about anything. Running
off the memory stick it loads faster and frees up my CD/DVD drive. The Swiss Army knife of recovery tools indeed!

---

### Post by sim085 on 2006-08-02
Hi,

First of all thanks to all for the replies :) I do have some questions however ...

coffeecat said that I need four partitions, since one of the partitions is used by linux uses it as a swap partition.  Now when I first installed Ubuntu, I do not remeber it asking me to set the size of the swap partition! 

Also andb mentioned ext2. Was is this?  I am sorry unfortunalty I come from the Windows environment and only know about FAT32 and NTFS, and never heared of ext2 (altough i will search about it now).

Also, what is the format used by linux then?

thanks again for all the replies :)

Regards,
Sim085

---

### Post by Lord Illidan on 2006-08-02
Linux can use many formats. The most common ones are ext2,ext3,and reiserfs.

ext2 is outdated now, though. Ext3 is the best option for sharing data as there are good windows drivers for it. On my Windows system I can mount ext3 partitions as normal harddrives.

My partitioning scheme is like this.

1st partition is a swap.
2nd is Windows.
3rd is Zenwalk.
4th is Ubuntu /
5th is Ubuntu /home

Some are primary, some are logical, forgot which though ;)

---

### Post by Frank Golden on 2006-08-02
> **sim085 said:**
> Hi,

First of all thanks to all for the replies :) I do have some questions however ...

coffeecat said that I need four partitions, since one of the partitions is used by linux uses it as a swap partition.  Now when I first installed Ubuntu, I do not remeber it asking me to set the size of the swap partition! 

Also andb mentioned ext2. Was is this?  I am sorry unfortunalty I come from the Windows environment and only know about FAT32 and NTFS, and never heared of ext2 (altough i will search about it now).

Also, what is the format used by linux then?

thanks again for all the replies :)

Regards,
Sim085
Ubuntu formats an ext3 (third extended filesystem) partiton for itself the installs itself to it. Ext3 is the filesystem most
linux distro's use. Ext2 is earlier version of ext3 mostly. Ubuntu creates a  small ext2 partition ( approx. the size of available ram) for a swapfile. Most install routines do this 
automagically. Read the link stoft posted for more than you will
ever want to know about filesystems. Here it is again.

[http://en.wikipedia.org/wiki/Compari...ems#Comparison](http://en.wikipedia.org/wiki/Compari...ems#Comparison)

Feel free to ask questions in this thread or post another thread.
We are here to help.

---

### Post by sim085 on 2006-08-02
Why Ubuntu and Ubuntu/home?

I mean what is the difference between the two?

regards,
Sim085

---

### Post by stoft on 2006-08-02
> **sim085 said:**
> Why Ubuntu and Ubuntu/home?

I mean what is the difference between the two?


By "Ubuntu /" and "Ubuntu /home" the root (written "/") and home (written "/home") directory of the operating system "Ubuntu" is intended. The windows equivalent would be "Windows C:" and "Windows C:\Documents and Settings".

Each directory/filesystem ("directory" and "filesystem" are synonyms in this context) of a linux system takes care of certain things. The /home directory is where the user profiles and all the users' files are stored. Because it is the default place for users' files it grows very easily. If /home lives on a different partition than "/" (root), where the base OS lives, even if /home gets filled up all the way it won't affect the basic operating system. If they both live on the same partition and the partition fills up you may find yourself in a situation where the OS tries to write to disk on startup, fails and gets generally unhappy. Similar happens in windows when the C: drive fills up because you have saved a much-too-large file in "My Documents" or similar. To learn more about the directory structure of linux check out the [dir tree overview]("http://www.tldp.org/LDP/sag/html/dir-tree-overview.html") of the [System Administrator's Guide]("http://www.tldp.org/LDP/sag/html/index.html") over at [The Linux Documentation Project]("http://www.tldp.org/").

The filesystems that tend to grow the most are /home, /var and perhaps /tmp (someone please correct me here, I'm unsure of the growth of /var and /tmp). /usr also fills up as you install applications but is more controllable since it doesn't fill up automagically, only when you install/update applications. Seeing as you are new to linux, if you have a large harddrive I'd suggest just leaving the other filesystems be and moving /home to another partition, maybe not even that. In the end it all depends on your intended use of the operating system.

On my system I have 6GB (swap included) reserved for Ubuntu, and /home on a separate 1GB partition. Since I have a shared partition between Ubuntu and Windows most of my files tend to end up there and not under /home but still /home is getting a bit crowded and in retrospect I would have put at least another GB there, maybe more.

---

### Post by coffeecat on 2006-08-02
> **sim085 said:**
> Now when I first installed Ubuntu, I do not remeber it asking me to set the size of the swap partition! 

It wouldn't have done. It would have created a suitable swap partition without asking you. If you've still got that installation, go to System > Administration > Disks and you'll see it listed. The only real difference between ext2 and ext3 is that ext3 is journalled. A swap partition has it's own filesystem. I don't believe it's ext2, but I could be wrong. But it doesn't matter because all Linux distros use the same swap partition format.

It's unfortunate that the idea of separate root (/), /home, and other partitions has been raised. It's a valid point but if you are new to Linux I advise you to keep it simple - that is, everything (except swap) in the root partition. If the Linux bug bites you, you are going to be installing other distros and reinstalling Ubuntu before you'll be needing separate partitions. You've enough to learn without worrying about complicated partitioning setups. When (if!) you find you need them you'll have the knowledge you need anyway.

---

### Post by andb on 2006-08-02
cofeecat has a good point, its better to just jump in and play with a working system than to stress about details like partitions. saying that ext3 has journaling simply means that the OS records what it wants to do before doing it, so if there is a sytem failure (power outage for example) its easy for the system to pick up and continue afterwards. So ext2 is the same filesystem with this record turned off. Thats what the windows drivers will do.

Swap doesnt use a filesystem, its just a data dump. In fact files can be used as swap space and ubuntu can work pretty intelligently even with no swap space, so the most important thing is to start :)

The one partition that really makes sense to have seperate is /home. Then, when you upgrade the system, all your data and settings survive in the isolated partition. The new system then will automatically use all this data. Makes upgrades really easy, unlike windows where user data is scattered all over the main partition...

If you make one big partition, then you learn why to have more, you can resize with partition magic or gparted, mount the new partiotions and continue. Dont worry that you'll be "locked in" to somthing, its easy to change! Jump in! 

I recognize now that the biggest ubuntuforums problem is that you can get too much help sometimes ;)

---

### Post by sim085 on 2006-08-03
There is nothing like to much help :)

I am happy that you people are telling me all this, since for me all this is new, and I always like to learn new stuff :) I now understand the need for putting ubuntu/ and ubuntu/home in a different partition and something I will keep in mind.  Also the difference between ext2 and ext3 is very helpfull :)

The only question I still have is wheather I should format my hard-disk space to be shared between Ubuntu and Windows as a FAT32 or ext3?  What would be the best option and why?

regards,
Sim085

---

### Post by andb on 2006-08-03
fat32 is universally readble & writeable. DOS, Windows, Linux, Mac, OS/2... Pretty much everyone can use it out of the box. Therefore, its great for usb drives. Disadvantages: Fragments easily. Slower access. Limited file size (like 4gig or something, so a non-issue for most users)

Ext3- standard linux drive. Best option because all drive utilities suport it. Disadvantages: All other OSes will require drivers for it. So if you take a EXT3 usb drive to your buddy's machine, he'll need drivers. If its on your harddrive in your own box, doesnt matter much, as you'll have the drivers. 

How do I have mine set up? I dont have a "shared" partition. I just let windows access my home partition via the EXT driver at [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) 

This way you wont waste space sitting there for when you need to transfre something. When Im not transfering in windows, I go to the control panel to the EXT driver and DISABLE all windows access to my linux drives. I just feel a bit nervous letting windows in there all the time. Linux may not get viruses, but I dont see a reason why a windows virus wouldnt be able to screw up your linux partition... 

Simplest answer for long term efficiency, add the space to your linux home partition (assuming you make a seperate partition for home) and use the EXT driver.

---

### Post by sim085 on 2006-08-06
Thanks :)

The explanation was really helpfull.  I would do some installations today and experiment a little and see what suits me best :)

thanks again
Sim085

---

### Post by OffHand on 2006-08-06
> **sim085 said:**
> Thanks :)

The explanation was really helpfull.  I would do some installations today and experiment a little and see what suits me best :)

thanks again
Sim085

You will want to use a seperate /home partition, trust me.
It will make upgrading and/or re-installing so much easier.

This is a pretty nice guide when you are going to use the alternative install:

[http://www.pcmech.com/show/os/903/](http://www.pcmech.com/show/os/903/)

---

### Post by sim085 on 2006-08-07
Thanks for the article and sugestion :)
having /home on a different partition would be very helpfull since I would be keeping my data from one installation of Ubuntu to another :) (at least I have came to that conclusion now :D)

regards,
Sim085

---

