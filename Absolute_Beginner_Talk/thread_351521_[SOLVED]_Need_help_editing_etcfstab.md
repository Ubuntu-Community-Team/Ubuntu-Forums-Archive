---
title: "[SOLVED] Need help editing /etc/fstab"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-02-02
I've just added a 320 GB hd to my comp, and I'd like to use this as, basically, music storage. Via gparted I've created two partitions, a primary which is the bulk of the drive, and a 10 GB swap. Now on to fstab...

 I have been reading various guides for editing /etc/fstab, and unfortunately I don't really understand a word of it. For example, one thread called on me to use ```
sudo mkdir /mnt/ext3
```
Unfortunately, I created this directory on my old disk (is that going to cause me a problem?)

Here's what I think I've been able to put together thus far for my fstab:
```
[device] = /dev/hdb1
[mount point] = ???
[filesystem] = ext3
[options] = defaults
[dump] = 0
[fsck] = 1
```

I have no clue what a mountpoint is or how to make one. Furthermore, my current drive's fstab looks different from what I'm seeing in other threads:
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
See what I mean? The order of entries appears to be different from what bodhi.zazen and others describe. Is this due to my upgrade to Edgy?

Anyhow, I need someone to spoon-feed me how to create a mountpoint, what to put in fstab and mtab, and how. Thank you all in advance.

---

### Post by be4truth on 2007-02-02
Hi,
you need to tell your computer which partition you want to mount where and what file system is it. Easy?! Everything is a bit difficult the first time.
Can you find out what partitions you want to mount?
I assume you have one player and 2 harddrives installed. Is that correct?
You first harddrive on your first IDE port is hda, the slave is probably hdb (could be the 2nd harddrive or the player) On the second cable the master is probably hdc, the slace hdd. Does that mean something to you?

---

### Post by aysiu on 2007-02-02
A *mount point* is just where you want the drive to appear to be accessible.

If you try to change directories to (or *cd* to) /dev/hdb1, you'll see it is not a directory. You cannot access the drive directly. You need a folder for it to appear in: ```
ricardisimo@ubuntu~$ cd /dev/hdb1
bash: cd: /dev/hdb1: Not a directory
``` After you've mounted /dev/hdb1 properly--let's say, as in your example, you decide to mount it in /mnt/ext3, then you *will* be able to do this: ```
ricardisimo@ubuntu~$ cd /mnt/ext3
``` I don't exactly know what dump and pass are, but I usually use 0 for both, and I've never experienced any problems.

You can make your mount point anything. If you want to mount it in /home/ricardisimo/newdrive, you can create a folder called *newdrive* inside your home directory and mount it there. If you want to mount it in /media/seconddisk, you can create a folder called *seconddisk* inside the media folder and have your new drive's contents appear there.

Let's just, for simplicity's sake, say you want to have it be /media/storage (really, you can put it just about anywhere that isn't already taken): ```
sudo mkdir /media/storage
``` creates a folder called *storage* inside the /media directory. *mkdir* stands for *make a directory called*. *sudo* allows you to do this inside of /media, which is usually protected, but *sudo* temporarily gives you administrative privileges to make system-wide changes.

Then, make a backup copy of your /etc/fstab file: ```
sudo cp /etc/fstab /etc/fstab_backup
``` *sudo*, once again, allows you the power to make changes to a system file, and the *cp* command stands for *copy*.

Next, edit the /etc/fstab file: ```
sudo nano /etc/fstab
``` This opens the file with the *nano* text editor.

Add in this line: ```
/dev/hdb1 /media/storage ext3 defaults 0 0
``` Then save (Control-X, Y, Enter).

Have the changes to /etc/fstab take effect: ```
sudo mount -a
```

And finally, make sure you own the drive, now that it's mounted: ```
sudo chown -R ricardisimo:ricardisimo /media/storage
sudo chmod -R 755 /media/storage
``` Now, if you go to the /media/storage folder, you should see whatever's in your drive. Or if nothing's there, you can put stuff there.

You can read more about /etc/fstab here:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

If all of this seems like too much trouble, use another Linux distro like Mepis--where you can one-click mount any drive (internal or external) without futzing about with the /etc/fstab file. Maybe Ubuntu will fix this in a future release to be less complicated.

---

### Post by pseudonym on 2007-02-02
OK, here's how to do it -

1. Run gparted again and repartition your drive - you do not need a swap partition on a storage drive, and you will most certainly not need a 10GB one.

2. A mount point is the area on your system where you will access the drive's data (eg. /home). /media is usually the place where extra hard drives are mounted. ```
sudo mkdir /media/store
``` (or whatever you want to call it).

3. You need to create an entry in /etc/fstab to mount the drive on startup. But first you need to get the drives 'UUID'. Do this by running 'blkid' in a terminal.

4. sudo gedit /etc/fstab and add a line like this -

# /dev/hdb1
UUID=8bc2c0e7-b680-4198-a137-0983a9b27e54 /media/store  ext3    defaults  0  0

Make sure to include your drive's UUID - the above is just for reference.

5. Save and exit gedit. Then run sudo mount -a and you should now have your drive set up. If you get permission problems just change the permissions on the mount point - sudo chmod 666 /media/store .

et voila!

now, did anyone beat me to this?

edit: yep! :)

---

### Post by aysiu on 2007-02-02
> **pseudonym said:**
> 
3. You need to create an entry in /etc/fstab to mount the drive on startup. But first you need to get the drives 'UUID'. Do this by running 'blkid' in a terminal.

4. sudo gedit /etc/fstab and add a line like this -

# /dev/hdb1
UUID=8bc2c0e7-b680-4198-a137-0983a9b27e54 /media/store  ext3    defaults  0  0

Make sure to include your drive's UUID - the above is just for reference. I don't believe you need the UUID, actually. Edgy defaults to using the UUID instead of the /dev, but the /dev should work just fine.

---

### Post by pseudonym on 2007-02-02
> **aysiu said:**
> A *mount point* I don't exactly know what dump and pass are, but I usually use 0 for both, and I've never experienced any problems.
Just FYI, setting 'dump' means that the filesystem will be, er, 'dumped' on startup ie. backed up (to where, I don't know).

'Pass' determines which filesystems will be fscked on startup. From the fstab manpage -

'The sixth field, (fs_passno), is used by the fsck program to determine the order in which filesystem checks are done at reboot time. The root filesystem should be specified with a fs_passno of 1, and other filesystems should have a fs_passno of 2. Filesystems within a drive will be checked sequentially, but filesystems on different drives will be checked at the same time to utilize parallelism available in the hardware. If the sixth field is not present or zero, a value of zero is returned and fsck will assume that the filesystem does not need to be checked.'

Opting to have each partition dumped and fscked (!) will seriously slow down your bootup time, so '0 0' are the best options for 'dump' and 'pass' in /etc/fstab.

---

### Post by pseudonym on 2007-02-02
> **aysiu said:**
> I don't believe you need the UUID, actually. Edgy defaults to using the UUID instead of the /dev, but the /dev should work just fine.
That's not what I've found. Edgy will include UUIDs at install time, but for drives added later you need to add them manually. Without it, I think the mount command returns an error about 'wrong fs type or bad superblock' or some such.

---

### Post by Malac on 2007-02-02
> **pseudonym said:**
> That's not what I've found. Edgy will include UUIDs at install time, but for drives added later you need to add them manually. Without it, I think the mount command returns an error about 'wrong fs type or bad superblock' or some such.

After upgrading to Edgy, I reset all my partitions to /dev/hd... values in /etc/fstab  as I can't stand the UUID number thing, far too confusing. I have had no problems with mounting and unmounting the drives whatsoever, no errors of wrong fs or bad superblock.

---

### Post by aysiu on 2007-02-02
> **pseudonym said:**
> That's not what I've found. Edgy will include UUIDs at install time, but for drives added later you need to add them manually. Without it, I think the mount command returns an error about 'wrong fs type or bad superblock' or some such.
That's not what I mean.

I'm not saying Edgy will automatically add new drives. In fact, I explicitly told the OP that doesn't happen in Ubuntu (and it's annoying), unlike in Mepis.

I'm saying you don't need to use the UUID. You can use /dev/hdb1 or whatever.

---

### Post by ricardisimo on 2007-02-02
OK. There's some logical gap in my brain that isn't allowing me either to understand what I need to do or explain what I don't understand. Here's the Catch-22: I can't access the new drive until I create a mountpoint, but I can't create the mountpoint until I can access the new drive. At least, that's what I've gathered here. This should give you an idea of how slow my brain works. From my perspective, ```
sudo mkdir /media/storage
``` is just going to create a directory on my old drive called /media/storage (which probably already exists). Meanwhile, if, as aysiu pointed out, I try to relocate via ```
cd dev/hdb1
``` before I try making a directory, well... it just won't work.

I'm missing something pretty basic here. What is it?

---

### Post by pseudonym on 2007-02-02
> **Malac said:**
> After upgrading to Edgy, I reset all my partitions to /dev/hd... values in /etc/fstab  as I can't stand the UUID number thing, far too confusing. I have had no problems with mounting and unmounting the drives whatsoever, no errors of wrong fs or bad superblock.
In that case I can only assume you must either have all of /etc/fstab as '/dev/...' , or all 'UUID', but not a mixture of the two. I tried adding a partition post-install with just '/dev/...' in an otherwise 'UUID' fstab and it wouldn't mount. So I 'UUIDed' it and it did.

---

### Post by aysiu on 2007-02-02
No.

```
cd /dev/hdb1
``` is not supposed to work. I was using that as an example so you could see the necessity of having a mount point. You can't access the drive directly. You need a folder for it to appear in.

Just follow the steps I gave you before:
1. Create the mount point (yes, before you edit the /etc/fstab, it will remain an empty folder)
2. Back up the /etc/fstab file
3. Edit the /etc/fstab file and put the appropriate line in
4. Save and mount everything
5. Change ownership of the drive to you

Now it's ready for use.

I also have generic instructions for this here:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by aysiu on 2007-02-02
> **pseudonym said:**
> In that case I can only assume you must either have all of /etc/fstab as '/dev/...' , or all 'UUID', but not a mixture of the two. I tried adding a partition post-install with just '/dev/...' in an otherwise 'UUID' fstab and it wouldn't mount. So I 'UUIDed' it and it did.
I don't know why you're encountering that problem, but I've successfully (in Edgy) mixed and matched /dev/xxx with UUID and had no such problems.

---

### Post by ricardisimo on 2007-02-02
I think I might be having a bit of an epiphany here. So, Filesystem encompasses the whole compootor, not just the drive on which it might *physically* be located (the master drive, of course). So I create a mountpoint for drive B on Filesystem which is physically on drive A, but that doesn't matter, because it governs the whole OS. Am I anywhere near reality here? OK. Let me go back and start from scratch. By the way, psuedo, I'm leaving the 10 Gigs alone, since I might one day change my mind and want to dual-boot on that drive with Red Hat or some such, just for goofs if nothing else. No big. I got by for four years with a 40 GB, I think I can somehow make do with 310 GB. Thanks all. Wish me luck.

---

### Post by ricardisimo on 2007-02-02
I'm not sure if it worked or not, aysiu. I created /mnt/hdb1 as per your instructions. Then I edited fstab, adding (along with a comment line - I assume that's OK):
```
# /dev/hdb1 -- adding new 320 GB drive
/dev/hdb1 /mnt/hdb1 ext3 defaults 0 0
```
On the plus side, /mnt/hdb1 immediately had within it a new folder (which I did *not* create) called "Lost+Found". That would lead me to believe that something substantive was accomplished. On the other hand, when I open my Home folder in Nautilus, I'm still down to 3.5 GB, which is what's left on hda. How do I access hdb? Also, is there no drag-and-drop from one drive to the other in Ubuntu? Thanks again for everything.

---

### Post by ricardisimo on 2007-02-02
Wait a second... /mnt/hdb1/lost+found is, indeed, 269.2 GB in size. This is just bizarre, though. Why doesn't my Home folder reflect the added space? How do I make it do so?

---

### Post by pseudonym on 2007-02-02
By adding the new hard drive, you have not increased the size of your /home directory. You have added more space which is mounted on another part of the system - /mnt/hdb1. If you want to access this space from your /home, what you need to do is create a 'symbolic link' to /mnt/hdb1. Open up a terminal at /home/your_user_name and enter the following - ```
ln -s /mnt/hdb1 .
``` A linked directory will appear in /home/your_user_name, and when you click on it you will be taken to the /mnt/hdb1 folder.

The 'lost+found' directory in /mnt/hdb1 has to do with the journalling feature of the ext3 file system - a certain amount of disk space is permanently 'reserved' in this directory by ext3 which is supposed to prevent it from becoming fragmented like windows file systems. This comes at a cost of some disk space, however.

A 'lost+found' directory will exist on each ext3 partition you have, but you will never have a reason to enter or use this directory, I should point out.

Assuming you did every thing right re the instructions in previous posts, if you browse to /mnt/hdb1 in Nautilus you should see the right amount of free space appear in the status bar. :)

---

### Post by ricardisimo on 2007-02-02
Would I be better off creating the symbolic link one level up? That is, couldn't I make it in / rather than in /home? Thanks.

---

### Post by pseudonym on 2007-02-02
> **ricardisimo said:**
> Would I be better off creating the symbolic link one level up? That is, couldn't I make it in / rather than in /home? Thanks.
You can create the link wherever you like, but if you want to have easy access to your storage drive from /home/your_user_name, then you would create it in that directory.

You can also create more than one link if you want. But some places (like /) will require you to use 'sudo ln -s ....' to create it.

---

### Post by ricardisimo on 2007-02-02
I think I understand. Maybe I was concerned about other users having access to the space, but that probably has nothing to do with where the link is, or does it? How do I make sure that other users can read and write on the new drive?

Also, I'm finally understand that I have, indeed, simply thrown away 9 Gigs by having a 10 GB swap. Is it a bad idea at this point to start over anew, delete the entire drive and repartition it with just a 1GB swap, just in case I do need it one day. Or maybe just one partition, no swap (assuming I can add it later). What do you think, and how do I delete and start over?

---

### Post by aysiu on 2007-02-02
If you already have a swap partition on your main drive, you don't need to have a swap partition (of any size) on the second drive.

You can delete it using GParted: ```
sudo aptitude update
sudo aptitude install gparted gksu
gksudo gparted &
```

---

### Post by pseudonym on 2007-02-02
> **ricardisimo said:**
> I think I understand. Maybe I was concerned about other users having access to the space, but that probably has nothing to do with where the link is, or does it? How do I make sure that other users can read and write on the new drive?
If you haven't already done so, set the permissions on /mnt/hdb1 like so - ```
sudo chmod 666 /mnt/hdb1
``` This gives all users read/write access. Then just create symbolic links to /mnt/hdb1 in each user's /home directory.

> **ricardisimo said:**
> Also, I'm finally understand that I have, indeed, simply thrown away 9 Gigs by having a 10 GB swap. Is it a bad idea at this point to start over anew, delete the entire drive and repartition it with just a 1GB swap, just in case I do need it one day. Or maybe just one partition, no swap (assuming I can add it later). What do you think, and how do I delete and start over?
Do you have a swap partition on your main hard drive? If so, you don't need another one on the storage drive. I think the system can only use one swap at a time anyway.

If you don't already have swap, and want to have one, you really don't need any more than about 512 MB. A modern (last 3-4 years) system with a decent amount of RAM is unlikely to use it, but it can be comforting to know its there if the need arises.

If you haven't filled up the new drive with data yet, and you have no other use for a 10 GB partition, then I'd reformat the drive and start over. Just unmount it and run gparted again, delete each partition, and create/format a single new one.

btw, if you want to maximise disk space, don't use ext3. Use reiserfs if you're going to be filling up the drive with small(ish) files, and xfs if you're going to work with large files (eg. video files).

If you do have a use for the 10 GB partition (eg. as a space to install and play around with other distros), then just use gparted to delete and reformat that one only.

Whatever you decide, you'll need to edit /etc/fstab again, deleting no longer exisiting partitions on this drive and/or changing the filesystem type on the new one(s).

HTH

---

### Post by ricardisimo on 2007-02-02
It was all looking really good until I restarted my comp. Now all of the folders I created there are gone, along with some of the files I moved over as a test. Mind you, I did unmount/resize/mount with gparted before restarting the comp. I just figured no matter what size I made it, it was still going to be "hdb1". Any clue what's going on?

---

### Post by Malac on 2007-02-02
> **ricardisimo said:**
> It was all looking really good until I restarted my comp. Now all of the folders I created there are gone, along with some of the files I moved over as a test. Mind you, I did unmount/resize/mount with gparted before restarting the comp. I just figured no matter what size I made it, it was still going to be "hdb1". Any clue what's going on?
You're not creating these from the live CD are you? As unless you mount your hard disk /mnt folder and use that not the CD /mnt folder, you will be creating them in the Live CD's volatile environment which disappears once you reboot.

Post a screenshot of gparted (Print Screen Key) or output of sudo fdisk -l and a copy of your hard-disk /etc/fstab file.

---

### Post by meomike2000 on 2007-02-02
Well I am very new to ubuntu or any linux, I have always used windows. But it seems to me that u can create a folder to mount the file anywhere or anyname that isnt used. Then u have to set that file to be the mount point for the new drive in /etc/fstab. I dont know which if either or if both are right but they have both told u diffrent was. All I can say is try the fist one and if that dont work restore your backup fstab and try the second idea.

---

### Post by ricardisimo on 2007-02-02
Firstly, an apology to everyone in Ubuntu; I'm working with two separate threads on the same issue, but for whatever it's worth, they started out as somewhat different topics.

That said, here are the screenshots, here's my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=f7733fa7-4cce-4d65-9ec8-c43327e30716 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=c4176c38-a4dd-4eb2-afe4-b883a51472a3 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hdb1 -- adding new 320 GB drive
/dev/hdb1 /mnt/hdb1 ext3 defaults 0 0
```
And here's fdisk output:
```
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4910    39439543+  83  Linux
/dev/hda2            4911        4998      706860    5  Extended
/dev/hda5            4911        4998      706828+  82  Linux swap / Solaris

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       38913   312568641   83  Linux
```

