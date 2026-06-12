---
title: "fsck help"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by miesnerd on 2008-03-31
didnt see the answer in any other fsck threads, but  here is the error I get:


Log of fsck -C -R -A -a 
Mon Mar 31 13:58:48 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=1ae48e60-5971-48b9-ab09-017ed582bb40'

/dev/sda4: recovering journal
/dev/sda4: clean, 80219/2080768 files, 614030/8307613 blocks
fsck died with exit status 8

Mon Mar 31 13:58:49 2008
----------------


how do I fix this? 
As reference, sda4 is not being used for anything. It had SuSe on it, and I dont have any other distro (currently) that I really want to put on there.

---

### Post by codeslicer on 2008-03-31
> 
fsck.ext3: Unable to resolve 'UUID=1ae48e60-5971-48b9-ab09-017ed582bb40'

This means that the UUID doesn't match any device on the computer, ie. if you changed/removed that drive. Try running this: to re-detect the hardware: 

```
sudo update-pciids
```

Actually, this might be irrelevant, but I got it from here: [http://ubuntuforums.org/showthread.php?t=710706]("http://ubuntuforums.org/showthread.php?t=710706")

---

### Post by philinux on 2008-03-31
If that dont work you could format the partition or edit fstab to ignore it as far as fsck is concerned for now.

---

### Post by plucky on 2008-03-31
@miesnerd,

```
cat /etc/fstab
``` and find the partition that has the **UUID=1ae48e60-5971-48b9-ab09-017ed582bb40**.That UUID is incorrect.To find the correct uuid  open a terminal window and use either ```
blkid
``` or ```
ls -l /dev/disk/by-uuid
``` and then edit the **fstab** file by ```
gksudo gedit /etc/fstab
``` and replace the incorrect UUID with the correct one obtained from the **blkid or ls -l /dev/disk/by-uuid** commands.


Good Luck

---

### Post by miesnerd on 2008-03-31
thanks so much. Now, can someone tell me what all this means. As a pretty experienced linux user, Im totally lost on this and I'd like to learn.

---

### Post by rkd on 2008-03-31
I can tell you some of what is going on. If I get something wrong, I hope someone else will jump in and correct it.

I don't know what is making fsck fail.  Maybe it is the incorrect UUID; maybe not.  Someone else will have to weigh in on that.

UUID stands for something like "Universal Unique IDentifier".  I believe it isn't truly unique, but the algorithm for generating the UUID is very unlikely to duplicate another UUID, even a UUID generated on another computer.  UUIDs can be used for many things (they are used for class identifiers in Microsoft's COM and related technologies, for example).  

In this situation, they are used to identify disk partitions.  I don't know for sure what puts the UUID on the partition, but I imagine it is whatever program was used to create the partition. As I understand it, the motivation is that given that technologies such as USB don't tie a disk to a hardware address, using /dev/sda[n] in fstab wasn't such a good idea any more, so the layout of the disk partition was enhanced to contain this UUID (and lots of additional information).  So now the preferred way to list partitions in fstab is by specifying their UUIDs.

I would expect that if fstab refers to a UUID that doesn't correspond to any partition on any device currently connected, that line of fstab would be ignored.  I would assume that UUID just refers to a partition on disk that doesn't happen to be connected at the moment.  But that seems not to be what is happening in your case. I'm sure there is a good reason why, but I don't know what it is.

---

### Post by miesnerd on 2008-04-01
rkd-
thanks for explaining that to me. In my case, sda4 is litearlly on the same physical disk as sda1 (ubuntu) and mounts fine each time, or so it says when I get into my graphical desktop. Its interesting that its causing problems. Maybe all my 64bit distro hopping a few months ago did that.

---

### Post by rkd on 2008-04-01
It isn't surprising that one partition of a disk can be perfectly okay while another has trouble.  If the trouble is that some of the data structures on the disk have gotten messed up due to a software bug, not that the physical disk drive is failing, the errors could easily occur only in one partition.  What happens in one partition usually doesn't much affect the other partitions.

I guess that if /dev/sda4 mounts, it might not be very badly messed up by whatever the error is, but I think you ought to get to the bottom of this, in case there is a problem that could hang around for a while, then become quite a catastrophe later.

