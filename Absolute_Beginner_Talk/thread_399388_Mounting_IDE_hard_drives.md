---
title: "Mounting IDE hard drives"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by darkViVi on 2007-04-02
Hello.

I have no less than 3 IDE hard drives, I currently use them all (not at once) but since Windows is messing with me I have to use them all.
Problem though, I've been sitting for a long while trying to mount them, but unsuccessful, so I wished there was an easy way to it because I'm a big big n00b and I don't know my way around the terminal well...

If it's not too much work for some expert I would really appreciate if someone took the time to write the commands in here, I've googled and googeled some more and now my head hurts :(
Right now, I want to mount atleast one partition which contains most of my files.
It's on my main hard drive where I have Windows installed but it's partition number 2 on it.

Please? *puppydog eyes*

---

### Post by jvc26 on 2007-04-02
Ok, so first Im presuming you can boot into Ubuntu.
Open the terminal - Applications -> Accessories -> Terminal and type:
```

sudo fdisk -l

```
Note l is a lower case L.
That will output where all your partitions and drives are mounted, if you post that up here we can take you the next step.
Il

---

### Post by darkViVi on 2007-04-02
Kk, thanks. And yes, I can boot on Ubuntu (and Windows XP) that is until my Windows registry gets messed up... But thats another story.

```
Disk /dev/hdc: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2709    20480008+   7  HPFS/NTFS
/dev/hdc2            2710       10337    57667680    7  HPFS/NTFS

Disk /dev/hdd: 20.5 GB, 20520493056 bytes
255 heads, 63 sectors/track, 2494 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2389    19189611   83  Linux
/dev/hdd2            2390        2494      843412+   5  Extended
/dev/hdd5            2390        2494      843381   82  Linux swap / Solaris

Disk /dev/sda: 512 MB, 512999424 bytes
16 heads, 63 sectors/track, 994 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         994      500943+   1  FAT12
Partition 1 has different physical/logical endings:
     phys=(993, 15, 63) logical=(993, 15, 61)

```

In additions to these I have a 40gig IDE on my desk. That's not important right now though, what is important is the 80GB and it's biggest partition (HDC2)

As for the 20GB, the FAT partition was only made for Knoppix which I tried to install prior to Ubuntu. So that's not important either and will probobly be formatted sometime.
Thanks for your reply :)

---

### Post by jvc26 on 2007-04-02
Right, so out of those which ones do you want to mount? For an easy example I shall show you how to mount the knoppix one EDIT:: REALISE I AM NOT SURE ABOUT THIS TINY BIT AS: is sda1 the knoppix disk you were talking about? I see that actually it registers as 512Mb??? also FAT12 as a filesystem? clightly confused by that one. I've left the intructions as is, but that may be an odd mistake which makes them not work My instructions have the method to mount fat drives, should you need to change the drive name from /dev/sda1 do feel generally free to one of the other partitions, presuming it is fat and the mounting instructions will be the same: Stuff in bold is intruction/explaination, you don't type that in
```

sudo mkdir /media/fatdisk 
**This is making what is called a mount point - basically a folder in which you can access your data**
sudo mount /dev/sda1 /media/fatdisk vfat users,noauto,rw 0 0
**This takes the device name, which you got from the sudo fdisk -l command (sda1) and telling the computer where to mount the disk The vfat bit is an option telling the computer what filesystem the drive is. The users stuff tells the computer to allow your user to read-write to the drive and to enable you to mount it**

```
Ok so thats nice and easy to mount, Now you may find that you have a load of ntfs hard drives you want to mount (which you do) This causes us a small problem as you will find that ubuntu cant read-write access to ntfs HDDs by default (ntfs is a MS proprietary filesystem) consequently you have to use a driver called ntfs-3g I would go through this step by step, however Im afraid I have to dash out. Here is the [howto on ntfs-3g]("http://www.ubuntuforums.org/showthread.php?t=217009") which explains how you need to do it.