Finally, no, I'm not running off of Live CD. Thanks again for any help.

---

### Post by pseudonym on 2007-02-02
Is the drive still being mounted when you restart? Is it readable/writable by all users? It should be, according to the info you gave above. It's just that the data which you had on it before your resize has disappeared, right?

I think the data must have been wiped during the resize. Personally, I never do this, even though many others report success. I prefer to reformat because there's less chance of something going wrong. Perhaps there is an option in gparted to 'retain exisiting data' (or similar) which you didn't set?

Anyway, if it was just a test you were doing, you should be OK to replace the data on the new drive. Just delete then recreate any symlinks to it you made and you should be good to go.

btw, in case you were wondering, the 5 GB which gparted reports as 'used' is the lost+found/journalling I mentioned earlier.

HTH

---

### Post by ricardisimo on 2007-02-02
[COLOR="Red"][SIZE="5"]SUCCESS!![/SIZE][/COLOR]
You know, sometimes it pays to be real stupid and real lucky. The short story is that I was asking for help in two different threads, and this appears to have been the source of both my troubles and the ultimate resolution of the problem. The somewhat longer version is as follows...

In one thread bodhi.zazen gave me these command lines regarding setting permission/ownership (please ignore the foldername fictions):
```
sudo chown user_name:users /media/music
sudo chmod 777 /media/music
```
Meanwhile in this thread aysiu recommended the following:
```
sudo chown -R ricardisimo:ricardisimo /media/storage
sudo chmod -R 755 /media/storage
```
Neither worked perfectly well in several different attempts. Finally, I sort of combined the two, keeping aysiu's "-R" and bz's "777". It worked.

