---
title: "FAT32 is read-only"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by 3ws on 2007-10-24
For some reason, my drive has read-only permission.

Here is the result of etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=35d98c14-2593-4aae-89ce-b0ada90cd630 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=457138a7-c448-4bbe-b96f-ed8ce0bafd68 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

I am completely new to Linux and have no idea what it means, apart from something is wrong.

I am sure the drive is FAT32; I used Partition Magic to partition and format.

Ant ideas?

Thanks

---

### Post by atlfalcons866 on 2007-10-24
try this website
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Hospadar on 2007-10-24
I don't know exactly about your permissions (I'm not all too familiar with fstab business) But if you just formatted the drive, and want to share it with windows (I'd assume that's why you didn't just format it ext3) then might I suggest you format it ntfs, and use the ntfs-3g drivers and the ntfs-config tool to set up read/write capability.  These drivers work great and ntfs (or ext3 with windows ext3 drivers) is a much better filesystem than fat32.

If that's not what's up, try having a look at the folder your drive is mounted to and see what the permissions are.
```
cd /media
ls -o[/media]
and the line for sda5 should look something like this:
[code]drwxrwxrwx 1 root 8192 2007-10-21 20:29 sda5
```

The important part is that "drwxrwxrwx" this tells the file permissions for that folder.

post the output of your "ls -o" and we'll go from there.

---

### Post by 3ws on 2007-10-24
Thanks, atlfalcons866 and Hospadar.

Hospadar, I didn't format to ext3 because I didn't know how to. Here's what happened: I installed Ubuntu on the drive, had problems, reinstalled but seemed to have two seperate installations, at least that's what I thought according to the boot loader (as I said, I'm completely new to Linux). So i thought I'd use partition magic.

During the next installation I don't remember seeing an option for ext3. i selected use entire disk and left Ubuntu to it.

Can I remount the drive somehow? If so, will I have read write permission? Should I reinstall?

output to follow.

---

### Post by ajgreeny on 2007-10-24
Your fstab file does not even show a windows fat32 partition in the list, just a linux and a swap partition.  If you want the partition to be mounted at boot-up you will need to add the following line to the fstab file.
** /dev/hda1    /media/windows vfat  iocharset=utf8,umask=000  0    0**
You may need to change the /dev/hda1 to fit your system, but otherwise that should work OK.

To edit fstab type these commands in a terminal
```
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```This will make the directory to mount windows, backup your current fstab and finally get you root privileges to edit the file.

I've only just noticed that you don't even mention windows so perhaps this is not quite your problem, but if you have a fat32 partition you could still mount it read/write the same way, just changing the mount point /media/windows to /media/storage if you wanted, in both the fstab line and the commands I showed you.

---

### Post by 3ws on 2007-10-24
here's the output, Hospadar

jmm@evo:~$ cd /media
jmm@evo:/media$ ls -o
total 4
lrwxrwxrwx 1 root    6 2007-10-22 19:08 cdrom -> cdrom0
drwxr-xr-x 2 root 4096 2007-10-22 19:08 cdrom0
jmm@evo:/media$ 

Did I do it right? Doesn't mention anything about a fixed drive.

---

### Post by kernel tom on 2007-10-24
> **3ws said:**
> For some reason, my drive has read-only permission.

Here is the result of etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=35d98c14-2593-4aae-89ce-b0ada90cd630 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=457138a7-c448-4bbe-b96f-ed8ce0bafd68 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

I am completely new to Linux and have no idea what it means, apart from something is wrong.

I am sure the drive is FAT32; I used Partition Magic to partition and format.

Ant ideas?

Thanks

FAT32 is writable and readable in linux.   You just have to change the permissions... to do this go to your mount point, most likely /media/<hard drive name>

then use this command

cd /media
sudo chmod -R 755 <hard drive name>

that should do it and you will have all permissions on the drive, no need to format anything

---

### Post by kernel tom on 2007-10-24
Is this your main hd or is it an external?

---

### Post by 3ws on 2007-10-24
Thanks for the advice ajgreeny.

I am really new to Linux, as I said; I first installed and used Ubuntu last Thursday, so bear with me.

where should I add the line, anywhere in fstab? You said i might "need to change the /dev/hda1 to fit your system", what did you mean by that?
Thanks

---

### Post by 3ws on 2007-10-24
Kernel Tom it's my main drive.

---

### Post by 3ws on 2007-10-24
Kernel Tom, I went to media folder and saw three folders - CDROM, CDROM0 and Windows. No hard drive! What's going on? Seems to be what the output file below said, no hard drive.

---

### Post by kernel tom on 2007-10-24
I suggest just re-installing linux using the live cd.  Remember to unmount your hard drive, by right clicking it and selecting unmount, before installing

---

### Post by kernel tom on 2007-10-24
the Windows folder is from when you followed someone elses idea, which was incorrect.  A re-install of Ubuntu or similar should format your drive into ext3 automatically, once you select use entire drive for Ubuntu

you can never edit the drive you are booting from, and this drive can not be viewed in /media.  

you can edit this HD using the live cd, or just re-installing ubuntu.

either way i can help, which would you like to do?

---

### Post by 3ws on 2007-10-24
Looks like reinstallation is the best solution. 

Thanks

---

### Post by 3ws on 2007-10-24
Kernel Tom, editing the HD from the Live CD sounds the quickest. Could you give me (idiot-proof) instructions how to do it?

Thanks

---

### Post by kernel tom on 2007-10-24
alrighty... this is entirely from memory.

first thing, boot from your live cd
next your hard drive should show on your desktop, if not you got a problem
make sure hard drive is mounted, do this by right clicking your hard drive and clicking mount, if mount is not an option, it's mounted and your good
now open up a terminal and run the following commands
cd /media
ls -l                   this should show your hard drive and it's permissions, if not try the /mnt directory
sudo chmod -R 755 "name of the hard drive"

and that should do it, restart your computer and boot like normal without the live cd


i'll be unavailable for the next hour, but I will check your responses as soon as i can

---

### Post by 3ws on 2007-10-24
Thanks, Kernel Tom. I don't have time to do it tonight. I will try tomorrow and let you know.

---

### Post by kernel tom on 2007-10-24
sounds good, i'll be sure to check in tomorrow

---

### Post by 3ws on 2007-10-25
Kernel Tom, I think I might need to try plan B - reinstall.

I followed the steps above, rebooted, logged in and got a message that said something like this

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you might be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem.

Had a look at the details, which said

"mkdtemp: private socket dir: Permission Denied"

Could there be a problem with the HD? It is a second-hand disk.

---

### Post by jaybombalous on 2007-10-25
what exactly are u trying to do? If u only want ubuntu installed on that hard drive then u don't need a windows file format (example fat32 , ntfs) formatted to the HD. U need a linux format, (example: ext3, refs.)

If u are trying to read and write to a windows disk from **within** a ubuntu install then u do as tom said and make it read and writable.

U also said u installed ubuntu twice and seen where it looked like ubuntu installed twice in the bootloader, well I have 4 options in my bootloader. But, those are **not different versions of ubuntu** but different versions of the **kernel**. U get these when u do updates to the kernel. each time u upgrade to a new kernel the old kernel still exist in case u wanna go back. I always delete the old kernels once I am sure the new one works.

Does any of this make sense? Because I am still not sure after reading this whole thread that u even understand whats going on.

---

### Post by jaybombalous on 2007-10-25
so lets clear things up some.

to install ubuntu u need a HD formatted with a ext3 or refs file format.

If u wanna install windows u need a NTFS or fat32 file format.

If u wanna read and write to another drive that has windows installed from a ubuntu session u need to change the permissions of the drive loaded with windows.

---

### Post by 3ws on 2007-10-25
Jaybombalous, I was told that installing Ubuntu on a FAT32 format would give read write permission. Is that not so? I thought the drive might be NTFS since it used to have XP on it. So I used Partition Magic to format to FAT32. Was that a mistake?

Does the Ubuntu installation format the drive to ext3 automatically?

---

### Post by jaybombalous on 2007-10-25
yes it should automatically format the drive since linux will not install on a NTFS or FAT32 partition as far as I am aware of. Those are windows file systems only.

Now if u have a windows partition that u wanna access through ubuntu then u will need to setup read and write permissions for that partion through your ubuntu install. But ubuntu will only install on a linux partition. Again that is a ext3 or refs partition.

---

### Post by jaybombalous on 2007-10-25
make sure u use the option 'Use entire disk' when it ask during the ubuntu install and it will automatically erase all partitions on the drive and format the entire disk with ext3 file format. This will allow you to install ubuntu.

Then we can discuss accessing NTFS and FAT 32 partitions.


If u want to dual boot with ubuntu and windows u will need to install windows first, not really sure why I just know it won't work the other way, installing ubuntu first.

Also, if u have two drives in your pc, like I did originally when installing ubuntu. I removed the windows drive (IE unplugged it) from the pc. This allowed me to install linux on a separate HD without having it write grub to my windows drive. This was strictly done by me to keep my data safe on the windows drive. 

Now that I don't use windows I did a fresh install of ubuntu on that HD and backed up ubuntu on the other. Just something to think about for yourself.

---

### Post by jaybombalous on 2007-10-25
[http://ubuntuforums.org/showthread.php?t=307887](http://ubuntuforums.org/showthread.php?t=307887)

here is a thread on FAT32 partition and installing ubuntu. I guess its possible but definitely not recommended.

---

### Post by 3ws on 2007-10-25
Thanks for your advice, jaybombalous. 

I think use of the word FAT32 has confused things. The drive was FAT32 prior to the installation of Ubuntu but if, as you say, Ubuntu formats to ext3 during the install then it must be ext3. I didn't know that when I started the post; I assumed that the drive was still FAT32.

However, ext3 or not I still have read-only permission.

I will do a fresh install when I get home from work in a couple of hours.

---

### Post by 3ws on 2007-10-25
OK, I have reinstalled. I selected the entire disk option. The disk is ext3. But I still have read-only permission.

etc/fstab shows this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0610306c-e8fd-4480-a444-c8015de7092e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=457138a7-c448-4bbe-b96f-ed8ce0bafd68 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

and in /media I can see CDROM and CDROM0. No HD. However, properties of CDROM show that it is the HD - well it is the same size as the HD.

Can the HD be remounted? Is the HD faulty?

Thanks

---

### Post by qpieus on 2007-10-25
By "read-only permission", what do you mean? Also if you could tell us how many hard drives are in your PC. It looks like only one, but please confirm. From the look of your fstab, you only have one disk and it is formatted ext3.

The default configuration for linux is that most of the filesystem is read only for a regular user. When you log in, you are logging in as a regular user. Maybe this is where the confusion is at. In your home directory, which is located at /home/*yourusername* in the filesystem, you have read and write permissions. This design is intentional - users should not be able to mess around in the filesystem, except in their own home directory. There is really not much need for a regular user to need write permissions outside their home. Some exceptions would be for usb storage devices of course, and ubuntu usually mounts those automatically upon plugging them in with write permissions for the user (and if not it's easily rectified).

---

### Post by ScatterBrain on 2007-10-25
> **3ws said:**
> For some reason, my drive has read-only permission.
 
Here is the result of etc/fstab
 
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=35d98c14-2593-4aae-89ce-b0ada90cd630 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=457138a7-c448-4bbe-b96f-ed8ce0bafd68 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
 
I am completely new to Linux and have no idea what it means, apart from something is wrong.
 
I am sure the drive is FAT32; I used Partition Magic to partition and format.
 
Ant ideas?
 
Thanks
 
From the looks of this fstab, there are only two partitions on the drive:
[LIST=1]
[*]/dev/sda1 - which is EXT3
[*]/dev/sda5 - which is the Swap Area.[/LIST]Open a terminal, and run this command:
 
```
 
sudo fdisk -l /dev/sda

```
 
Please post what the results are.

---

### Post by jaybombalous on 2007-10-25
qpeuas has a point, what exactly are u trying to do when u get the error u only have read permissions?

To edit some files and write to other system file directories u will need to use root access, this is what the sudo command does. It allows the regular user to edit files as root with read and write capabilities.

---

### Post by 3ws on 2007-10-26
Qpieus, jaybombalous, I was trying to delete some files but couldn't. That's when I was getting the message about not having permission. However, when I tried to delete files last night I was able to do so.

It looks like the problem has gone. But I have a couple of questions. Firstly, does "errors=remount" in etc/fstab mean there is a problem? 

Secondly, does SDA in etc/fstab mean that Ubuntu thinks my HD is SCSI? Because it isn't. It is definitely IDE. I don't think the board has any SCSI interfaces (I will check this after work). Does it make a difference if its SDA or HDA?

Finally (I think), when I navigate to /media I see two folders: CDROM and CDROM0. Ubuntu sees or has named the HD CROM0. Is this important? Or is it just a name and not affect how the drive operates?

Being completely new to Linux, I am not sure if the 3 points above indicate problems or not. I appreciate your patience.

---

### Post by qpieus on 2007-10-26
This post talks a little about errors=remount-ro. Having the option in fstab does not mean there's a problem. If you find that you can't write to your home directory because it's been remounted as read only, then that would indicate the system sa some kind of error and remounted the partition - that may mean a hard disk problem.
[http://ubuntuforums.org/showthread.php?t=315850](http://ubuntuforums.org/showthread.php?t=315850)

Regarding the sda designation, this is normal for ubuntu. It gives ide drives the sd designation. I forget the reasoning behind this, but don't worry about it, it's normal. You can search around the forums to get the answer of why ubuntu does this.

Regarding the /media folder - the partition that the OS is installed on will not appear in /media. This directory is where cd drives, dvd drives, usb drives, secondary HDs, and other HD partitions (other than the root and swap partitions) get mounted. That's why I asked you if you only had one HD. If yes, then you won't see any HDs in /media directory. This is normal. If you have a third partition on your single HD, it WOULD be mounted in the /media directory as /media/sda2 (the number following the sda may vary depending on the number of partitions on the drive). Having cdrom and cdrom0 show up in /media is normal, but I forget the reason why- I think one on them is a link to the real cdrom drive. In any case, don't worry about it, it's normal.

When you said you tried to delete files and you could not, where were these files located? If they were files you created in your home directory that you found later you could not delete, that may mean the hd got remounted due to errors. That means maybe your hd is failing. If you tried to delete files NOT in your home directory and could not do it, this is normal. Regular users cannot, in general, delete files outside of your home. This is to prevent accidental deletion of important system files. To delete files outside your home, you need superuser priveledges, which in ubuntu you do by using sudo (you can search here for sudo and how to use it. It's been discussed millions of times, so I'm not going to rehash it here :))

I hope this has helped, please continue asking questions - that's how we all learn.

---

