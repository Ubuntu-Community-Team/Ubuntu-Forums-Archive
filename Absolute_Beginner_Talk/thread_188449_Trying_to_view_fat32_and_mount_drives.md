---
title: "Trying to view fat32 and mount drives"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Kristy on 2006-06-04
Hello,

Before I begin, I have read and read and read .. my eyes hurt.  Yes, I am very new (thus I am at the newbie thread).  However as my topic says, I am trying to view my files on my hard drive.  

Ill go ahead and list what I have.  I am running a dual boot system.  I have xp and I just installed ubunto from the live disk (the lastest version).  I have a 40gig drive partitioned into 5 parts.

Disk /dev/hda: 40.8 GB, 40822161408 bytes
255 heads, 63 sectors/track, 4963 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1342    10779583+   7  HPFS/NTFS
/dev/hda2            2472        4963    20016990    f  W95 Ext'd (LBA)
/dev/hda3   *        1343        2471     9068692+  83  Linux
/dev/hda5            2525        4403    15093036    b  W95 FAT32
/dev/hda6            4404        4963     4498168+   b  W95 FAT32
/dev/hda7            2472        2524      425659+  82  Linux swap / Solaris

Partition table entries are not in disk order

Somewhere along the lines I musta have missed something.  I am desperately trying to view and be able to use files from the fat32 drives ( im under the impression I can do this).  Most of these files are data, text, pictures,mp3's and others.  I dont think I really need anything off of the partition that xp is on.  From what I understand ntfs is read only anyhow. 

I have read and read and read.  I cannot get anything to work.  I just finished the page  [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) and after the last command this is waht I have in the window ..

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/hda6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

