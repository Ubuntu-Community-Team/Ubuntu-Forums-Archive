---
title: "Shared data partition Ubuntu/OS X: Filesystem?"
date: 2008-11-09
forum: Apple Hardware Users
---

### Post by __david on 2008-11-09
Hello everybody,

I&#8217;d like to set up a shared data partition for Ubuntu and OS X and wondering which file system to pick. The choices are, as far as I know, FAT, NTFS, ext2, HFS+ (case sensitive/non-journaling), and UDF.

FAT has a file size limit of 4 GB and tends to fragment very fast, so I&#8217;m not considering it seriously.

Using NTFS may be kind of straight forward with fuse/ntfs-3g, but it doesn&#8216;t support UNIX permissions and symlinks. In addition, it seems odd using a proprietary windows file system on a non-windows computer.

Ext2 access on OS X is supported through the [ext2fsx]("http://sourceforge.net/projects/ext2fsx") and the [ext2fuse]("http://http://sourceforge.net/projects/ext2fuse") projects, the former not being developed anymore and tending to cause kernel panics, the latter still being in alpha state and not compiling on OS X without source modifications.

HFS+ write support is supported for non-journaling partitions in Ubuntu. Fragmentation is prevented by an OS X system daemon. I will be using linux at least 80% of the time, so I&#8217;m interested if fragmentation can become a problem. Also, I&#8217;d like to know whether &#8220;Hot Files&#8221; are supported through the hfsplus package and what will be happening using two operating systems optimizing the &#8220;Hot Files&#8221; zone.

UDF is a file system with open specification and r/w access on both Ubuntu and OS X (at least up to version 2.01). The problem might be the lack of maintenance tools (wrudf is undocumented in Hardy). But the open specification may have lead to a more stable driver (compared to hfsplus).

Which filesystem would be your choice? My favorites are HFS+ and UDF. Are there specific advantages or disadvantages?

Thank you in advance,
David

---

### Post by JacaByte on 2008-11-09
If I didn't need to be able to read/write off the partition using Windows I'd personally use HFS+, but I don't know what the disadvantages of using it in Linux would be, if any. When I used the hfsplus package for my PowerMac 9500, it could read/write to the partition just fine, but I didn't use it long enough to find any serious problems with it.

Now, if there were a Windows machine in the picture, then I'd use NTFS, ironically enough. The more likely case is that I'd have to use the partition across four OSes if it were networked (Windows, OS X, OS 9 and Xubuntu) in which case I'd be forced to use FAT32, but another irony there is that Windows would be more likely to disembowel the filesystem than Linux and OS X as many versions of FDISK used by Windows don't recognize FAT32 partitions larger than 32 GB, and then you run into the inhernet 4 GB file limit.

Moral of story; there isn't one good universal filesystem in the entire world of computing. With, of course, the exception of UDF...

---

### Post by cyberdork33 on 2008-11-09
Apple's version of UDF is not the same as the normal Unix UDF. As far as I know, you cannot access Apple UDF volumes in Linux.

The best option is a networked file share.

---

### Post by __david on 2008-11-10
Thank you for your replies.

I know that a networked share would be the best solution, but since I&#8217;m using a notebook, it would be quite useful having particular data with me all the time.

I&#8217;ve tried out a few things:

[LIST]
[*]OS X-formatted UDF is not mountable on Linux
[*]Linux-formatted UDF is mountable & writable on OS X
[*]HFS+ is accessible on both systems.
[/LIST]
[LIST]
[*]&#8220;mount&#8221; on OS X cannot force a file owner for UDF partitions
[*]&#8220;mount&#8221; on Linux cannot force a file owner for HFS+ partitions (did I miss something?)
[/LIST]

That means fiddling around with setting the same uids/gids and umasks for my users on both systems?

---

### Post by cyberdork33 on 2008-11-10
> **__david said:**
> That means fiddling around with setting the same uids/gids and umasks for my users on both systems?

yep. I think you can set masks on hfs, but not hfs+...

---

### Post by Mattventura on 2008-11-11
ext2fsx actually worked quite well for me. I never got any kernel panics or other problems. It also has the advantage that you don't need a separate shared partition as you can use your native Linux partition as long as it is ext2/3. I would not recommend using your HFS+ OS X partition in Linux because you have to disable journaling, which would make an OS crash, power failure, etc, much more likely to destroy data.

---

### Post by __david on 2008-11-13
Hi,

to avoid creating users and groups with equal ids on both Ubuntu and OS X I will try out [bindfs]("http://code.google.com/p/bindfs/"), which is based on FUSE and should work with MacFUSE, too. It remaps a mounted directory to another one, allowing to set different owner and group for existing files as well as for newly created files. Seems promising to me. 

And there is a deb in intrepid, too! Gonna make a request to get this thing into MacPorts...

Hope this is useful for others as well.

Concerning the filesystem, I think I will go with HFS+, simply because udftools are missing some sort of fsck.udf and testdisk has no support for UDF.

@Mattventura: I’m neither going to mount my OS X partition in Linux nor my Linux system partition (and home directory) on OS X, that would be to risky. I will create a dedicated partition that will be backed up regularly.