Now let me be perfectly clear about something - I have absolutely no idea what I'm doing, and so obviously this little maneuver may have had less than nothing to do with fixing the problem. However, I did it and now it's all good. That's my story, and I'm sticking with it.

I want to thank all of you for being so very patient with this numskull. Special thanks to pseudonym, aysiu and bodhi.zazen.

---

### Post by pseudonym on 2007-02-03
Glad to hear it. :)

In case you were wondering, the '-R' stands for 'recursive', meaning the action you're performing should apply to the specified directory and everything within it. And '777' is the most relaxed permissions you can have, meaning everything is readable, writable, and executable by all users.

If you want to read up on all this, [this wiki entry]("https://help.ubuntu.com/community/FilePermissions?highlight=%28permissions%29") should help.

---

### Post by ricardisimo on 2007-02-03
> **pseudonym said:**
> Glad to hear it. :)

In case you were wondering, the '-R' stands for 'recursive', meaning the action you're performing should apply to the specified directory and everything within it. And '777' is the most relaxed permissions you can have, meaning everything is readable, writable, and executable by all users.

If you want to read up on all this, [this wiki entry]("https://help.ubuntu.com/community/FilePermissions?highlight=%28permissions%29") should help.

I was wondering, and in fact I had asked about just that in another thread a few weeks ago, and no one ever responded. Thanks, I'll check it out.

