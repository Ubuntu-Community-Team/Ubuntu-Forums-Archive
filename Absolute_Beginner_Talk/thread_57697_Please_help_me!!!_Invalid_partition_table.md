---
title: "Please help me!!! Invalid partition table"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by bvilches on 2005-08-17
Hi!

I have 2 disks, one with Ubuntu and the other for data. Yesterday, I formatted the ntfs data disk into ext3 and copied a LOT of information ... everything was working perfectly


Today, I turned the computer on and the data disk (supposedly ext3) wasn't mounted. So I used the command "fdisk -l" and says

```
Disk /dev/hdc: 30.0 GB, 30020272128 bytes
16 heads, 63 sectors, 58168 cylinders
Unidades = cilindros de 1008 * 512 = 516096 bytes

**The disk /dev/hdc does not contain a valid partition table**
``` 

How do I solve this?? I'm desperate! I have valuable data I cannot afford to lose the data!

 ](*,)  ](*,)

---

### Post by crispingatiesa on 2005-08-17
post the fstab

---

### Post by bvilches on 2005-08-17
Here's the fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc1       /home/bru/MisDocumentos   ext3    defaults        1 1
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
```

---

### Post by crispingatiesa on 2005-08-17
I´m asuming you have a single partition in /dev/hdc.


substitute the line 

/dev/hdc1       /home/bru/MisDocumentos   ext3    defaults        1 1

by the line

/dev/hdc       /home/bru/MisDocumentos   ext3    defaults        0 0

Tell me if it works. Besides, check that the mount point is correct, I never liked it to mix UPPER and lower cases in files names because it tends to be confusing as hell sometimes

---

### Post by crispingatiesa on 2005-08-17
If it doesn´t work then the problem is almost certainly asscoiated with permissions to access the device )changes are that you mounted and copyed everithing yesterday as root or sudo and today the user cannnot access to it. but lets see if that works first

---

### Post by bvilches on 2005-08-17
Thank you for your reply.

I've tried changing the last "1 1" to "0 0" and then I did

sudo mount /home/bru/MisDocumentos

This is what I get:

mount: the special device /dev/hdc1 does not exist

> f it doesn´t work then the problem is almost certainly asscoiated with permissions to access the device )changes are that you mounted and copyed everithing yesterday as root or sudo and today the user cannnot access to it. 

That is true .. I've mounted it with and copied with sudo.

But my question is: what does it say "invalid partition table"? Now I'm truly desperate.

---

### Post by crispingatiesa on 2005-08-17
Actually, I think I know what is going on, by using the defaults in th e mount options you will be using the option ¨nouser¨so change the line for /dev/hdc by 

/dev/hdc1   /home/bru/MisDocumentos  ext3 user,rw  0 0

---

### Post by crispingatiesa on 2005-08-17
Below the explanation of the two numbers at the end just in case you want to know what the heck is that, 

The 5th column in /etc/fstab is the dump option. Dump checks it and uses the number to decide if a filesystem should be backed up. If it's zero, dump will ignore that filesystem. If you take a look at the example fstab, you'll notice that the 5th column is zero in most cases.

The 6th column is a fsck option. fsck looks at the number in the 6th column to determine in which order the filesystems should be checked. If it's zero, fsck won't check the filesystem.

Don´t despair, we will fix it.

---

### Post by macgyver2 on 2005-08-17
[QUOTE=bvilches]But my question is: what does it say "invalid partition table"? Now I'm truly desperate.[/QUOTE]
No need to get desperate...if it's just your partition table, your data should still be intact.

I would recommend that you just have a little patience and wait a bit longer to see if crispingatiesa or any other members of the forum community have any more ideas.  If not, though, there is an excellent utility called testdisk that you can find at [www.cgsecurity.org](www.cgsecurity.org).  I've used it in the past.  It's very good.  It basically scans the hard drive itself to actually look for the markers for your partition(s).  Then you can have it rewrite the partition table with the values it found.

---

### Post by bvilches on 2005-08-17
Thank you guys for your replies .. I REALLY appreciate them

Changing the line in fstab to "/dev/hdc1 /home/bru/MisDocumentos ext3 user,rw 0 0" didn't solve it ... but i think the line should be like this.

I'll try the app you told me

Thanks again

---

### Post by macgyver2 on 2005-08-17
[QUOTE=crispingatiesa]Actually, I think I know what is going on, by using the defaults in th e mount options you will be using the option ¨nouser¨so change the line for /dev/hdc by 

/dev/hdc1   /home/bru/MisDocumentos  ext3 user,rw  0 0[/QUOTE]
This thread has made me more interested in learning more about the inner workings of filesystems...

There's something here I don't understand.  How would the user/nouser option relate to the invalid partition table warning?  When I try to mount, as a normal user, a partition that has the "nouser" option I just get a warning that only root can do that.  Likewise, when I try to fdisk a drive as a normal user, I get a permission denied warning...nothing about the partition table.

---

### Post by macgyver2 on 2005-08-17
[QUOTE=bvilches]I'll try the app you told me[/QUOTE]
I should have fired up Synaptic and looked before...testdisk is in universe.

Also, note that you can scan the disk but don't have to write the changes right away.

---

### Post by bvilches on 2005-08-17
I'm having difficulties to run testdisk ... but here's what i could do:

I did: "sudo testdisk /list" and this is what I got:

```
Disk /dev/hda - CHS 59323 16 63 - 29198 MB, sector size=512
Disk /dev/hdc - CHS 58168 16 63 - 28629 MB, sector size=512

