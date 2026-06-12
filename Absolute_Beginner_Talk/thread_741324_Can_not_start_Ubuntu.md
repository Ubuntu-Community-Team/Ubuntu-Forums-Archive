---
title: "Can not start Ubuntu"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by JonWasHere42 on 2008-03-31
Hey, I have a problem starting up Ubuntu. When I last turned off my computer, it was because it was saying something to the effect that I could not save Makefiles, because the I/O was read only. (Or something like that). Anyway, I tried to turn off my computer, but it froze during the shutdown, and said something (which i cant remember), so I was forced to do a hard shutdown.

Now when trying to start up i receive a message that says:

/bin/sh: line 6: /etc/init.d/rcS: is a directory
/bin/sh: line 6: exec: /etc/init.d/rcS cannot execute: Success
init: rcS main process (2381) terminated with status 126
/bin/sh: line 7: /etc/init.d/rc: is a directory
/bin/sh: line 7: exec: /etc/init.d/rc cannot execute: Success
init: rcS main process (2389) terminated with status 126

Any ideas?

--Jon

---

### Post by rkd on 2008-03-31
What were you in the middle of doing when you got that message about Makefiles couldn't be saved?

---

### Post by JonWasHere42 on 2008-04-01
I wasnt doing anything in particular. As i recall, i was writing a program the evening before. left the computer on (not in standby or anything) and came back, and was programming just fine.. could save those files. tried to create a Makefile, got the response (something like) can not save variable is already defined. or undefined variable. (something about a variable and how its defined).. 
So i COULD save my created files, but could not open a Makefile to save it. (Nor could I open any already made Makefiles).

--Jon

---

### Post by rkd on 2008-04-01
At the moment, I have no idea what happened to your computer or what to do to fix it.  Maybe someone else will come along with better ideas of what you can do. In the meantime, here are my thoughts.

One way to approach your problem would be to copy all the files you want to save onto some external disk or Flash drive, reinstall Ubuntu, reinstall any packages you had added, then restore your files from the copy you made.  That is guaranteed to work, but would not tell us what caused the problem in the first place.  It also wouldn't take very long unless you have a lot of customization to redo.

Another way to approach your problem would be to examine your system and try to figure out what went wrong and how to fix it.  Before doing that, it would be prudent to make copies of all the files you want to save, since trying to fix whatever the problem is might make the system completely unusable.  The advantage to this approach over reinstalling is that if it were successful, you wouldn't have to reinstall all the additions and customizations you have done. The disadvantage is that the investigation could take a long time.

I think I'd recommend backing up your files and reinstalling.

If you want to investigate, you could do it by booting from the Live CD, mounting your hard drive, and looking to see what you can find.  Or you could try to boot to a command line using the recovery mode selection in the boot menu.  I'm not sure that would work, but I think recovery mode bypasses the startup scripts, which is what the error messages you showed are about.  However, those might not be the only things going wrong.

Whichever way you pick to investigate, what should you look at? The only thing I can see to do at the moment is look at the files mentioned in those error messages.  Are they really directories rather than files, as the error messages say?  If they are, how did they get to be directories?  If they are files, why do you get an error that says they are directories? I'm not sure where we would go from there.

So it is up to you whether to try to find and fix the problem or just reinstall. If you need help with any of the steps in either approach, ask here in this thread and I or someone else will try to help.

Be sure to make copies of any files you want to save before doing much more with the computer.  If you have an external drive of any kind, you should be able to make those copies after booting from the Live CD, unless, of course, the disk is damaged already such that you can't mount it from the Live CD.  If you can't mount the hard disk from the Live CD, it might be worth trying to boot into recovery mode and trying to make the file copies from there.  You'd have to do everything from the command line in that case, and it might be that some of your devices, such as external drives, won't work.

If you can afford to wait for a while to see whether anyone else comes along with better suggestions than these, I encourage you do to so.  There might be some fairly easy way to recover from this problem and I just don't know about it.

---