There is one further question that I might as well ask here (although i think it should properly be in a new post)... is there any way to have the desktop "Trash Can" control every .Trash folder on the compootor (on every fixed and on every removable)? <CTRL H> and then manually deleting will get a tad tiresome in the future, I suspect. Thanks again.

---

### Post by vuarra on 2007-02-03
Okay.

Everything in this thread makes complete sense.  I even remember bits and pieces from my high school days where the higher end computers were using QNX, a Canadian educational version of Unix.


```
sudo chmod -R 666 /dev/sda2
```

gives me absolutely no feedback, and the HPFS disc remains unreadable.  As a matter of fact, it doesn't even ask for a password. I tried a blkid, and this is what it came up with:

/dev/sda1: LABEL="HP_RECOVERY" UUID="4382-D2F5" TYPE="vfat" 
/dev/sda2: TYPE="ntfs" 
/dev/hda1: UUID="2d722fd3-6d8c-47fc-8ec6-f7228c3bc4e1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: UUID="db73e05b-b5ab-49f0-8d04-038af5cd4aad" TYPE="swap" 

As much as I'd love to just remove the complete Winbloze drive, my wife won't let me, and I don't have enough storage to move the assorted files there anyway.  I have mounted the drive under /windows, and under home/*user*/windows (and learned the umount function, too :)), but I still have no access to any data on that hard disc.