Disk /dev/hda - CHS 59323 16 63 - 29198 MB
 1 * Linux                    0   1  1 57837   2 63   58299822 [/]
Bad ending head
 2 E extended             57837   3  1 59319   5 63    1494045
Bad starting head
 5 L Linux Swap           57837   4  1 59319   5 63    1493982
[B]Bad starting head
Disk /dev/hdc - CHS 58168 16 63 - 28629 MB
Partition sector doesn't have the endmark 0xAA55
Run "MBR code" in TestDisk to correct it[/B]
TestDisk exited normally.
``` 

What should I do now??

Thanks once again

---

### Post by crispingatiesa on 2005-08-17
You are right, it shouldn´t give you a message like that but, It happened to me at least once. I was trying to hook a digital camera (formatted FAT32) and the message was the same message wrong file system and later invalid partition table. Funny, though, when I hooked the camera HAL recognised the device and eventhough it was usb it used the SCSI driver to try to mount it.

Anyways the problem was solve by changing the permissions in the fstab. 

In this case I think that there is various level of potential problems.

1. Permissions (that the first step)
2. Hardware (it could be as failling harddrive)
3. filesystem (is necessary to check that the fs is actually ext3 and not ext2)
4. Partitioning, It could be happening that the hd is actually partitioned in 2. Since it was a former NTFS drive chances are that it contained some Windows version before. If that is the case it might well be that the disk had a windows boot partition (windows ussually leaves as close to 8mb of the hard drive as "system" wherever that is supposed to be) that became hdc1 in its configuration when formatted and the data actually redides in hdc2

So, if testdisk doesn't find anything he should fire gparted and look what it says about the fisical drives and partition.

I think this link could be of interest to you [http://www.tldp.org/HOWTO/Partition/partition-2.html](http://www.tldp.org/HOWTO/Partition/partition-2.html)

---

### Post by bvilches on 2005-08-17
In this case, the disk didn't contain a bootable windows partition, just data ...

TestDisk found what I posted before ... but I dont know what to do with it

---

### Post by crispingatiesa on 2005-08-17
[QUOTE=bvilches]I'm having difficulties to run testdisk ... but here's what i could do:

I did: "sudo testdisk /list" and this is what I got:

```
Disk /dev/hda - CHS 59323 16 63 - 29198 MB, sector size=512
Disk /dev/hdc - CHS 58168 16 63 - 28629 MB, sector size=512

Disk /dev/hda - CHS 59323 16 63 - 29198 MB
 1 * Linux                    0   1  1 57837   2 63   58299822 [/]
Bad ending head
 2 E extended             57837   3  1 59319   5 63    1494045
Bad starting head
 5 L Linux Swap           57837   4  1 59319   5 63    1493982
