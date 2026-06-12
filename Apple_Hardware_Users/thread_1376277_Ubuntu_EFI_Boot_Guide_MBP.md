---
title: "Ubuntu EFI Boot Guide MBP"
date: 2010-01-09
forum: Apple Hardware Users
---

### Post by Fox11 on 2010-01-09
How I booted Ubuntu from a USB thumb drive on a Macbook Pro 3,1 Santa Rosa

Introduction

There's very little information on booting Ubuntu from a USB drive on Apple computers, and the information that is out there is scattered all over message boards and wikis and help sites. This is how I got a full install of Ubuntu running off of a 4GB Lexar Jumpdrive USB flash drive / USB stick / thumb drive- all of the steps/information in one place for the next person who attempts to do something similar. -Fox

These steps might not be perfect, or always completely efficient, but this is exactly what I did.

**These steps are shared for informational purposes only. Don't attempt any of this until having read everything through, and understanding most of what is done. Before considering following the steps I took, I'd strongly suggest backing up all data on both your internal hard drive and external USB device (especially the USB device, as my method erases everything off of the USB drive).**

The necessary files are attached in the UbuntuMBP_EFI_BOOT_PACK.zip file I put together.

1. Burn Ubuntu Disc

-Download Ubuntu from: [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
(I've tested both 9.10-Karmic Koala and 9.04-Jaunty Jackalope: both work)
-Burn the .iso image to a blank CD (or DVD, as I did since I couldn't find any blank CD-Rs lying around)
(To do this on a mac, open up Disk Utility-in the /Applications/Utilities folder. Drag the .iso to the sidebar- if it isn't already there- and select it. Insert the blank disc. Click the "Burn" icon in the top of the window. and make sure "verify burned data" is selected. Burn the disc.)
-Re-insert burned Ubuntu disc and shut down.

2. Setup USB Drive

*Connect the USB drive and confirm that the Ubuntu disc is in the computer*
-Turn the computer back on- after hearing the Apple "dong" sound, hold down the "C" key to boot from the CD/DVD drive. This takes a little while.
-Eventually, an Ubuntu menu should appear. Choose "Try Ubuntu" and boot into the OS off of the CD.
-Once the OS has fired up, open gparted (Menubar: System->Administration->gparted).
*This next step erases all data on the USB drive*
-Select the USB drive from the drop-down menu on the right (in my case, /dev/sdb). Make sure the right drive is selected. Right-click and delete all partitions on the drive (might need to 'unmount' these first). Apply the delete operation(s) by clicking- Edit->Apply all operations. Now the whole drive should be marked "unallocated."
-Create a new FAT32 partition, 32MB in size. (Right-click 'unallocated' space and choose &#8220;New...&#8221;. Choose &#8220;Primary&#8221;. File system: &#8220;FAT32&#8221;. Label: Whatever (I used &#8220;EFI Bootloader&#8221; to keep organized, name will be erased during install). New size is 32MB) This will become the EFI Boot partition.
-Create an ext4 partition (at least 2.5GB in size, in my case, 3GB). (Choose "Primary". File system: "ext4". Label: Whatever (this will be the final name of the Ubuntu partition, so I used "UBUNTU"). This will become the Ubuntu OS partition.
-Leave the rest unallocated-around 800MB on my drive, if memory serves (during the install, I created this as swap, but I later on reformatted it to FAT32 for cross-system file-carrying, since having a swap partition on a flash drive seemed fairly unanimously regarded as not a good idea).
-Apply these operations and confirm the partitions were created successfully. Close gparted.

3. Install Ubuntu to the USB Drive

-Double-click the "Install Ubuntu" icon on the desktop (alternatively, choose "Install" from the Menubar: System->Administration)
-Follow the steps until the partitioning step (step 4). (Click &#8220;Yes&#8221; if asked to unmount drives) Choose the last option- for a "manual" install (Specify Partitions Manually (Advanced)).
-The next step shows a list of all the partitions on all connected drives. Choose the 32MB FAT32 partition on the USB drive. Click the "Change..." button. New partition size is unchanged (number may be different, but this is just some sort of discrepancy between gparted and the installer- just leave it be). Use as: EFI Boot Partition. Click 'OK.'
-Choose the ext4 partition on the USB drive. Click the &#8220;Change...&#8221; button. Don't change the size, again. Use as: Ext4 Journaling System. Do not check &#8220;Format the partition.&#8221; Choose &#8220;/&#8221; as mount point.
-Choose the 'free space' (unallocated space). Click &#8220;Add...&#8221; Change the new partition size this time to something around 50 MB less than the number given. (Something about the discrepancy between gparted and the installer will give an error on install if this isn't done, as there isn't enough space or something. This leaves a bit of unallocated space, not a big deal, and if it's decided to eliminate the swap partition, all of it can be regained in a future reformat.) Location: Beginning. Use as: swap area.
-Click 'Forward' and continue with the installation until the last step ('Ready To Install').
-Before finishing the installation, choose "Advanced" on the last step- choose for the Boot Loader to be on the USB drive (in my case, /dev/sdb).
-Install!
-When finished installing (it'll take a while) shut down the system.

4. Set up EFI Boot Loader

-Reboot into Mac OS X.
-The EFI Boot partition should mount (as "NO NAME" in my case).
-Copy the "efi" folder to the partition.

*If needed, edit the grub.cfg file- for instance, if the Ubuntu install is not on /dev/sdb2, it needs to be changed.
**To do this: Open Terminal (/Applications/Utilities) Enter "sudo nano" and then drag and drop the grub.cfg file from the USB drive onto the Terminal window. This should give the full command "sudo nano /Volumes/NO\ NAME/efi/boot/grub.cfg." Hit enter and put in password (characters will not appear, just type the password and hit enter). The nano editor should come up to edit the grub.cfg file. When finished with any edits, press Ctrl+X, then Y (for yes), hit enter, and then hit enter again. The file is now saved with the edits.

-Save the blacklist-agp.conf and xorg.conf files to the EFI Boot partition as well. Make sure these are copied over.

5. Configure Ubuntu Install to Get it to Boot Correctly

-Put the Ubuntu disc back in. Reboot, boot from the disc again (hold "C" on startup). Boot into the OS again ("Try Ubuntu").
-Once the OS loads up: Drag and drop the blacklist-agp.conf and xorg.conf files to the desktop from the EFI Boot partition (mounted partition might have a weird name)
-Open Terminal (Menubar:Applications->Accessories->Terminal).

*Warning: Be precise during this next step. Everything I read about this command suggested to be very careful as it gives full control of the user to mess with important system files (and to copy, as I did here, without permissions errors)*

-Type in Terminal: gksu nautilus. Wait.
-A window should pop up. Browse to the Ubuntu USB partition (make sure it's not the CD's filesystem)- Open 'etc' folder. Open 'modprobe.d' folder. Drag and drop the "blacklist-agp.conf" from the Desktop (underneath the window) to the 'modprobe.d' folder. Go back to 'etc' folder. Open 'X11' folder. Drag and drop "xorg.conf" from the Desktop to the 'X11' folder. Navigate to the EFI Boot partition and delete the "blacklist-agp.conf" and "xorg.conf" files (move to trash, empty trash-although empty might not be necessary, don't remember) leaving only the 'efi' folder on the partition (the copies on the desktop will disappear on their own once Ubuntu is shut down, since it's being booted from the disc). Close the nautilus window, close the Terminal.
-Shut down Ubuntu again.

6. Boot into Ubuntu!

-Turn on the computer- hold down "alt" as it starts up (after 'dong') to display available boot options. One should be "EFI Boot." Choose it.
-A window should appear. Choose "Ubuntu MBP" from the list (should be the only option).
-Wait and Ubuntu should eventually boot! Voila!

*Optional Step: Turn swap into FAT32 disk space for carrying around files
**Upon inquiring through Google, it seems that using any part of a USB flash drive as a swap partition could potentially shorten its lifespan considerably (limited number of read/write cycles). Plus, I wanted some space to carry files around. So I erased the swap partition I created and reformatted it as FAT32. Here's how I did it: Open gparted in Ubuntu, select swap partition and turn swap off. Delete the swap partition and apply the operation. Select the unallocated space and format as FAT32 with whatever label you want. Done!

I take no credit for all the work that went into creating everything that made this possible- I'm only trying to put all of the information into one cohesive place for others to use. This worked for me on my Macbook Pro 3,1 (Santa Rosa) and there's no guarantee it will work for others.

For sources, and more documentation:

The most helpful thread- but it has over 1000 posts! The first two posts were updated and have some of the most useful information, anything else must be dug up (but there's a lot there!). Where I downloaded the grub2 boot loader.
[http://ubuntuforums.org/showthread.php?t=995704]("http://ubuntuforums.org/showthread.php?t=995704")

More info on grub.cfg
[http://grub.enbug.org/grub.cfg]("http://grub.enbug.org/grub.cfg")

Similar problem to my original issue (instead of booting GUI, the command line just flickered)
[http://superuser.com/questions/63759/no-gui-after-upgrade-to-ubuntu-9-10-boots-to-command-line]("http://superuser.com/questions/63759/no-gui-after-upgrade-to-ubuntu-9-10-boots-to-command-line")

Nano Editor tip and somewhat useful install info
[http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive]("http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive")

Official general instructions for install on USB
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

Instructions for install on USB (old)
[http://ubuntuforums.org/archive/index.php/t-1065670.html]("http://ubuntuforums.org/archive/index.php/t-1065670.html")

---

### Post by gnumengor on 2010-01-31
BIG thank you! I made my Mac Mini boot from external USB without pain thanks to your howto.

It was a pain configuring bluetooth keyboard and mouse, but everything works OK.

Thanks again :)

---

### Post by hardawayd on 2010-02-28
I have done this two times and both times it does not work. I get the menu showing Ubuntu but once I select Ubuntu and click enter is says something about it needs to load the operating system first. Tried with 32 bit Ubuntu and then 64 bit thinking maybe it made a difference but neither worked.  There must be something detailed that the instructions assumes. I have Ubuntu running on several partitions of my Mac drive using Refit and have done that a hundred times but would like to know how to just launch from a USB stick.  Any ideas?

---

### Post by las_vegas on 2010-03-02
> **hardawayd said:**
> I…once I select Ubuntu and click enter is says something about it needs to load the operating system first.

Actually, it wants to load the kernel. For some reason, your link to initrd is problematic. What you can do is modify the menuentry in the grub.cfg to point directly to the needed files rather than the links in the root directory. For instance what may currently read as:

menuentry "Ubuntu, Linux" {
  search	--set /vmlinuz
  insmod	ext2
  linux		/vmlinuz root=/dev/sdc2 video=efifb
  initrd	/initrd.img
}

Try adding a copy of the above, but change it as such:

menuentry "Ubuntu, Linux 2.6.31-14-generic" {
  search	--set /vmlinuz
  insmod	ext2
  linux		/boot/vmlinuz-2.6.31-14-generic root=/dev/sdc2 video=efifb
  initrd	/boot/initrd.img-2.6.31-14-generic
}

This way it loads the kernel directly. Once booted, go to your /boot folder and note the most recent version of vmlinuz and initrd and add them as yet another menuentry into your grub.cfg file until you find the one that works best.

Note: I prefer to replace the search line to address the drive directly. Changing, in my case:

  search	--set /vmlinuz

to

   set root=(hd1,2)

I also removed the 'video=efifb" since my iMac's nVidia card is supported.

LasVegas

---

### Post by warriork26 on 2010-07-18
I can't get the kernel to load. Any suggestions? I've done this whole process 3 times!

---

### Post by linkrox on 2010-11-20
Hi,

I followed your tutorial but when I set the 32MB partition as EFI partition and started installing it says "the efi file system creation" sdb etc etc. "failed"

:(

I tried with several usb disks but nothing, always the same error.

I'm using UBUNTU 10.10 :)

Any suggestions?

Thank you in advance.

Marco

---

### Post by Fox11 on 2010-11-20
Have you followed my steps *exactly*? Could be that Ubuntu 10 doesn't work with this method? That would be my first guess... I know it's a long process, but try with 9.10 or 9.04 and see if that works... best of luck!

> **gnumengor said:**
> BIG thank you! I made my Mac Mini boot from external USB without pain thanks to your howto.

It was a pain configuring bluetooth keyboard and mouse, but everything works OK.

Thanks again :)

And gnumengor, great to hear that my notes/'guide' helped you with your Mac Mini!

If anyone's had success with different macs, please post and let others know! As I've said, I can only vouch for my experience with my 3,1 Santa Rosa MacBook Pro.

---

### Post by linkrox on 2010-11-22
Mate,

I have tried with ubuntu 9.10 and everything it's great!

**MacBookPro 5,5 with Ubuntu 9.10 works perfectly.**

I noticed that with Ubuntu 10.10 the error could possibly depends on the filesystem of EFI, in fact during installation and just before the error I described in the other post, it said "Writing Efi Fat16..." so I tried to format efi partition in fat16 but nothing.

I had a bit problems when I change the partition swap to fat32 (like you did), in fact at restart grub didn't find the system saying "install kernel first".

I think is a problem of setting root directory (I also tried to modify it but I'm not so familiar with grub so I'm studying it and let you know when I manage to solve)

Thank you again for your detailed guide!

Marco

---

### Post by thekyz on 2011-02-18
Ok, it worked for me untill it it tried to start the X server at boot time. I had to remove the efi graphic card info for it to work.

Tested on a macbook air 2,1.

Thx a lot!

---

### Post by julowe on 2011-04-10
> **thekyz said:**
> Ok, it worked for me untill it it tried to start the X server at boot time. I had to remove the efi graphic card info for it to work.

Tested on a macbook air 2,1.

Thx a lot!
Similar (same?) problem, but no fix yet.  I get this error "Conflicting fb hw usage Nouveaufb vs VESA VGA Removing generic driver"
I removed from line 10 of the grub.cfg 'video=efifb agp=off' but that didn't fix it. Is this what you did when you say you removed the EFI graphic card info? Or did you do something else/more?
MacBookPro 3,1 installing Kubuntu 10.10 from a liveccd

---

### Post by julowe on 2011-04-10
> **linkrox said:**
> Hi,

I followed your tutorial but when I set the 32MB partition as EFI partition and started installing it says "the efi file system creation" sdb etc etc. "failed"

:(

I tried with several usb disks but nothing, always the same error.

I'm using UBUNTU 10.10 :)

Any suggestions?

Thank you in advance.

Marco
I also got this error, but fixed it by increasing the partition size to 48 megs. (Less would probably work, but 36 didn't work for me - same error)

---