Any hints, tips, etc, before I follow someone's advise - borf the drive and install Linspire?


EDIT
Assuming that the general population of lemmings (yeah, like myself) are so stupid as to be using Microshaft Winbloze, why wouldn't info listed on a few other spaces be posted in a sticky?

---

### Post by bodhi.zazen on 2007-02-03
Well, if you are lazy, mount the drive then, in a terminal, enter : ```
gksudo nautilus
```

This will open your browser as root. Navigate to your mount point.

Alternate it to follow this thread:

[http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

---

### Post by Malac on 2007-02-04
> **ricardisimo said:**
> I was wondering, and in fact I had asked about just that in another thread a few weeks ago, and no one ever responded. Thanks, I'll check it out.

There is one further question that I might as well ask here (although i think it should properly be in a new post)... is there any way to have the desktop "Trash Can" control every .Trash folder on the compootor (on every fixed and on every removable)? <CTRL H> and then manually deleting will get a tad tiresome in the future, I suspect. Thanks again.
Unfortunately each drive has it's own Trash folder at present I (and several others) have asked for a single Trash folder feature, we'll just have to wait and see if it will be taken up. I think there is a thread on the forum somewhere that is running a poll on which one people prefer.

If you don't like send things to Trash then having to empty the Trash folder, press <Shift><Delete> which deletes the file instead of moving it to the Trash. (Be careful) :)

---

### Post by xhaan on 2007-02-04
> **Malac said:**
> Unfortunately each drive has it's own Trash folder at present I (and several others) have asked for a single Trash folder feature, we'll just have to wait and see if it will be taken up. I think there is a thread on the forum somewhere that is running a poll on which one people prefer.

If you don't like send things to Trash then having to empty the Trash folder, press <Shift><Delete> which deletes the file instead of moving it to the Trash. (Be careful) :)

I wonder... is the trash folder a normal folder, or is it special like lost+found?
Can you link it in other words? :0

---

### Post by ricardisimo on 2007-02-04
> **xhaan said:**
> I wonder... is the trash folder a normal folder, or is it special like lost+found?
Can you link it in other words? :0

Are you thinking about maybe some sort of script to perform action x in a/b/c folders?

---

### Post by ricardisimo on 2007-03-01
So I'm kind of back to square one. I was having persistent audio problems that were only resolved by a fresh install, specifically of Feisty (Herd 3 as I recall, but all caught up by now I'm sure). Feisty detects and displays the drive perfectly well in Nautilus' "Tree" and "Places" views, but only as an existing drive, *not yet mounted*. To mount I just double-click on it and enter my password.

This would be fine if not for the fact that sometimes I forget to mount, and often I'll start downloading music or other binaries, which will download and then get purged because my newsreader can't yet access this, my storage drive. Total waste of bandwidth, as you can imagine.

I tried repeating from above the following:
```
sudo chown -R username:username /media/disk
sudo chmod -R 777 /media/disk
```
... to no avail. No difference in behavior, nor in /etc/fstab as far as I can tell. Obviously, this could be a quirk with Feisty as it develops, but I suspect that since the situation is somewhat different than before I need to do something somewhat different as well. Any help? Thanks in advance.

---

