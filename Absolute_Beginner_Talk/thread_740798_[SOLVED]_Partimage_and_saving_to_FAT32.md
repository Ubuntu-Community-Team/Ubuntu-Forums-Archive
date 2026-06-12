---
title: "[SOLVED] Partimage and saving to FAT32"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Daveg4otu on 2008-03-31
I have  made the .ISO CD for Partimage with a  view to creating a backup image of my Ubuntu  installation.

The intention is to save the  image in one of  the FAT32 partitions on the PC(Dual boot Ubuntu and WinXP-FAT32.

Reading the  Partimage  page on Manual usage there are some warniings that  FAT32 may not be ideal...however from the look of it that page was written a long while ago....

Does anyone know  what problems there may be and if so how to get around them.

(Before anyone says it - yes I know NTFS is better  and I could change ...but  for reasons of compatability with other PCs in the house I keep to FAT32)

---

### Post by kpkeerthi on 2008-03-31
A file cannot be bigger than 4 GB if it has to be stored on a FAT32 partition. That explains why FAT32 is not ideal for backup drives as backups (tar/image files) tend to grow larger than 4 GB.

---

### Post by kellemes on 2008-03-31
> **Daveg4otu said:**
> I have  made the .ISO CD for Partimage with a  view to creating a backup image of my Ubuntu  installation.

The intention is to save the  image in one of  the FAT32 partitions on the PC(Dual boot Ubuntu and WinXP-FAT32.

Reading the  Partimage  page on Manual usage there are some warniings that  FAT32 may not be ideal...however from the look of it that page was written a long while ago....

Does anyone know  what problems there may be and if so how to get around them.

(Before anyone says it - yes I know NTFS is better  and I could change ...but  for reasons of compatability with other PCs in the house I keep to FAT32)

Patimage can split files into smaller peaces, this option is given when walking through the wizard, so keep your files smaller as 4 Gb and FAT32 will be fine.. It works for me anyway.

---

### Post by Daveg4otu on 2008-03-31
Thankyou both - have however hit a problem - CD loads fine - Xterm laods - entered "partimage" and Partimage opens.
I can select  Partition to copy with Up/Down arrows 
then  (I presume) "Enter" but no way I can get any test I type in to appear on the line "Image to be saved/restored".I have tried just about every option(CTRL, ALT,Caps etc etc)I can think of.


Am I missing something here?

Am using the Wizard and second GUI option...Keyboard obviouasly works in the Terminal but not within Partimage....

Any advice please before I use the Rscue CD as a Coaster.

---

### Post by kellemes on 2008-03-31
Try <TAB>

---

### Post by Daveg4otu on 2008-03-31
Thanks for "TAB" - that works - however still not out of the woods.

I  select the drive I wish to save an image of((sda7-Linux) and then try to fill out the destination.

The chosen  destination is on FAT32 drive is "hdb5"on the list below......(altho all the  names are **sda** etc in the CD version- the list is from fdisk whilst running ubuntu) ...... which is actually Windows drive"F"...A folder has been created there "ubackup"....

However whenever I try to then make the file  I get  either "cannot make the required file.

THe Linux  partition is 27GB of which  only 3.5 has been used - destination has approx  15GB free(I have tried  another destination  with 40+gb free - no diff).

I'm obviously doing something wrong - presumably the syntax for the destination and file image name(chosen was bakup.gz)...
any help very welcome....

Below is the fDisk results(note that when running from CD  I get **s**da etc not hda
And to be specific I want to save hda7 to hdb5

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe406e406

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4484    36017698+   c  W95 FAT32 (LBA)
/dev/hda2            4485       14946    84036015    f  W95 Ext'd (LBA)
/dev/hda5            4485       10859    51207156    b  W95 FAT32
/dev/hda6           14507       14946     3534268+  82  Linux swap / Solaris
/dev/hda7           10860       14506    29294496   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8a8d8a8

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1790    14378143+   c  W95 FAT32 (LBA)
/dev/hdb2            1791        4866    24707970    f  W95 Ext'd (LBA)
/dev/hdb5            1791        4866    24707938+   b  W95 FAT32

---

### Post by kellemes on 2008-03-31
You're working from a lifecd?
Or are you working from a GNU/Linux install?
"Image file to create/use" by default saves the image in your /home/<user> directory.. If you have enough room you can simply type the filename and let it do it's thing.. and afterwards copy the files to the FAT32 device.
Otherwise you need to mount the FAT32 device first and fill in the mount-directory used by this device..
So instead of /dev/sda1 or whatever, you need to use the mount-directory like /mnt/mylittlefatdisk or whatever directory it's mounted at.

Maybe I'm not understanding the question?

Edit: sorry.. you probably are working from cd since you can't image a mounted partition..
So basically you need to mount hdb5 and work with the mount-directory..

---

### Post by Daveg4otu on 2008-03-31
Yes - woring from the "Rescue CD".

Some slight progress.....

Chose  sda7 for the  partition to save.
Entered destination as "/mnt/sdb5/bakup.gz"
Partimage tells me "OK"- checks  system - starts copying file.

At around 10% it tells me "Disk is full- please elect a new path to continue with bakup.gz.oo1"

At this point it has apparently   copied around 10% of 3.7GB into a space that is 15gbs freespace.

Trying to select another path (EG: /mnt/hdb1/ ) produces  same disk full message.


Frustration starting to set in!

:(

---

### Post by kellemes on 2008-03-31
> **Daveg4otu said:**
> Yes - woring from the "Rescue CD".

Some slight progress.....

Chose  sda7 for the  partition to save.
Entered destination as "/mnt/sdb5/bakup.gz"
Partimage tells me "OK"- checks  system - starts copying file.

At around 10% it tells me "Disk is full- please elect a new path to continue with bakup.gz.oo1"

At this point it has apparently   copied around 10% of 3.7GB into a space that is 15gbs freespace.

Trying to select another path (EG: /mnt/hdb1/ ) produces  same disk full message.


Frustration starting to set in!

:(

This is because you have a 4 Gb limit, but apparently it's 3.7 Gb ;-)
So I guess you need to split the files in portions not larger as 3.7 Gb.
I'd try 3.5Gb just to be safe and see how it works..

---

### Post by Daveg4otu on 2008-03-31
By default the CD version of partimage states it will split into 2gb files...but  I'm only getting as far as around 350MB before it stops.

---

### Post by Daveg4otu on 2008-04-01
bump - 

Any ideas?
Please

---

### Post by Ozzz on 2008-04-03
Ok Dave - I have been in the same boat you are in and only just now got my image created w/o errors. I was hitting the same issues as you. Here is a recap of what I did to get mine to create an image.

This is what fdisk -l gave me:

sda1   ntfs      55.89GB (this is my laptop internal WinXP disk)
sdb1   fat32    72.16GB (this is my external USB drive partition 2)
sdb2   swap    2.37GB (Linux swap)
sdb3   ext3fs  74.51GB (this is my external USB partition 1 Ubuntu)

Booted using the System Rescue CD (as it has PartImage on it):
<Enter> to boot
<Enter> to use Default key mapping
typed wizard at the prompt
selected the option for Xorg-Run

In the terminal window that comes up automatically I typed the following commands:
mkdir   /ubackup
mount   /dev/sdb1  /ubackup

Richt click on the main window to get the Menus options and selected PartImage

In PartImage:
I tab down to select my sdb3 drive to backup

Under the name/path of the file I where I am going to backup the partition I typed   " /ubackup/sdb1partition" (sdb1 is my fat32 USB partition used for storage)

I elected to use gzip compression of the image file (my Ubuntu is only taking 4.88GB at this time and compression will drop this down to below the 4GB fat32 file size limit, but just in case I also elected the option to automatically size the file rather than the default size of 2037MiB)

End result:
It created by image just fine (100% this time). I then exited out of the System Rescue CD and rebooted into Ubuntu. I found the image file in the root of my USB partition exactly where I wanted it but, the file name was sdb1partition.000 - looked at the properties and all seemd fine. The reported file size was 2.12 GB, the same as the result given in PartImage. I just renamed the image to "ubuntuimage04032008.000".

It is obvious that I need to look at creating the correct filename, but at least I have n image to fall back on at this point.

Good Luck

---

