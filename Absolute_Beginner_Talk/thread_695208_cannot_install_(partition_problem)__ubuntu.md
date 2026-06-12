---
title: "cannot install (partition problem)  ubuntu"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by zzigmond on 2008-02-12
Trying to make a clean install of Ubuntu 7.10 (not a dual boot). The partitioner stops at 33%. Its says "mount of  partition #1 failed". Have tried Live and alternate Cd's, Partedmagic,Gpart Live without sucess. 20 G harddrive. I also tried Ubuntu 6.10 which I installed in the past as a dual boot, no go. Have tried 3 different drives. Obviously I'm missing something! My last attempt Sudo fdisk -lu  gave me this:

ubuntu@ubuntu:~$ sudo fdisk -lu
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x2262 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 10.1 GB, 10110320640 bytes
255 heads, 63 sectors/track, 1229 cylinders, total 19746720 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000da630

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     2034898     1017418   83  Linux
/dev/sda2         2034899     2966412      465757    5  Extended
/dev/sda5   ?  3563539300  1993519664  1362473830+  4f  QNX4.x 3rd part

I am fairly new to linux/Ubuntu so I don't understand the file system very well yet.

---

### Post by KMW on 2008-02-12
Am new to this also so there is probably an easier way but if you have a Windows system availabe you could slave the drive into Windows then run SeaTools or Data Lifeguard to reformat the drive as a new drive. Then retry the install.
From my experience Windows will not remove a Linux partition and Partition Magic will most of the time.

Also looks like there is something there as it looks like it's only finding 10.1gig on the drive..

---

### Post by dstew on 2008-02-12
That fdisk output is strange. All those warnings, and the last partition makes no sense. I think your partition table may be messed up. Do you think there is any useful data in there? If not, I would delete /dev/sda5 and maybe also /dev/sda2 and start over, or maybe even delete all the partitions.

---

### Post by oedha on 2008-02-12
maybe you can try gparted :==> [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
or....if you dont have any data......
focus on step 4 of 7 of ubuntu installation....
delete everything first then make new partitions....for ubuntu ( i suggest 3...../ , home, swap )

---

### Post by zzigmond on 2008-02-13
Thanks for the replies, :)

[COLOR="Red"]KMW[/COLOR]: I have used Ontrack Disk Manager(they made Seatools) to set up drive several ways, as new, as Ntfs, and Fat32. No method worked. BTW this is likely my attempt with a 10G hard drive, hence the 10.1G. But the partitioner only shows 7.74G when I run it. All 3 drives I tried had  the same result.](*,)

[COLOR="Red"]dstew:[/COLOR] I agree the fdisk output is strange, and I have deleted all and repatitioned several times. I may connect to my windows machine and try Partition Magic, but I feel it would be more useful to myself and others find out why I can't do it in Ubuntu. Xp will partition format and install on any of these drives without difficulty. My past install of Ubuntu, I was told to setup my drive with XP and then let Ubuntu take over the space, however this workaround will not work this time.:confused:

[COLOR="Red"]oedha[/COLOR] I have no data on any of these drives and I have tried Gparted live without success. What I can tell you is that Gpart makes the partitions, but does does actually format them to the proper file system(or it appears that way) and since they are not formatted properly when the installation attempts to mount the partition, it fails. If I continue with Gpart, when it reloads the partitions are all there but they are of an unknown file type.:confused:

I have read many posts, but nothing seems to be directed towards this exact problem.

---

### Post by max renn on 2008-02-13
Partitioning should not be such a problem, you maybe have a lowlevel hardware problem,fix with your seagate tools.  Don't waste your time with high level tools, when it probably low level issue.  Consult the OEM, seagate has 5yr warranty.

---

### Post by KMW on 2008-02-13
What kind of drives are these? Seagate, WD, Maxtor?

Have you checked the jumpers? Have you tried using Cable Select?

Try SeaTools again, run fitness test and then use it to write zeros to entire drive if these are Seagate drives.   

Once received a drive that had some third party software on it and had a heck of a time getting it to format correctly. Writing zeros to it finally resolved the problem.

---

### Post by zzigmond on 2008-02-13
Thanks for the replies::)


