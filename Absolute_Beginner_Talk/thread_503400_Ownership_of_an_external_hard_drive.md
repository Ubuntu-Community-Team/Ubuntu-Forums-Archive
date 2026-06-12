---
title: "Ownership of an external hard drive"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by dloudy on 2007-07-17
Can someone tell me the quick fix for setting up my ownership rights to my external hard drive?  I am running Feisty Fawn, and it will not let me write to the drive.  It recognizes it, and I can browse it, but I cannot save files to it.  Any and all help will be greatly appreciated!!

I have tried to go into the properties, but it indicates the ownership as "root"....

Thanks,
Derek

---

### Post by aktiwers on 2007-07-17
What filesystem is on the drive? Remember that NTFS filesystems need additional software, if you want Linux to be able to write to it.

Go to terminal and type:
```
gksudo nautilus
```

Now from this new window, try go to your external harddrive again and set the permission to your user instead. Should work.

Or type this in terminal:
```
sudo chmod -R 777 /media/yourHardrive
```

where "yourhardrive" should be changed to the name your external hardrive has in /media/.

---

### Post by dloudy on 2007-07-17
I actually formatted it in Windows 2000, so I assume it is NTFS.

---

### Post by fdrake on 2007-07-17
you cannot change the ownership of a nfts filesystem you have to use NTFS configuration tools to write on it.

---

### Post by aktiwers on 2007-07-17
Automatix2 will let you install the necessary software: 
[http://www.getautomatix.com/](http://www.getautomatix.com/)

Its called ntfs-3g
Or install manually:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

But you should check what filesystem it is first.

---

### Post by HermanAB on 2007-07-17
Yup, NTFS is a robust file system, but it is very inefficient and on Linux systems, it is best avoided.  The default driver that comes with most versions of Linux is a read-only driver.  As mentioned above, in order to write to NTFS, you need the somewhat experimental ntfs-3g driver.

Be careful when you unplug the thing, since it can screw up if you do so during a write access.

---

### Post by dloudy on 2007-07-17
Funny, I began to do it manually, and I don't even have the system tools option under Applications.....

---

### Post by aktiwers on 2007-07-17
Did you remember to do first step?
```
sudo apt-get install ntfs-config
```

?

Else right-click on the menu and pick "Edit menu's". From there enable the "System Tools". :)

---

### Post by dloudy on 2007-07-17
OMigod.....talk about an idiot......boy am I a newbie at this.....

Got that part figured out now!!!! LMAO....!!!

---

### Post by dloudy on 2007-07-17
Okay, got that part figured out.....I actually got the program installed and opened it up....now, for some reason, it doesn't recognize the drive as being one that's able to be partitioned.  I open up the NTS config proram and click on "enable write write support.  It doesn't prompt me for a password, nor proceed any further.......

---

### Post by aktiwers on 2007-07-17
Glad it worked .
Let us know if you hit any other problems.. :)

Edit:
That was fast! :D
Doesnt it ask you for password when you open the program??

---

### Post by aktiwers on 2007-07-17
Or does it take you straight to this screen?
[IMG]http://www.ubuntugeek.com/images/ntfs/5.png[/IMG]

---

### Post by dloudy on 2007-07-19
Yeah, it takes me to that screen, so I check the box for external device, click o.k., and it does nothing else.

---

### Post by fdrake on 2007-07-19
try "sudo mount -a" what's the output?

---

### Post by dloudy on 2007-07-19
command-not-found: error: no such option: -a
bash: sudo mount -a: command not found

---

### Post by fdrake on 2007-07-19
u don't have it installed .

sudo aptitude install mount

sudo mount  -a

---

### Post by dloudy on 2007-07-19
derek@derek-desktop:~$ sudo aptitude install mount
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
derek@derek-desktop:~$ sudo mount -a
derek@derek-desktop:~$ "sudo mount -a"
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -a
bash: sudo mount -a: command not found

---

### Post by fdrake on 2007-07-19
now type 
mount -l

---

### Post by dloudy on 2007-07-19
derek@derek-desktop:~$ mount -l
/dev/hda3 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/External Hard Drive type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096) [External Hard Drive]

---

### Post by fdrake on 2007-07-19
> **dloudy said:**
> Can someone tell me the quick fix for setting up my ownership rights to my external hard drive?  I am running Feisty Fawn, and it will not let me write to the drive.  It recognizes it, and I can browse it, but I cannot save files to it.  Any and all help will be greatly appreciated!!

