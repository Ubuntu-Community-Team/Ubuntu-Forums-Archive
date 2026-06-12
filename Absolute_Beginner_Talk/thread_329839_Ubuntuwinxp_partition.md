---
title: "Ubuntu/winxp partition"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Sportingfan on 2007-01-02
Hi,

i'm willing to install ubuntu for the first time. But, i don't want to format my hd because of my mp3's wich are on it. 
Currently, my HD has 2 partitions (both ntfs):
- first with only mp3's on it (30 gb)
- second witch win xp and software installation files (90 gb)

I want to make a new Ubuntu partition and i want to be able to listen to my music when using ubuntu.
And at last, i actually want to extend my music partition because it is almost full.

Can somebody tell me what to do?!

---

### Post by bernied on 2007-01-02
Windows is usually on the first partition - so be careful with this configuration. That first ntfs may be involved in the Windows boot process. Is it really only mp3s? Are there any Windows system files on it?

If it's not part of the Windows boot process (probably the case), then I suggest doing the following using gparted:
- reduce size of Windows ntfs partition, so that new space is created at the end of the disk
- create new partition for mp3s, in the new space
- format new partition with vfat

then,
- copy the mp3s
- wipe partition 1 and put a ubuntu-friendly filesystem on it (gparted again).
- install, yay

---