[B]Bad starting head
Disk /dev/hdc - CHS 58168 16 63 - 28629 MB
Partition sector doesn't have the endmark 0xAA55
Run "MBR code" in TestDisk to correct it[/B]
TestDisk exited normally.
``` 

What should I do now??

Thanks once again[/QUOTE]


I think that the option 4 in my previous post is the correct one, this was probably your bootable windows drive. What the message is telling you is that you need to correct the MBR in the drive (the system is still thinking is a bootable drive when in fact is not)

I haven't used TestDisk before so, I don't know what the best way to deal with this using the application (What you have to do is to flag the drive off i.e. turn the boot flag off) I think you can do it from within gparted (I don't have the linux box here so I cannot check) I'm doing this from memory.

Try to run geparted and post here all the information on partition and flags of that drive. to tell you what has to be modified.

In any case something that surely will solve the whole thing is to: save your data, run gparted and delete all parttions in hdc, redefine the partitions and  format hdc as ext3 or ext2 your choice and copy the information back. But I believe you shouldn't have to do it.

CORECCTION: I ddn't see your previous post about the hdc not containing systems files. Still the solution applies though.

---

### Post by crispingatiesa on 2005-08-17
I went to the TestDisk manual and they have this example:
EXAMPLE :
Recovery of a damaged FAT boot sector

Analyse Disk 80 - CHS 3737 255 63 - 29313 MB (Enh BIOS mode)
1 * FAT32                    0   1  1   382 254 63    6152832 [LOKAL DISK]
2 E extended LBA           383   0  1  3736 254 63   53882010
Partition sector doesn't have the endmark 0xAA55
5 L FAT32                  383   1  1  3736 254 63   53881947
5 L FAT32                  383   1  1  3736 254 63   53881947

The boot sector of the logical FAT32 partition is damaged. (Windows error message is usually "The type of the file system is RAW." or "The disk in drive D is not formatted. Do you want to format it now ?") In Advanced, select this partition:

Interface Advanced
1 * FAT32                    0   1  1   382 254 63    6152832 [LOKAL DISK]
2 E extended LBA           383   0  1  3736 254 63   53882010

5 L FAT32                  383   1  1  3736 254 63   53881947
Boot sector
test_FAT :
[COLOR=Red]Partition sector doesn't have the endmark 0xAA55[/COLOR]
Backup boot sector
OK
First sectors (Boot code and partition information) are not identical.
Second sectors (cluster information) are not identical.
Third sectors (Second part of boot code) are not identical.

The backup boot sector is valid, choose "Backup BS" to copy backup boot sector over boot sector.

END EXAMPLE.

As you can see the error message is similar to yours, therefore, what is going on is what I told you in th eprvious post; the harddrive MBR still thinks is a windows drive.

---

### Post by macgyver2 on 2005-08-17
[QUOTE=crispingatiesa]As you can see the error message is similar to yours, therefore, what is going on is what I told you in th eprvious post; the harddrive MBR still thinks is a windows drive.[/QUOTE]
What do you think about the "Run 'MBR code'..." part?

Were it my disk I would personally give that a try.  It's only modifying the MBR, so even if it doesn't solve the problem, the data will still be intact...

---

### Post by crispingatiesa on 2005-08-17
I check the manual of TestDrive in [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

and this is what it says


MBR Code

If you use this command, TestDisk will overwrite the present code area of your Master Boot Record (MBR) and write the MBR signature (the Hex Word 0xAA55) to your drive's MBR sector. This might be useful if your system doesn't boot at all, and you've tried everything else! See below for details on how this new MBR will function on your system.

Beginning with version 5.7 of TestDisk, new MBR code was created specifically for TestDisk by Neil Turton (the author of mbr-install; version mbr-1.1.8 includes the source code for the TestDisk MBR). This change means that TestDisk is now 100% GPL (Open Source) code.

Versions prior to 5.7, overwrite the MBR code with a copy of the Standard Master Boot Record (similar to MS-DOS's fdisk with the 'undocumented' /MBR switch). For a fully-commented copy of this DOS Standard (or 'Classic') MBR code, see: An Examination of the Standard MBR (edited copy for CGSecurity.org; France) or: An Examination of the Standard MBR (The Starman's web site).
The TestDisk MBR

If you use TestDisk to write its MBR code to the first sector of your hard disk, it will very briefly identify itself by displaying TestDisk on the screen at boot up. The code is programmed to try booting up from whatever Boot Sector resides in the first partition of the drive. If that's not possible, you will then see a mini-menu displayed on your screen like this:

    TestDisk
    1234F:


Pressing the 1, 2, 3 or 4 keys on your keyboard, will command the MBR to try booting up from any Boot Sector(s) it finds in the 1st, 2nd, 3rd or 4th Partition Table entries in the MBR sector. Failing to do so will simply repeat the TestDisk MBR menu on your screen each time it fails to boot. If you press the F/f keys on your keyboard, the MBR will try to boot up the system from a floppy disk in your first (A:\ or /dev/fd0) floppy drive.

In most cases, once you're able to boot up your drive's original OS again, you'll want to change the TestDisk MBR code back to whatever you were using before encountering a boot problem. Note: Be sure you know exactly how to do that before proceeding; you don't want to erase your Partition Table again!


End quote.

I think it will be not advisable (unless you are ready to risk loosing ALL your info.)

What Gparted said? Lets try Gparted before doing anything drastic.

---

### Post by bvilches on 2005-08-17
Gparted says it can't read the file system ... I can't find anything to do with it

---

### Post by macgyver2 on 2005-08-17
[QUOTE=crispingatiesa]I think it will be not advisable (unless you are ready to risk loosing ALL your info.)

What Gparted said? Lets try Gparted before doing anything drastic.[/QUOTE]
Okay.  Maybe you can help me understand better what gparted (or other partitioning programs like *fdisks) actually do when you change the partitions.  Back when I had my partition table issue--that's how I found testdisk--I was hesitant to use gparted because I thought that if I didn't get the partitions exactly the same way they were, when I wrote them to the table it would cause my data to be inaccessible.  Does gparted just write to the partition table, or does it also put in those "markings" throughout the actual disk that show where partitions start and end (the markings that testdisk looks for when it's--parsing, I suppose the word is--the disk)?

---

### Post by crispingatiesa on 2005-08-17
Of course is not mounted!! That was stupid from my part.

Ok lets  do a checklist. We:

1. modify the fstab (done)
2. Try to mount as sudo (done)?
3. Run TestDisk (information about problems with MBR) I don't like that because it was running yesterday and no problem.

Lest do the following:
1, Reboot and see if you can mount the device as sudo or otherwise (we have been making a lot of changes and I'm not certain whether we should have reboot in one of the steps or not)

If it doens't work then.---> Boot using the Ubuntu CD at the prompt write: Rescue <enter>

and follow the instructions for language etc...
When you get to the partitioning tool choose manual partitioning. When the system present you with the partition table look at the hdc and write down:

How many partitions the device has.
Type of fs the device has and 
If it has a bootable flag on (will show like a lightning on the right side of the table or something similar) You should have only one lightning and in your first partition of your firts hard drive.

If the partition utility cannot tell you the fs or the number of partitions etc then we are F***  And then we will try to fix the partition table with TestDrive or something else.

---

### Post by bvilches on 2005-08-17
I was able to see the disk with the partition utility:

It has only one partition
It doesn't have the "bootable flag"
It's ext3

Now I'm more confused ...   :???:

---

### Post by crispingatiesa on 2005-08-17
[QUOTE=macgyver2]Okay.  Maybe you can help me understand better what gparted (or other partitioning programs like *fdisks) actually do when you change the partitions.  Back when I had my partition table issue--that's how I found testdisk--I was hesitant to use gparted because I thought that if I didn't get the partitions exactly the same way they were, when I wrote them to the table it would cause my data to be inaccessible.  Does gparted just write to the partition table, or does it also put in those "markings" throughout the actual disk that show where partitions start and end (the markings that testdisk looks for when it's--parsing, I suppose the word is--the disk)?[/QUOTE]

Gparted and for that matter all the  disks utilities relay in information provided by the BIOS regarding the disk geometry (cilinders head etc..) some low level utilities (like the ones provided by the manufacturers of hard drives or fdsk for Dos) will read directly from the BIOS. (I think that gparted gets it from the kernel IDE modules that gets it from the BIOS but this is irrelevant)

Look at the partition table like an index. In a simplified way , it resides in the first sector of the disk and in each IO operation the head of the drive goes there to start seeking , is like the little plastic things with capital letters in a "rolodex" (does anybody here remeber what a rolodex is :-))

To re-write the partition table is ussually a destructive operation, (you are overwriting the directions for finding the files in the fisical medium), that's way programs like fdisk force you delete a partition before creating a new table. Same reason why, by default, all the programs I know for dealing with hard drives try to "fix" the partition table when order to re-write unless you are specifically creating new partitions. (By trying to fix I mean to try to guess what is the table based on the "markins" you mention above)

Whether is this Gparted default behaviour or not, I can't tell you now because I'm not looking at a linux box and there is no manual for gparted where i'm now. I'll dig and let you know. But it should let you to try to "fix" the table. My idea was to try to get as much information from the drive as possible using gparted before doing anything drastic, but this is impossible because the fs is not recognised by the system.

---

### Post by bvilches on 2005-08-17
OK, thank you ... I will keep trying.

Please let me know if you guys come up with something else ...

BTW, what would happen if I delete the partition (without erasing the data) and create it again??

---

### Post by crispingatiesa on 2005-08-17
[QUOTE=bvilches]I was able to see the disk with the partition utility:

It has only one partition
It doesn't have the "bootable flag"
It's ext3

Now I'm more confused ...   :???:[/QUOTE]

Wow, that a tough one, so, the partition utility says that:

1. the fs is OK since it recognises it as ext3
2. The drive is not bootable (which in this case is good news)
3. It has just one partition. 

Did you have this drive in your computer before or you just put it in yesterday?

If you put it in yesterday or modified its configuration:
a) Set the BIOS to auto-detection of hardrives
b) Check that is no "jumped" as slave 

boot the computer
try this:

sudo chmod 777 /home/bru/MisDocumentos
sudo mount -v -t ext3 /dev/hdc /home/bru/MisDocumentos

The -v option will tell you everithing that is happening

---

### Post by bvilches on 2005-08-17
The disk was in the computer long ago ... I just install ubuntu yesterday and did what i told you.

I tried with the commands you told me and here's the output:

```
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by crispingatiesa on 2005-08-17
[QUOTE=bvilches]The disk was in the computer long ago ... I just install ubuntu yesterday and did what i told you.