### Post by JonWasHere42 on 2008-04-01
So I have looked through my system in safe mode. And if i go to 
/media/
there are the directories:
cdrom cdrom0 sda sda1 sda2 sda3

all of the sda's are empty.. and i dont think they used to be.
A while back i unmounted my external hard drive.. and im thinking maybe i managed to unmount my internal hard drive as well. Is this possible? would this explain the problem.
When I opened up my filesystem in Safe Mode, i couldnt sudo change anything because i kept receiving a message that says. "... read only file system." Would this be because I loaded in safe mode, or might be caused by the original problem?
And if so.. how can i remount my hard drive?
(I did think of reinstalling and starting all over.. but i have quite a few customized programs installed, that would be very annoying to have to reinstall).

Thanks.

---

### Post by mick8985 on 2008-04-01
Jon, they are empty because the drives aren't mounted, for some reason the drives aren't mounting at boot, they could be broken or the filesystem corrupted. Is what I am thinking off the top of my head. do you have an odd partition layout? or use lvm or raid?

---

### Post by philinux on 2008-04-01
As an option you could download the alternate cd iso. It has a menu option to repair broken systems if memory serves.

Advice before is good - backup anything important.

---

### Post by JonWasHere42 on 2008-04-01
As far as I know, I dont have any strange partitioning. Ive been running linux on here for 6 months maybe, and when i installed it, it was the first time i had ever used it.. So the install was pretty standard. 
It was mentioned before, to try to mount the hard drive from the Live Cd? how do i do that? and would that help? Or the alternate Cd? 
And i have backed up all my work, thats pretty much the first thing i do whenever i need to sign in as root. since im pretty sure the odds of my messing everything up are pretty high.

---

### Post by mick8985 on 2008-04-01
Jon, just boot the livecd

```
mkdir partition1
sudo mount /dev/sda1 ./partition1 -t ext3
```
and see if it mounts

---

### Post by rkd on 2008-04-01
Entries in /media usually are not for the partition that your system is running from, so my first impulse is not to worry too much about them at the moment -- perhaps they were for the external drive.

I don't know anything about the recovery option on the alternate CD. It might be a good thing to try; I simply don't know.

You said you opened your filesystem in safe mode and couldn't change anything because it said read-only filesystem. If by "safe mode" you mean you booted from the hard disk and selected recovery mode, then what you are seeing seems to be that your root partition is mangled a bit and the boot program doesn't think it is safe to mount it normally, so it mounts it read-only.  

I don't think you mean you booted from the Live CD because the /media directory starts out empty when you boot from CD, and the hard disk isn't mounted.  If you really do mean you did that from the Live CD, then please explain a little more what you did.

I suppose something you could try is to boot from the Live CD and try to use fsck to correct errors on the hard drive.  Fsck will delete things if it decides that is necessary to clean up corrected data structures on the disk, so you might want to use the -n option first to see what fsck says about the problems.  

I see that mick8985 is suggesting that you boot from the Live CD and just try to mount the partition of your hard disk and see what happens.  That is worth trying, but check first to be sure that /dev/sda1 is really the Linux partition on your hard drive.  Those sda[n] entries you saw in /media might have been from your external drive.  To see what you have use the command:```
sudo fdisk -l
```(and that is lowercase "l" after the hyphen, not the numeral "1").

---

### Post by mick8985 on 2008-04-01
rdk is absolutely right, I don't know how I missed that, Those will almost definately be old folders for that externel drive. Considering all usb drives mount as sd**, and those folders are called sda*, that indicates your root partition must be an IDE hard drive which would be hda*.

so just sue the fdisk command as rdk says, 

```
sudo fsck.ext3 /dev/hda1
```

where /dev/hda1 is whatever shows up in fdisk. You might as well run it for all your partitions that show up, (presuming all of your partitions are ext3, of course), and then try and give them a mount as a said earlier.

---

