---
title: "M$ took everything?! Heellp!"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by squidward_tentacles on 2006-07-07
I (foolishly) inserted a Beta 2 Vista DVD I burned, entertaining thoughts of seeing what all the hype was about...I came to the point of the installation where it advised me to select a partition to install to. At this point I abandoned the install, as it said it could not install to a non-ntfs partition, and to install I would need to format the drive. (and I definantly did NOT want to overwrite my existing partitions) so I choose CANCEL and removed the DVD/iso, I was planing on using gparted to create a new blank partition to install to...However upon reboot this is what comes up...

Uncompressing Linux...OK, booting the kernel
mount: Mounting on dev/hda1 on /root failed: invalid argument
mount: Mounting /root/dev/ on dev./static/dev failed: No such file or directory
mount: Mounting /sys on root /root/sys/ failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target file system doesnt have /sbin/init

BusyBox v.1.01(Debian 1:1.01ubuntu3) Built in shell Cash)
Enter 'help' for a list of built in commands.
/bin/sh: can't access tty; job control turned off
#_

Aaarggh!! I dont mind reinstalling, but is there ANY way to save all the files I have been working on (aka a nearly complete web site)...<quietly>...and no I did not back-up....I should have known better, but can anyone help me fix this trainwreck?

---

### Post by Sonofmoog on 2006-07-07
Not enough information to advise you properly, but off what you provide, I would suggest that you load the Ubuntu LiveCD, and copy all your files in $HOME to a floppy, CD, or USB stick - whatever is most convenient .. 

But, you also need to:

1) fire up gparted on the LiveCD to see what your hard drive looks like.
2) open a console and type df -h and see what's there.

Here's where it gets iffy:

3) Mount the hard drive
4) Your Ubuntu install may not be on /dev/hda1 anymore, and df will tell you that .. So, the solution is to update menu.lst to point to the correct kernel location, and then edit /etc/fstab to point to your ext3 filesystem.
5) Now, unmount the file system 
6) Assuming both partitions are still there, and they should be, I'd run sudo e2fsck /dev/hda1 (or wherever your ext3 partition wound up), and see if your Linux partition can be repaired.

HTH

---

### Post by catlett on 2006-07-07
If you have the ubuntu live cd installer, put it in and boot. When you get to the login enter ubuntu and then press enter for the password (there is no pasword)
Once you are in open a terminal. Then enter these commands to mount your ubuntu partition 
```
sudo mkdir /media/ubuntu
```
```
sudo mount /dev/hda1 -t ext3 /media/ubuntu
```Once you do that an icon will appear on the desktop with that partition. Open it up and se if your files are there.
Do this and the result will dictate what to do next.

---

### Post by squidward_tentacles on 2006-07-07
Thanks a million for the reply:-D 
As I am kindda unsure of what information you need exactly I will post the output from the commands you gave:

gparted:
______________________________________________________
/dev/hda1 ext3 152.33 gb  9.33gb (used)  142.98gb .boot
/dev/hda2 extended 1.07gb    --         --
/dev/hda5 linuxswap 1.07gb   --         --

df-h
_____________________________________________________
union   811m  699m  142m 83%  /
varrun  189m  80k   189m  1%  /var/run
varlock 189m  4.0k  189m  1%  /var/lock
udev    189m  108k  188m  1%  /dev/
devshm  189m  0     189m  0%  /dev/shm
lrm     189m  8.8m  180m  5% 
 /lib/moudules/2.6.15-23-368/volatile
tmpfs   189m  12k   189m  1%  /tmp

mount /dev/hda1
______________________________________________________
mount:can't find /dev/hda1 in /etc/fstab or /etc/mtab

So, if im following you correctly I need to edit /etc/fstab to point to hda1? sorry, Im kind of getting a little lost here trying to follow these instructions...how exactly do I edit it? And based on the output here am I correct in assuming that my missing data/OS is on the 9.33gb block?

