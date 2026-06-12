---
title: "2nd Drive 250GB HD can't access"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by speed32219 on 2007-02-12
OK, so I am a noob.  I just recently installed 6.10 Ubuntu on a 466 192MB ram Emachine that has a 4.3 GB HD.  I also installed a 250GB Western Digital HD prior to installing Ubuntu and formated with the FAT32 partition.  Of Course my home/user is on the 4.3GB (now only 1.7GB since OS is on there too).

I am setting this up for a video file server using XBMC (Modified Xbox).  I finally can get to my home /user area in the first HD from the network attached PC/Xbox but I can't get to the 250GB drive.  This is where I want to copy my video's to and I will be adding another 1.5TB once I get this up and running.  I did create a new file system called video files1 but it created it in my user area (small hard drive), so how do I get to the bigger HD?  (In windows it would be d:, E;. f:. etc.  and then just copy or drag and drop)

I can see the drive in device manager so I think it is mounted, is there a command that will show all the drives in the system. (Like window explorer)  I want to copy or move video files from my XP machine to the new ubuntu video  server.

FYI, I did install samba and assign user/passwd,  that's why I can get to the home/user file system from the network.  Just can't get to the 250GB.

---

### Post by dannyboy79 on 2007-02-12
how familar are you with linux? open a terminal window and please post the output of these few commands. the terminal can be found within the aka start menu, then under accessories.

sudo cat /etc/fstab

sudo fdisk -l

from here I can help you out.

---

### Post by speed32219 on 2007-02-12
Not familiar with linux.  I sued to know some intel and sco, but that was years ago. (many)

Just now jumping back into it, I am over MS, no vista for me. 

OK, here is what I copied and thanks for your quick response.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=92545bc4-7f43-4f14-a5d1-be440ea0cbe6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=b91caa0a-4d11-4d94-a401-d7a683dd9762 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


sudo fdisk -l

Disk /dev/hda: 4327 MB, 4327464960 bytes
255 heads, 63 sectors/track, 526 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         500     4016218+  83  Linux
/dev/hda2             501         526      208845    5  Extended
/dev/hda5             501         526      208813+  82  Linux swap / Solaris

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       30332   243641758+  83  Linux
/dev/hdd2           30333       30401      554242+   5  Extended
/dev/hdd5           30333       30401      554211   82  Linux swap / Solaris

---

### Post by dannyboy79 on 2007-02-12
ok, I see. the problem is that you haven't added an fstab entry for your new drive. that's what we need to do. here is what you need to add into the fstab file. in order to edit this file though you'll have to have root privalages, we do this in ubuntu using sudo. so the command is going to be like this.