### Post by rkd on 2008-04-01
As I said before, I suggest using the -n option on fsck, to prevent it from changing things on the disk until you decide to let it try to fix things.  When fsck fixes a problem on the disk, that sometimes involves deleting large numbers of files and directories.  It's goal is to make the structure on the disk be completely valid, NOT to recover data.  The -n tells it just to report what problems it finds, without trying to fix anything.

So if you want to run some fsck commands, after looking at the fdisk output to see what the partitions are named, I think the commands should be like this:```
sudo fsck -n /dev/<whatever>
```You could use fsck.ext3 instead of just fsck, if you like -- that is what fsck will run, anyway, if the partition is ext3.  My feeling is you might as well let fsck figure out which type it is and select the correct one, but if you want to make the choice yourself, go ahead.

---

### Post by JonWasHere42 on 2008-04-02
Ok Ive booted from the live cd. And i CAN mount sda4 (sda4 is apperantly the linux partition). It works fine. But it still wont do this during boot up. How can i get this to work during boot?
Ive run fsck. It reports a bunch of errors, and fixes non of them. 
Should i try an fsck -y?


--Jon

---

### Post by rkd on 2008-04-02
If you were running the fsck with the -n option, as I suggested, that would have prevented it from fixing the errors.  If you feel like going ahead and letting it fix things, you can run it with no options and for each error it finds, it will ask you whether to fix it or not.  If you want it to fix everything it sees wrong, use the -y option.

Remember that to fsck, "fix" sometimes means discard the stuff that doesn't look right. You might end up with an unusable system after that, but then it isn't usable now.  You might have to reinstall in either case, so it is your choice whether to try fsck's fixes now.

When you mounted /dev/sda4 in the Live CD, did you look at what was there, to verify that it was your Ubuntu root partition? I don't know how you have arranged things, but it is possible that /dev/sda4 is not your root partition, but some other partition you have set up.  

Without knowing a lot more about your system, and what your priorities are, it is hard to tell you what is the best choice right now.  If you want better advice, tell us more about your system and what you want to do.  If you feel like letting fsck do its best, go ahead.

---

### Post by JonWasHere42 on 2008-04-02
Lets see.. when i run fdisk -l
i see a bunch of /dev/sda#
where # goes from 0 1 2 3 4.
I think 2 is my windows partition. 3 i think is the swap partition. and 4 is the linux. 0 and 1 i think are dell recovery partitions. 

Im pretty sure sda4 is my linux partition. Ive mounted it with the Live CD. and im pretty sure its right.. Ive been able to move my files around. copy them, move them.
So i think everything is just fine on that. But I think when it boots that it is not mounting properly. 
How can i get it to mount properly.

---

### Post by rkd on 2008-04-02
Partition numbers start at 1, so I'm pretty sure you didn't see a partition 0.  It might help if you would copy the output of the fdisk into a post here. You can do that this way:

1. Run the fdisk command in a Terminal
2. Open the browser, come here and start a post
3. Use the mouse to highlight all the lines that fdisk displayed in the Terminal
4.  Go back to the browser, left click in the post compose text box, then click the middle button (or the scroll wheel) to paste the text into the post

If you have to save output for a while, you can open an editor, paste the text into the editor window, then save the editor contents to a file in your home directory.

It would also help to see the output of blkid and your fstab.  From the Live CD open a Terminal and enter the following commands::
```
mkdir x
sudo mount /dev/sda4 x
cat x/etc/fstab
blkid
```Those commands create a directory x in your current directory, mount your Linux partition on x, then copy the fstab from your root partition to the Terminal, and finally run the blkid command. Then copy the output from cat and blkid into the post.

Do you see any messages during the boot that seem to be saying that something is wrong with the disk?  If so, please describe them as accurately as you can.  I suppose there aren't any messages from the boot in the system log, since the root partition is getting mounted read-only, but it probably would be a good idea to look at the log, anyway. Maybe there will be some messages from the time of the original error.

