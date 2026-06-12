---
title: "Partimage - does it work w/ ext3?"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Episteme on 2006-09-03
Now that my system is up and running the way I want it... for now... I would like to copy the drive image for easier restore when I inevitably mess it up by tinkering (recemtly messed up the mbr - lesson learned).

I've learned that partimage will do this, but upon closer inspection of the discription - this program doesn't seem to include ext3 file systems (ext2, reiser, fat32, but no ext3). 

Does anyone know of a program I can use to backup sda to sdb1, and create a bootable cd for recovery?

Peace and stable code,

Sean

---

### Post by xyz on 2006-09-03
> The utility supports the ext2fs, ext3fs, ReiserFS, FAT16, FAT32, HPFS, JFS, XFS, UFS, HFS, and NTFS file systems. Note that if you are not using Linux, and want to use Parition Image on

Take a look here:
[http://www.thefreecountry.com/utilities/backupandimage.shtml](http://www.thefreecountry.com/utilities/backupandimage.shtml)

Hope this is what you're looking for!

---

### Post by xyz on 2006-09-03
Something went wrong. Didn't mean to double post. Sorry!

---

### Post by Frank Golden on 2006-09-03
> **Episteme said:**
> Now that my system is up and running the way I want it... for now... I would like to copy the drive image for easier restore when I inevitably mess it up by tinkering (recemtly messed up the mbr - lesson learned).

I've learned that partimage will do this, but upon closer inspection of the discription - this program doesn't seem to include ext3 file systems (ext2, reiser, fat32, but no ext3). 

Does anyone know of a program I can use to backup sda to sdb1, and create a bootable cd for recovery?

Peace and stable code,


Sean

partimage most certainly does do ext3 it doesn't do NTFS though.
I have used it to make an image of my Ubuntu install and I have 
it stored on a Fat32 partition on the same drive my Ubuntu is on.
I have partimage as part of a disc called the Linux SystemRescueCD a bootable CD full of useful Linux recovery/repair
utilities. 

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

The above web site even has instructions for placing SystemrescueCD on a USB flash drive and making it bootable.
That is of course if your BIOS supports booting USB flash devices. Using from a USB flash device is much quicker than a CD.

When I need to restore I just boot SystemRescueCD and point partimage in recover mode to my saved image and tell it to overwrite my damaged Ubuntu install.
I have written a How To here, based on my experiences.

[http://www.ubuntuforums.org/showthread.php?t=226402](http://www.ubuntuforums.org/showthread.php?t=226402)

Partimage only copies your used data blocks to make an image and includes a way to compress the image. If you are storing the image on a Fat32 partition it must be less than 4GB.
Although it only copies used data blocks it remembers the size of the original partition. So if you try to recover to a partition that is smaller it will fail.

I have it down to where I can screw up my Ubuntu install and restore it in 6 minutes including booting up the RescueCD.

I regularly make a new image after a big update or after I have
made significant changes. I only do this after I have proven that
the updates or changes are OK.
I maintain the latest image and the one before that. When I make a new image I delete the earliest one. So I always have two on my Fat32 storage partition. My images are around 3.32GB apiece.


Post the output of sudo fdisk -l (l is lower case L) so I can make better recomendations. This command will list the partitions on your machine.

---

### Post by xyz on 2006-09-03
What would you recommend here? Thank you, Frank.

> /dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        3187    10241437+  83  Linux
/dev/hda3            3188        9548    51094732+   b  W95 FAT32
/dev/hda4            9549        9729     1453882+   5  Extended
/dev/hda5            9549        9729     1453851   82  Linux swap / Solaris


---

### Post by Episteme on 2006-09-03
My fstab looks like this...

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4314    34652173+  83  Linux
/dev/sda2            4315        4500     1494045    5  Extended
/dev/sda5            4315        4500     1494013+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+  83  Linux


Presumably, I can take an effective image of my os from /dev/sda (to include /sda1 /sda2 and /sda5... which begs the question, why are sda3 and 4 skipped? Do they even ixist?) to /dev/hdb1/rescueimage (existing folder).

Additionally - so that I don't lose any emails in the process - I would like to change my evolution-mail folder option to /hdb1/email - but don't see that option anywhere in the evolution menu system - is there an 'evolution.conf' file I should be looking for?

I'm burning the iso for the linuxrescue now... any last minute suggestions?

---

### Post by Frank Golden on 2006-09-03
> **xyz said:**
> What would you recommend here? Thank you, Frank.From the looks of your fdisk -l output I would use
the /dev/hda3 partition as the destination for the image you make
with partimage of your /dev/sda2 Ubuntu install. If you start the imaging process and partimage reports the size of the 
image to be greater than or equal to 4GB abort the process. It will abort itself when the progress bar reaches 4GB anyway. The Fat32 4GB file limitation here is the culprit.
If that is the case resize the Fat32 partition and make a ext3
partition large enough for your backup. You cannot copy image to 
a NTFS volume nor can you make an image of your XP install
if it NTFS with partimage.

So you would boot to the System rescue CD and after the CD boots
at the prompt type [mkdir /backup] without the brackets.
The following code lines will be bracketed for clarity ignore
the brackets.
now type [mount -t vfat /dev/hda3 /backup]
this will mount your Fat32 partition to the /backup directory created
by the previous command, in RAM, so partimage can manipulate it.
Now start up partimage by typing [partimage].
On the first screen you will see your partition structure.
Using the up/down arrow keys, highlight the /dev/hda2 partition
and tab down to the next section. Leave it on the "save image to new..." option and type in the space provided
[/backup/sda2partition]. Now press F5 you will be at the next page. Here, using the arrow keys again choose your compression type. I use no compression because it is quicker. I also maintain
a Ubuntu install of around 3.3GB so it doesn't run up against the Fat32 file size limit. Use the space bar to select.
Tab down or arrow down and leave the default X's in "check partition" and "enter description". The first option will check for errors before making image and the second one will ask you to provide a description of you image at the next screen. Arrow over to the right and 
highlight "reboot" and use spacebar to select. Arrow down to the "image split mode" field and choose "into files whoose size is..." and change the default size to 4000MB. Spacebar to select.
Press F5. A dialog box will open up to type in your description,
keep it simple ubuntu backup or anything you can remember is OK.
Press enter. Partimage will take a few minutes to examine
your system, be patient. An information box will appear if there are no errors. Press enter. 
The image making process will begin. Check the progress bar and info for the size of the image if it is 4GB or greater abort now.
I don't know how to determine the exact size of the image before now. Again be patient. Depending on the amount of ram you have,
you processor speed and HDD speed this could take awhile.
I have 2 GB ram and a sata HDD so my 3.3GB image takes about 4
minutes. It is being written to the partition you mounted at the beginning (hda3). When it is done wait until the computer reboots. In my case about 30 seconds after the progress bar reaches 100%. You now have an exact byte by byte image of your Ubuntu install on you Fat32 partition waiting for the day you
mess up your Ubuntu. 

When that time comes. Boot to your System RescueCD again and
at the prompt again create a mount point in RAM.
Type [mkdir /backup] and press enter.
Mount your Fat32 partition like before type [mount -t vfat /dev/hda3 /backup] press enter.
Now start up partimage by typing [partimage] and pressing enter.
On the first screen highlight /dev/hda2 and tab down. Highlight the restore image option and press the space bar to select.
Type in the space provided [/backup/hda2partition.000]
and press F5. (notice the .000 you must include)
On the next screen a dialog will appear with the descriptive term
you entered during the image making process if it is what you want press enter. Tab or arrow down to reboot and select by pressing spacebar. Press enter, another dialog will appear 
with partition info select OK and press enter. A final box will appear asking if you are really sure you want to overwrite
/dev/hda2, press enter. Sit back and wait when progress reaches
100% program will reboot computer. Be patient. Again depending on the variables mentioned earlier this could take awhile.
When computer reboots choose your Ubuntu from the boot menu
and enjoy.:mrgreen: 

If you have partimage save the image to an external USB HDD
it will take a lot longer to save/restore than if it is on a separate partition on the same drive. You can after creating image copy it to any suitable storage device you want for safekeeping.

---

### Post by Frank Golden on 2006-09-03
> **Episteme said:**
> My fstab looks like this...

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4314    34652173+  83  Linux
/dev/sda2            4315        4500     1494045    5  Extended
/dev/sda5            4315        4500     1494013+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+  83  Linux


Presumably, I can take an effective image of my os from /dev/sda (to include /sda1 /sda2 and /sda5... which begs the question, why are sda3 and 4 skipped? Do they even ixist?) to /dev/hdb1/rescueimage (existing folder).

Additionally - so that I don't lose any emails in the process - I would like to change my evolution-mail folder option to /hdb1/email - but don't see that option anywhere in the evolution menu system - is there an 'evolution.conf' file I should be looking for?

I'm burning the iso for the linuxrescue now... any last minute suggestions?
Ok, first don't worry about the strange partition arrangement of sda. Apparently when you installed
Ubuntu the partitioner setup sda1, your Ubuntu install as a primary partition. It created an extended partition sda2 with 
sda5 as a logical drive. That is your swap.
It would be quicker (ie: more efficient) if you could resize sda1
to allow another appropriately sized ext3 partition on this drive
to store your image on. That is if your other drive hda1 is an external HDD. If not an external drive then go ahead and use it.
What is on the drive? You can create an image on a external drive but it will be slower. 
Read the info in the above post. In your case the drive/partition
you will mount after the SystemRescueCD boots would be hda1.
The partition you image/copy will be sda1 your Ubuntu install.
Don't do anything with the swap or sda2. Follow the directions above
and you should be alright.

I don't know how to move your saved e-mail folder. I don't use 
Evolution. I use Tbird. You could choose save as when you open your emails and save to a folder on one of your other drives. That is assuming they are mounted when you are in Ubuntu.

---

### Post by xyz on 2006-09-04
Thank you, Frank, you took a lot of time explaining and it is very clear and most helpful.

---

### Post by Episteme on 2006-09-04
Thanks for the advice, Frank. I ended up ln -s the email folder to my hdb1/emails/.evolution (or, something like that) - that solved the email issue.

I've also managed to backup sda1 to hdb1 nicely.  So, again, thanks for the advice - much appreciated.

Peace and stable code,

Sean

---

### Post by xyz on 2006-09-11
Hi-
Now that I've time to really dig into your personalized HowTo, I'm glad to see that I even understand what's going on, not just the "Copy/Paste" type of procedure...thanks to your great explanation.

Just a couple of things that I would just do as you said; however I wouln't understand what I'm doing:
 
-at the second line of 1st paragraph:
> the /dev/hda3 partition as the destination for the image you make
with partimage of your **/dev/sda**buntu instal

-and at about 1/3rd of your 2nd paragraph:

> Leave it on the "save image to new..." option and type in the space provided
[**/backup/sda2partition**].

_Why do you talk about **/sda2** when it's /hda2 all along..._if you know what I mean?
I'll post this again so you'll have it handy:

[/quote]/dev/hda1 * 1 1912 15358108+ 7 HPFS/NTFS
/dev/hda2 1913 3187 10241437+ 83 Linux
/dev/hda3 3188 9548 51094732+ b W95 FAT32
/dev/hda4 9549 9729 1453882+ 5 Extended
/dev/hda5 9549 9729 1453851 82 Linux swap / Solaris[/quote]

Thanks for taking a look at this!

---

### Post by xyz on 2006-09-12
Well, I'm wondering why it didn't work. What did I do wrong?
Thanks for reading.

At the SysRescue boot prompt, I typed:
```
mkdir /backup
```
and then:
```
mount -t vfat /dev/hda3/backup
```
and it said:
> could not find kernel image...

then Ctrl+Alt+Delete to reboot and I retyped the 1st command line and it said again:

> could not find kernel image: mkdir

I let it boot the regular way and at the root prompt typed:
```
partimage
```
and went through the process as if nothing happened til I got to the dialog box asking for a description. I typed "backup" and waited.

After a while, it said:
> cannot create temp file [/backup/pi094a8f16.tmpPlease, check there is enough space and you have access rights

I cancelled!

Then, in a console:
```
df -h
```

> /dev/hda2             9.7G  3.8G  5.4G  42% /


I'm allowed 4G so I should be fine there!!:confused:

```
mount
``` 
> /dev/hda2 on / type ext3 (rw,errors=remount-ro)


Is there an "access rights" problem on hda2?
What can I do about this?

---

### Post by xyz on 2006-09-13
I was able to free more space on hda2. Would that help?
> root@luser:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             9.7G  2.4G  6.8G  26% /

Now: 2.4G  Before: 3.8G

---