Thanks in advance for your help, I would REALLY like to recover that data, (the Vista CD got tossed out into the desert in a fit of rage, lol)

---

### Post by squidward_tentacles on 2006-07-07
> **catlett said:**
> If you have the ubuntu live cd installer, put it in and boot. When you get to the login enter ubuntu and then press enter for the password (there is no pasword)
Once you are in open a terminal. Then enter these commands to mount your ubuntu partition 
```
sudo mkdir /media/ubuntu
```
```
sudo mount /dev/hda1 -t ext3 /media/ubuntu
```Once you do that an icon will appear on the desktop with that partition. Open it up and se if your files are there.
Do this and the result will dictate what to do next.

Thanks for the post, however that didnt seem to work for me](*,) 
heres the output:
sudo mount /dev/hda1 -t ext3 /media/ubuntu
mount:wrong fs type, bad option, bad superblock on dev/hda1/, missing codepage or other error
In some cases usefull info is found in syslog -try dmesg | tail or so

---

### Post by squidward_tentacles on 2006-07-07
hmmm Im begining to think my new handle should be "screwed by M$"....output from dmesg | tail:

[4297128.622000] EXT3 - fs error (device hda1):ext3_check_desciptors: Inode bitmap for group 448 not in group (block 2147483647)!
[4297128.622000] EXT3 - fs: group descriptors corrupted!

Is there any fix for this or am I just completely screwed?

---

### Post by catlett on 2006-07-07
That's not good. It's saying there is something wrong with your partition. 

Just to tell you what the commands did.
The first command just made a place to mount the partition to. Sudo (invoke root privileges) mkdir (the command to make a directory) /media/ubuntu (the directory to be made is ubuntu inside of media)

The next command is how you mount a partition manually for one session only (making an entry in /etc/fstab is how you mount a partition so it is mounted every time you start-up.) Sudo (root) mount (the command to mount) /dev/hda1 (this is the partition to mount) -t (is the an option for the mount command which basically refers to the next parameter i.e. says the next entry is the file system type) ext3 (the type of file-system the partition is formatted to) /media/ubuntu (the directory to use for the mounting)

Your error [COLOR="Red"]mount:wrong fs type, bad option, bad superblock on dev/hda1/, missing codepage or other error[/COLOR] is not good. It is saying it didn't find an ext3 file-system on that partition.

There is a possibility that the windows installer started to format your drive or may have started to put data on your hard drive as part of a pre-install setup. I don't really know the ins and out of a MS installer but I do know it doesn't look for anything other than MS compatible. It may have even scanned you drive and thought it had errors and automatically tried to fix the file-system. You never know with MS. They just use so many defaults and auto run stuff anything could have been done.

The only thing I do know is that when vista was in early beta it couldn't format raw hard drives. You had to use XP to format it to ntfs first and then run it. I wonder if they tried top improve on that and it saw your drive as raw and tried to alter it. I am only guessing. 
The next thing is to run ```
dmesg | tail
``` and see what it says .

[COLOR="Red"]EDIT[/COLOR] I didn't see your post. The only thing I can think of is to try and see if gparted can convert the partition to ext3. Some partitioners can convert without loosing data (Partition Magic can but I never tried with gparted) I don't think gparted has a convert option, just a format option so I don't know. Format means data loss so I wouldn't attempt it until you have resolved to reinstall. Then before you reinstall try it. Either it will fix the bad sectors or it will prepare your drive for the new install

---

### Post by squidward_tentacles on 2006-07-07
> **catlett said:**
> That's not good. It's saying there is something wrong with your partition. 

Just to tell you what the commands did.
The first command just made a place to mount the partition to. Sudo (invoke root privileges) mkdir (the command to make a directory) /media/ubuntu (the directory to be made is ubuntu inside of media)

