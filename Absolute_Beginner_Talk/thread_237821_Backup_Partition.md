---
title: "Backup Partition?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by dillbertdabomb on 2006-08-16
I have a windows reinstall partition and it it in front of my windows partition. I need to keep this on here when I install. it is a 6.06gib with 712mib of spare space partion with a fat32 filesystem. my windows partiton which is after it (reinstall partition) is 142gib with 100gib free space. How do I install with that, I need to keep both...

---

### Post by xpod on 2006-08-16
Defrag defrag defrag your xp.........Then you jump in,put your live cd in and once it`s up n running you start the installer which will
begin with a few preferance related stages(country,keyboard etc).

Then you have to resize your big partition with the xp on it down by whatever you feel you`ll need for Ubunto(30g?).Gparted should list both your main and your recovery partition so telling which is which should`nt be hard.

A lot of people will tell you to create all your partitions manually with separate partitions for home etc(and quite a few more at times)...But i reckon your better just creating the space then pointing gparted to the new space and letting it do it automatically...Entirely up to you though.

New too so cant give to much technical advice other than basics

EDIT:not sure if that little partition at start would have a bearing on grub(bootloader that sets up your dual boot with xp)
Ive got something similar but on end of XP and my Ubunto`s on a slave so i cant be 100% sure....Somebody else can mabey clarify things a bit better than what i can

---

### Post by dillbertdabomb on 2006-08-16
can you give me an idea of the partiton table I need?

I have 512mib of ram now, I want double for my swap and I need to know about how much room linux needs.

---

### Post by bodhi.zazen on 2006-08-16
Do you want to keep Windows?

Do you have a Windows restore CD?

Linux "needs" at least 5 Gb, 10 is better.

General advice:

I assume Keep Windows, No restore CD. In that case keep re-install partition and re-size windows partition. Make a swap partition size = RAM X2. Make Linux partition(s).

If you can not shrink the Windows partition as small as you would like (you will lose all your data):
Keep re-install partition, wipe windows partition. Now use cfdisk to create a new windows partition of the desired size and linux partitions of the desired size. Re-install Windows. Install Linux.

No keep windows - Wipe the hard drive, partition, install Ubuntu.

Consider making a data partition (rather then a home partition). This partition can be shared between Linux and Windows.

If you want more specific advice, post more specific question.

---

### Post by dillbertdabomb on 2006-08-16
I need to keep the windows I have now - the specs are above i don't know how to keep my data!

---

### Post by bodhi.zazen on 2006-08-16
use GParted to resize your windows partition. Do this from the Ubuntu Live CD, I believe GParted is a desktop icon.

CAUTION: Before your resize DEFRAGMENT and compact the windows partition.

CAUTION: No guarentee of data preservation.

---