sudo gedit /etc/fstab   (note: if you are using kubuntu, than gedit isn't installed. you have kate I believe. these are both just simple text editors.)

now that the file is open, we need to add this to it on a new line

/dev/hdd1 /media/video_files1 vfat defaults,utf8,umask=007,gid=1000,uid=1000

you're going to want to hit enter once at the end of this line so that the cursor comes down to the next line also. NOTE: the /media/video_files1 can be any location you want. this is called a mount point in linux. I strongly suggest you never use spaces in linux in file names as well as in folders, so I added an underscore to your name. this entry will only work if you move that folder you created from /home/username, so that the fodler is located within /media/. you can move folders using nautilus, nautilus is just like windows explorer. or you can use the terminal.

that would be done using this in a terminal

sudo mv /home/username/video (then hit tab and it should pick the folder name for you cause I forget how to enter folder names with spaces) once it addes the name of the folder so that you know you're moving that folder now hit a space and enter the new location. so that would be /media/video_files1. so the entire command would be like this

sudo mv /home/username/video /media/video_files1

then you want to make sure you own this folder. that's done with 

sudo chown username:groupname /media/video_files1

example: rick is going to be the username and the group you'll belong to is the same name.  
sudo chown rick:rick /media/video_files1

after you do this, we need to mount the partition that we just added to your fstab. this is done by jsut mounting everything within fstab with this:

sudo mount -a

now waht you'll want to do is check that that partition is mounted with this command.

df -h

you should get a list of all the partitions and mount points, you should see /dev/hdd1 is mounted to /media/video_files1

good luck!

just a note. you did tell me that you formatted your 250gb drive as fat32 and according to fdisk, it's formatted for linux, so it's either ext2 or ext3 most likely. this will only be able to be read by windows directly with a driver called fs-driver. of course you  know the limitations with fat32 is that you can't store a file larger than 4gb. also, you don't need more than 1 swap space. if I were you i would reformat that 250gb drive and make it just 1 partition that is ext3 if you're going to make it a movie server for xbox media center. this is what I did. you will want to use the graphical interface within system, admin, i think it's called gnome partition editor. you want to erase the 3 partitions and create just 1 ext3 or fat32 partition but you don't need that extended partition or the other swap you have right now. if anything is on the drive now, you'll need to move it off of there soemwhere else as formatting will erase everything. also, if you're going to be putting tons of drives in your box you'll need at least a 600watt power supply as I have 2x 250gb, 1x 300GB, 1x 400gb, 1x 500gb, 1x 20gb os drive, and 1 dvd-rewriter and my 400watt power supply wasn't cutting it so I upgraded and it's fine now.

---

### Post by speed32219 on 2007-02-12
rut roh!  DB79, followed your instructions,and got everything kinda worked out and when I went to mount the files systems I got the following error.

gellex@xbmc-vids:~$ sudo mv /home/gellex/video /media/video_files1
gellex@xbmc-vids:~$ sudo chown gellex:gellex /media/video_files1
gellex@xbmc-vids:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Here is the dmesg | tail cmd output.

gellex@xbmc-vids:~$ dmesg | tail
[  123.012194] Bluetooth: HCI socket layer initialized
[  123.124795] Bluetooth: L2CAP ver 2.8
[  123.124820] Bluetooth: L2CAP socket layer initialized
[  123.144409] Bluetooth: RFCOMM socket layer initialized
[  123.144482] Bluetooth: RFCOMM TTY layer initialized
[  123.144493] Bluetooth: RFCOMM ver 1.7
[ 2007.108261] FAT: bogus number of reserved sectors
[ 2007.108300] VFS: Can't find a valid FAT filesystem on dev hdd1.
[ 2057.514383] FAT: bogus number of reserved sectors
[ 2057.514409] VFS: Can't find a valid FAT filesystem on dev hdd1.

---

### Post by dannyboy79 on 2007-02-12
i told you that your 250gb hard drive is not formatted as fat32. if you had it installed during the install thatn ubuntu must have done formatted it as ext2 or ext3 and also created an extended partition and also added another swap partition which you don't need. so i don't have to rewrite everything, I am merely copying and pasting everything pertaining to what I posted about fixing this issue with your 250gb hdd.

just a note. you did tell me that you formatted your 250gb drive as fat32 and according to fdisk, it's formatted for linux, so it's either ext2 or ext3 most likely. this will only be able to be read by windows directly with a driver called fs-driver. of course you know the limitations with fat32 is that you can't store a file larger than 4gb. also, you don't need more than 1 swap space. if I were you i would reformat that 250gb drive and make it just 1 partition that is ext3 if you're going to make it a movie server for xbox media center. this is what I did. you will want to use the graphical interface within system, admin, i think it's called gnome partition editor. you want to erase the 3 partitions and create just 1 ext3 or fat32 partition but you don't need that extended partition or the other swap you have right now. if anything is on the drive now, you'll need to move it off of there soemwhere else as formatting will erase everything. also, if you're going to be putting tons of drives in your box you'll need at least a 600watt power supply as I have 2x 250gb, 1x 300GB, 1x 400gb, 1x 500gb, 1x 20gb os drive, and 1 dvd-rewriter and my 400watt power supply wasn't cutting it so I upgraded and it's fine now.

edit: if you want to leave it as ext3 which can be shared over samba to your xbmc, then you simply need to change the fstab entry to read this if you don't want to do what I suggested above.


/dev/hdd1 /media/video_files1 ext3 defaults 0 0



I also noticed that if you are going to go with fat32 (vfat within fstab) than I kind of forgot the last 2 entries on the end of the fstab entry, you need to add the 2 last zero's on the end of the line, just like your /dev/hdc line. also, i don't think your floppy line is correct as there is nothing after the /dev/ which I don't think is correct. you can search this forum for fstab and you get tons of returns and you can find out what others have for their floppy fstab lines.

---

### Post by speed32219 on 2007-02-12
DB79, I would swear on a bible that I chose FAT 32 when installing Ubuntu.  I knew of the Windows limitations of 4 GB files, but I did not think that applied to Linux and since the file system was on Linux I could copy all my 4.37 GB ISO movie files over with a hitch.  So after figuring out that I needed to install Gnome partition Editor (through use of Synaptic package manger I finally got it load.  

Using GPE it shows /dev/hdd1 as Unknown file system (232.35GB) and /dev/hdd2 file system as  Extended (541.25 MB). Then another entry of /dve/hdd5 unknown file system (541.22 MB).

So, going to try the EXT3 partition and hope I can read it with XP and the XBMC.  I can't wait to get her  going, looked good on XP, but I need nothing more than a file server with fast loads.  Thanks for the heads up on the Pwr supply, I am going to add another 3 500-750GB drives to handle my movies for now.

---

### Post by dannyboy79 on 2007-02-12
you are going to want to use gpe and erase all 3 of those partitions and create 1 new one. and if you are going to need to put files that are larger than 4 gb on this drive without .rar'ing or using some king of archive system, then you need to go with ext3. windows will be able to read and write to it over samba just fine, it would be if you ever wanted to take the drive and hook it up directly to windows than you would need to use the fs-driver driver in windows. as I was saying erase those 3 partitions and create 1 new one. format at what you want, then apply the changes. that's one thing weird about gpe, you have to hit the apply button or your changes won't really occur. I would suggest that before you write anything to the drive that you shutdown your system and reboot. make sure your fstab auto-mounts as expected. and you write a few files to the drive, then shut down, restart. open the files, erase some, rewrite some to make sure the filesystem is good prior to you transferring tons of stuff to it and then finding out it wasn't a good filesystem creation by gpe. i am not trying to scare you it's just that I am the same as you. I have over 300gb of backed up xbox games, over 700 gb of .avi files along with backed up dvd files. as well as 10gb of music. this is all something that I would HATE to lose hence I am suggesting the testing of the filesystem you're writing it some of it to. good luck

ps, I just saw that Comp USA has a 750gb Seagate for $279.00. you can beat I am getting 1 of these. great deal. other great deal is Wester Digital 500gb for $149.00 at tigerdirect.com. again, good luck

---