### Post by freebird54 on 2007-03-02
The problem would appear to be a conceptual one.  Linux treats your entire filesystem as just one drive - no matter how many partitions/drives actually make it up.  A 'mount point' then is just the apparent directory in which your newly mounted partition/drive 'shows up' after it is mounted.

If you chose /media/newdrive as this point, the beginning of that drive will appear as if it was the directory /media/newdrive.

Anyway - first create a directory where you WISH your new drive/partition should be, then mount it with that directory as the mount point.

Clearer?  (we hope)

---

### Post by ricardisimo on 2007-03-02
Does it matter that Feisty has already given a mountpoint, namely /media/disk? I probably should have clarified that, but I figured it was apparent in the question, or at least the code i posted. Thanks again.

---

### Post by freebird54 on 2007-03-02
Doesn't matter.  If YOU want it there, then put it there.  If you choose something else - so long as it exists when you try to mount it, the file system does not care.

If you wish to mount it as /media/disk on Mon Wed Fri, /home/extradisk on Tue Thur Sat and /media/newname on Sunday - the system will just do it that way - though it sounds like more work than its worth!! 

Flexibility is the name of the game with these systems.  My own /media/windows mountpoint often has a different drive there on different boots - depending on whether I have actual Windows there, or a drive full of music files that I'm slowly converting to ogg format.  I know which drive it is by looking at the file structure (and by knowing which one I plugged in, hopefully).

---

### Post by Chazall1 on 2007-03-03
I just switched from a single HD, Dual booting XP and Edgy. to Dual Booting with 2 HD's. Both IDE. I moved XP from the Primary Master HD to the Primary Slave, Both cable select. I have the Same XP partitions that were on the 1st HD and moved to the 2nd HD. Would the UUID # change for the NTFS partition? My fat 32 had mounted when I changed the DH info, from had,1 to hdb,1 for the fat32 but when I changed the hda,2 to hab,2 for the NTFS It has not mounted yet. I did (mount -a) and it indicated that I needed to boot Windows 3 times for this to function. How do I get new UUID #? How can I force mount? That was also an option stated to me when I ran the mount -a. I would like to have my NTFS mounted on startup. Here is my Fstab info!

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6 -- converted during upgrade to edgy
UUID=8bd36f06-7967-47e4-9933-669abf52b03f / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=18c79eac-b4e4-4fea-a502-786ce82af86e /home ext3 defaults 0 2
# /dev/hdb1 -- converted during upgrade to edgy
UUID=07D4-0C0C /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hdb2 -- converted during upgrade to edgy
UUID=CAF012F3F012E58B /media/hda2 ntfs-3g silent,umask=0,locale=en_US.utf8,no_def_opts,allow_other 0 0
#/dev/hdb3       /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda7 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Thanks

---

### Post by ricardisimo on 2007-03-04
Success again, only with a little quirk. I had to make a new directory, and i don't really understand why. I edited my fstab with nano, adding </dev/hdb1 /media/disk ext3 defaults 0 0>, and then ran ```
sudo mount -a
```
Unless I'm very much mistaken that folder, /media/disk, got wiped out, or at least I couldn't see it where it should have been. I'll go back and look tomorrow. Anyway, no big. I created a new mount point, namely /media/storage repeated the above and now it's all good. Thanks again to everyone.

P.S. - I agree with Aysiu that Ubuntu would do well to come up with an easier system, maybe just autodetect with a first-run prompt asking whether and how to mount the drive, what protections, etc. When I plugged in an ethernet cable Feisty did everything without asking a single question. I installed a DVD writer and it didn't even blink; there it was the next time I booted, working perfectly without even a mention that anything was different or new. I have to believe the same can be done with internal hard disks.

---

### Post by ricardisimo on 2007-06-07
An addendum to the whole story: as of the latest kernel upgrade, linux-image-2.6.20-16-386, UUIDs are no longer optional, as many of you may have noticed. You can get the UUID by entering in a terminal (for example):
```
sudo vol_id /dev/sdb1
```
or whatever descriptive name the drive currently has in your /etc/fstab. Then edit your fstab as described earlier in this thread.

I'm curious whether CD and DVD drives can or should also get UUIDs. Does anyone know? It might resolve some issues k3b and especially Nautilus are having on my work compootor, where I have both a CD burner/DVD Reader and a CD-DVD RW (don't ask... seemed like a good idea at the time). Thanks in advance.

---

### Post by bodhi.zazen on 2007-06-07
Nice one.

You can also get UUID with :```
blkid
```

---

### Post by ricardisimo on 2007-06-14
Why are there no UUIDs for CD/DVD drives? I'm having quite [a difficult time of it]("http://ubuntuforums.org/showthread.php?p=2846610") right now without them. At least I'd like to believe that they could help right now. Here's the basics:
[LIST]
[*]I have a CDRW/DVDROM and a CDRW-DVDRW;
[*]DVDs are invisible in the DVDRW;
[*]Audio CDs are invisible in either slot for everything except Sound Juicer (you name it - k3b, Audacious, XMMS, Grip, etc.).
[/LIST]
Here's my current fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=5cbae883-1ea5-4909-a0f7-25dd778ffc45 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1cfc19bb-b5dc-4199-8498-7bb897ec58f6 none            swap    sw              0       0
/dev/sdb1 /media/storage ext3 defaults 0 0
#/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
#/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```
Here's the grep output:
```
~$ ls -l /dev | grep cd
lrwxrwxrwx 1 root root           4 2007-06-14 17:45 cdrom -> scd1
lrwxrwxrwx 1 root root           4 2007-06-14 17:45 cdrw -> scd1
lrwxrwxrwx 1 root root           4 2007-06-14 17:45 dvd -> scd1
lrwxrwxrwx 1 root root           4 2007-06-14 17:45 dvdrw -> scd1
crw-rw-rw- 1 root tty       2, 221 2007-06-14 17:44 ptycd
brw-rw---- 1 root cdrom    11,   0 2007-06-14 17:44 scd0
brw-rw---- 1 root cdrom    11,   1 2007-06-14 17:44 scd1
crw-rw---- 1 root cdrom    21,   2 2007-06-14 17:44 sg2
crw-rw---- 1 root cdrom    21,   3 2007-06-14 17:44 sg3
lrwxrwxrwx 1 root root           4 2007-06-14 17:45 sr0 -> scd0
lrwxrwxrwx 1 root root           4 2007-06-14 17:45 sr1 -> scd1
crw-rw-rw- 1 root tty       3, 221 2007-06-14 17:44 ttycd
```
... or, the variant that makes more sense to me in this case:
```
~$ ls -l /dev | grep cdrom
lrwxrwxrwx 1 root root           4 2007-06-14 17:45 cdrom -> scd1
brw-rw---- 1 root cdrom    11,   0 2007-06-14 17:44 scd0
brw-rw---- 1 root cdrom    11,   1 2007-06-14 17:44 scd1
crw-rw---- 1 root cdrom    21,   2 2007-06-14 17:44 sg2
crw-rw---- 1 root cdrom    21,   3 2007-06-14 17:44 sg3
```
And, just to be a completist:
```
~$ sudo lshw
*-cdrom:0
                description: DVD reader
                product: RW/DVD GCC-4520B
                vendor: HL-DT-ST
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/scd0
           *-cdrom:1
                description: DVD-RAM writer
                product: DVD-RAM GSA-H22L
                vendor: HL-DT-ST
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.00
                serial: [HL-DT-STDVD-RAM GSA-H22L1.0006/08/05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
```
Any help would be appreciated, and I can certainly try to give more info. Thanks in advance.