I have tried to go into the properties, but it indicates the ownership as "root"....

Thanks,
Derek

your first post says you have an external driver but when i look at the screen-shot aktiwer posted later i see (s)he checked only the internal device option . make sure you select them both. and type again
sudo mount -a
mount -l

---

### Post by dloudy on 2007-07-19
Naaah......that was a screen shot from Aktiwer, not mine.  When I use the NTFS configuration tool, it asks me for my password, which I enter, then only has the check box enabled for "external device", which I make sure is checked.  I can't even check the box for internal, so external is all that is selected.  I click OK, and it does nothing else.

---

### Post by fdrake on 2007-07-19
try this:
sudo mount /dev/sda1  "/media/External Hard Drive" -t ntfs-3g

---

### Post by stinger30au on 2007-07-21
i have a similar error on my machine.
i have 3 hard drives and dvdrw on this machine.
the first hard drive is setup exclusively with ubuntu fiesty on it. (used to be xp pro)
other 2 hard drives, one is ntfs the other is fat32

on one of the hard drives i installed a copy of "[portable office suite]("http://portableapps.com/")" when i had xp pro running and i saved all my data in it and used thunderbird email client etc.

i have now wiped off xp pro and installed Ubuntu and thunderbird.
im trying to copy the profiles from the thunderbird directory on the 2nd hard drive, but when i right click on it almost everything is greyed out and i can not select copy.
i have a backup of the data on both drives ntfs/fat32 and i get the same error on both drives.

how do i take controll of both internal hard drives data??? Thank you

---

### Post by fdrake on 2007-07-21
can you past here your fstab and mount list? type:

cat /etc/fstab

sudo mount -l

sudo fdisk -l

---

### Post by stinger30au on 2007-07-22
> **fdrake said:**
> can you past here your fstab and mount list? type:

cat /etc/fstab

sudo mount -l

sudo fdisk -l

 cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=7c5742f6-6eb1-49ae-86dd-e5ec9c41d5ee / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=e016d093-9363-494e-a19d-e592c2e90e9d none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb1 /media/hdb1 ntfs-3g defaults,locale=en_US.utf8 0 0


sudo mount -l
Password:
/dev/hda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hdb1 on /media/hdb1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096) [backup]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdc1 on /media/NET_GOODIES type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077) [NET_GOODIES]



 sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4660    37431418+  83  Linux
/dev/hda2            4661        4865     1646662+   5  Extended
/dev/hda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4865    39078081    7  HPFS/NTFS

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        5169    39077608+   c  W95 FAT32 (LBA)

---

### Post by jrev on 2007-07-22
Best avoid using the NTSF file system on your Ubuntu. You don't need it ...
I have already been four years on Linux and never used NTFS or only to copy a file from my windows partition to my ubuntu desk ...

---

### Post by stinger30au on 2007-07-22
> **jrev said:**
> Best avoid using the NTSF file system on your Ubuntu. You don't need it ...
I have already been four years on Linux and never used NTFS or only to copy a file from my windows partition to my ubuntu desk ...

is there a program to convert NTFS to EXT3 like linux uses??? if there is could i run it and it will solve my issues???

only reason they are NTFS and FAT 32 is cos i have just jumped XP Pro off this machine.

---

### Post by fdrake on 2007-07-22
you said u cannot copy or write on those drivers. for your fat32 driver try this

sudo chown your_username -R /media/NET_GOODIES
sudo chmod 755 --R /media/NET_GOODIES

can you try now to copy or paste on this hd now and let as know?

---

### Post by stinger30au on 2007-07-22
> **fdrake said:**
> you said u cannot copy or write on those drivers. for your fat32 driver try this

sudo chown your_username --R /media/NET_GOODIES
sudo chmod 755 --R /media/NET_GOODIES

can you try now to copy or paste on this hd now and let as know?

i did a copy/paste of your command with my user name
sudo chown dez --R /media/NET_GOODIES

and i got this error
chown: unrecognized option `--R'
Try `chown --help' for more information.

---

### Post by meierfra on 2007-07-22
Your /etc/fstab/ and your mount list don't agree with each other. Please reboot and post the result of 


cat /etc/fstab

sudo mount -l

---

### Post by stinger30au on 2007-07-22
i just fixxed the NET_Goodies hard drive.
on my desk top i right click on it  and went to properties
set folder access to create and delete. now its working.
will reboot pc and give you results you were looking for

---