The next command is how you mount a partition manually for one session only (making an entry in /etc/fstab is how you mount a partition so it is mounted every time you start-up.) Sudo (root) mount (the command to mount) /dev/hda1 (this is the partition to mount) -t (is the an option for the mount command which basically refers to the next parameter i.e. says the next entry is the file system type) ext3 (the type of file-system the partition is formatted to) /media/ubuntu (the directory to use for the mounting)

Your error [COLOR="Red"]mount:wrong fs type, bad option, bad superblock on dev/hda1/, missing codepage or other error[/COLOR] is not good. It is saying it didn't find an ext3 file-system on that partition.

There is a possibility that the windows installer started to format your drive or may have started to put data on your hard drive as part of a pre-install setup. I don't really know the ins and out of a MS installer but I do know it doesn't look for anything other than MS compatible. It may have even scanned you drive and thought it had errors and automatically tried to fix the file-system. You never know with MS. They just use so many defaults and auto run stuff anything could have been done.

The only thing I do know is that when vista was in early beta it couldn't format raw hard drives. You had to use XP to format it to ntfs first and then run it. I wonder if they tried top improve on that and it saw your drive as raw and tried to alter it. I am only guessing. 
The next thing is to run ```
dmesg | tail
``` and see what it says .

yeah...I really should have known better...Im starting to think this is a lost cause...the output from "dmesg | tail" is one post above your last one....(we must have been typing at the same time) and it DOES NOT look encouraging...but I really do appreciate the help:D

---

### Post by squidward_tentacles on 2006-07-07
well, gparted does have a conversion option, I went ahead and converted the partition (back) to ext3...at which point the partition went from 9+ gigs to 2.5 gigs..hmmmm, again not good, additionally It came up with a msg telling me I needed to reboot because the partition that was being formated was already mounted, which doesnt make a whole lot of sense to me, as everything else told me I could not mount it...upon reboot I recieved an GRUB error15. I put the live CD back in and ran through the "mkdir /media/ubuntu" after this I was able to mont the said directoty, but no desktop icon appeared for the mounted directory....even after refreshing gnome panel, still no icon, I then tried to mount: from the terminal;
the results were: according to mtab, dev/hda1 is already mounted on /media/ubuntu mount failed....so what im wondering is are those 2.5 gigs whats left of my data, and if so how do I veiw them...

---

### Post by Frank Golden on 2006-07-07
> **catlett said:**
> 

There is a possibility that the windows installer started to format your drive or may have started to put data on your hard drive as part of a pre-install setup. I don't really know the ins and out of a MS installer but I do know it doesn't look for anything other than MS compatible. It may have even scanned you drive and thought it had errors and automatically tried to fix the file-system. You never know with MS. They just use so many defaults and auto run stuff anything could have been done.



Way to go M$. :rolleyes:

---

### Post by richbarna on 2006-07-07
I think that you may have messed up here and lost your data when you converted the partition to ext3.
Anyway, Anytime I or others have had this problem, I use a mini linux distro like Damn Small Linux or Dyne:Bolic.
Basically they are live cd's that range from 50Mb upwards and download quickly. Dyne:bolic is my favourite because it boots fast and also gives you direct access to the existing partitions.
You can get it here :- [ftp://ftp.mirrorservice.org/sites/www.dynebolic.org/dyne-2.0.iso](ftp://ftp.mirrorservice.org/sites/www.dynebolic.org/dyne-2.0.iso)
Other than that, I would do a complete Ubuntu install again. If you need to use Windows as well, make sure you install that first. Here's the best guide on the net :-[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by squidward_tentacles on 2006-07-07
Yeah, My feelings exactly, you would really think CANCEL would mean, well CANCEL...not "OK, we'll cancel just as soon as we trash your existing partitions"

<cackels brokenly, nose scant inches from screen> "Tell me Kid, ...Have you ever danced with Bill Gates in the pale moon light?"

---

### Post by KrisDwyer on 2006-07-07
Oh Squiddy you echo my sentiments time and time again.

---

### Post by Kabatwa on 2006-11-08
Hi, I'm having pretty much the same problem except that I haven't done anything to the hard drive yet. I booted into Windows this morning which is on my secondary drive (ubuntu on my primary) and then I formatted an external drive through computer management. Came back to boot ubuntu and I have the same error.
Can't mount hda1, dmesg | tail reads this : 

[4296487.011000] EXT3-fs: group descriptors corrupted !
[4296489.547000] EXT3-fs error (device hda1): ext3_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)!
[4296489.547000] EXT3-fs: group descriptors corrupted !
[4296517.100000] EXT3-fs error (device hda1): ext3_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)!
[4296517.101000] EXT3-fs: group descriptors corrupted !
[4296523.747000] EXT3-fs error (device hda1): ext3_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)!
[4296523.747000] EXT3-fs: group descriptors corrupted !
[4296526.596000] cdrom: This disc doesn't have any tracks I recognize!
[4296849.356000] EXT3-fs error (device hda1): ext3_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)!
[4296849.356000] EXT3-fs: group descriptors corrupted !