[COLOR="Red"]max renn:[/COLOR] 3 separate drives bad, unlikely, I'm sure its something I'm doing wrong, just can't figure out what it is. It could be a bug, but very few posts concerning this issue.



[COLOR="Red"]KMW[/COLOR]: 2 20G Seagates, and a 10G Maxtor, the first drive I tried was cable select, I switched them all to master since. I will try the writing zeros, when I get home from work.


Thanks again

---

### Post by max renn on 2008-02-13
> **zzigmond said:**
> Thanks for the replies::)


[COLOR="Red"]max renn:[/COLOR] 3 separate drives bad, unlikely, I'm sure its something I'm doing wrong, just can't figure out what it is. It could be a bug, but very few posts concerning this issue.

Thanks again

Sorry, I missed that, thought it was three 20GB partitions on one drive.  

I guess I was thrown off because I've never heard of a SATA under 100GB.  You posted:
> Disk /dev/sda: 10.1 GB, 10110320640 bytes
255 heads, 63 sectors/track, 1229 cylinders, total 19746720 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000da630

Device Boot Start End Blocks Id System
/dev/sda1 * 63 2034898 1017418 83 Linux
/dev/sda2 2034899 2966412 465757 5 Extended
/dev/sda5 ? 3563539300 1993519664 1362473830+ 4f QNX4.x 3rd part

sda = SCSI = SATA

So you have three 20GB & 10GB SATA drives that are doing the same issue?  Or are these PATA on some Raid controller or converter?  You are putting three partitions on a 10GB drive?  My next course of action would be to move the drives to a different controller/computer (or without converter) and make sure that bit of hardware is functioning properly.

---

### Post by rkd on 2008-02-13
I have a feeling that it is the Ontrack Disk Manager that is causing the problem. It probably is putting something odd into the partition table that is confusing Ubuntu.

My suggestion is to wipe out the partition table by writing zeros over the first few sectors of the disk, then let Ubuntu do the partitioning as part of the installation.  Is there some reason you didn't want to have the Ubuntu installer create the partitions? If you aren't sure how to tell it to lay out the partitions the way you want, explain and we'll tell you how to do it.

After booting from a Live CD, open a Terminal and enter this command:```
sudo dd if=/dev/null of=/dev/sda bs=512 count=5
```This will write zeros over the first few sectors of the disk. The partition table is at the end of the first sector, so this will erase the old partition table.

Then double-click the Install icon on the Ubuntu desktop to start installing Ubuntu from the Live CD. At step 4 of the installation setup, you get to tell it how to use the disk. If you want to control exactly how it gets partitioned, choose the Manual method. On the screen, there will be a list of the partitions, initially empty. Create the partitions you want. Make sure you check the box under the heading "Format?". That will tell it to format the partition before using it during the installation. If you don't really want to control the details of the partitioning, you can tell Ubuntu to use the whole disk and make the partition decisions itself.

I have a feeling that if you do this, the problem you have been having will be gone.

Concerning your comment that gparted doesn't format a partition properly: You may have been fooled by a bug in the installer. The installer tries to check an existing partition to see whether it is properly formatted, but it gets the test wrong and always complains. The workaround is to let the installer format the partition itself. But you usually don't have to partition and format the disk before starting the installer because you can do all of that in step 4 of the installation setup.

Post again if you have questions about this or if it doesn't work right.

---

### Post by KMW on 2008-02-13
> **rkd said:**
> I have a feeling that it is the Ontrack Disk Manager that is causing the problem. It probably is putting something odd into the partition table that is confusing Ubuntu.

My suggestion is to wipe out the partition table by writing zeros over the first few sectors of the disk, then let Ubuntu do the partitioning as part of the installation.  Is there some reason you didn't want to have the Ubuntu installer create the partitions? If you aren't sure how to tell it to lay out the partitions the way you want, explain and we'll tell you how to do it.

After booting from a Live CD, open a Terminal and enter this command:```
sudo dd if=/dev/null of=/dev/sda bs=512 count=5
```This will write zeros over the first few sectors of the disk. The partition table is at the end of the first sector, so this will erase the old partition table.



Great post! I just learned something also. Thought there would be an easier way.
Is there a command to write to the whole drive also?

---