---

### Post by Heleen on 2008-11-14
Hello,

I would like to install both Mac OS X and Linux on my MacBook 5.1, but I'm having a hard time setting up the partitions (bootcamp and Mac not recognising my data partition and such).
I would like to have a Mac partition, an Ubuntu partition and a Data partition, and maybe a swap partition for Ubuntu, but if that's not possible a swap file will have to do. My Mac doesn't have to see my Ubuntu and my Ubuntu doesn't have to see my Mac as long as they are both able to read and write to the data partition. I will probably be using both 50% of the time.

Could you maybe explain to me how you did the partitioning on your Mac? (I'm assuming you have a mac)

Thanks!
Heleen

P.s. I hope this isn't too much off topic, feel free to move my post to a new topic if it is.

---

### Post by __david on 2008-11-14
Hi Heleen,

unfortunately I’m still awaiting the delivery of my Mac. The only one I have currently access to is at my workplace.

I will explain every step soon as I have my MacBook here, thus I’m asking you to be patient for some days.

It would be helpful to know how experienced whether you already have experience in compiling software from source (on OS X and Linux). Also, it would be good to know if you need features provided by UNIX-filesystems (symlinks, access rights, etc.).

---

### Post by Heleen on 2008-11-14
Hi David,

Thanks for your reply! I will definitely wait for a couple of days then (I'm not in a hurry). I've searched the web for the problem, but didn't find anything but people saying it's not possible or how to do it with windows (which didn't work for linux).

I've used Linux for a couple of years now (Ubuntu mainly) and I'm a Computer Scientist, but I'm not that experienced. I won't use it for anything advanced like symlinks. And I will be the only user on the system. I should probably also mention that this is my first Mac and my first experience with the OS.
As I said I'm not that experienced, I don't think I know how to compile things from source myself on Linux or on Mac (apart from simple C programs :P), but it shouldn't take me too long to figure it out I think and I've got some Linux expert friends who can help me out. 
You probably won't have to explain it in a too noobish way ;).

Thanks again very much for your reply and I shall await the arrival of your MacBook :).

---

### Post by cyberdork33 on 2008-11-16
> **__david said:**
> Hi,

to avoid creating users and groups with equal ids on both Ubuntu and OS X I will try out [bindfs]("http://code.google.com/p/bindfs/"), which is based on FUSE and should work with MacFUSE, too. It remaps a mounted directory to another one, allowing to set different owner and group for existing files as well as for newly created files. Seems promising to me.
Interesting tool.

> **Heleen said:**
> I would like to install both Mac OS X and Linux on my MacBook 5.1, but I'm having a hard time setting up the partitions (bootcamp and Mac not recognising my data partition and such).
I would like to have a Mac partition, an Ubuntu partition and a Data partition, and maybe a swap partition for Ubuntu, but if that's not possible a swap file will have to do. My Mac doesn't have to see my Ubuntu and my Ubuntu doesn't have to see my Mac as long as they are both able to read and write to the data partition. I will probably be using both 50% of the time.

Could you maybe explain to me how you did the partitioning on your Mac? (I'm assuming you have a mac)

Thanks!
Heleen

P.s. I hope this isn't too much off topic, feel free to move my post to a new topic if it is.
You should make a new thread for such questions for future reference.

In OSX, install rEFIt (this is really needed and can be removed later if you do not want it). Then start Disk Utility and select your hard drive on the left. On the partition tab, click the '+' button to "add" partitions. Create a msdos partition as your data / storage partition and then create a second partition that can be any type and be the size that you want for Ubuntu (including the swap partition).

Then boot up the Ubuntu LiveCD, and start the partition editor (gparted) in System > Administration and delete the final partition you created (leaving blank space). Apply changes.

Now start the installer and install Ubuntu. When prompted, choose to install to the "largest continuous free space" and the installer will create your root and swap partitions. (Be sure to click the "Advanced" button and install GRUB (bootlaoder) to the Ubuntu root partition and not the MBR.

You will likely have this problem upon reboot:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by Heleen on 2008-11-16
Cyberdork33: thank you very much for your reply. Next time I shall start a new thread. 
You've answered my question and I will try it out in a moment. I already expected that to be the answer to be fair, but since I'd already tried several things before I decided that that was probably the answer I thought I'd post anyway to make sure it's the correct way to do it and not have to restart again and again. I've also already come across the problem you mention but managed to figure out myself how to fix it.
Thanks again and sorry about not starting a new thread.

---

### Post by Heleen on 2008-11-16
Cyberdork33: Again thank you very much for your reply. I just repartitioned my drive and installed Linux and it all works.
I managed to keep my Mac installation, I now have a DATA partition and I have Ubuntu installed. 
The key to the partitioning with DiskUtil was that in order to keep your Mac installation you first resize the Mac partition, so there's enough space for your Linux. You then create a partition for Linux from the empty space. And then you click on the Mac partition and click the + to split it up (this is the only way you can create 3 partitions without removing your Mac install as far as I know). You can then resize those as well. And then you have 3 partitions with the Data partition in the middle.
Anyway, thanks again!

---

