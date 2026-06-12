---
title: "Screwed up adding 2nd hard drive"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by Bubba Ho-Tep on 2006-01-07
Hi, my first post!

I followed the instructions on the [wiki](https://wiki.ubuntu.com/InstallingANewHardDrive) to install a new hard drive.

But cos i dunno what I'm doing i've managed to mount it twice - kind of.

It's a 80gig drive and I want to have it as one partition (I'm backing up stuff from my win 'puter)

But looking on the file browser in Gnome it seems I've managed to create /backup (which is 7.2gigs) and on my second go /musicbackup which is 69gig (both on the 80gig'er)

I've figured out that in Linux you don't look at the file system as you do in Windows (eg no C: etc) 

So my question is how do I scrub what I've done and start again? I just want one /folder of 80gigs on the drive
I tried unmounting the /backup bit but umount said it was 'not mounted'
How can this be if it shows up in the GUI file manager?

Do I unmount both /backup and /musicbackup and then create a new /folder of 80gigs or can I unmount one and expand the other to include the spare space?

The instructions on the wiki are exactly what I want to do but altho i added the drive, formatted it etc I couldn't find (using the GUI) where it was etc

TIA!

BHT


oh i nearly forgot  - in the wiki it says

"Next add an entry in /etc/fstab using existing entries as a guide and you can then mount and/or unmount your new drive as you see fit by using the command: 

user@myubuntubox:~ $ sudo mount /backup <enter>
password: supersecret <enter>"

errr what does that mean? I get the bit about mounting/unmounting but fstab? existing entries?

---

### Post by gerbman on 2006-01-08
Hi there!> Do I unmount both /backup and /musicbackup and then create a new /folder of 80gigs or can I unmount one and expand the other to include the spare space?You don't do it by changing the folders. What you need to do is delete one of the partitions from the disk. This can be done with a program called 'gparted' in gnome. You can run it from a terminal window with ```
sudo gparted
```The interface is pretty simple, but all you need to do is delete one of the partitions and make the remaining partition fill all of the space on the drive. If you already have data on the drive, make sure you delete the right partition ;-).> "Next add an entry in /etc/fstab using existing entries as a guide and you can then mount and/or unmount your new drive as you see fit by using the command: 

user@myubuntubox:~ $ sudo mount /backup <enter>
password: supersecret <enter>"

errr what does that mean? I get the bit about mounting/unmounting but fstab? existing entries?The file '/etc/fstab' lists different storage devices as well as where they get mounted in the file system and the different mounting options used. In the file, the first column is the device name (for example, some partition on some hard drive), the second column is where that device gets mounted (the folder location), and the remaining columns are mounting options. The existing entries referred to are the lines already in /etc/fstab. You can model new entries on them, but a standard one that will probably work for you is ```
<device> <folder> defaults,uid=<your username> 0 0
```Make sure you have permissions on <folder> by doing ```
sudo chown <your username>:<your username> <folder>
```I hope some of that makes sense.

Cheers!

---

### Post by Bubba Ho-Tep on 2006-01-09
thanks for the response!

my Linux box isn't connected to the net yet and i don't have gparted so i've been dicking about with parted instead

however not been getting far with this, read the info and man pages and can't figure out how to do anything with it.

I'm doing "parted [/dev/hdb [check]]"

I've tried replacing "check"  with "print" and "select"

but each time it returns "could not stat device [/dev/hdb - no such file or directory." I guess my syntax is wrong or something


Using "df -h" shows 

Filesystem	Size  Used  Avail Use% Mounted on
/dev/hda1	9.1G  8.1G  526M  95%  /
tmpfs		 62M     0   62M   0%  /dev/shm
/dev		9.1G  8.1G  526M  95%  /.dev
none		5.0M  2.8M  2.3M  55%  /dev
/dev/hdc	587M  587M     0  100% /media/cdrom0

as you can see my /dev/hdb doesn't appear (it was before i started playing) does this mean it isn't mounted? :confused: 

I actually started from scratch following my post, unmounted /hdb and deleted the two folders /backup and /musicbackup and followed the instructions in the wiki from scratch.

So I mounted /hdb created a /backup folder (again) etc etc. But the flaming /backup folder is only about 6.7gigs not 80gigs. Arghhhhhh! :mad: 

so how do i get parted to work? (I'd love to use gparted instead but I need to connect the Linux box to the net via the Win box with ICS - which is a whole other learning exercise)

And how the hell if /dev/hdb is nowhere to be seen is the /backup folder appearing in the GUI file manager?

I haven't altered the fstab thingo yet but here's a good [link](http://www.tuxfiles.org/linuxhelp/fstab.html) explaining it if it helps anyone

many thanks :cool: 

BHT

---

### Post by xmastree on 2006-01-09
First thing to do is run this:```
 sudo fdisk -l