### Post by bartbes on 2007-01-02
You can partition on the live-cd with a program GParted or QtParted (i don't know which of those two), if you have space left it's easy, but if you don't you have to resize. Before you do this make a backup! And as you told your mp3 partition is the first, and the windows the seconf, you have to move the win partition to the 'end' of the drive, so you have space to expand the drive, again, backup!
If you don't understand it, just ask.

---

### Post by Sportingfan on 2007-01-02
> **bernied said:**
> Windows is usually on the first partition - so be careful with this configuration. That first ntfs may be involved in the Windows boot process. Is it really only mp3s? Are there any Windows system files on it?

If it's not part of the Windows boot process (probably the case), then I suggest doing the following using gparted:
- reduce size of Windows ntfs partition, so that new space is created at the end of the disk
- create new partition for mp3s, in the new space
- format new partition with vfat

then,
- copy the mp3s
- wipe partition 1 and put a ubuntu-friendly filesystem on it (gparted again).
- install, yay

This sounds like a nice solution. But how do i reduce the size of my win partition?
What is vfat?
To wich filesystem should i partition my new mp3 partition? FAT32?
And what is yay?

THX!

---

### Post by bernied on 2007-01-02
Gparted is a graphical program that should give you the option of reducing the size of your windows partition. Try it - as bartbes says it should be on your ubuntu live cd (if you don't have this   you will need it for the install anyway)

vfat is FAT16 or FAT32 - FAT32 works well for sharing between windows and linux 

yay is an english slang for celebration - hooray, happy days, etc

---

### Post by huntingbear on 2007-01-02
"yay is an english slang for celebration - tard"



lol!

---

### Post by logos34 on 2007-01-02
Your main ntfs partition (where the mbr likely is) has to be on the left side/end (as seen in the gparted table, which is actually the beginning of the disk) in order to shrink it and both expand the mp3 one AND install ubuntu on freedup (unallocated) space.  If Gparted on the Ubuntu livecd can't handle it, get the gparted livecd. 

[http://gparted.sourceforge.net](http://gparted.sourceforge.net)
[http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.3-0.iso?modtime=1165447791&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.3-0.iso?modtime=1165447791&big_mirror=0)

Start here and look for howtos on installing and dual booting:

[https://help.ubuntu.com/community/UserDocumentation](https://help.ubuntu.com/community/UserDocumentation)
[http://www.psychocats.net](http://www.psychocats.net)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

The only thing I would add is that you'll need to create a minimun of two partitions for linux--one ext3 for / (root) and a /swap of at least 500MB.  10GB minimum is recommended for /.  You can have at most 4 primary partitions on a disk, so that leaves two for linux.  I would advise creating an extended partition and then subdividing it up for your /swap and possibly a separate /documents or /home.  If you just want to be able to listen to your mp3's linux you don't need to worry about reformatting it as vfat (unless you plan to rip cds in linux and write them to that partition). 

Make sure to verify the checksum/md5sum before you burn the Ubuntu livecd image to cd.  Then burn it at 4X speed or slower.  When you boot from the cd for the first time do the cd integrity test and memtest86.  These steps could save you a lot of frustration.

Before you start partitioning, make sure to defragment your windows volumes two or three times if necessary to compact it as much as possible.  Also, run chkdsk/error checking with both the repair options enabled.  If you can't get through the install using the Ubuntu livecd, then try the alternate install cd (text based).

---

### Post by fsando on 2007-01-02
One additional advice:
I just installed ubuntu a few days ago on an xp-machine with 5 ntfs partitions (dual boot). I realized that ubuntu does not write to ntfs disks, so I changed the file system to fat32 my main data partition (without deleting).
After that something went terribly wrong, the numbering of the partitions changed and
Grub came with 'Error 17' instead of booting. All attempts to repair the system with the install CD failed. Fortunately I found a tools CD that let me boot into somewhere where I had access to fdisk (fdisk /mbr) to repair and boot to windows. Then I had to do a complete reinstall of ubuntu.
So my advice: make all necessary changes to the harddisk before installing ubuntu.

---

### Post by Frank Golden on 2007-01-02
Hi All,
Please have a look here

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

This is the definitive guide to dual booting XP/Ubuntu.

Personally, If you have a way to backup those MP3 files
and you should (external HD etc.), I would do that and backup
your data on XP. Then wipe your drive and reinstall XP at the beginning of drive. Where it prefers to be located.

Then use the diskmgmt utility in XP to delete the second partition and create a smaller ntfs
one (still large enough for those MP3 files) and leave enough free space (unallocated) at the end for Ubuntu. Ubuntu can function with as little as 4 GB but I prefer at least 10 GB.
You can then install Ubuntu to the unallocated space.. If you use the alternate CD (prefered) that the above tutorial was written for, when you get to the partitioner
step choose the "install to the largest free space" option. This will be the unallocated
space at the end of drive. The installer will automatically format a ext3 partition for
Ubuntu and a much smaller Linux swap partition.

Copy your MP3 files back to your drive in the new partition created for them.

Ubuntu can access them read only.

I use XMMS in Ubuntu to play mine. You need to install XMMS using Synaptic Package
installer as it is not installed by default. Use the search feature in Synaptic.
You can use Automatix2 to install the non free codecs.

[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29)

Choose your exact distro.

---

### Post by tagginannie on 2007-01-02
> **Sportingfan said:**
> Hi,

i'm willing to install ubuntu for the first time. But, i don't want to format my hd because of my mp3's wich are on it. 
Currently, my HD has 2 partitions (both ntfs):
- first with only mp3's on it (30 gb)
- second witch win xp and software installation files (90 gb)

I want to make a new Ubuntu partition and i want to be able to listen to my music when using ubuntu.
And at last, i actually want to extend my music partition because it is almost full.

Can somebody tell me what to do?!

Hi  Sportingfan

Fist make sure that you have you will have enough room on your HD,  judging by your post it looks like you have a almost full 120 GB drive? Ubuntu needs 6-9GB of space, If you can make some room for Ubuntu than boot up the live CD and when Ubuntu gets done loading click on the install icon. After you answer a few simple questions your keyboard and language and detects your network and you hardware it is time for the fun partitioning. Just choose "use existing free space"


BTW, if you have dial up it will take more work getting connected to your ISP because Ubuntu geared more
for high speed users, people who don't yet have DSL or any type of high speed connection or it is not yet available where they live it will take a little more work at getting connected to their ISP.



Hope this helps
Suzy

---

### Post by Sportingfan on 2007-01-03
Hi,

At this moment, i just installed Ubuntu. But how can i get back in Win xp? 
Do i have to install something for dual boot?

I created an extra partition for my music, but ubuntu does not seem to find it.
The partition tree looks like:

-part 1 (ubuntu)
-part 2 includes:
   -part 4 win xp (ntfs)
   -part 5 music only (fat32)

thx for your help.

---

### Post by tagginannie on 2007-01-03
> **Sportingfan said:**
> Hi,

At this moment, i just installed Ubuntu. But how can i get back in Win xp? 
Do i have to install something for dual boot?

I created an extra partition for my music, but ubuntu does not seem to find it.
The partition tree looks like:

-part 1 (ubuntu)
-part 2 includes:
   -part 4 win xp (ntfs)
   -part 5 music only (fat32)

thx for your help.

yes there is, in Linux it is called grub. To choose witch OS you want reboot and when you see "Grub Stage 1.5" in lthe upper left hand coner of your screen push "ESC". As for FAT 32 that is going to be tricky, this thread may help you  
[http://www.ubuntuforums.org/showthread.php?t=102220&highlight=change+permissions]("http://www.ubuntuforums.org/showthread.php?t=102220&highlight=change+permissions")

Suzy

---

### Post by Sportingfan on 2007-01-03
> **tagginannie said:**
> yes there is, in Linux it is called grub. To choose witch OS you want reboot and when you see "Grub Stage 1.5" in lthe upper left hand coner of your screen push "ESC". As for FAT 32 that is going to be tricky, this thread may help you  
[http://www.ubuntuforums.org/showthread.php?t=102220&highlight=change+permissions]("http://www.ubuntuforums.org/showthread.php?t=102220&highlight=change+permissions")

Suzy

I tried it and the result is that i get a screen with the following options:

-Ubuntu, kernel 2.6.17.10 generic
-Ubuntu, kernel 2.6.17.10 generic (recovery)
-Ubuntu memtest86+

---

### Post by Bartender on 2007-01-03
> **Sportingfan said:**
> The partition tree looks like:

-part 1 (ubuntu)
-part 2 includes:
   -part 4 win xp (ntfs)
   -part 5 music only (fat32)



sportfan, something isn't making sense here.  Are you saying that ubuntu is now the first partition on your HDD?  

Can you explain exactly how you created the above partitions?  Did you use the Ubuntu install CD, or a partitioning tool like Partition Magic?  What do you mean by "Part 2"?

I hope I'm wrong, but it looks to me like you may have overwritten your XP installation.  In 99.9% of the cases, we leave XP at the front of the HDD, create room for Ubuntu behind it, and go from there.

Do you have a thumb drive?  One of the quickest ways to get to the bottom of this might be posting a screenshot.

Toss your Ubuntu LiveCD back in the optical drive and reboot.  When you get to the Ubuntu desktop, plug in your thumb drive.  If it's recognized an icon should pop up in a few seconds.  Click on System>Administration and find Gnome Partitioning.  Start that.  Go to Applications > Accessories> take Screenshot.  Take the shot.  If the thumb drive was recognized it'll be in the list of places to save the screenshot.  Save it, get out of the LiveCD, attach the screenshot to a post.

---

### Post by Sportingfan on 2007-01-03
Here is the screenshot i made:

[IMG]http://users.telenet.be/Desertfox/Screenshot.png[/IMG]

Ubuntu is on the first one, win xp 2nd and my music 3th.

Thx!

---

### Post by Frank Golden on 2007-01-03
> **Sportingfan said:**
> Here is the screenshot i made:

[IMG]http://users.telenet.be/Desertfox/Screenshot.png[/IMG]

Ubuntu is on the first one, win xp 2nd and my music 3th.

Thx!
All you need to do is edit /boot/grub/menu.lst and add an entry for XP.
can you please post your /boot/grub/menu.lst file
as well as the output of sudo fdisk -l
this last will show the partition structure.

Below is a valid entry for XP pro for your setup it should be inserted into your menu.lst file
after the line that reads ## ## End Default Options ##
 

title		Microsoft Windows XP Professional
root		(hd0,4)
savedefault
makeactive
chainloader	+1

Note the root (hd0,4)
Even though your XP partition is /dev/hda5, grub numbering is (hd0,4) the grub partition number is always one number less than
the /dev/hdx convention. 

Backup your menu.lst file first though.

All of this is much more clearly explained in the guide I linked you to earlier.

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

---

### Post by Sportingfan on 2007-01-04
Hi,

my [http://users.telenet.be/Desertfox/menu.lst]("http://users.telenet.be/Desertfox/menu.lst")

and output of sudo fdisk -l:

Schijf /dev/hda: 120.0 GB, 120034123776 bytes
255 koppen, 63 sectoren/spoor, 14593 cylinders
Eenheden = cylinders van 16065 * 512 = 8225280 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hda1   *           1        3824    30716248+  83  Linux
/dev/hda2            3825       14592    86493960    f  W95 Ext'd (LBA)
/dev/hda5            3825        9208    43246948+   7  HPFS/NTFS
/dev/hda6            9209       14592    43246948+   b  W95 FAT32

Thx

---

### Post by Sportingfan on 2007-01-04
I changed the menu.lst as you adviced.

Now, win xp is in the list of os's wich i can boot but when i choose it, i get an error:

invalid device requested.

What must i do?

---

### Post by Frank Golden on 2007-01-04
> **Sportingfan said:**
> I changed the menu.lst as you adviced.

Now, win xp is in the list of os's wich i can boot but when i choose it, i get an error:

invalid device requested.

What must i do?
Ok first what version of XP do you have? Pro or Home.
If you have Home change the entry to XP Home.

To mount your Fat32 partition first create a directory for it in /media

sudo mkdir /media/xxx 

where xxx is any short name you want. I call mine 
share. You could call yours MP3 for example.

next sudo gedit /etc/fstab and add this line to end of file

/dev/hda6       /media/xxx    vfat    iocharset=utf8,umask=000    0       0

where xxx is the name you chose for your mount point when you made the directory.
Save changes. Reboot.
When you reboot a nice shiny icon should be on your desktop named xxx.
Because of the fstab entry you should have read/write access to your MP3.
This is also a good place to place files you want to share with your XP install.

/media is a special directory. When a volume is mounted there it automatically places
an icon on the desktop when you boot Ubuntu.

I noticed from the output of fdisk -l that your Ubuntu is ?German?
You may have to adjust the above entry accordingly though I doubt it.

If you still get the error about wrong device while trying to boot XP
you may very well have messed up XP.
I would be surprised if you got it working as XP PREFERS to be at the physical beginning of drive. Something about being past the 1048 sector or such.

If this is the case then reinstall XP to the /dev/hda1 and leave the space formerly taken up by XP unallocated. When you install Ubuntu have the partitioner use the largest free space. It will format it ext3 and create a swap space also.
When grub installs it will overwrite the MBR and XP will automatically have an entry
with Ubuntu.

I really hope that the problem is that you have XP Home and not Pro.
I assumed Pro when I posted the menu.lst entry.
Except for the location of root that was the entry from my grub.

[COLOR="Red"]UPDATE: I just changed my menu.lst to XP Home and it made no difference.
My guess is that when you moved your XP install past the 1048 cylinder boundary you indeed made it unbootable.
Looks like you have some work to do.[/COLOR]

---

### Post by Malac on 2007-01-04
Is it just me but from the gparted screenie he doesn't appear to have a /swap partition?
And also XP/ntfs filesystem is on an extended partition.
To the best of my knowledge XP will not boot off an extended partition at all.
I suspect as mentioned earlier that XP had boot files on /dev/hda1 and these have been erased by the Ubuntu install.
The only sure way to restore this, that I know of, is with the XP CD "Recovery Console" or "Repair Existing Setup" option after reformatting /dev/hda1 to fat32.

---

### Post by CroEragon on 2007-01-04
Just one note to this. I dont see point of making fat32 partition for music. I have XP and Ubuntu on sata drive and 2 partitions on second hdd drive. First of all Ubuntu can read ntfs partitions (cant write them) so you can access your music if it is ntfs(after mounting of course ). Second, all my partitions are ntfs (except Ubuntu witch is ext3 and swap) and i can write on any partition with help of ntfs-3g. I know you'll say it's beta, can be buggy and so on, but i didnt have any problem with using it so far.
It is much better solution than fat32 partition. fat32 is easily fragmented. So it slows down computer.

---

### Post by Frank Golden on 2007-01-04
> **CroEragon said:**
> Just one note to this. I dont see point of making fat32 partition for music. I have XP and Ubuntu on sata drive and 2 partitions on second hdd drive. First of all Ubuntu can read ntfs partitions (cant write them) so you can access your music if it is ntfs(after mounting of course ). Second, all my partitions are ntfs (except Ubuntu witch is ext3 and swap) and i can write on any partition with help of ntfs-3g. I know you'll say it's beta, can be buggy and so on, but i didnt have any problem with using it so far.
It is much better solution than fat32 partition. fat32 is easily fragmented. So it slows down computer.
How fragmented will it get if you only read from it? For instance playing MP3 files.

---

### Post by CroEragon on 2007-01-04
> **Frank Golden said:**
> How fragmented will it get if you only read from it? For instance playing MP3 files.

I wrote it as general note to anyone with same question. Some people use fat32 for documents and other stuff. And if you use it long time with minimum writing it will still get fragmented. Not too much but will.
Also guy said that he would like to expand existing partition so we can assume that he plans to expand his music collection. That includes writing, correct me if im wrong.
And if he will ONLY read from it he can still use ntfs because Ubuntu can read ntfs.

---

### Post by Frank Golden on 2007-01-04
> **CroEragon said:**
> I wrote it as general note to anyone with same question. Some people use fat32 for documents and other stuff. And if you use it long time with minimum writing it will still get fragmented. Not too much but will.
Also guy said that he would like to expand existing partition so we can assume that he plans to expand his music collection. That includes writing, correct me if im wrong.
And if he will ONLY read from it he can still use ntfs because Ubuntu can read ntfs.
Your right. I use my shared fat32 partition for my MP3 collection, but I also use it to share files between XP and Ubuntu, PCLinuxOs .93 and Zenwalk 3.0. I figure I can defrag from XP when needed.

---

### Post by Sportingfan on 2007-01-04
> **Frank Golden said:**
> Ok first what version of XP do you have? Pro or Home.
I
...

I noticed from the output of fdisk -l that your Ubuntu is ?German?
You may have to adjust the above entry accordingly though I doubt it.

If you still get the error about wrong device while trying to boot XP
you may very well have messed up XP.
I would be surprised if you got it working as XP PREFERS to be at the physical beginning of drive. Something about being past the 1048 sector or such.



First, it is win xp pro.

Second, it's dutch, not german.;) 

I still can't get to my music, the folder has been created but is still empty.

Before i installed Ubuntu on the first partition, i could still boot win xp while it allready wassent at the beginning of the drive and it was at an extended partition. (it was where it is now)

About the swap partition, i choose to create a swap file after installing ubuntu, i thought it was the better solution.

---

### Post by Malac on 2007-01-04
> **Sportingfan said:**
> 
Before i installed Ubuntu on the first partition, i could still boot win xp while it allready wassent at the beginning of the drive and it was at an extended partition. (it was where it is now)


The (hidden) boot files would still be on /dev/hda1 even though all the other Windows/System files would be on the extended partition. XP _cannot_ boot directly off an extended partition I've checked as I wasn't sure.
Booting would use the boot files ntldr, boot.ini, etc. on the first partition to boot the system then pass control over to the extended partition files to carry on the boot sequence. Without those files XP will not boot.

---

### Post by Sportingfan on 2007-01-04
> **Malac said:**
> The (hidden) boot files would still be on /dev/hda1 even though all the other Windows/System files would be on the extended partition. XP _cannot_ boot directly off an extended partition I've checked as I wasn't sure.
Booting would use the boot files ntldr, boot.ini, etc. on the first partition to boot the system then pass control over to the extended partition files to carry on the boot sequence. Without those files XP will not boot.

Then issen't it possible to put those files back in place?!

Else i think i will have to install win xp on the first partition (what i don't like to do because all the updates), get the most important files from partition 4 to partition 1 and install ubuntu on 4.  :(

---

### Post by Frank Golden on 2007-01-04
> **Sportingfan said:**
> Then issen't it possible to put those files back in place?!

Else i think i will have to install win xp on the first partition (what i don't like to do because all the updates), get the most important files from partition 4 to partition 1 and install ubuntu on 4.  :(
Even though you may not be able to boot XP you should be able to mount the XP partition
in Ubuntu and recover any important files. To mount create a directory in /media
like before call it /media/hda5 then type [COLOR="Red"]sudo mount -t ntfs /dev/hda5 /media/hda5[/COLOR] If you don't get a desktop icon go to /media/hda5 and click.
If you have room to put files in your Fat32 partition for safe keeping put them there.
I know you can't see the contents of your Fat32 partition right now, we must not have the 
correct entry in fstab. We can fix that later after we get everything sorted out. However we can still access it temporarilly type [COLOR="red"]sudo mkdir /media/hda6[/COLOR] Then type [COLOR="red"]sudo mount -t vfat /dev/hda6 /media/hda6[/COLOR] This will mount your Fat32 partition. Again if you don't have a desktop icon (you probably won't) type [COLOR="red"]gksudo nautilus /media/hda6[/COLOR] this will open up your file browser to the Fat32 partition with full read/write priveleges temporarily, allowing you to copy your important XP files.

I don't see any other way out.

BTW sorry about the language but I knew it wasn't english.

---

### Post by Sportingfan on 2007-01-04
This sounds like a good "solution" to me.

For some reason, i'm not the admin. I cannot browse threw the /media/hda5 folder i created.
On the other hand, when i type sudo dir /media/hda5 into the terminal, i get to see all the files in there.
If i have to search everything using the terminal, it is gonna take me a long long time.:( 

If this eventually works, i m gonna get myself an external HD to put all shared files on and then format my other drive to start all over. :)

Edit:

i got it working by: gksudo nautilis /media/hda5

reEdit:

I don't seem to have rights to write on media/hda6.
What can i do about it?

rereEdit:

i got it working.

Now im gonna get that extarnal hd and have some fun with formatting and reinstalling.

Thx guys!

---

### Post by Duck2006 on 2007-01-04
One last foot note did you get windoze to boot if not you will have to remap in grub to do so

---

### Post by Sportingfan on 2007-01-04
No i cannot boot windows.
Like somebody said, you need the windows boot files to be on the first partition. These files were deleted when Ubuntu formatted the partition before installation.

---

### Post by Malac on 2007-01-04
> **Sportingfan said:**
> No i cannot boot windows.
Like somebody said, you need the windows boot files to be on the first partition. These files were deleted when Ubuntu formatted the partition before installation.
To repair the Existing Windows XP installation. 
Try booting of the install CD and go all the way to a blue screen that gives you 3 choices:
1/. Fresh Install
2/. Repair with Recovery Console
3/. Re-install Repair
I can't remember the exact wording but you need the Recovery Console option.
It will load a few files, don't panic these are temporary.
Then run ```
fixboot
``` and then ```
fixmbr
```This should re-do the loader files.
Exit and reboot.
If that doesn't work try the full repair install.

I would suggest if you don't want to reformat your drive change partition 1 (/dev/hda1) to be say 500MB and just use it to boot off. And "insert" a new partition directly after it to take up the free space. Use this one for Ubuntu.

Hope this helps.

---

### Post by Frank Golden on 2007-01-04
> **Malac said:**
> To repair the Existing Windows XP installation. 
Try booting of the install CD and go all the way to a blue screen that gives you 3 choices:
1/. Fresh Install
2/. Repair with Recovery Console
3/. Re-install Repair
I can't remember the exact wording but you need the Recovery Console option.
It will load a few files, don't panic these are temporary.
Then run ```
fixboot
``` and then ```
fixmbr
```This should re-do the loader files.
Exit and reboot.
If that doesn't work try the full repair install.

I would suggest if you don't want to reformat your drive change partition 1 (/dev/hda1) to be say 500MB and just use it to boot off. And "insert" a new partition directly after it to take up the free space. Use this one for Ubuntu.

Hope this helps.

This will overwrite grub (which is presently on the MBR) and then you won't be able to access Ubuntu. And it still may not allow XP to boot. The files mentioned are in XP on the root of C:\ not in the MBR.

If you are going to backup your data to an external HDD (this is a good idea anyway).
I would completely format removing all partitions and then use the tool you used before
create a XP partition at the beginnng of drive. Install XP and patch and install drivers.
Next create a partition large enough for your MP3 files (Fat32) bearing in mind the 
advice about fragmentation. Leave the rest of the drive unallocated.
Now install Ubuntu to the unallocated free space using the option in the installer
to install to the largest free space. Ubuntu will create a ext3 / and a swap automatically and install itself. When grub installs it will detect XP and create a boot menu item for it.
Grub stage 1 will overwrite the MBR and point to /boot/grub/menu.lst which will present you with a menu to choose OS. This time choosing XP should boot XP.

After you customize everything copy your MP3 files to you fat32 storage area.

Ask here or PM me and I will help you get Ubuntu to automount your Fat32.
Better yet use the guide I linked to earlier.

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

This guide is great.

---