If anybody can help I'd really appreciate it as I need some photos desperately. I know, I know I should backup but that is what I was about to do that day! :( ](*,)

---

### Post by catlett on 2006-11-08
Try booting to the ubuntu live cd. The desktop install cd is a live cd. Then try to mount your ubuntu drive.
You need to know what partition ubuntu is on so enter this in the terminal to get a list of your partiotions/drives
```
sudo fdisk -l
```
Hopefully you can tell which one ubuntu is on. It should be an ext3 file system with a boot flag in fron of it (the symbol # is the boot flag)
Once you know that, you can mount the partition. First create a mount point for the ubuntu partition ```
sudo mkdir /media/ubuntu
```
Then emter this command replacing the question marks with ubuntu's partition number
```
sudo mount /dev/??? -t ext3 /media/ubuntu
```
If all goes well ubuntu's partition will be mounted in the media foler in a folder called ubuntu. Go to the top panel and enter into Places and select Computer. Then select Filesystem and when it's windows iopens, select Media and then Ubuntu. If you get an error post or if you can't figure out which one ubuntu is on post the output of sudo fdisk -l

---

### Post by Kabatwa on 2006-11-09
Just tried that - Booted with Live Cd fdisk -l and I get:

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7169    57584961   83  Linux
/dev/hda2            7170        7476     2465977+   5  Extended
/dev/hda5            7170        7476     2465946   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1314    10554673+   7  HPFS/NTFS
/dev/hdb2            1315        9729    67593487+   f  W95 Ext'd (LBA)
/dev/hdb5            1315        5139    30724281    7  HPFS/NTFS
/dev/hdb6            5140        9729    36869143+   b  W95 FAT32


So I'm guessing I had to go 
sudo mkdir /media/ubuntu
sudo mount /dev/hda1 -t ext3 /media/ubuntu
At which point I get

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Thanks for your help so far.

when I boot from the ubuntu partition though GRUB obviously loads because it asks me whether I want to boot into windows or ubuntu. Also when I get to that busybox thing and I ls the directory it looks like a complete root filesystem. Just some random thoughts

---

### Post by Archmage on 2006-11-09
> **squidward_tentacles said:**
> Yeah, My feelings exactly, you would really think CANCEL would mean, well CANCEL...not "OK, we'll cancel just as soon as we trash your existing partitions"

I think the point is, that Vista will put files on your harddrive as soon as you put the DVD in. Of course Vista isn't caring where it put the files, what format is the partition and what is happening with the old data. ](*,)

---

### Post by catlett on 2006-11-09
> **Kabatwa said:**
> Just tried that - Booted with Live Cd fdisk -l and I get:

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7169    57584961   83  Linux
/dev/hda2            7170        7476     2465977+   5  Extended
/dev/hda5            7170        7476     2465946   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1314    10554673+   7  HPFS/NTFS
/dev/hdb2            1315        9729    67593487+   f  W95 Ext'd (LBA)
/dev/hdb5            1315        5139    30724281    7  HPFS/NTFS
/dev/hdb6            5140        9729    36869143+   b  W95 FAT32


So I'm guessing I had to go 
sudo mkdir /media/ubuntu
sudo mount /dev/hda1 -t ext3 /media/ubuntu
At which point I get

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Thanks for your help so far.

when I boot from the ubuntu partition though GRUB obviously loads because it asks me whether I want to boot into windows or ubuntu. Also when I get to that busybox thing and I ls the directory it looks like a complete root filesystem. Just some random thoughts
You mounted it correctly but it appears there is something wrong with the partition. If you can boot into windows, you can use this utility to recover data from the ubuntu system. [http://www.data-recovery-software.net/Linux_Recovery.shtml](http://www.data-recovery-software.net/Linux_Recovery.shtml) It is a linux filesystem recovery application but it is run from within windows.
After you get out your i

---

### Post by Kabatwa on 2006-11-09
Thank you!
I've copied my whole hard drive over to my external one now and I'll format (Something I was going to do this week anyway) and then install Edgy. Will it be ok for me to just copy my old home folder over to the new one I'll install? Obviously I'll have to reinstall all the programs I had but thank you for all your help Catlett.

---

### Post by darkhatter on 2006-11-09
I believe vista has to uncompress files before it can run the installer, which what it is doing to you, I had a similar problem only vista killed my xp partition.

---

### Post by catlett on 2006-11-09
> **Kabatwa said:**
> Thank you!
I've copied my whole hard drive over to my external one now and I'll format (Something I was going to do this week anyway) and then install Edgy. Will it be ok for me to just copy my old home folder over to the new one I'll install? Obviously I'll have to reinstall all the programs I had but thank you for all your help Catlett.

If you had edgy before and now you are going to install edgy then I would think it would be fine to copy over the old home folder (I have never done it so I can't speak in absolutes) but if you had Dapper I would say no. I say that because your home folder has a bunch of hidden configuration files for your system. Almost everything that makes your install unique from a base install is there (this is how you can have your own specialised system when you are part of a network of many. Your home folder is the thing that is unique about your user account. You own the home folder and it can save configurations that make your account customised to your likings without affecting the base system) Long story short, your old home folder if from Dapper, will have conflicting and different folders than an Edgy install. It may cause issues. I would selectively copy over what you want from the old into the new to be safe. You can 'snoop' around the hidden folders by pressing Ctrl-H (press the control key and the capital h key at the same time) This makes hidden folders viewable. One file that I know will be different and have issues is your mozilla firefox file. Your old Dapper home (if your old home was from a dapper install) will have files for Firefox 1.5 but Edgy has Firefox 2.0 installed.

---

### Post by podunk on 2006-11-09
One thing you could do is download the partimage boot disk and make an image of the diisk. It has some utilities to recover corrupt partitions (Microsoft corrupts things, in Linux they are broken. Enough said! :-) )
[http://partimage.org/Main_Page](http://partimage.org/Main_Page)


In fact, I think the first thing I would do is make an image of the drive. If you can't recover the partition table you can send th image off. Another slim chance is you can restore the image to a different partition and then try to recover files once you have a good Linux install.

A couple of people have had good luck with this:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I used this a few years ago to recover a dying hard drive:
[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

sort of pricey, but works very good.

---

### Post by kthakore on 2006-11-09
```
There is a possibility that the windows installer started to format your drive or may have started to put data on your hard drive as part of a pre-install setup. I don't really know the ins and out of a MS installer but I do know it doesn't look for anything other than MS compatible. It may have even scanned you drive and thought it had errors and automatically tried to fix the file-system. You never know with MS. They just use so many defaults and auto run stuff anything could have been done.


```

another reason I won't try vista

---