To look at the system log, from the Live CD open a Terminal and enter the following commands:```
mkdir x
sudo mount /dev/sda4 x
gksu gedit x/var/log/syslog
```If your root partition is still mounted on x, you don't have to repeat the first two commands.

Go to the end of the file and see whether the messages there have timestamps from about the time you first had the problem a day or two ago. You might have to look a bit earlier than the end of the log. I don't know exactly what you are looking for. Just look for messages that seem to be saying something about problems with the disk.  If you find anything that seems relevant, copy the messages in that area of the log file into a post.

If it happens that I'm wrong and the timestamps at the end of the log are more recent than the time of the original problem, then look back from the end to see whether there are any messages about why it won't mount the root partition. The boot sequence produces a large number of messages, so you may have to page back a lot. You can recognize the beginning of the boot by a message that says```
kernel: Inspecting /boot/System.map-2.6.22-14-generic
```or something similar to that.  If you see any messages that seem relevant, copy them and the surrounding ones into a post.

It might be possible to compress the system log and attach it to a post. This would be useful if you aren't confident that you can recognize the relevant messages. I don't know whether the there is enough room in the Live CD to make a copy of the log. Here are the commands, in case you want to try it:```
cp x/var/log/syslog logcopy
gedit logcopy
gzip logcopy
```The point of the gedit is for you to delete all of the lines before the beginning of the current boot. That will save space in the forum. If you think there is information we should see from before that point include however much of the log you think is relevant. Trouble is, even compressed, the log file is pretty big, and the forum has a size limit on attachments.  All I can say is that if you think it would be useful, try it and see whether it is under the size limit. To attach a file, look below the post composition text box for a button named "Manage Attachments" (it isn't immediately below the box -- scroll down a bit).

---

### Post by JonWasHere42 on 2008-04-02
Sorry sda0 is actually just sda.
I dont have time to go into the error file now.. but here is the output from the first part:

> ubuntu@ubuntu:~$ cat x/etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda4 :
UUID=fce92eb1-3b0e-46d2-9a85-1a5fc162e10c / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb1 :
UUID=07D4-091C /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sda2 :
UUID=FE8896C788967DB9 /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda3 /media/sda3 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0


And blkid returns nothing. If this doesnt tell you very much, then ill go into the system log later today. I just have to go to work now.

---

### Post by rkd on 2008-04-02
Sorry about the blkid command. It should be```
sudo blkid
```I don't understand why, but sometimes blkid works without using sudo and other times it doesn't, and I forget that.

When you post the output from sudo blkid, please post the output from the fdisk -l too.

---

### Post by JonWasHere42 on 2008-04-02
Heres the output from blkid:
> ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D4-091C" TYPE="vfat" 
/dev/sda2: TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sda4: UUID="fce92eb1-3b0e-46d2-9a85-1a5fc162e10c" SEC_TYPE="ext2" TYPE="ext3" 


fdisk -l
[/QUOTE]Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       11479    92164905    7  HPFS/NTFS
/dev/sda3           11480       11936     3670852+  db  CP/M / CTOS / ...
/dev/sda4           11937       14593    21342352+  83  Linux
[/QUOTE]

dmseg returns a lot of these, with the first number changing:
> ..[31655.740330] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
..


---

### Post by JonWasHere42 on 2008-04-02
As a last resort.. the reason i dont want to reinstall, is because of all the libraries ive had to download. Is there anyway, i can make a list of the packages installed by synaptec. And or the libraries ive had to install? So that i can install them quickly when i reboot?

---

### Post by rkd on 2008-04-03
Sorry for being slow to respond -- I've had other things to do.

I will look at your recent posts and suggest anything that seems worth trying.

Meanwhile, to answer your question, there are two ways I think you can use to look at what is installed.  The directory /var/cache/apt/archives contains the packages that you've downloaded.  I don't know whether it contains anything else in addition to that.  So you could redirect the output of an ls command to create a text file containing a list of what is in that directory, which will be at least somewhat related to what you installed.

Another way is to ask for history in Synaptic.  You open Synaptic by System -> Administration -> Synaptic Package Manager.  From the File menu, select History.  In the dialog that pops up, you have a history of what was installed, by date. You have to display each date's history separately, so if you did installs on many dates, that could be a pain, but it probably will be small.  For each date, the packages appear in the right pane.  You can copy the right pane with the mouse and paste into an editor window to gather all the lists together and save them.

I imagine you could take the list of package names, edit it to insert "sudo apt-get install " on the front of each line, and use the result as a command file to reinstall everything.  You would have unnecessary commands there because some packages install a bunch of others because of dependencies, but I don't believe that would hurt anything.  I've never seen this method suggested anywhere, so there might be some reason not to do it, but then, I haven't investigated package management very much.

---

### Post by rkd on 2008-04-03
Well, I don't see anything obviously wrong with the fdisk, blkid, and fstab output.

It is a little odd that blkid does not show a UUID for /dev/sda2, the Windows partition. I don't know how that could be causing the problem you have, though, so let's forget that.

Another minor mystery is why, in fstab, the comment line about /dev/sdb1 is followed by a line that shows it mounting something on /media/sda1 (b vs. a).  There's nothing illegal about that; it's just seems a little odd to me that it wasn't /media/sdb1. Maybe it doesn't make up the names in /media the way I think it does.

Another thing that's a little unusual is that there is no swap partition. /dev/sda1 is a Dell private partition, /dev/sda2 is the Windows partiition, /dev/sda3 is another Dell private partition, and /dev/sda4 is the Linux partition. No Linux swap partition.  I seem to recall that it is possible to have Linux not use a separate swap partition, but just put /swap inside the root partition.  Did you do that?  I don't remember how it is done.

Unless you did have a Linux swap partition and it just disappeared at the time the problem started (unlikely, see note at end), I guess that setup has been working fine for you for six months, so that difference in your setup probably isn't what is causing your problem, either. But maybe having the swap run on the normal filesystem isn't well-debugged and something happened a few days ago when your problem started that triggered a bug that caused the swap activity to corrupt the rest of your filesystem.  There probably is only a small chance that that is the explanation, but unless we find evidence of some other possible cause, that's the only guess I've been able to come up with so far.

The messages in the log about bcm43xx are, I believe, about a Broadcom wireless LAN controller, and so probably aren't the cause of your current problem.  

You used dmesg to display the log. I'm pretty sure that is displaying the messages from your Live CD session, not the old log messages on your hard disk.  Since the Live CD doesn't try to mount the hard disk during boot, the log from the Live CD session won't tell us anything.

In my earlier post where I described how to get and look at the system log on the hard disk from the Live CD, I should have mentioned that you should use ls to see what files are there. Ubuntu regularly opens a new syslog file and renames the current one. Use a command like ```
ls -l x/var/log/sys*
```to see what files are there and their last-modification timestamp. When looking for messages that might have indicated a problem with your hard disk sometime between the time you quit the night before the problem and the morning when you noticed the problem, you might have to look at syslog files older than the most recent one. I believe only the current log and the one immediately prior to it are ordinary text files. The ones older than that are compressed with gzip, so if you want to look at one of them, after copying it to your current directory in the Live CD environment, use gunzip to expand it (hoping there is enough space).  If the copy you made is called logcopy.2.gz, you could expand it with this:```
gunzip logcopy.2.gz
```That would delete logcopy.2.gz and put the expanded logcopy.2 in its place. Then you could look at it with the editor, as usual.

NOTE: The reason I said above that it was not likely that you had had a swap partition and it had disappeared is that one may have only 4 primary partitions on a disk.  If you had had a swap partition, that would have been 5 partitions, so you would have needed an extended partition to hold the Linux partition and the swap partition.  The extended partition would have been /dev/sda4, and inside it would have been the Linux partition and the swap partition, named /dev/sda5 and /dev/sda6 (in either order). So if your swap partition had just up and disappeared, we would not be left with the set of partitions that you are seeing now.

---

### Post by JonWasHere42 on 2008-04-03
I went through the log, and didnt see anything unusual. Oddly enough the log ends on the 30th.. and my problem started on the 31st. And there is no errors leading up to it (other than those wireless ones). I think ive had enough, I am going to run fsck -y, hope it doesnt crash everything.. which it probably will. and then reinstall linux. 
Besides Im getting the impression I should reinstall it anyway, since it for some reason is on sda. 

Oh well.
Thanks for your help though. Ill let you know what ends up happening.

--Jon

---

### Post by rkd on 2008-04-03
I agree. Trying the fsck recovery and, if necessary, reinstalling may be the only option. I can't think of anything else.

I didn't understand your comment about feeling you should reinstall because it is on sda.  That is your internal hard drive, so that's where the reinstall will end up, too.  Maybe you meant something else that I'm just not thinking of -- probably isn't important.

Good luck.  I'll be watching for your report of the result.

---

### Post by JonWasHere42 on 2008-04-06
Hey,
So I ran fsck. Definitely did not work. It ran into some cyclic thing.. Im not sure what.
Long story short, crashed the partition. (Luckily I backed everything up.) Reinstalled Ubuntu, and took a close look at whats going on with my partitioning...
So the way hard drive is partitioned, is with sda1,2,3,4. 
4 being the linux, 2 windows, and 1 and 3 being random Dell partitions.
So aside from that internal drive, I have an external drive, which USED to be my internal hard drive. It is partitioned into 3 partitions, the main storage partition, and another 2 random dell partitions. (When I formated it, i didnt repartition it).

When I plug in that hard drive, my storage drive mounts fine, one of the dell drives mounts as an sdb (i think). But the other Dell partition mounts to sda1. (Probably have the same mount point.) Anyway, so Ive always had problems ejecting the removable drive. In essence I can never eject it safely. (Its just a minor annoyance with NTSF (?) disks, and Ubuntu..). Anyway so i tried a 
umount (storage),
umount (sdb),
umount (sda1).

This last one, I think unmounted the Dell recovery partition or something, and eventually I think the computer wigged out with an unmounted sda1 drive.. or something, and started booting them all in read only mode. 
At least this is what i think originally caused it.

So I suppose my last question then, how can i repartition my external drive into 1 partition (to get rid of the Dell ones) and so it will work on windows and linux? Mounting, unmounting and (most importantly) not crashing my hard drive?

Anyway, thanks for all your help.
--Jon

---

### Post by rkd on 2008-04-06
Yes, it is possible to repartition the external drive.  However, there usually aren't problems unmounting NTFS drives, so it might be a good idea to look into the situation a little bit more before doing that.

I've not partitioned any external drives, so I can't give you directions from my actual experience.  Either gparted or fdisk should be able to do the job, but I have seen occasional reports that sometimes people seem to have trouble getting them to work with an external disk.  You do have to be sure all the existing partitions are unmounted before you can repartition it, and the unmounting seems to be giving you troubles, so that's why I say we should look at that part first.

One thing that seems odd is that you said that in the course of unmounting the external disk, you did umount (sda1).  Do you remember exactly what you typed? You might have gotten a little confused because, for some reason, your fstab was mounting /dev/sdb1 on /media/sda1. To unmount that, you should use either
```

umount /media/sda1
or
umount /dev/sdb1
but NOT
umount /dev/sda1

```
Maybe you were having trouble unmounting because you mistakenly entered the umount for /dev/sda1, so one of the partitions on the external drive remained mounted when you thought it was unmounted.

Since you reinstalled, that should have created a new fstab, so maybe that confusion won't be there any more. We'll see once we look at it closely.

To gather information about this, I'd like you to do the following commands with the external drive plugged in and post the results.```
sudo fdisk -l
sudo blkid
mount
cat /etc/fstab
```

I might not be able to get back to you today because I have a lot of other things to do. If someone else doesn't see your post and join in, I'll get back to it late today or sometime tomorrow.

---

