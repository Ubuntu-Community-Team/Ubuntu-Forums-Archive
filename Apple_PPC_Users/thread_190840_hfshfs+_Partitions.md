---
title: "hfs/hfs+ Partitions"
date: 2006-06-06
forum: Apple PPC Users
---

### Post by Phsyco_kid on 2006-06-06
I have to make a 2Gig root partition for the install, but does it have to be an HFS type partition? And how come I cannot make an hfs+ partition? hfs cannot support a big enough file size to have 2gig root partition.

---

### Post by tidris on 2006-06-06
The LINUX root partition is normally formatted as ext3 or ext2.

---

### Post by nuke on 2006-06-06
tidris is correct.

For X/K/Ubuntu, you will want to use one of the Linux partition formats.  I don't want to start a flame war here but there are many more than just ext2/3.

However, you will want to use one of these two if you want to run OSX or OS9 in addition to X/K/Ubuntu as there are free kernel extensions to mount and read ext2/3 from the Mac at Sourceforge.

---

### Post by Phsyco_kid on 2006-06-06
Okay, thanks for the help.

*edit* When I try to format the swap partition, the root partition, and the other partition for holding all of the files, they show up as "unformatted" or have a corrupted file format. I tried to make the swap partition "linux-swap", the root partition "ext3" and the other partition "ext3". The changes I made to the hard-drive also do not show up on the "Prepare mount poitns" section. What's happening there? *edit*

---

### Post by nuke on 2006-06-07
I have to apologize, but I think this has gone beyond my capabilities to help.  Anyone else help here please?

I presume that you have already partitioned the drive and are just having problems with the file systems?  The only thing that I can think of is to check that qparted hasn't already locked those partitions ... i.e. won't let you touch them without umounting or disabling.  

In the installer, you may also try the "format" command during the partitioning.  I had some problems until I found "format" command.  It is a few menu items into the "file system" part of the partitioning.

Sorry that I can't be more helpful.

---

### Post by xurios on 2006-06-07
When I was doing my initial install, I had lots of problems trying to figure out what I should do with the partitions. Essentially, what ended up working was to completely erase (make into free space) the partition(s) I intended to use for linux, and then let the installer do what it wants. Trying to second guess the installer before I had a clear idea of what ubuntu needed to function properly only led to failure. By letting the installer do what it wanted, I got something that worked, which I could then study to learn about ubuntu partitioning schemes on ppc.