I tried with the commands you told me and here's the output:

```
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```[/QUOTE]
What dmesg | tail says?

and post what is the ouput of:  uname -r  (his will tell you the kernel version u are using)

---

### Post by macgyver2 on 2005-08-17
[QUOTE=crispingatiesa]Whether is this Gparted default behaviour or not, I can't tell you now because I'm not looking at a linux box and there is no manual for gparted where i'm now. I'll dig and let you know.[/QUOTE]
Don't go out of your way...you've been very informative already!  I can try to find more info myself.  For some reason I keep getting error 404s when I try to get to the GNU Parted site or manual.  The man page indicated that documentation is provided in a separate parted-doc debian package, so I'm gonna grab that and read through it.

---

### Post by bvilches on 2005-08-17
dsmeg | tail :
```
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
JBD: no valid journal superblock found
EXT3-fs: error loading journal.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
``` 

uname -r :
```
2.6.10-5-386
```

---

### Post by crispingatiesa on 2005-08-17
[QUOTE=bvilches]dsmeg | tail :
```
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
JBD: no valid journal superblock found
EXT3-fs: error loading journal.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
``` 

uname -r :
```
2.6.10-5-386
```[/QUOTE]

Booom.... hdc is your cd-rom dude!!!!

Change the line is fstab by (hdc1 by  hdb1) and try again, I think we found it.