### Post by rkd on 2008-02-13
KMW:

I'm not sure what you are asking concerning a command to write to the whole drive. If you just omit the count=5 from the command I showed there, it will write zeros over the whole disk, if that is what you are asking. Making the blocksize bigger might make that run a bit faster. Try entering the command "man dd" to learn more about the dd command. Depending on what you are interested in doing, "man badblocks" might be helpful, too. I know the man pages often are hard to decipher, but sometimes they are the only documentation we have.

---

### Post by discodan on 2008-02-13
I ran into a similar issue last night installing 7.10 server.  I have bunch of physical hdds installed and was attempting to setup the software raid.  Somewhere I messed it up.  I don't remember the exact errors, but basically it wouldn't let me install.

So, I restarted the install 2-3 times thinking I would wipe out the partitions and start over.  But for some reason, I couldn't wipe out the partitions.  What ended up working was going back to an old dos boot disk and using fdisk to wipe out all the partitions.

So maybe try wiping out all the partitions before starting the install?

-disco-

---

### Post by darius_stavrox on 2008-02-13
Hi! I'm completely brand new to Linux and I started installing ubuntu.
Ok, how long is the installation process supposed to take? Because it seems like the computer freezes during the partition process, my cursor doesn't respond. Nothing happens for hours. I've accumulated 5 hours so far.

---

### Post by max renn on 2008-02-13
> **darius_stavrox said:**
> Hi! I'm completely brand new to Linux and I started installing ubuntu.
Ok, how long is the installation process supposed to take? Because it seems like the computer freezes during the partition process, my cursor doesn't respond. Nothing happens for hours. I've accumulated 5 hours so far.



Total install took me abt 30 minutes, including partition to a 70GB drive

---

### Post by darius_stavrox on 2008-02-13
> **max renn said:**
> Total install took me abt 30 minutes, including partition to a 70GB drive

wow thanks
at least I know that something is wrong

---

### Post by zzigmond on 2008-02-13
Thanks again everyone:

Good news, my disk partitioned properly or at least it looks alright to me, I wrote the zeros as KMW and rkd suggested. I used rkd's suggested method in terminal to do so. It recognized my harddrive size properly and the partitions show up as formatted after. However the "mount partition #1 failed" error is still there. I will try the alternate cd. I finally feel I/We made progress at least.:)

---

### Post by rkd on 2008-02-13
I'm glad you are making some progress.

It isn't clear from what you wrote what you did after writing zeros to the beginning of the disk. Did you start the install from the Live CD, and do the partitioning in step 4 of the installation setup?

When does the message about the error mounting partition #1 occur? Does that happen right after you confirm all the installation setup information is correct and you tell it to go ahead and install Ubuntu?

If you haven't already wiped out things by trying the alternate CD, it might help us understand the problem if you post the output of sudo fdisk -lu done from the Live CD after you get the error about mounting partition #1.

---

### Post by zzigmond on 2008-02-14
[COLOR="Red"]rkd: [/COLOR]

Yes, I started from the Ubuntu Live cd, used terminal to write zeros, and then began the installation from the Live cd. I used the the partitioner in the install process, used the guided process, entire disk. It created the partitions correctly, but failed  with ".... mount partition #1 scsi0,0,0, sda 0 failed" (this is from memory so it might not be exact). I have tried manual partitions, and the alternate cd with the same error. 

Thanks again

---

### Post by rkd on 2008-02-14
Can you describe more clearly at what point you get the message that the mount of partition #1 failed? Is it while you are still in the installation setup steps, right after the final setup step where you confirm all the setup settings are okay, sometime later?

---

### Post by dstew on 2008-02-14
Did you check the Format Partition box before you left the partitioner? One reason a partition is not mountable is if it does not have a file system on it. Another reason is that there are errors (like bad blocks) on the partition. I suspect the second problem. You can use the **fsck** command from the Live CD terminal window to check your ext3 partition for errors.```
 fsck -a /dev/sda1
```(if /dev/sda0 is the right name.)

---

### Post by zzigmond on 2008-02-14
[COLOR="Red"]rkd[/COLOR]: ok...its after you click install at the 7th step, the process creates partitions then formats and then says installing system and returns the following error,  "The attempt to mount a file system with type ext3 in SCSI1 (0,0,0), partition #1 (sda) at / failed." When I check my partitions they look as follows:

Disk /dev/sda: 20.0 GB, 20020264960 bytes
255 heads, 63 sectors/track, 2433 cylinders, total 39102080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b06b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    37608164    18804051   83  Linux
/dev/sda2        37608165    39085888      738862    5  Extended
/dev/sda5        37608228    39085888      738830+  82  Linux swap / Solaris

which looks ok to me, but like I said I am new to this.

[COLOR="Red"]dstew[/COLOR]: I am not sure I am using Fsck properly I tried it and it gave me the same response for sda1, sda0, sda. Bad magic block.... I assume its "sudo fsck -a /dev/sda1"

[COLOR="Red"]Max Renn[/COLOR]:Just a note: the drives are IDE, not SATA don't know if this changes anything

[COLOR="Red"]Discodan[/COLOR]: Tried fdisk earlier unsuccessfully, but yes there was a problem removing partitions and disk/size recognition which **seems** to be corrected now, though I still can't finish the installation.

Thanks again to all............

---

### Post by rkd on 2008-02-14
Well, this seems odd. It seems as if it started formatting the partition, but didn't finish the format.

You are right -- the fdisk output looks correct now.

But another thing that seems a little odd: Your disk is an IDE disk, but Ubuntu is giving it a name normally used for SCSI, SATA, or USB disks. I would expect to see /dev/hda, /dev/hda1, and so on. It is connected to the IDE connector on the motherboard with a ribbon cable, correct? It isn't in an external disk enclosure and connected via USB, is it?

I think the next thing to try is to do the format from the command line, to see whether it reports any errors. Boot from the same Live CD you used when trying to install, open a Terminal, and enter the command```
sudo mkfs -t ext3 /dev/sda1
```If it gives any errors, post them for us to see.

---

### Post by zzigmond on 2008-02-14
[COLOR="Red"]rkd[/COLOR]: It is connected via ribbon cable to the IDE primary and it is presently set to cable select but I have tried it at master/single drive as well. I try the comand line format you suggested and post the results. thx

---

### Post by dstew on 2008-02-14
> sudo fsck -a /dev/sda1I believe that is correct. Please post the error you get, so we can have a look at it.

---

### Post by zzigmond on 2008-02-14
[COLOR="Red"]rkd[/COLOR]: It seems to have formatted properly: 

ubuntu@ubuntu:~$ sudo mkfs -t ext3 /dev/sda1
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
2354688 inodes, 4701012 blocks
235050 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
144 block groups
32768 blocks per group, 32768 fragments per group
16352 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 26 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

I will now try to install. thx again

---

### Post by rkd on 2008-02-14
dstew: He said fsck reported bad magic block. We don't need to see any more than that, do we?

---

### Post by rkd on 2008-02-14
Don't be surprised if the install fails again with the same error, because I think the install will do the format again itself, and I don't expect it to work this time when it has been failing all along.

Maybe I'm wrong and having the partition be formatted before the install will help. If so, I'll be puzzled, but at least you will be past the problem.

---

### Post by zzigmond on 2008-02-14
[COLOR="Red"]dstew[/COLOR]: This is the result, I mistakenly said magic block 

sudo fsck -a /dev/sda1
fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

[COLOR="Red"]rkd[/COLOR]: The partitioner does not see the formatted partition so i cant continue with this installer. I could try the text installer on the alternate cd to skip the partition process. Also i am going to check for bios updates because this sda/hda seems like a recognition problem, even though the bios gives the correct size.

---

### Post by rkd on 2008-02-14
The partitioner doesn't see the formatted partition? That's very odd or you are misinterpreting something.

At the partitioning step, did you choose Manual? If not, try it again and do that. It should show the partitions on the disk and ask you how to use them. Select the first partition, click Edit, tell it to use this partition for "/" and check the format box. I think it will know to use the other partition for swap, but if not, select it, click Edit, and make the partition type be swap.

If you already tried this and it wouldn't let you use the first partition, I don't know what to think.

---

### Post by zzigmond on 2008-02-14
[COLOR="Red"]rkd[/COLOR]: I will try these steps again, just in case I missed something and let you know what happened. thx