If you'd like to try to figure out what is happening and clear up any problems, I'll be happy to try to help, as I'm sure others will be, too.  If you want to get started on that, I think the first thing to do is run the following commands in a Terminal and post the output here:```
sudo fdisk -l
blkid
cat /etc/fstab
```Note that on the fdisk command, the character after the hyphen is a lowercase letter "l", not the numeral "1".

Another thing you probably should do is run fsck on the partition from a Terminal and post the output:```
umount /dev/sda4
fsck -n /dev/sda4
```The -n tells it to report errors but don't try to fix them.  It might not show anything different than the message you have been seeing, but I think it worth trying.

---

### Post by miesnerd on 2008-04-05
hey, i just got around to doing this again (i dont restart my system often, so I hadnt paid much attention to the error.
Anyways, i ran the above commands (sudo fsck -n /dev/sda4 and got:

fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda4: clean, 80219/2080768 files, 614030/8307613 blocks


so what gives? Should I just re-partition it? Will that solve the problem? Like I said before, no big deal, since I dont use the partition right now, but on the other hand, i want to deal with whatever the problem really is.

Miesnerd

PS- thanks for the help so far.

---

### Post by rkd on 2008-04-05
It might be that there isn't anything you have to do.  The problem might have been corrected already.

When you restarted your system this time, did you get the same error messages that you showed us in your first post?  Did you get any similar messages?

I assume that you did correct the UUID value in fstab.  That would have corrected the message about the UUID.  The only other message it gave at that time was that it had recovered the journal, and I think that only happens if the previous shutdown wasn't clean.

So it looks like there aren't any problems left to fix.  Have you seen any other messages that indicate a problem with that partition?

---

### Post by miesnerd on 2008-04-08
hey-
system is giving me the same error. I looked into it, and Im confused (maybe, just a little tired).
here's the output from the terminal and from /etc/fstab

miesnerd@miesnerd-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=290ad335-9fda-477d-82f0-04d85adff862 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=1ae48e60-5971-48b9-ab09-017ed582bb40 /media/sda3     ext3    defaults        0       2
# /dev/sda4
UUID=121a44b4-f0ff-4c54-b6d0-ec4091f02054 /media/sda4     ext3    defaults        0       2
# /dev/sda2
UUID=0edc0faf-f850-44f2-a166-5e89a63aaa31 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
miesnerd@miesnerd-desktop:~$ blkid
/dev/sda1: UUID="290ad335-9fda-477d-82f0-04d85adff862" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="0edc0faf-f850-44f2-a166-5e89a63aaa31" 
/dev/sda3: UUID="6fb00d98-71ca-42f9-821e-6f0c5726fb2a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="301db964-d249-4795-a5c1-741bba3e9da9" SEC_TYPE="ext2" TYPE="ext3" 


and /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=290ad335-9fda-477d-82f0-04d85adff862 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=1ae48e60-5971-48b9-ab09-017ed582bb40 /media/sda3     ext3    defaults        0       2
# /dev/sda4
UUID=121a44b4-f0ff-4c54-b6d0-ec4091f02054 /media/sda4     ext3    defaults        0       2
# /dev/sda2
UUID=0edc0faf-f850-44f2-a166-5e89a63aaa31 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

I didnt see anything that looked wrong to me. But if it is, let me know what to put where. Maybe I am just tired.

---

### Post by miesnerd on 2008-04-08
going back, I think I understand, but I'll hold off until someone confirms this.

Am I supposed to copy 
301db964-d249-4795-a5c1-741bba3e9da9 from the terminal and replace
 
121a44b4-f0ff-4c54-b6d0-ec4091f02054

but if that's correct, doesnt that mean i need to do that for sda3 and sda4 both?

thanks,
Miesnerd

---

### Post by rkd on 2008-04-08
I believe the error message will stop if you copy the UUID values for /dev/sda3 and /dev/sda4 shown in the output of the blkid command into fstab at the appropriate points.

I don't know why it is complaining only about one partition's UUID instead of both of the partitions whose UUIDs don't match what is really on the disk.  Actually, I'm surprised that it complains about either UUID -- I would expect it to consider an unmatched UUID as being for some removable drive's partition.  Maybe I misunderstand how that works.

I imagine the way you got into this situation is that sometime after installing Linux, you deleted partitions /dev/sda3 and /dev/sda4, then recreated them.  They would get different UUIDs when you created them, and if the fstab didn't get updated with the new UUIDs, that would lead to the situation you see now.  Or something like that.  Does that match the history of this system?

---