I would reccomend using parted from the console ([http://www.ubuntuforums.org/showthread.php?t=89960&highlight=resize+hfs+parted](http://www.ubuntuforums.org/showthread.php?t=89960&highlight=resize+hfs+parted)) to resize your hfs+ partition, if you haven't already, and free up whatever amount you need for linux. Then run the installer and trust it to do the right thing by default. 

For me, the installer showed three partitions for my OS X setup, (One little thing, 32K or something for the partition map, one main partition (mulitple Gigs) and one boot partition). It then made three more, it's own boot partition for yaboot, a main partition, and a swap. This setup works well.

---

### Post by tidris on 2006-06-07
I feel like you might be making this much more complicated than it needs to be.

If you are dedicating the entire disk to LINUX the easiest way to go is to let the ubuntu installer erase and automatically partition the disk for you.

If you want to have OSX and LINUX in the same disk, then create free space in the disk using the OSX disk utility and then let the ubuntu installer automatically partition the free disk space during installation.

---

### Post by kellogs on 2006-06-07
I made it using the osx cd to create the HFS newwordlmac type partition,  then ubuntu installer to create / (ext3) and swap(swap). yaboot finds the HFS and it does its work.

---

### Post by N8K99 on 2006-06-15
what if I want to make another partition that is mountable by both os x and kubuntu? do I make it hfs or hfs+? I want to have a partition which I can store data that is usable by both ossen. Mostly MP3s but also images as well.

---

### Post by swartzfeger on 2006-06-15
[QUOTE=N8K99]what if I want to make another partition that is mountable by both os x and kubuntu? do I make it hfs or hfs+? I want to have a partition which I can store data that is usable by both ossen. Mostly MP3s but also images as well.[/QUOTE]

I would like to know as well...

[edit] [This]("http://www.versiontracker.com/dyn/moreinfo/macosx/18619") allows OS X to read Linux /ext2 disks.

---

### Post by nuke on 2006-06-15
I think you could use either ext2/3 or hfs+.  I wouldn't go back to using hfs.

Option 1)  format shared file space as hfs+.  My personal preference is to use this.  You can install the hfs+ modules for the Ubuntu kernel so it can mount and read these files.  I don't think it is installed by default. (Can someone clarify this?)

Option 2) format shared file space as ext2/3.  It should work but you have to install the [http://sourceforge.net/projects/ext2fsx/]("http://sourceforge.net/projects/ext2fsx/") so when you are running the Mac OS you can see and use files on the ext2/3 partition.

I use Option 1 ... all shared files are on the hfs+ partition.  But I have also installed the ext2/3 module because inevitably, there is some file on the ext2/3 partition that I need when I am running the Mac OS.

I realize this doesn't exactly give you a definitive answer, but as with many things in the world of computers ... it depends on what you need to do.

Good luck!

---

### Post by N8K99 on 2006-06-17
Excellent! This is pretty much what I did in order to set up my laptop the way that I want. 

First, I partitioned the HD during the OS X installation. I made two HFS+ partitions and left one Free Space. The first HFS+, I named OS X and the second I named Superfluidity ( I have a perchance for using the thesaurus during my naming schemes). Then I installed OS X in the suitably named partition. 

Next, I installed Kubuntu and allowed the partitioning tool to use the largest continuous space. I made sure to name this partition, Kubuntu.

Once all this business was complete. I edited /etc/fstab so that the partition Superfluidity is auto mounted; this was very simple to do, if you can use a text editor you can add the appropriate line. NOTE: I had to create a directory within my /media directory. At this point, I can read and write to Superfluidity no matter which Ossen I am running, with the exception of when I have mol running OS X at the same time. Maybe I can use ftp to transfer across the localserver in this case, I don't know yet.

---

### Post by Najand on 2006-06-17
[QUOTE=N8K99]what if I want to make another partition that is mountable by both os x and kubuntu? do I make it hfs or hfs+? I want to have a partition which I can store data that is usable by both ossen. Mostly MP3s but also images as well.[/QUOTE]

I don't know if it can help you or not, but for mounting HFS+ partitions in Linux use the followiing command (when your source is /dev/hda3 and your destination is /media/MacOsX):

```
mount -t hfsplus -o rw,users /dev/hda3 /media/MacOsX/
```

---

### Post by N8K99 on 2006-06-18
oh thank you for this suggestion - if you see my post just above your reply, you will see that I have configured my system so that when I start up the computer I have a separate partition which allows me to access it no matter which OS I am running at the moment.

---

### Post by SogniX on 2006-06-19
[QUOTE=Najand]I don't know if it can help you or not, but for mounting HFS+ partitions in Linux use the followiing command (when your source is /dev/hda3 and your destination is /media/MacOsX):

```
mount -t hfsplus -o rw,users /dev/hda3 /media/MacOsX/
```[/QUOTE]

Hi, I need to use an HFS+ formatted disk on Ubuntu (on a PC), and this code does indeed mount the drive - but does not allow me to write. 
Any idea how to fix it? :(

---

### Post by xurios on 2006-06-20
In order to write to the hfs+ from the linux side, you have to disable journaling on the hfs+ volume from the os x side.

From terminal in os x, this command:

```
diskutil disableJournal /<volume here>
```

<volume here> being replaced by the volume you want to write to from linux.
That's what it takes to get it to work if you are using a mac with ubuntu on it. Since you are using a PC, I don't know if you will be able to write to it at all (never tried it), but it's worth a try.

---

### Post by nuke on 2006-06-20
Hmmm.  I think it should work since the command has the "rw" option.  (r=read, w=write).

Are you sure you used these options?

---

### Post by onehotcutey on 2006-06-20
For reading and writing a HFS+ drive in linux you also need to check the owner ID of the files and directories you are trying to write to.

OS X, as least Tiger, starts the UID at 500 or 501 and Dapper starts at 1000 or 1001.  So if you try to write to the 500 owned files from within Dapper it won't write, sometimes it won't even let you view them. (at least it didn't let me until I change the permissions)

I changed the group permission to rw in os x, since I am the only user of my laptop, and created a new group in Dapper with the same GID number.  It worked for me though the problem may have come from me fiddling around with everything.

---

### Post by SogniX on 2006-06-20
Thanks guys, I figured it out and xurios was right, I had journaling on. I stuck it in a USB IDE box to my iMac and reformatted it without Journaling. Now it works beautifully! :)

---