The other thing is if you want to make the drive mount permenantly on boot. This is done in a file called fstab. Instructions on how to add a drive onto the fstab are [here]("http://www.ubuntuforums.org/showthread.php?t=283131") again I do apologise for having to run out, I hope the links provided will help you (as they are the proper Howtos from the forum (saves you more googling) when I get back later if your still not fixed up and someone else hasnt talked you through the rest I'll finalise my instructions.

Good luck mate, hope that helps,
Il

---

### Post by darkViVi on 2007-04-02
Thanks.
> For an easy example I shall show you how to mount the knoppix one
 EDIT:: REALISE I AM NOT SURE ABOUT THIS TINY BIT AS: is sda1 the knoppix disk you were talking about?
I see that actually it registers as 512Mb??? also FAT12 as a filesystem? clightly confused by that one
OMG, thats my JumpDrive!

I didn't realize this before you said it was 512MB, so I suppose HDD1 is the one I formatted for Knoppix since HDD2 says "EXTENDED" (EXT3?)

But yeah, anyway thanks a lot, I'll look at the links and try to mount it. :)


Edit:
I got this... *shrugs*

```
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

When I copied+pasted the stuff in the code... (the USB JumpDrive is already mounted as a removable.)
When I tried...

```
root@robin-desktop:/home/robin# sudo mkdir /media/ntfsdisk
root@robin-desktop:/home/robin# sudo mount /dev/hdc2 /media/ntfsdisk vfat users,noauto,rw 0 0
```
I got the same, this is the NTFS disc I really need to atleast fread data from. I also tried replacing "vfat" with "vntfs" but same.

So I tried a...

```
root@robin-desktop:/home/robin# sudo mkdir /media/fatdisk
root@robin-desktop:/home/robin# sudo mount /dev/hdd1 /media/fatdisk vfat users,noauto,rw 0 0
```

And big surprise I got the same response from terminal, though I didn't know if it mounted anything I opened up the folder but nothing, neither in the "ntfsdisk" or "fatdisk"...

*tries again from the beginning*

---

### Post by jvc26 on 2007-04-02
The thing is, which is slightly why I am confused: If you have linux installed, (Ubuntu) which drive is that on? That must be on one of the hddx partitions, what is the output of:
```

cat /etc/fstab

```

Ignore how to mount the JumpDrive - obviously, this is now automounted so thats not an issue.

This one may well work for the windows drives, but it will mount in read only. Try:
```

sudo mount -t ntfs /dev/hdc1 /media/ntfsdisk

```

EDIT:: I have the odd feeling that all the options order I put above was wrong (hence the command was rejected), have gone through and checked my commands out with man mount sorry about that, pretty tired tbh see the revised command in the code of this post. This should mount with no problems (but in read-only mode) The command I gave was what the fstab line should look like for the fat mount, please ignore it and try this one. If this doesnt work as a mount please can you post the error message. Apologies again for not getting it sorted first time.
Il

---

### Post by darkViVi on 2007-04-02
Heey no apologies needed :)

I appreciate the help, yo, thanks.

Output of "root@robin-desktop:/home/robin# cat /etc/fstab
"


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=aa879bd0-8934-451d-b169-068815354fdf /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=1f9f4c49-c2f0-4a19-a29b-965b93f507fc none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/windows ntfs umask=0222 0 0
```

And now, I'll try your command and edit in the result **and Ubuntu is on HDD2, I think, maybe HDD1.**

EDIT, Ok that seemed to work, now I don't have permission to read the content of the "ntfsdisk" folder. 
Why? it's my computer ;_;;

Haha, I guess that's something to do in terminal.. Peculiar though..

EDIT again, my partitions and drives seem to make this harder for you... Look.

My main with XP installed: "HDC1" aka "C:/"
Partition number two (the one I really want atleast read access too: "HDC2" aka "E:/"
Obviously those are on the same physical hard drive.

Ubuntu installation is located at: "HDD1" (I think)
Finally of my current installed drives is the "HDD2" which I belive is the FAT partition I formatted for Knoppix.

Also there is my third HDD but that's not inside my computer now... (only 4 IDE cables)

---

### Post by jvc26 on 2007-04-02
Ok, with the new info:
hdd1 is where your current Ubuntu system is installed.
You want access to hdc2 but its telling you you're not allowed. I think the next line of attack would be first to unmount the drive as it is, then to remount it with different permissions:
```

sudo umount /dev/hdc1
sudo mount -t ntfs -o users /dev/hdc1 /media/ntfsdisk

```
And see if that mounts it and lets you at it. If it lets you access the stuff (this is for your c-drive) then close the folder, and execute these commands which will allow you access to the hdc2 drive which is the one you're after:
```

sudo umount /dev/hdc1
sudo mount -t ntfs -o users /dev/hdc2 /media/ntfsdisk

```
The reason it didnt work before (I'm pretty sure so) is because when you mount it, you get the automatic mounting options which only allow root access (if someone else reads this and knows thats incorrect, do correct me) so, you have to specify that you want anyone on your computer to be allowed to use it.
Hopefully that works.
Il

---

### Post by darkViVi on 2007-04-02
Well I'm the only one that uses this PC, and I tried all of that, twice, as root and user in the terminal but didn't work.
Still no access.... :(

Peculiar hmm?

Thanks for the help yo.

---