### Post by fdrake on 2007-07-22
> **stinger30au said:**
> i did a copy/paste of your command with my user name
sudo chown dez --R /media/NET_GOODIES

and i got this error
chown: unrecognized option `--R'
Try `chown --help' for more information.

YOU ARE TYPING --R (2 minus symbols) instead i am typing -R (1 minus symbol). 
i just find out i wrote the command with 2 minus symbols. i corrected it now.

---

### Post by stinger30au on 2007-07-22
> **meierfra said:**
> Your /etc/fstab/ and your mount list don't agree with each other. Please reboot and post the result of 


cat /etc/fstab

sudo mount -l

cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=7c5742f6-6eb1-49ae-86dd-e5ec9c41d5ee / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=e016d093-9363-494e-a19d-e592c2e90e9d none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb1 /media/hdb1 ntfs-3g defaults,locale=en_US.utf8 0 0


sudo mount -l
Password:
/dev/hda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hdb1 on /media/hdb1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096) [backup]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdd on /media/XMEN2_DISC1 type udf (ro,nosuid,nodev,uid=1000) [XMEN2_DISC1]

---

### Post by stinger30au on 2007-07-22
> **fdrake said:**
> YOU ARE TYPING --R (2 minus symbols) instead i am typing -R (1 minus symbol)

if i do like you say i get this

 sudo chown dez -R /media/NET_GOODIES
