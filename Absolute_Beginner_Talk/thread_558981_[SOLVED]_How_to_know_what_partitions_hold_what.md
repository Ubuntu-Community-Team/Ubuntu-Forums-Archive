---
title: "[SOLVED] How to know what partitions hold what"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-09-24
I need to repair my MBR. I use only Ubuntu on 2 hard drives.

I found a way to repair the MBR/Grub at: [http://www.arsgeek.com/?p=655](http://www.arsgeek.com/?p=655)

I have to know, generally what partitions hold what and how to determine what my partitions hold; so that I don't harm my data.

---

### Post by scrooge_74 on 2007-09-24
Is more of a question of how you divided your disks?

A good idea is the partition a drive in three parts: one for the system (where /, /etc, /tmp, etc), another partition for your /home directory (so if you mess up your system your data is ok), and a third is for the swap space needed by the system.

---

### Post by vanadium on 2007-09-24
You get an overview of all partitions Linux can see (mounted or not) with the command

sudo fdisk -l

You see which partitions are mounted and where with the command

mount

You see which partitions are mounted at boot time, or prepared to be mounted manually, from the contents of /etc/fstab

cat /etc/fstab

Besides that, to actually see the content, you must make sure the partition you want to look at is mounted and then look at it using a file manager or the commands "ls" to list files and directories, and "cd" to change directories.

---

### Post by bodhi.zazen on 2007-09-24
> **Mark_in_Hollywood said:**
> I need to repair my MBR. I use only Ubuntu on 2 hard drives.

I found a way to repair the MBR/Grub at: [http://www.arsgeek.com/?p=655](http://www.arsgeek.com/?p=655)

I have to know, generally what partitions hold what and how to determine what my partitions hold; so that I don't harm my data.

Could you boot a live CD, mount your partitions, and look at what they hold ?

Open a terminal and enter : ```
sudo fdisk -l # lists partitions
sudo mount /dev/xxx /mnt
gksu nautilus /mnt
sudo umount /mnt
```

Cycle through partitions as needed.

---

### Post by Mark_in_Hollywood on 2007-09-24
I don't understand the line from your post:

**sudo mount /dev/xxx /mnt**

what is xxx, please?

---

### Post by Adramelech on 2007-09-24
xxx is your partiion, for example hda1 hdb1,...

btw he forgot about making the directory first:

sudo fdisk -l # lists partitions
sudo mkdir mnt/xxx
sudo mount /dev/xxx /mnt/xxx
gksu nautilus /mnt
sudo umount /mnt

---

### Post by bodhi.zazen on 2007-09-24
> **Adramelech said:**
> xxx is your partiion, for example hda1 hdb1,...

btw he forgot about making the directory first:

sudo fdisk -l # lists partitions
sudo mkdir mnt/xxx
sudo mount /dev/xxx /mnt/xxx
gksu nautilus /mnt
sudo umount /mnt

Thanks.

Well, I was thinking of mounting directly to /mnt

sudo mount /dev/hda1 /mnt

saves a step (of making a directory /mnt/hda1)

---

### Post by Irihapeti on 2007-09-25
> **bodhi.zazen said:**
> Thanks.

Well, I was thinking of mounting directly to /mnt

sudo mount /dev/hda1 /mnt

saves a step (of making a directory /mnt/hda1)

It might be worth mentioning that if you do that while using the GParted liveCD (use /mnt directly, that is) the system locks up completely.

Irihapeti

---

### Post by bodhi.zazen on 2007-09-25
> **Irihapeti said:**
> It might be worth mentioning that if you do that while using the GParted liveCD (use /mnt directly, that is) the system locks up completely.

Irihapeti

OK, thanks for the info. I have not had that experience, but good to know ;)

---

### Post by Irihapeti on 2007-09-25
bodhi.zazen:
I had the experience of the GParted liveCD locking up on me on several occasions, and I had no idea why. Then I happened to see a warning about not using /mnt itself while I was using the CD. Evidently it happens to other people as well. Since then I've had no further problems of that sort.

---

### Post by Mark_in_Hollywood on 2007-09-25
I can't follow what is being talked about above.

I have a Canonical issued LiveCD, (not the "alternate" CD).

I do not have a GParted CD.

Does the Canonical LiveCD use GParted, without my knowing it?

From reading the above posts, one person wants to /mnt and another says doing such will harm the OS. To both gents: please tell me what systems you are using. My system info is always part of my signature.

---

### Post by bodhi.zazen on 2007-09-25
In general , you list your partitions with ```
sudo fdisk -l
```

A partition is listed as /dev/xxx where xxx is hda1 or sda1

See this link for information of partitions : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

You then make a mount point and mount the partition.

Standard location is in /media

So :

```
sudo mkdir /media/hda1
sudo mount /dev/hda1 /media/hda1
```

You can then see the contents of the partition with :

```
gksu nautilus /media/hda1
```

repeat for each partition.

For additional information :

fstab : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

Mounting :

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

What part are you having problem with ? partitions, mounting ???

---

### Post by Irihapeti on 2007-09-25
Point taken. It was getting unnecessarily complicated and perhaps off-topic, if you're not using the GParted liveCD.

---

### Post by Mark_in_Hollywood on 2007-09-26
[QUOTE=bodhi.zazen;3425358]In general , you list your partitions with ```
sudo fdisk -l
```

A partition is listed as /dev/xxx where xxx is hda1 or sda1

Output of sudo fdisk -l

Disk /dev/sda: **10.2 GB**, 10202050560 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1181     9486351   83  Linux
/dev/sda2            1182        1240      473917+   5  Extended
/dev/sda5            1182        1240      473886   82  Linux swap / Solaris

Disk /dev/sdb: **40.0 GB**, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4485    36025731   83  Linux
/dev/sdb2            4773        4865      747022+   5  Extended
/dev/sdb5            4773        4865      746991   82  Linux swap / Solaris

I have the drives set backwards at the moment, so as to preserve /home on the 40GB disk. That is 10GB is primary master and 40GB is primary slave.

I am going to remove the 10GB from the box. I will put the 40GB as Primary Master. Then, using the Canonical LiveCD, so as to be able to get on the 'net, I will start working with that disk to restore the MBR and Grub, where were damaged, when I tried to put a Windows 98 disk as primary slave.

My response to Bodhi.Zazen's question is: I want to fix the MBR. I don't know whether menu.lst is damaged as well. I think it may be. I added a windows section at the end of it per some posts this forum. I have removed the offending Windows drive. Forever. I'm unable to keep myself from anger at Windows over this, so it's **quits** with them. If I had a way to back up the /home on the 40GB drive, I would, but currently, I don't. So I'm being extra cautious in trying to resolve this problem.

As my drives are 'generically' labeled as scsi devices, once the 40GB is on the cable as Primary Master and the LiveCD running, will the live session "see" that drive as sdb. 

Is the first partition that the MBR/Bootloader reads sdb1?
Is my home folder in sdb2?
Is sdb5 the swap?

How can the 3 questions be answered?

---

### Post by bodhi.zazen on 2007-09-26
> **Mark_in_Hollywood said:**
> In general , you list your partitions with ```
sudo fdisk -l
```

A partition is listed as /dev/xxx where xxx is hda1 or sda1

Output of sudo fdisk -l

Disk /dev/sda: **10.2 GB**, 10202050560 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1181     9486351   83  Linux
/dev/sda2            1182        1240      473917+   5  Extended
/dev/sda5            1182        1240      473886   82  Linux swap / Solaris

Disk /dev/sdb: **40.0 GB**, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4485    36025731   83  Linux
/dev/sdb2            4773        4865      747022+   5  Extended
/dev/sdb5            4773        4865      746991   82  Linux swap / Solaris

I have the drives set backwards at the moment, so as to preserve /home on the 40GB disk. That is 10GB is primary master and 40GB is primary slave.

I am going to remove the 10GB from the box. I will put the 40GB as Primary Master. Then, using the Canonical LiveCD, so as to be able to get on the 'net, I will start working with that disk to restore the MBR and Grub, where were damaged, when I tried to put a Windows 98 disk as primary slave.

First step is to position the hard drives where you want them. If you want to remove a drive, pull the data and remove it. If you want to change primary/slave make the change.

I will follow the terminology you posted in the rest of my response. If you change your hard drives, re list the partitions with "sudo fdisk -l" and adjust accordingly.

_Note_: For the record, you do not *need* to change your hard drives. Linus will run just fine on the secondary drive and you can format and use the first drive without repositioning it.

> My response to Bodhi.Zazen's question is: I want to fix the MBR. I don't know whether menu.lst is damaged as well. I think it may be. I added a windows section at the end of it per some posts this forum. I have removed the offending Windows drive. Forever. I'm unable to keep myself from anger at Windows over this, so it's **quits** with them. If I had a way to back up the /home on the 40GB drive, I would, but currently, I don't. So I'm being extra cautious in trying to resolve this problem.

To fix the MBR, see this link : [uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

Or Supergrub : [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

> As my drives are 'generically' labeled as scsi devices, once the 40GB is on the cable as Primary Master and the LiveCD running, will the live session "see" that drive as sdb.

This is a basic partitioning question and is fully answered here : 

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Your Master Hard drive is sda. Your slave drive is sdb.

The first partition on your master is sda1, etc.

So, when you change the physical configuration master/slave the designation will change, same as Windows, just the terminology has changed is all.

Grub uses numbers, starting of course with 0. Primary drive is (hd0), first partition is (hd0,0)

> Is the first partition that the MBR/Bootloader reads sdb1?

You MBR is the first track on the primary drive, sda or (hd0). This is NOT the same as sda1. sda1 is the first partition (the MBR is NOT a part of the first partition).

> Is my home folder in sdb2?

No. sdb2 is an extended partition and contains sdb5. See the link on partitioning terminology.

You can find /home by looking at the contents of /etc/fstab :

```
sudo grep home /etc/fstab
```

Or mounting a partition and looking at it.

Try sdb1:```
sudo mkdir /media/sdb1 #If you get a message the the directory exists, proceed
sudo mount /dev/sdb1 /media/sdb1
sudo ls /dev/sdb1
```

That will list the contents and should tell you if it is /home.

> Is sdb5 the swap?

Yes as is sda5.

You only need 1 swap, although 2 will not hurt anything.

> How can the 3 questions be answered?

HTH

---

### Post by Mark_in_Hollywood on 2007-09-27
Following:

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

I powered up with LiveCD, opened a terminal and typed

sudo grub

returned was 

grub>

next I hit the TAB key and this returned:

 Possible commands are: blocklist boot cat chainloader clear cmp color configfi
le debug device displayapm displaymem dump embed find fstest geometry halt help
 hide impsprobe initrd install ioprobe kernel lock makeactive map md5crypt modu
le modulenounzip pager partnew parttype password pause print quit quiet read re
boot root rootnoverify savedefault serial setkey setup terminal terminfo testlo
ad testvbe unhide uppermem vbeprobe

Then I tried:

grub> find /boot/grub/stage1

and this returned:

Device not found Error 11

Eventually Grub determined my disk was (hd0,0) and following the rest of the instructions, it seems to have had success re-writing the MBR. I will now to a cold-boot and see.

---

### Post by Mark_in_Hollywood on 2007-09-27
On cold-boot, OS menu, offered:

2.6.16-28-386 (on /dev/sdb1)

selecting that kernel returned:

Error 15 file not found

selecting any other /recovrey or earlier kernel did the same.

There is now, only 1 hard drive on the cable, set as Pri.Master. Disk's jumpers are set as master-single. Why is the OS selection screen (is that part of Grub?) saying: sdb1?

---

### Post by Mark_in_Hollywood on 2007-09-27
I'm posting this here because I can't save it to a file on disk.

grub> 
 Possible commands are: blocklist boot cat chainloader clear cmp color configfi
le debug device displayapm displaymem dump embed find fstest geometry halt help
 hide impsprobe initrd install ioprobe kernel lock makeactive map md5crypt modu
le modulenounzip pager partnew parttype password pause print quit quiet read re
boot root rootnoverify savedefault serial setkey setup terminal terminfo testlo
ad testvbe unhide uppermem vbeprobe

grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

---

### Post by bodhi.zazen on 2007-09-27
THAT'S IT \o/

You should now be good to go :twisted:

---

### Post by Mark_in_Hollywood on 2007-09-27
No on rebooting I received the Kernel selection / recover mode / memory test screen

Selecting

Other Operating Systems returns

Error 11 Unrecognized device string

Selecting

Ubuntu, kernel 2.6.15-28-386 (on /dev/**sdb1**) returns:

Error 15 file not found

and for all other lines in this screen, e.g.,

ubuntu, kernel 2.5.15-23-386 [and/or] recover mode / memory test **(on /dev/hdb1) (on sdb1)** 

returns:

Error 15 file not found

disk has no bootability

---

### Post by bodhi.zazen on 2007-09-27
Looks like you need to edit your menu.lst

boot a live CD...

Mount the partition (sda1)

edit /media/sda1/boot/grub/menu.lst

```
gksu gedit /media/sda1/boot/grub/menu.lst
```

Change sdb1 to sda1 (in the kernel lines and in the configuration lines at the top of the file ...) and make sure root (hd0,0) on the root lines.

Or you could :

```
sudo sed -i -e 's_sdb1_sda1_g' /media/sda1/boot/grub/menu.lst
```

---

### Post by Mark_in_Hollywood on 2007-09-27
Using either of the two lines of code provided returns the text editor with an filename open to menu.lst.

There is nothing in the file (or on the screen).

I don't know if this helps, but googleing around I found:

tring to install 2.6.11.7 now. but need a hand
[http://www.linuxforums.org/forum/debian-linux-help/60377-installed-kernel-2-6-8-1-blank-screen-after-grub.html](http://www.linuxforums.org/forum/debian-linux-help/60377-installed-kernel-2-6-8-1-blank-screen-after-grub.html)

which suggested:

Debian-Kernel-Compile-Howto (Kernel 2.6)
[http://www.falkotimme.com/howtos/debian_kernel2.6_compile/](http://www.falkotimme.com/howtos/debian_kernel2.6_compile/)

ubuntu@ubuntu:~$ ls /boot
abi-2.6.20-15-generic             memtest86+.bin
config-2.6.20-15-generic          System.map-2.6.20-15-generic
initrd.img-2.6.20-15-generic.bak  vmlinuz-2.6.20-15-generic
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ less /boot/grub/menu.lst
/boot/grub/menu.lst: No such file or directory

[posted under the above had been the text of /boot/grub/menu.lst. I removed it] I guess I hadn't caused the disk to mount. After mounting,I found the /boot/grub/menu.lst populated with stanzas. Whether they work correctly I don't know, but I did change all **sdb1** to **sda1**. 

Rebooting returned the same grub errors: #'s 11 and 15.

When I tried:

gksu gedit /media/sda1/boot/grub/menu.lst

I got a blank menu.lst and when I looked in /media there is no item: sda1

The best I could find is:

ubuntu@ubuntu:/media/disk$ ls
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old
ubuntu@ubuntu:/media/disk$ cd /media/disk/media
ubuntu@ubuntu:/media/disk/media$ ls
cdrom  cdrom0  cdrom1  floppy  floppy0
ubuntu@ubuntu:/media/disk/media$

---

### Post by bodhi.zazen on 2007-09-27
LOL

We are obviously having trouble communicating, I am so sorry 

You need to mount the partition first.

Boot a live CD

Open a terminal

```
sudo -i
```You should new be root, so we can skip the sudo

continue
```
mkdir /media/sda1
mount /dev/sda1 /media/sda1
```

You can now manually edit /media/sda1/boot/grub/menu.lst

Or, as root :

```
sed -i -e 's_sdb1_sda1_g' /media/sda1/boot/grub/menu.lst
```

Reboot ...

===========

You also might find it easier if you downloaded supergrub ...

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Mark_in_Hollywood on 2007-12-07
After many other posts and several weeks of distress, I can say that what I wanted has been solved, but adding more than that would involve, oh, say 40 to 50 links, and several hours of cutting & pasting.

No computer system is easy, Ubuntu comes closest, but until the "end user" can change drives, without losing valuable data SIMPLY, the promise of LInux will remain only the promise.

---