### Post by dillbertdabomb on 2006-08-16
how do you compact and are these drives linux compatible for backups? [http://www.lacie.com/products/range.htm?id=10033]("http://www.lacie.com/products/range.htm?id=10033")

---

### Post by bodhi.zazen on 2006-08-16
1. Go for a USB drive, I think firewire support is more spotty in Linux.

2. ... rusty .... on ...Microsft......
? I think this is part of the defrag tool, else in the admin section? If not, do not sweat it.

3. If you are in the market for a drive, why not install a new internal hard drive? Cheaper. Better perfomance.

---

### Post by dillbertdabomb on 2006-08-16
if i edit the partition table during install will it work right, i need an example table for that...

---

### Post by bodhi.zazen on 2006-08-16
err.. not sure what you are asking.

Back up your data from windows first.

You can partition with GParted. No need to re-partition during subsequent install.

If partitioning during an install I use cfdisk.

As far as a partition table, what is your current table (with your restore partition)?

My advice for a partition table (other then wipe windows he.. he..)

Keep you current windows restore partition and re-sized Windows partition.

Resized Windows partition- As small as possible.

Swap partition 1024 Mb
Linux Home 10 Gb
Data partition (share with Ubuntu and Windows)-> As large as possible. Partition type FAT or NTFS.

I would keep the Windows partitions "primary" and the Linux and shared data partition "Logical" with extended partitions.

Windows uses C:\ E:\ etc for partitions. Careful not to wipe your Linux partition from Windows !!

Linux partitions will be something like this:
(Sorry it looks so ugly)

partition   size            Type                 ID
Windows:
/dev/hda1 <size> Mb ? FAT/NTFS Windows Restore partition
/dev/hda2 <size> Mb ? FAT/NTFS Windows C:\

Linux/Share:
/dev/hda4 1024 Mb     Swap             Swap
/dev/hda5 <size>      ?Ext3            / (Ubuntu root)
/dev/hda6 <size>      ?FAT/NTFS        Data partition


The data partition preserves data in the event you need to re-install your OS, Windows or Ubuntu

---

### Post by dillbertdabomb on 2006-08-16
theres a partitioner in the installation - can I use that and get the same results?

I am liking your thoughts about windoze - i hate as much as you do but I have to keep it...

---

### Post by bodhi.zazen on 2006-08-16
err.... Not sure what you are exactly referring to. ?cfdisk, GParted, or the partitioning section of the "alternate CD" install.

I assume you are asking about cfdisk. cfdisk is my personal preference, but there is a learning curve.

You need to resize windows first as cfdisk will not re-size a partition (only destroy or create).

I prefer cfdisk to GParted for a variety of reasons.

If you are referring to the partitioning portion during installation from the "alternate CD" it will not re-partition, it will assign existing partitions a mount point but not destroy, create, or re-size.

ie

/dev/hda2 ---> /mnt/windows
/dev/hda4 ---> swap
/dev/hda5 ---- /
/dev/hda6 ---> /mnt/data

---

### Post by dillbertdabomb on 2006-08-16
the installer thatis no the desktop - it asks to resize main partition, delete main partition, or manually edit partition table its in the 6.06 version!?!

---

### Post by bodhi.zazen on 2006-08-16
If you are referring the the "Live CD"

1. You should know that some have experienced problems installing from the Lived CD and the alternate CD is advised by most, including myself. It is not a "point and click" but it is very doable.

2. If you are using the Live CD anyways...
Set up all partitions with GParted.
Then Install -> manual edit -> Use mount points as above.

Note: you may not want to mount your Windows partition, but you can edit /etc/fstab later and change the "auto" to "noauto". If this does not make sense, use /mnt/windows for now and I will help you with /etc/fstab post install.

---

### Post by dillbertdabomb on 2006-08-16
ok but do you make the partitions and than manually edit the partition table in the installer or not?

---

### Post by bodhi.zazen on 2006-08-16
Yes, exactly. partition then install with a manual edit. With the manual edit you are not partitioning, just setting up /etc/fstab (mount points).

When you manually edit you will assign each existing partition (/dev/hdax) a mount point (in /ect/fstab). Some of it (swap and /) is point and click.

---

### Post by dillbertdabomb on 2006-08-16
as in the screenshot? it

---

### Post by bodhi.zazen on 2006-08-16
Looks good to me he... he..

Where are your two windows partitions?

The size of your partitions is also off.

Swap should be 1024 Mb

---

### Post by dillbertdabomb on 2006-08-16
ooh i took those from a site, just wanted to show you

now do i set up three partitions; swap, boot, and home or just swap and / ?

---

### Post by bodhi.zazen on 2006-08-16
Yes, you have it.  The "manual" part is under the "Mount Point"

You will need to enter /mnt/windows and /mnt/data (on the appropriate partitions) manually.

---

### Post by bodhi.zazen on 2006-08-16
No /home partition. Change this to /mnt/data.
No /boot partition.

You Ubuntu partitions should be:
/
swap
/mnt/data
/mnt/windows

---

### Post by dillbertdabomb on 2006-08-16
this shows alot of stuff: :sad: what do i need /mnt/usr ; swap ; /
anything else? and do I need the data part because i plan to make the linux partition huge anyway isn't that / ?

opps and what about my backup, what do i name that?

and do you lose data when you shrink partitions?

---

### Post by bodhi.zazen on 2006-08-16
Easy-does-it with that windows partition.

No need for /boot.
/home is an alternate scheme, but what I advise for you is /mnt/data as you are not mounting /home as a networked drive and if you ever need, back up /home to /mnt/data/home.

Share /data with Windows. Needs to be NTFS or FAT.

---

### Post by dillbertdabomb on 2006-08-16
so split drive to 3rds

1 third shared data

2 third windows

3 third linux

right?????

---

### Post by bodhi.zazen on 2006-08-16
So many choices, so little partitions.

Under my scheme you are keeping basic Ubuntu system files in / ;  all data in a separate partition. Your system files are not likely to exceed 10 Gb. The data partition can be shared with Windows, helpful with dual booting and data sharing between Ubuntu and Windows.

Advise: Keep you / partition 10-20 Gb, make Data 90++ Gb. Swap 1024 Mb. Windows may need a little more, say 20-30 GB of free space (do not cut it too tight).

---

### Post by bodhi.zazen on 2006-08-16
your 1/3 1/3 1/3 split is reasonable, but you still need swap.

---

### Post by dillbertdabomb on 2006-08-16
OPPPPPPSSSSSSSSSSSSSSSSS! ok so 10 gib for linux, 1024mib for swap(in linux part?), 100 gib shared rest windoze?

---

### Post by dillbertdabomb on 2006-08-16
Umm after reading something random, I figured out fat32 can no be bigger than 32gib True or not?



DUH me thats what the 32 means...


ohh silly me bigger...

---

### Post by bodhi.zazen on 2006-08-16
Since you have the space....

20 Gb for /
1024 Mb for swap
an additinoal "extra" 20 Gb to Windows.
and 59 or so for your data partition.

Quick question, How big is your Windows partition? If you have not re-sized do that first to see how much free space you have for Ubuntu, swap, and data

---

### Post by dillbertdabomb on 2006-08-16
142 gib with 112 gib to spare, im not installing linux at the sec, im researching how to get it to work, i use the live cd. Your help is still helpful though, it will help me!

---

### Post by bodhi.zazen on 2006-08-16
Not sure re Fat size limits. This is likely a Windows limitation and not a Linux limitation. ie Linux can mount a larger FAT partition for sure.

To be safe, why not NTFS? I assume you are running Windows XP. Linux handles NTFS OK, I use it all the time with a shared USB with NTFS. No problem with read/write or data loss with Linux or Windows XP.

You will need to modify /etc/fstab to allow read-write access. Worry about that post-install.

sudo chown root:users /mnt/data
sudo chown root:users /mnt/windows
sudo chmod 777 /mnt/data
sudo chod 777 /mnt/windows

Edit /etc/fstab and change the "ro" entry to "rw".
If you are paranoid, use chmod 770 rather then 777.

---

### Post by dillbertdabomb on 2006-08-16
really... can i make a ntfs partiton in gparted? and right now linux gives me a error when i try to acsess a drive:

you do not have the permissions to access this drive

i don't get it...

---

### Post by bodhi.zazen on 2006-08-16
If not with GParted, certainly with Windows, just format the partition.

As far as your permissions you need to change owner of the mount point and modify /etc/fstab as above.

You should be able to do this within the Live CD and try it now for yourself.

use sudo nano /etc/fstab to edit.

---

### Post by dillbertdabomb on 2006-08-16
Im a noob how do you change fstab?

---

### Post by bodhi.zazen on 2006-08-16
Open a terminal.
At the CLI type:
sudo nano /etc/fstab

Use arrow keys, change the portion of the line 
/dev/hda2 ............... auto,ro   0  0
to read:
/dev/hda2 ............... users,rw (likely reads auto,ro)
Leave the 0 0
?May be /dev/hda1 rather then /dev/hda2
the mount point is listed in the second comlumn

When finished type Ctrl X, type y for save.

change ownership of you mount point as above.

Unmount and then re-mount the drive.

umount /mnt/mount_point (NOTE: NOT unmount, just 1 u)
mount /mnt/mount_point

In Ubuntu mount pint may be may be /media/windows ?
Sorry, I am rusty with Windows.

Your changes will not be saved when you re-boot.

---

### Post by bodhi.zazen on 2006-08-16
With GParted, at the terminal type;

sudo gparted

This will start GParted as root.

---

### Post by dillbertdabomb on 2006-08-16
how come when you get on your not root, i read that you were...

---

### Post by bodhi.zazen on 2006-08-17
err.. come again?

Not so sure re : Ubuntu Live CD, it has been a while.

On some live CD 's you are root, others not.

running as a non-root user is for security and to some extent you own protection, especially if you are new to Linux.

(At a terminal)
to run a command as root, generally type sudo

to become root (in a terminal) type su

Were you able to edit fstab? Access your windows partition?

---

### Post by dillbertdabomb on 2006-08-17
no i didn't have permissions to...

---

### Post by xpod on 2006-08-17
> Linux "needs" at least 5 Gb, 10 is better.


Believe it or not my Ubunto is on a 3.2g slave that i salvaged from even older pc as i was a bit hesitant about playing with Xp`s hd.Bit risky when i aint got XP cd...

Ubunto runs faster on THIS than what xp does on it`s 40g hd....
I`ll get round to investing in decent hardware once im a bit more proficient in the art of it all.

HEY HEY....you`ve all got swap partitions BIGGER than my hd`s....lol

---

### Post by dillbertdabomb on 2006-08-17
is 20gibs to much for linux than?

---

### Post by bodhi.zazen on 2006-08-17
20 Gb is more then enough. It can be done with 5 GB as a minimal size. It depends on how much additional software you need to load after a base install.

Partitioning is an "art" not a science. With the amount of HD space you have available the size of your Linux partition 5-15 or 20 Gb is almost a non-issue. If you are tight on space....

---

### Post by dillbertdabomb on 2006-08-17
yea I plan to put lots of software on it

---