kristy@orange-apples:~$ dmesg | tail
[4295059.572000] ibm_acpi: ec object not found
[4299048.822000] eth0: link down
[4299061.182000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[4299515.350000] cdrom: This disc doesn't have any tracks I recognize!
[4301739.330000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4301739.342000] FAT: bogus number of reserved sectors
[4301739.343000] VFS: Can't find a valid FAT filesystem on dev hda1.
[4301739.629000] NTFS-fs error (device hda1): parse_options(): Unrecognized mount option unmask.
[4301739.631000] FAT: Unrecognized mount option "unmask=000" or missing value
[4301739.632000] FAT: Unrecognized mount option "unmask=000" or missing value
kristy@orange-apples:~$


Obviously Im not doing something correct.y.  Im actually sleepy and frustrated.  
If I need to post this elsewhere or this is not the correct place, please guide me.

Can someone guide me through the steps so that I can have access to my fat32 disks.

I appricate your help.

---

### Post by Sutekh on 2006-06-04
[quote=Kristy]

...

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1342    10779583+   7  HPFS/NTFS
/dev/hda2            2472        4963    20016990    f  W95 Ext'd (LBA)
/dev/hda3   *        1343        2471     9068692+  83  Linux
/dev/hda5            2525        4403    15093036    b  W95 FAT32
/dev/hda6            4404        4963     4498168+   b  W95 FAT32
/dev/hda7            2472        2524      425659+  82  Linux swap / Solaris

...

I just finished the page  [http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows") and after the last command this is waht I have in the window ..

...

kristy@orange-apples:~$ dmesg | tail
[4295059.572000] ibm_acpi: ec object not found
[4299048.822000] eth0: link down
[4299061.182000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[4299515.350000] cdrom: This disc doesn't have any tracks I recognize!
[4301739.330000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4301739.342000] FAT: bogus number of reserved sectors
[4301739.343000] VFS: Can't find a valid FAT filesystem on dev hda1.
[4301739.629000] NTFS-fs error (device hda1): parse_options(): Unrecognized mount option **unmask**.
[4301739.631000] FAT: Unrecognized mount option "**unmask=000**" or missing value
[4301739.632000] FAT: Unrecognized mount option "**unmask=000**" or missing value
kristy@orange-apples:~$


Obviously Im not doing something correct.y. [/quote] Ok I think I pretty much know whats going wrong, but if you post your /etc/fstab mounting file
```
cat /etc/fstab
``` I will know for sure.  

I'll quickly post what I would think your /etc/fstab *should* look like.  I'll explain where you may have acceptable differences
```
[COLOR=Blue]/dev/hda1[/COLOR]    [COLOR=Red]/mnt/hda1[/COLOR]    [COLOR=SeaGreen]ntfs[/COLOR]    [COLOR=DarkOrchid]nls=utf8,umask=0222[/COLOR]    0    0
[COLOR=Blue]/dev/hda5[/COLOR]    [COLOR=Red]/mnt/hda5[/COLOR]    [COLOR=SeaGreen]vfat[/COLOR]    [COLOR=DarkOrchid]iocharset=utf8,umask=0000[/COLOR]    0    0
[COLOR=Blue]/dev/hda6[/COLOR]    [COLOR=Red]/mnt/hda6[/COLOR]    [COLOR=SeaGreen]vfat[/COLOR]   [COLOR=DarkOrchid] iocharset=utf8,umask=0000 [/COLOR]   0    0
``` - [COLOR=Blue]/dev/hda1 /dev/hda5 and /dev/hda6[/COLOR] - are the locations of the partitions you want to mount

- [COLOR=Red]/mnt/hda1 /mnt/hda5 and /mnt/hda6[/COLOR] - these are the folders where the partitions will be *mounted*.  The location of these is entirely up to you, just make sure you create the folder first, for example
```
sudo mkdir /mnt/hda1
```- [COLOR=Green]ntfs[/COLOR] and [COLOR=SeaGreen]vfat[/COLOR] - this specifies the filesystem as NTFS or as FAT

 - [COLOR=DarkOrchid]nls=utf8,umask=0222[/COLOR] - these options set the character encoding to utf8 (for special chars) and sets the **umask** (not u**n**mask).  The umask is important as it restricts the access to the drive.[COLOR=DarkOrchid]  umask=0222[/COLOR] only allows read and execute access to the partition NOT write access

 - [COLOR=DarkOrchid]iocharset=utf8,umask=0222[/COLOR] - these options set the character encoding to utf8 (for special chars) and sets the **umask**.  [COLOR=DarkOrchid]umask=0000[/COLOR] allows read, write and execute access to the partition.

---

### Post by Kristy on 2006-06-04
Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hda1       /windows        ntfs    nls=utf8,unmask=0222    0       0
/dev/hda6       /music          vfat    iocharset=utf8,unmask=000 0     0
/dev/hda5       /keeps          vfat    iocharset=utf8,unmask=000 0 0

------------------------------------------------------------------

I see it should say umask and not unmask.  I will go back through the page I followed and try once again.  I will repost again my results.  Wish me luck :KS 

Thanks.

---

### Post by Kristy on 2006-06-04
Edited lines in fstab

tried to remount with  sudo mount -a
returned with this ...

kristy@orange-apples:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: mount point  does not exist
------------------------------------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0
0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222     0       0
/dev/hda6       /music          vfat    iocharset=utf8,umask=000 0      0
/dev/hda5       /keeps          vfat    iocharset=utf8,umask=000 0      0
--------------------------------------------------------------------------------------------------

Any suggestions please.

---

### Post by Kristy on 2006-06-04
I seem to be able to view my files in the file manager.  

Is there anything else I should check so that I can be sure I have my system configured properly?  

Thanks for the help ;)

---

### Post by kokas on 2006-06-04
Does the icon to the FAT32 partition shows in your desktop like the others ? I had the same problem and thought I can see it trough file manager I can't see it in desktop and when I download a file trough firefox in the Save to box the drive doesn't show either....maybe it's because I called it /backup instead of /media/hd6 like the other partitions.....

---

### Post by dyrer on 2006-06-04
I have mounted and fat32 Harddisk but i dont have permission to delete files,
How can setup permissions

---

### Post by RRS on 2006-06-04
```
/dev/hda1 /media/windows vfat iocharset=utf8,umask=000 0
0
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
```

It would appear that you're trying to mount hda1 twice as two different directories.

Try commenting (preceed with #) one of the lines and then; ```
sudo mount -a
```

You might try this alternately with each line to compare results.

---

### Post by Kristy on 2006-06-04
It seems that it shows up twice.  Once as /media/windows and also as just /windows.

How do I get rid of the /media/windows.  I really only need the /windows.


Those ntfs should be read only correct.  I havent tried to write or del to the other 2 drives that I mounted (/keeps and /music/)

As for the other question .... There is nothing on my desktop.  Should there be?

Thanks again.  

now I am trying to find out how to install roboform.  :-k

---

### Post by kokas on 2006-06-04
I don't really now if it is supposed to show in the desktop or not but all my 2 other partitions show....

---

### Post by RRS on 2006-06-04
I believe you have to mount the drives as /media/....... for them to appear on the desktop.

To remove a directory from fstab; ```
sudo gedit /etc/fstab
```

Then you'll be able to delete the lines you don't want, or simply add # to the beginning of the line so it won't be active. Remember to click on "save" in the upper toolbar of of the gedit window before closing (took me a couple times to figure that one out)

You might want to consider starting over using [this guide]("http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only") 

Though I've found the Psychocats directions to be very good and often more indepth then most, the Krazypenquin layout makes it a little easier to copy and paste the needed commands.

I seem to recall that Roboform is installed thru Firefox as an extension rather then a standalone application

Edit; Roboform info

---

### Post by cjm5229 on 2006-06-04
I don't believe there is a Roboform available for Linux. You have to install an exe. file and then put in an extension to run it. I use InFormEnter,  nowhere  near  as good as Roboform, but does the job. Be sure and send an email to Roboform support asking for a Linux version, I have.

---

### Post by Kristy on 2006-06-04
Thanks for your help.  I deleted the other windows folder /media/windows and now it does not show up in the fstab.  However it still shows up in my file manager.  I guess it really doesnt matter.  

I also added the KDE desktop to try.  I was enjoying that desktop untill the "task bar' or the applications bar (i dont know what to call it) dissappeared.  Just gone.

I guess I will uninstall the entire KDE and reinstall?  Will that fix it?  I have also wondered how I could remove the Gnome and only use the KDe without completely reinstalling the entire Kubuntu.

Should I make another thread?

---

### Post by Kristy on 2006-06-04
InFormEnter.  Ill check on that.  I use roboform mainly for security and not having to enter huge alpha=numeric pw's into sites.  You say it isnt as good, can you compare the two, if you dont mind.

Do you always have to enter the zip code for your area everytime firefox starts up (after restarting).  Everytime I have to reenter the zip for forecastfox?

---

### Post by Ptero-4 on 2006-06-05
Welcome Kristy. You don't need to mount into the "media" folder to have the drive shown in the desktop. You only need to mount to "media" if you need it to be handled by hotplug which is usually only needed in the case of removable or optical drives, not for your internal HD.

---