---

### Post by ricardisimo on 2007-06-16
I also appear to be having difficulties playing DVDs. I just getting farting noises, for lack of a better description. This may, of course, be a completely separate issue, perhaps relating to codecs, css or something else, but I thought I'd toss an extra little twist in here. Thanks again for any help.

---

### Post by theDaveTheRave on 2007-07-05
Hi All.

I recently bough a new laptop with vista. everthing is going really well so far and I am really getting into the forums in a major fashion.

quick bacground on the laptop;

Acer 3680.
80GB HDD - partitioned by Acer as:
                              10GB system restore.
                              35GB main vista system
                              35GB unused partition.
512 MB memory.

Brilliant thought I, nice and ready for ubuntu (I allready dual boot Dapper / XP on an old desktop and dedicated 486 laptop with Feisty).

when I tried to install Fiesty everything was great untill the part about partitioning. for some strange reason I couldn't shrink the main Vista partition - I wanted to use 10 -15GB as a share for common stuff I may need on both OSs.

So I just went for  clean instal of Fiesty onto the unused partition, everthing went great... even the wirless worked, and with a little fiddle I got DVD playback. :guitar: 

Well I started doing what I allways do, Virtual desktop, with college work (Programming) going on one, instructions and virtual books open on others.... All done to give the memory a really good kicking, expecially when using the internet as well!!

It wasn't untill it was going really slowly I decided to kill a couple of processes that had become unresponsive and ran a TOP, I was quite surprised when I noticed there was no swap allocated!

So I proceeded to fiddle to get the Vista partition to reduce in size and use some of the remaining as a swap partition.

----- appologies if this is getting a little long winded! -----;)

Reading through this thread there was a generally consensus that I would be just as well off with a swap file rather than a partition.