chown: cannot access `/media/NET_GOODIES': No such file or directory

---

### Post by SPQQKY on 2007-07-22
I have this same issue and none of this is helping. I have two 300GB Seagate sata drives. One has two partitions with Vista/Ubuntu FF. The second is my storage drive formatted to NTFS with about 180GB of files on it. I would like to download/save files to the storage drive. 
I'd really hate to have to boot to Vista everytime I want to download a file and obviously I can't access files on the ext3 partition from Vista to save files to the storage drive. What's a fella to do?

---

### Post by stinger30au on 2007-07-22
*sigh* i did have it working when i set the permissions via the GUI now i have restarted, it wont work again

---

### Post by meierfra on 2007-07-22
Since you changed the permissions via "properties" you are all set on that part. All what needs to be done is edit the file /etc/fstab so that your  third hard drive is mounted at boot up.   Do you need help for that?

---

### Post by stinger30au on 2007-07-22
> **SPQQKY said:**
> I have this same issue and none of this is helping. I have two 300GB Seagate sata drives. One has two partitions with Vista/Ubuntu FF. The second is my storage drive formatted to NTFS with about 180GB of files on it. I would like to download/save files to the storage drive. 
I'd really hate to have to boot to Vista everytime I want to download a file and obviously I can't access files on the ext3 partition from Vista to save files to the storage drive. What's a fella to do?

I can READ the data, but if i try and select one or two files and copy/paste... no it wont happen.
i can not create a new file or directory either.will be something simple i bet

---

### Post by stinger30au on 2007-07-22
> **meierfra said:**
> Since you changed the permissions via "properties" you are all set on that part. All what needs to be done is edit the file /etc/fstab so that your  third hard drive is mounted at boot up.   Do you need help for that?

my drives are mounted on boot up.all of them. i even get icons on the desktop

---

### Post by meierfra on 2007-07-22
I'm confused. Can you right now read  the files in  NET_GOODIES?

---

### Post by stinger30au on 2007-07-22
> **meierfra said:**
> I'm confused. Can you right now read  the files in  NET_GOODIES?

yes i can read the files now. this is strange.

one minute i can read files and select files and right click and copy the files, and in afew minutes it magically changes and if i right click on a file i can not copy it and everything is greyed out!!!

its just stopped again. i went to my net_goodies drive, went down a few directory levels and again now i select some files and when i right click the only things that comes up is scripts, create archive, send to, everything else is grayed out

---

### Post by fdrake on 2007-07-22
> **stinger30au said:**
> my drives are mounted on boot up.all of them. i even get icons on the desktop

can you pls post here a screen shoot

and can u also post here the output of this command

ls -al  /media/

ls -al  /mnt/

---

### Post by stinger30au on 2007-07-22
> **fdrake said:**
> can you pls post here a screen shoot

sure here is a screen shot of desktop

---

### Post by SPQQKY on 2007-07-22
My problem is now solved. 
Using synaptic package manager, I installed the ntfs-3g and ntfs-config packges. On reboot I went to the ntfs configuration tool and enabled write to internal drive and I can now save downloads to my storage drive.
Hope you get yours sorted out soon, stinger30au.

---

### Post by meierfra on 2007-07-22
I think I start to understand what is  going on. Your cd-rom drive used by called "hdc". But now your  third hard drive is called hdc and the cd-rom drive is called hdd.   In your f-stab hdc is still being mounted to "media/cdrom0". 

So "hdc" in the /etc/fstab needs to be changed to "hdd"

fdrake, would you agree with that?

---

### Post by stinger30au on 2007-07-22
> **SPQQKY said:**
> My problem is now solved. 
Using synaptic package manager, I installed the ntfs-3g and ntfs-config packges. On reboot I went to the ntfs configuration tool and enabled write to internal drive and I can now save downloads to my storage drive.
Hope you get yours sorted out soon, stinger30au.

Thanks. mine does strange things. got to be something very simple to fix it for sure.
strnage how if i right click on properties of my net_goodies hdd i get some data i can change, but when i got to my other hdd, its all grayed out

---

### Post by stinger30au on 2007-07-22
> **meierfra said:**
> I think I start to understand what is  going on. Your cd-rom drive used by called "hdc". But now your  third hard drive is called hdc and the cd-rom drive is called hdd.   In your f-stab hdc is still being mounted to "media/cdrom0". 

So "hdc" in the /etc/fstab needs to be changed to "hdd"

fdrake, would you agree with that?

i dont know if this helps, but when i set ubuntu up i unplugged my 2 other hard drives and only had my main hard drive and dvd burned plugged in and installed ubuntu.
i did this to be double sure i did not delete any data from my other 2 hard drives, when ubuntu was loaded and worked i shut down my pc and plugged in my other 2 hard drives.

---

### Post by stinger30au on 2007-07-22
well for about the 5th time now i went to the termial and i ran sudo ntfs-config

now it works and i managed to copy my data out off it to get my thunderbird running.
wonder how long it will last for.

*sigh* sheer frustration

---

### Post by fdrake on 2007-07-22
to stinger30au

now that your net_goodies folder is mounted can u try to use the commands i gave u before

sudo chown your_username -R /media/NET_GOODIES
sudo chmod 755 -R /media/NET_GOODIES

and try if u can copy and paste.

---

### Post by meierfra on 2007-07-22
Lets try to work one problem at the time. If your open the back up folder, can you see any files? Can you open the files?

---

### Post by meierfra on 2007-07-22
I'm going to bed. But I don't think Net_Goodies is really mounted right now. Maybe rebooting one more time would help. I thing Ubuntu still remembers  the folder from the last time session, but according to  fstab and mount, nothing is really mounted in it.

---

### Post by fdrake on 2007-07-22
i have to go to bed too it's 2 am here goodnight.
maybe somebody will help u soon. anyway we will try to figure out something tomorrow bye!

---

### Post by meierfra on 2007-07-22
I missed one of your message (that every works again by running nfts-conf)  believe that for the backup folder. But I doubt  that Net_Goodies will be mounted after the next reboot. I'll check back sometime later.

---

### Post by stinger30au on 2007-07-22
thanks guys, i will restart my pc agian.

---

### Post by bodhi.zazen on 2007-07-22
> **fdrake said:**
> to stinger30au

now that your net_goodies folder is mounted can u try to use the commands i gave u before

sudo chown your_username -R /media/NET_GOODIES
sudo chmod 755 -R /media/NET_GOODIES

and try if u can copy and paste.

Those commands do NOT work with FAT or NTFS.

To change ownership and permissions are set as options at the time of mount ...

so mount -t <vfat or ntfs-3g> <device> <mount_point> **-o uid=1000,gid=100,umask=000**

or for fstab :

<device> <mount point> <vfat/ntfs-3g> users,uid=1000,gid=100,umask=000 0 0

So ...

You can use ntfs-config (this will take care of read-write permissions) or manually mount the partition 

```
sudo mkdir /media/net_goodies
sudo mount -t ntfs-3g /dev/hdb1 /media/net_goodies -o uid=1000,gid=100,umask=000
```

Or update fstab :
> /dev/hdb1 /media/net_good ntfs-3g auto,users,uid=1000,gid=100,umask=000 0 0
 

See man mount for further details

---

### Post by stinger30au on 2007-07-22
cool, thank you

---

### Post by dloudy on 2007-07-28
fdrake ---- in response to your last instructions....here is the output I get.

fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda1 (External Hard Drive)
derek@derek-desktop:~$

---