---

### Post by dstew on 2008-02-14
> fsck.ext2: Bad magic number in super-block while trying to open /dev/sda1If you got this report doing fsck just after you created the file system, then you probably have a hardware error. If it is a new file system, it should not have any problem with superblocks. Sometimes, in established file systems, you can recover from a bad superblock error by using the backup superblocks. However, since this is a brand new file system, I wouldn't bother with that. At this point, my only thoughts are, try a different disk, or try to format and check a different partition that lives on a different space on the disk. You could also try to write zeros to the whole drive using the dd command as suggested earlier.

---

### Post by max renn on 2008-02-15
Like I said before, I wonder what would happen if you put these disks on a different controller/computer.  Now that we have established they are PATA drives, it is obvious linux picks this controller as SCSI.  Why?  Is it RAID capable?  Is it trashed?

Since they are PATA, then it's always possible the seagate and the WDs won't like being on the same chain.  It is also likely the WDs won't like Cable select and will need to be master/slaved.  They are not Ultra ATA right?  So they should also be on a 40 wire ribbon cable, not an 80 wire?

Again, if it was me, I would run an OEM diagnostic with low-level format, if required, and, at this point, on a different controller.  These drives are 10+? years old.  Anything could be wrong, but it's pointing to the controller.

---

### Post by zzigmond on 2008-02-15
[COLOR="Red"]Max Renn[/COLOR]: They all were installed and working properly on Xp when I removed them, the present one was working on this very machine until I decided to do the Ubuntu install.

Just a note: Breezy Badger recognizes the drive as hda instead of sda but the size is incorrect(if I remember correctly in this version the drive size was a known bug). This sda/hda problem would "**appear**" to be a bug in the new version.

---

### Post by max renn on 2008-02-15
> **zzigmond said:**
> [COLOR="Red"]Max Renn[/COLOR]:  This sda/hda problem would "**appear**" to be a bug in the new version.


Cool.  And that would be a bug that affects the controller?  So have you tried a different controller?  Just asking...

---

### Post by dstew on 2008-02-15
There is a program called Testdisk that can recover lost partition tables, some people have had good success with it. It can be installed to the Live CD using synaptic, and you can try it. It might be more powerful than fsck, but I don't know...

---

### Post by rkd on 2008-02-15
I seem to recall reading an article somewhere about redoing the disk driver software. Seems that the code for IDE controllers is not very well structured (and so hard to maintain and improve) while the code for SCSI and SATA is well-organized (or at least better-organized). The intent was to move support for IDE into the SCSI and SATA code, after which all disks, even IDE disks, will have names like /dev/sda. 

I thought it was something coming along sometime in the future, but maybe the future has caught up to us.  But I'd be surprised if they would make such a change as maintenance rather that release it in a new kernel version.

So maybe this has nothing to do with the names we are seeing, but I wanted to mention it in case someone else remembers something about it relevant to this problem.

---

### Post by zzigmond on 2008-02-15
[COLOR="Red"]max renn[/COLOR]: I have a Compaq with Xp and Ubuntu GG running as dual boot. I will hook the drive up to this machine over the weekend and see what happens.

[COLOR="Red"]dstew[/COLOR]: I have heard of Testdisk and Photorec, but I opted not to try it since I was already dealing with Ubuntu which I am new to and I figured I might make more problems. I might look into it as well this weekend.:popcorn:

Well at least its been a learning experience:) even if I haven't found a solution yet, thanks again to all of you.

---

### Post by zzigmond on 2008-02-15
[COLOR="Red"]rkd[/COLOR]: Thats interesting:

[I]I seem to recall reading an article somewhere about redoing the disk driver software. Seems that the code for IDE controllers is not very well structured (and so hard to maintain and improve) while the code for SCSI and SATA is well-organized (or at least better-organized). The intent was to move support for IDE into the SCSI and SATA code, after which all disks, even IDE disks, will have names like /dev/sda.
[/I]

It could mean its not a bug, but meant to be that way or it could mean their new driver file has some bugs. This might turn out to be a wait and see type of problem.  I will continue to try things this weekend and I'll  post any results. Thx again.

---

