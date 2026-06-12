---
title: "Harddrive Trouble"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Tr0n on 2007-01-23
Hi I'm pretty new to Linux, I just started using it because I got fed up with windows hanging and crashing constantly, and I was told that Ubuntu would be a good distro to try. Anyways my question is after I installed Ubuntu My slave harddrive isn't even recognized by Ubuntu, but it is by my BIOS. Does anybody have any suggestion on how to fix this. Any help will be greatly appreciated.

---

### Post by teitunge on 2007-01-23
could you paste what sudo fdisk -l (this is an L) says?

---

### Post by Tr0n on 2007-01-23
Disk /dev/hda: 33.8 GB, 33820284928 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/hdb: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2375    19077156   83  Linux
/dev/hdb2            2376        2480      843412+   5  Extended
/dev/hdb5            2376        2480      843381   82  Linux swap / Solaris
tr0n@tr0n-desktop:~$ 
 
This is what it said now I'm assuming the top is the hard drive that I can't seem to find, but this is also odd, because the HDD is not 33.8 GB, but 120.0.

---

### Post by teitunge on 2007-01-23
That IS weird. What kind of file system do you use on that harddrive? (NTFS, Fat32)?

---

### Post by Tr0n on 2007-01-23
I believe when I installed windows on it awhile back, it was in NTFS.

---

### Post by teitunge on 2007-01-23
Try to mount the harddrive to see whats up.

sudo mkdir /media/windows
sudo mount /dev/hda /media/windows/ -t ntfs -o nls=utf8,umask=0222

Now your harddrive should be mounted in the /media-folder, which you can access by entering /.

---

### Post by Ocxic on 2007-01-23
it's not the the drive isn't recognized (althogh is should be...)  just that ubuntu is not mounting the drive (ie: trying to use it)... (mounting means, to put it simply, turning the drive on and off, mounting it turns it on, and unmounting it turns it off)

to mount you drive you fisrt have to find out what its called, it'll be "hd??" the 1st question mark is the drive letter so to speak, hda will be primary master hdb primary slave etc... and the second would be the partition number.

to find out you drive names, open a terminal and type "sudo fdisk -l" this will list all of you drives and partitions.

to mount your drive the command is "sudo mount /dev/hd?? /mount/point"

change the question marks to your requirments, and change the "/mount/point" part of the command to any folder you currently have, it can be mounted anywhere you wish.

to unmount to drive it's "sudo umount /dev/hda??"

now that will mount the drive for this session only, so as soon as you reboot, you'll have to mount it again. to mount the drive automatically on boot, you have to edit the "/etc/fstab" file

this is mine:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=1297a354-556f-45fb-8c69-a449382a56a8 /               xfs     defaults        0       1
# /dev/md2
UUID=45d0cbd5-60a4-43ce-80b9-711a8baaf814 /Storage        xfs     defaults        0       2
# /dev/hda1
UUID=bda7bdb1-dc0c-4a17-a394-116203ecdb0a /boot           ext3    defaults        0       2
# /dev/md1
UUID=9f752cf3-8415-4ef7-81af-63fb984bf721 /home           xfs     defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

don't worry about the UUID part, for now. you would need to add a line that looks like this:
/dev/md1 /home           xfs     defaults        0       2

"/dev/hda1" is my drive/partition, "/home" is the mount point, "xfs" is the filesystem type, at the rest should be as it is.

post back if you need any more help.

---

### Post by Tr0n on 2007-01-23
I made the directory just fine, but the command for the mounting just gave me an error explaining proper mounting commands. It also says that you don't mount a device, but a file system. I don't know if thats important so I included it.

---

### Post by Tr0n on 2007-01-23
> **Ocxic said:**
> it's not the the drive isn't recognized (althogh is should be...)  just that ubuntu is not mounting the drive (ie: trying to use it)... (mounting means, to put it simply, turning the drive on and off, mounting it turns it on, and unmounting it turns it off)

to mount you drive you fisrt have to find out what its called, it'll be "hd??" the 1st question mark is the drive letter so to speak, hda will be primary master hdb primary slave etc... and the second would be the partition number.

to find out you drive names, open a terminal and type "sudo fdisk -l" this will list all of you drives and partitions.

to mount your drive the command is "sudo mount /dev/hd?? /mount/point"

change the question marks to your requirments, and change the "/mount/point" part of the command to any folder you currently have, it can be mounted anywhere you wish.

to unmount to drive it's "sudo umount /dev/hda??"

now that will mount the drive for this session only, so as soon as you reboot, you'll have to mount it again. to mount the drive automatically on boot, you have to edit the "/etc/fstab" file

this is mine:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=1297a354-556f-45fb-8c69-a449382a56a8 /               xfs     defaults        0       1
# /dev/md2
UUID=45d0cbd5-60a4-43ce-80b9-711a8baaf814 /Storage        xfs     defaults        0       2
# /dev/hda1
UUID=bda7bdb1-dc0c-4a17-a394-116203ecdb0a /boot           ext3    defaults        0       2
# /dev/md1
UUID=9f752cf3-8415-4ef7-81af-63fb984bf721 /home           xfs     defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