so by now I had allready taken the extra bit off vista and declared 10GB as fat32 system (NTFS wasn't an option from grparted for some reason), and the remining 1.2gb as Linux Swap.

Thinking that would be that I rebooted, well the 10GB was there but TOP didn't show the Swap being used automatically.

I followed the instruction in the thread, and here is a pasting of various codes etc.



> 
davemyers@Aramis:~$ blkid
/dev/sda1: TYPE="ntfs" 
/dev/sda2: TYPE="ntfs" 
/dev/sda3: UUID="755065ff-3e44-43c0-939c-1e79394e6d2e" TYPE="reiserfs" 
/dev/sda5: UUID="375b5042-1f19-4b9f-bdc1-fc2e75ae502d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="d742ae2a-1757-425f-9c93-06f020853f6e" TYPE="reiserfs" 
davemyers@Aramis:~$ 


which fits with the system details
sda1 - rescue
sda2 - vista
sda3 - Ubuntu

sda5 - 10gb ext3 / fat 32 storage area
sd6 - 1.2 GB swap extentsion.

by the way, to get sda5 and sda6 I needed to created am extended partition (this parent partition is designated sda4 when viewing the partition in gparted

which is confirmed with fkdisk

[quote=]
davemyers@Aramis:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   12  Compaq diagnostics
/dev/sda2   *        1020        3926    23349275+   6  FAT16
/dev/sda3            5395        9729    34820887+  83  Linux
/dev/sda4            3927        5394    11791710    5  Extended
/dev/sda5            3927        5201    10241406    b  W95 FAT32
/dev/sda6            5202        5394     1550241   83  Linux

[/quote]

and here is a copy of my /ect/fstab
> 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=755065ff-3e44-43c0-939c-1e79394e6d2e / reiserfs notail 0 1
# Entry for /dev/sda1 : Vista Backup
#old entry UUID=70DC233216D9B5D2 /media/sda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
UUID=70DC233216D9B5D2 /mnt/VistBackup ntfs-3g defaults,locale=en_GB.UTF-8 0 1

# Entry for /dev/sda2 : "Acer" partition
# old entryUUID=5C0C85240C84FA72 /media/sda2 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
UUID=5C0C85240C84FA72 /mnt/acer ntfs-3g defaults,locale=en_GB.UTF-8 0 1

#Entry for /dev/sda5 - created as 10GB of EXT-32 (vfat) for share between Linux$
UUID=488D232f /mnt/SysShare vfat defaults 0 0

#Entry for /dev/sda6 - to hold a file for memory swap.
UUID=d742ae2a-1757-425f-9c93-06f020853f6e reiserfs default 0 0

#Entry for CD player.
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0




Anyway I still can't be sure that the drives are being loaded at /mnt/....   appart from the main Vista partition.

running the mount -a command gives me what seems like astrange response of

> 
mount: special device /dev/disk/by-uuid/488D232f does not exist
mount: mount point reiserfs does not exist
davemyers@Aramis:~$ 




What I was planning on doing was creating a swap file on the partition of SDA6, but I haven't gone this far as it doesn't seem to be working as I expected??

The other reason is I want to get rid of the icons on my desktop for the drives, I hate having a "messy" desktop with files and links all over the place, right now it is just a nice picture, and nothing else., empty and clean looking - which is what I like about Gnome over KDE, forced me to keep things better organised!

I'm heading for some sleep now, maybee in the morning it will seem easier?

thanks in advance.

Dave

---

### Post by theDaveTheRave on 2007-07-06
Hi all.

brief update.

I turned on my laptop this morning, and all my drive now mount in /mnt/.... just like they should! so as I had hoped the morning did bring good fortune.

I do have one question.

When installing Ubuntu it asks for a swap drive, and in GParted it give the option of formating a partition as "linux swap".

Why doesn't Ubuntu automatically recognise this as the Swap area on boot up?? and as it doesn't how do I tell Ubuntu to use this partition as swap - I understand that using a file is "easier" and I will probably set the partition and insert a file to use the whole of the "disk", and what permisions should I give this portion of the disk??

one question on this is what file system should the Swap be?? i wsa thinking of reiserFS but then it occured to me that the size of the files may be quite small? is the native linux swap created at installation special in some way?

your help is most appreciated.

Dave

---

### Post by ricardisimo on 2007-07-06
I thought "linux-swap" **was** the filesystem for swap area, which makes it that much more confusing as to why your system isn't recognizing it. Maybe position on the disk, or some other factors are crucial.

You raise a question I've wanted to ask for a while: Is there ***a*** native filesystem for Linux and/or Ubuntu? Above and beyond all others in which it *can* work, is there one in which it was *designed* to work best or by default?

---

### Post by bodhi.zazen on 2007-07-06
> **theDaveTheRave said:**
> Hi all.

brief update.

I turned on my laptop this morning, and all my drive now mount in /mnt/.... just like they should! so as I had hoped the morning did bring good fortune.

I do have one question.

When installing Ubuntu it asks for a swap drive, and in GParted it give the option of formating a partition as "linux swap".

Why doesn't Ubuntu automatically recognise this as the Swap area on boot up?? and as it doesn't how do I tell Ubuntu to use this partition as swap - I understand that using a file is "easier" and I will probably set the partition and insert a file to use the whole of the "disk", and what permisions should I give this portion of the disk??

one question on this is what file system should the Swap be?? i wsa thinking of reiserFS but then it occured to me that the size of the files may be quite small? is the native linux swap created at installation special in some way?

your help is most appreciated.

Dave

Hi dave.

1. Swap is it's own format, so you format it as "swap" and not ext2/3 or reiser ...

2. When you format a partition the uuid changes ... so ... you will need to update your fstab again ...

FYI, in the future, ubuntu (and most distro's) should recognize a pre-existing swap so you do not need to format it, just mount it as swap. BSD will also use Linux swap, so share and share alike ....

---

### Post by theDaveTheRave on 2007-07-08
Bodhi.

Thanks for the info... I'll try it now.

Dave

OOh quick question, I use VLC media player for CD / DVD playback, is there any reason why this process may "break" this utility - as now when I try to play anything I get an error message reported back that the "connection refused".

I will ask this on the VLC forum / website but I haven't been able to find anything specific to VLC on ubuntu.org - any good links people out there are aware of?

thanks again in advance

Dave

---