---

### Post by bvilches on 2005-08-17
[QUOTE=crispingatiesa]Booom.... hdc is your cd-rom dude!!!!

Change the line is fstab by (hdc1 by  hdb1) and try again, I think we found it.[/QUOTE]


I swear it's not.

It's hdc, look at "fdisk -l" :

```
Disk /dev/hdc: 30.0 GB, 30020272128 bytes
16 heads, 63 sectors, 58168 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

The disk /dev/hdc does not contain a valid partition table
```

---

### Post by crispingatiesa on 2005-08-17
Ok. There is something weird that dmesg is posting posting failure to open the cdrom .. well

Is this your configuration:

hard drive 1 bootable with ext3 fs and operating system.
CDrom as slave of hard drive 1
Hard drive 2 as master in the other IDE channel?

If yes:
create a dir in media with:

sudo mkdir /media/documentos

Substitute your fstab by this one

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
/dev/hdc1       /media/documentos  ext3   rw,user      0       0


try to mount the drive 
sudo mount -v  /dev/hdc1  /media/documentos

if success the we will  make a link to it in /home/MisDocumentos

---

### Post by bvilches on 2005-08-17
Well, I took a deep breath (very deep) and finally encouraged myself to re-write the MBR with testdisk



AND IT WORKED!!!!   :smile:  :smile:  :smile: 


Thank you guys for everything!!!

P.S: What do you recommend doing now? backing up everything and formatting again?

---

### Post by crispingatiesa on 2005-08-17
Thanks god congratulations....

Dude to backup is always a good suggestion.

---

### Post by macgyver2 on 2005-08-17
[QUOTE=bvilches]P.S: What do you recommend doing now? backing up everything and formatting again?[/QUOTE]
Heh heh, I second crispingatiesa...*back up your data!* :) I'm curious though...why do you want to format again?  If everything's working...wouldn't it be best to leave it be now?

---

