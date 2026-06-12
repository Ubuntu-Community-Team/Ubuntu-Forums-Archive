---
title: "Switching from 1HDD to 2HDD setup"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by durrell on 2007-06-12
I'm switching from a single hard drive dual boot setup to a 2 hard drive dual boot setup. What do I need to know (If anything)? And what can I do to make it less painless? I have been in Ubuntu about 2 weeks and have installed several things I'd like to avoid having to reinstall if possible, but if that's not possible then I'll deal with it.

Thanks in advance for any input. :)

Edit: And I plan to leave Windows on the current primary disk, I don't plan to reinstall Windows. Would it be easiest to use PartImage and move an entire image of my Ubuntu setup to the 2nd disk, then take it out, swap the 2 disks and make the new disk my primary and boot into Ubuntu and just edit grub to look for the Windows install on the old disk? Hopefully you guys understand that, haha.

---

### Post by dannyboy79 on 2007-06-12
this is what I suggest. as you said, leave your windows partitions alone. get the gparted livecd (it's invaluable for many many things, not just this) [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php), after burning the gparted livecd to a cd (not data but as an image) you need to boot the gparted livecd on the machine you want to do this work on, you'll need the new disk installed. you'll want to create an image using partimage (great guide: [http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)) of any partitions that are mounted and needed for your current Ubuntu to work (meaning if you have a seperate /home and / or even /boot partitions). 

you can save the part image images onto your windows partitions, make sure you have enough room. (this command will tell you sizes, df -h) I've never used compression but it does work and can be a lifesaver if you don't haev enough room.  you'll need to create mount ppoints for wherever you'll be saving the images, create them within the /mnt folder. Ensure you're chosing the correct location (mount point) when you're creatign the images. Then when you have saved all the images of each required partition (if you had more than 1, you won't need to back up /swap obviously), you'll want to use gparted within the gparted livecd to create your new partitions for your images. Try to create them exactly the same as before. put /swap in the same place etc etc, if you can't than that just means you'll haev to update the fstab file within your /etc folder. Make sure you make the new partitions on the new drive large enough of course. Once you have all the partitions created and formatted within gparted, then you again use partimage to apply/extract the images to your new hard drive's partitions. 

Then you'll have to reinstall grub on your new hard disk for it to be able to boot your new drive. If you have problems with that you can always come back and get help. When you try to boot it up, you'll want to ensure that your new ubuntu disk is the one being booted frmo the bios and that grub is installed properly on it and is pointing to the locatuion of the /boot/grub/stage1.5 and stage2 files. There are many guides on how to reinstall grub onto your master boot record and it's not hard. I know you don't need a reinstall but that's the same as installing it.

Then when you haev all that figured out and you know that your new hard drive works, then you can finally delete all teh other partitions or do whatever you want to do with the ubuntu install from the first disk (windows hard drive). Then, if you're going to stay booting the new ubuntu disk and leaving the windows disk as the seciond hard drive you may have to use the grub options called map (hd0) (hd1) and map (hd1) (hd0) so that you can chainload windows frmo grub. windows doesn't like booting from a second hard drive. 

there are many many guides for dual booting 2 hard drives my suggestion would be to read one, here ya go: [http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

let me know if I can be more help. IF after all is said and done and you can't get Grub to work or you get boot errors or whatever, DON'T REINSTALL ANYTHING. I can walk you thru and fix it, i"ll just need info. GOOD LUCK and I know you can do this, be confident.

---

### Post by durrell on 2007-06-12
Wow, what an awesome response..thanks a ton. I understand it all and feel pretty confident, but I want to make sure I backup the right partitions. Is it possible to backup my entire extended partition and move it?

[IMG]http://img.photobucket.com/albums/v157/Durrell12/partitions.png[/IMG]

That is my HDD as it stands right now.

Edit: I'm assuming I can as long as I tell PartImage to backup /dev/sda2..or should I JUST backup the ext3 partition?

---

### Post by dannyboy79 on 2007-06-12
NO, partimage can't backup extended partitions as it's not really a partition! You need to backup /dev/sda5 and that's it. then continue on from there.

---

### Post by durrell on 2007-06-12
So I'll just make a new Swap and FAT32 partition on my Linux hard disk?

---

### Post by dannyboy79 on 2007-06-12
well whatever you want to be on the new drive than yes, that doesn't mean you have to partimage if it's small like the fat32 partition, so you could always just copy and paste within nautilus frmo the /dev/sda6 to /dev/sdb2 or sdb3 for example. If you going to be creating / as /dev/sdb1 and then you'd want to have /swap next, then you'd want /dev/sdb3 to be fat32 that way swap is next to the root of your ubuntu install (which is /) that should be good. isnt' fat32 just for storage, so I was saying you only needed to backup partitions that are required for ubuntu to work properly. also, since all these are chganges, we'll deinitely have to correct your fstab.

---

### Post by durrell on 2007-06-13
So basically the GRUB will have to be edited and the fstab will have to be edited but as long as I make a PartImage of my ext3 partition and then set my Linux drive as my primary, I should be able to boot into Ubuntu..right? I'm planning to make Linux primary and Windows secondary.

I have another question too..I'm not really planning to share files between Windows and Linux..Windows will be there strictly as a backup OS in case something beyond my expertise happens to Linux and I need to get on Windows for help. Do I still need the FAT32 partition and Linux Swap or can I do without them?

Thanks. :)

---

### Post by dannyboy79 on 2007-06-13
yuou don't need the fat32 but don't delete it until you have moved it onto your ext3 partition after you get ubuntu working, or move the data onto your windows partition/hard drive. Yes you always need swap for linux although some say if you have 2GB of memory than you don't but I always use it anyway. Also, no you can edit grub! you'll need to reinstall it, it's just easier than editing it! also, as I said, if you're booting ubuntu drive as primary and have windows as secondary you have to use the map command within grub after you reinstall it. just as a precautiinary measure, backup your menu.lst file to your windows partition (using ntfs-3g) or to the fat32 partition. only after you verify that you can get into ubuntu on the secondary drive will you then move all data from fat32 to your new ext3 ubuntu partition, then delete fat32 and old swap which is on windows drive and then grow your ntfs parition for windows. Yes you'll have to edit your /etc/fstab no matter what! you can use the /dev/sdb1 as your device locations OR find out what the UUID's are by issueing this command from a livecd: ls -l /dev/disk/by-uuid/
that's if you want to use the UUID and not the /dev/hda or /dev/sda (they have been changing how the kernel interacts with IDE and SATA drives so the recent kernel upgrade to 16 changed all references from /dev/sda to /dev/hda so needless to say, this screwed tons of people from even booting! so as I said, you amy want to stick with UUID. good luck!

---

### Post by durrell on 2007-06-14
Ok so I need a definite game plan here. When the drive first comes in, I need to install and go ahead and format the disk. How does it need to be formatted? Then I need to move my ext3 partition to the new disk, then change disks by moving the new disk to master and the old disk to slave. Then boot up into Ubuntu and reinstall grub like this:

This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.

(This how to is written for Ubuntu but should work on other systems. The only thing to take note of, when you see "sudo" that will mean to you that the following command should be entered at a root terminal.)

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

Now the explanation.
Sudo grub gets you the grub shell.
Find /boot/grub/stage1 has grub locate the file stage1. What this does is tell us where grub's files are. Only a small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup. So you find the files and then you tell grub where to locate the files it will need for setup.
So root (hd?,?) tells grub it's files are on that partition.
Finally setup (hd0) tells grub to setup on hd0. When you give grub the parameter hd0 with no following value for a partition, grub will use the mbr. hd0 is the grub label for the first drive's mbr.
Quit will exit you from the grub shell.

Then I'll have to edit /etc/ftsab after I have everything booting correctly. Does that sound right?

---

### Post by dannyboy79 on 2007-06-14
> **durrell said:**
>  Ok so I need a definite game plan here. When the drive first comes in, I need to install and go ahead and format the disk. How does it need to be formatted?  
make sure you set the jumper as slave temporarily and original drive as master, boot the gparted livecd and format as Ext3. create swap as swap obviously.

> **durrell said:**
>  Then I need to move my ext3 partition to the new disk, then change disks by moving the new disk to master and the old disk to slave. 
using partimage from within the gparted livecd, you'll backup the partition we talked about and store it on your windows partition or the fat32 partiiton, where ever has enough room, I would first try to do it without compression. don't forget to create a dir and mount the partition where you want to save the partimage image to. then you'll use partimage again to extract or restore that image onto the new drive. once it's done, you close down the gparted livecd and your machine and then move the drives around to their fnal location. and reboot back into any livecd, as your done using partimage now.


> **durrell said:**
>  Then boot up into Ubuntu and reinstall grub like this:

This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.

(This how to is written for Ubuntu but should work on other systems. The only thing to take note of, when you see "sudo" that will mean to you that the following command should be entered at a root terminal.)

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

Now the explanation.
Sudo grub gets you the grub shell.
Find /boot/grub/stage1 has grub locate the file stage1. What this does is tell us where grub's files are. Only a small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup. So you find the files and then you tell grub where to locate the files it will need for setup.
So root (hd?,?) tells grub it's files are on that partition.
Finally setup (hd0) tells grub to setup on hd0. When you give grub the parameter hd0 with no following value for a partition, grub will use the mbr. hd0 is the grub label for the first drive's mbr.
Quit will exit you from the grub shell.

Then I'll have to edit /etc/ftsab after I have everything booting correctly. Does that sound right? 

Sort of, I have read that you can install grub that way but I haev also read that you have to chroot into your ubuntu install so that the menu.lst gets written in the correct location. you can try it this way first, if that doesn't work, then follow this here: [http://ubuntuforums.org/showthread.php?t=459257&highlight=chroot+into+system](http://ubuntuforums.org/showthread.php?t=459257&highlight=chroot+into+system)
it's specifically thread #4.
and no, your system won't boot because the fstab is wrong! You'll need to correct the fstab from within the livecd. you have to mount the drive to see it's contents and to edit the file just like you mount the drive from within the gparted livecd for storing the image. you;ll need to make sure that the fstab matches up with your new drive scheme which can be found out by using 
sudo fdisk -l

then you'll be able to boot into your new ubuntu install. once you know everything works, and after you have transferred over your fat32 data onto your new ext3 ubuntu install, then you can delete those other partitions from original disk and grow your ntfs partition using winxp or just make a new partiiton so you have 2.

---