```to see if the disk is recognised by the system.
Where is the drive conencted? Primary slave? Secondary slave? If it's secondary slave it will show up as /dev/hdd

---

### Post by rooster on 2006-01-09
[QUOTE=Bubba Ho-Tep](I'd love to use gparted instead but I need to connect the Linux box to the net via the Win box with ICS - which is a whole other learning exercise)
[/QUOTE]
Maybe the connection to the I-Net with your Ubuntu-box is easier then you think. You can use dial-in (analog or ISDN) or DSL with built-in programs. You need, of course, the configuration data for the internet-access. Post your problems with it and we will try to help you!

When you're online you can use ```
sudo apt-get install gparted
``` or use Synaptic for installing the necessary programs.

On your problem on the disk:
- you have to format the drive (which you already did),
- then partitionate it (you built two partitions, but for you, one is enough), so delete one partition and resize the other
- then create a folder in your file system for the mounting point of the new partition (for example "/backup") with read (and write?) access for your user
- then add the data in fstab for automounting the partition.

I just wrote the last part for a overview of what you have to do to succeed (details in the posts above and in the wiki) and to show you what you already have finished. You're close to success!

Rooster

---

### Post by gerbman on 2006-01-09
[QUOTE=Bubba Ho-Tep]but each time it returns "could not stat device [/dev/hdb - no such file or directory." I guess my syntax is wrong or something[/QUOTE]Don't put the brackets in the device name, they're just there to explain the syntax.

---

### Post by Bubba Ho-Tep on 2006-01-10
Ok,

the disk is primary slave and 
sudo fdisk -l gives:

---
Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdb doesn't contain a valid partition table
---

Which is errr kinda confusing. As I said i started again, mounted a folder (/backup) and I stuck some images in there. If I open the GUI file manger I can see them. How can this be if /dev/hdb doesn't have a valid partition table?

Anyways I removed the [] (thanks gerbman) and parted now 'sees' /dev/hdb

Er then I got stuck.

I want to see what partitions are on the disk so i can figure what i need to delete, extend etc etc

But I can't see a command in the man page that will do this  - the print command looks kinda like what i want but when i do 

sudo parted /dev/hdb
	[which works and i get "using /dev/hdb"]
/dev/hdb print

it just returns a list of commands and their function And then it doesn't take any commands and i have to close the terminal.

BHT

---

### Post by xmastree on 2006-01-10
> the disk is primary slave and
sudo fdisk -l gives:

Disk /dev/hdb: 80.0 GB
Try **sudo fdisk /dev/hdb**
Or **sudo cfdisk /dev/hdb** for a slightly more user-friendly version.


> As I said i started again, mounted a folder (/backup) and I stuck some images in there. If I open the GUI file manger I can see them. How can this be if /dev/hdb doesn't have a valid partition table?The folder you created (/backup) exists under the root directory. If there's no filesystem mounted there you can still (as root) save files to the folder itself, just like any other folder.
I just tried that, unmounted my windows disk and I could still save files to that directory. they aren't on the (unmounted) windows disk, but on the same disk as the folder itself. i.e. the linux disk.

FWIW, the 'traditional' place to mount external filesystems is /mnt/<whatever> but you don't *have* to use that, you can put them anywhere you like.

Hope that makes sense.

---