don't worry about the UUID part, for now. you would need to add a line that looks like this:
/dev/md1 /home           xfs     defaults        0       2

"/dev/hda1" is my drive/partition, "/home" is the mount point, "xfs" is the filesystem type, at the rest should be as it is.

post back if you need any more help.
I got this error:
can't find /dev/hda/mount/point in /etc/fstab or /etc/mtab
Sorry if I'm asking too many questions I would just like to use the HDD.

---

### Post by teitunge on 2007-01-23
Ah, by /mount/point he meant for example /media/windows - where /media/windows IS the mountpoint. 

with text sudo mount /dev/hda /media/windows means, superuser power-on /device/hda /where/you want the files to be listed

---

### Post by teitunge on 2007-01-23
..and you do not have to apologize for anything. the reason this forum exists, is for people to ask for questions :)

---

### Post by Tr0n on 2007-01-23
> **teitunge said:**
> Ah, by /mount/point he meant for example /media/windows - where /media/windows IS the mountpoint. 

with text sudo mount /dev/hda /media/windows means, superuser power-on /device/hda /where/you want the files to be listed
Ok I'm still getting the error now it's just saying /media/windows instead of /mount/point/. Sorry about beings so noobish, I'm still learning all this but I appreciate the help.

---

### Post by teitunge on 2007-01-23
When you write the command, do you use a space between /dev/hda and /media/windows?
write the command you are using in the terminal, here..

if you are going to learn using linux, asking questions, trialing and failing is the way to go :)
also reading [www.ubuntuguide.org](www.ubuntuguide.org) would be a nice thing to do.

---

### Post by Tr0n on 2007-01-23
> **teitunge said:**
> When you write the command, do you use a space between /dev/hda and /media/windows?
write the command you are using in the terminal, here..

if you are going to learn using linux, asking questions, trialing and failing is the way to go :)
also reading [www.ubuntuguide.org](www.ubuntuguide.org) would be a nice thing to do.
Ok, I didn't use the space, I didn't get the same error now it just says I need to specify the filesystem type, not quite sure if that means like NTFS, fat32, ext3, etc., or what and also I don't don't know how to include that in the command.

---

### Post by teitunge on 2007-01-23
sudo mount /dev/hda /media/windows/ -t ntfs -o nls=utf8,umask=0222

just remember the spacing ;)

---

### Post by Tr0n on 2007-01-23
Ok now I get this error:
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Is it possible that my HDD is just fried, or is this just as odd problem, because it seems like it shouldn't be this problematic.

---

### Post by teitunge on 2007-01-23
Are you sure the file-system is NTFS? 
I think you disc is ok :) It`s always a little tricky in the beginning.

---

### Post by teitunge on 2007-01-23
..and what does dmesg | tail  reply? 
remember the spaces between them

---

### Post by Tr0n on 2007-01-23
I'm pretty sure it is, is there anyway to check? Also, it may be possible that it was formatted I was having a friend do the installation at first, but then in the middle of it he just said he didn't feel like finishing and he didn't tell me what he had done, so it may have been formatted not sure if that makes a difference. Sorry if that was a little wordy.

---

### Post by teitunge on 2007-01-23
Ah, why didnt I think about this before.

Go to this link and add the repositories:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

after you have done that, you are going to install a program called gparted

sudo apt-get install gparted



after you have done that, write 
sudo gparted
in the terminal

that is a program close to windows' partition magic, then you will be able to check your disc.

---

### Post by Tr0n on 2007-01-23
Ok that worked well, it says that both my partition and file system are unallocated and it's giving the wrong size for my HDD it's saying it's 31.49GB when it's 120GB.

---

### Post by teitunge on 2007-01-23
Hm, that`s so weird. Do you have anything on the disc? if not, you could try to completely format it again?

---

### Post by Tr0n on 2007-01-23
There's nothing there, so I could format, how exactly would I go about that correctly, I've never been good with formatting or partitions.

---

### Post by teitunge on 2007-01-23
in gparted, right-click and "format to" - ext3 if you are only going to use it under linux..

---

### Post by Tr0n on 2007-01-23
Ok when I right click the format to option is grayed out the only thing available is new and information.

---

### Post by teitunge on 2007-01-23
Ah, that`s because there isnt a partition to format..and if you press New, that partition will be 33gb. This is a weird hardware problem. Do you have some other computer to test the harddrive on?

I`ve got to go to sleep now. It`s four in the morning over here, and I gotta get up for work in  two :P so if I wanna keep my job, I`ve got to leave you :/

Hope you will get it working.

[www.ubuntuguide.org](www.ubuntuguide.org)
and google might help you.
also check if you have LBA-support (BIOS).

---

### Post by Tr0n on 2007-01-23
Alright thank you for the help and I did get it working, all I have to do now is figure out how to get all the space recognized.

---

### Post by teitunge on 2007-01-23
It seems like a well-known problem when I surf google for it.

[http://www.serverelements.com/phpBB2/viewtopic.php?p=2404](http://www.serverelements.com/phpBB2/viewtopic.php?p=2404)
I guess the link is windows-related, but it`s probably nothing wrong with your disc, just so you know :)

Try google with 120gb+33gb+linux and maybe you`ll find something useful :)

take care mate.

---

