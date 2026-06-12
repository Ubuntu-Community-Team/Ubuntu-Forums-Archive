---
title: "Dual boot Windows 8.1 and Ubuntu 14.04?"
date: 2016-05-08
forum: Apple Hardware Users
---

### Post by Robert_Jackson on 2016-05-08
First the why's ... 

I need CATIA V5 to put food on the table and it only goes as high as Windows 8.1 professional.
I want to create a host for developing NVidia Jetson base Robots and Ubuntu 14.04 is the current supported level.
I don't need OSX.

Where I am at...

Was able to install all three OS'es by themselves (as the sole OS) on the MacBook pro 11,5 with no issues.

Now I want to get both 8.1 and 14.04 working at the same time.
I loaded up windows first and used diskpart to clean the disk and create a windows partition.
Formatted NTFS, loaded windows, put the bootcamp drivers down.
rebooted
everything was great.

I started a live install of 14.04 and added swap and / partitions.
Started the install and then followed the instructions on the Ubuntu site to fix up the efi mbr at the end.
rebooted
grub came up.
picked Ubuntu. 
It loaded.
everything was great.

Now here's where I am stuck.
If I restart and pick windows from grub ... I get the message that it can find windows.
If I restart and hold down the options key...I show one drive on the screen labeled windows...and it boots windows perfectly.

So I would like to either get windows working from grub.
Or a second drive showing up when options is held down that show Ubuntu.
Seems like I have half a solution on either side....even though its technically does work.

[http://paste.ubuntu.com/16293031](http://paste.ubuntu.com/16293031)

Any advice???

---

### Post by oldfred on 2016-05-08
I do not know Mac.
But report shows Windows standard issue where you left fast start up on.
Linux will not mount or see NTFS partition(s) that are hibernated or need chkdsk.
And Windows 8 or later uses fast start up which is always on hibernation.

       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

It looks like you have hybrid partitions. That was a Windows requirement when it used to only install in BIOS/MBR boot mode.
       
 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

I have not used rEFInd on my PC, but see many Apple users like it.
       
 [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by Robert_Jackson on 2016-05-08
Well I am able to reliably install solo Win 8.1 and solo Ubuntu 14.40.
It looks like I could not replicate both of them working together as described above.
I need to sort this out first.

> So I would like to either get windows working from grub.
 > Or a second drive showing up when options is held down that show Ubuntu.
 > Seems like I have half a solution on either side....even though its technically does work.

---

### Post by Robert_Jackson on 2016-05-08
I was surprised to see that they was hybrid data in the report.
I can see where it says I need to turn off fastboot...but where in the report does it show the hybrid mbr?
I'm new to ubunto...so I may be staring right at it.




This is what I am to....

Under live ubuntu
I can add swap partition with gparted
I can add / partition with gparted
I run gdisk and make sure there are no hybrid mbrs.
If I reboot windows is OK

Now if I boot back into live Ubuntu and do an install "other" and pick those partitions (using ubiquity -b) ... it trashes windows startup.
It does this without -b
It does this with install alongside windows
It does this with other and creating the partitions in the install tool.

If I try to reinstall windows over itself at this point I get a message about the disk being invalid to install windows.

Does this scenario somehow add the legacy/hybrid mbr to the efi partition?
Am I not installing Ubuntu UEFI?

---

I just turned off windows 8 fastboot.

I will try the scenario again.

---

### Post by Robert_Jackson on 2016-05-08
It is absolutely ubiquity that is changing my partition table from protective to hybrid.
I did a gdisk before and after the install step that create the partitions.
So any idea on what's the root cause of this?

---

### Post by Robert_Jackson on 2016-05-08
So I think I have the first of two tasks worked out.
 1) get windows and Ubuntu dual booting on a MacBook pro 11,5
 2) get Ubuntu to show up as a partition when holding down option at boot and make grub boot straight into unbuntu


 So instructions for part 1)

Create a windows 8.1 install USB stick
upgrade to El Capitan (this should get you latest bootcamp drivers and firmware updates)
start bootcamp and go to menu bar and select download windows support software
copy windows support software onto USB stick
Create a ubuntu 14.04 install USB stick
 insert windows usb
 power on computer holding down option key
 select efi boot icon
 windows will start to load setup
 when the language and other preferences dialog appears press shift F10 to get a windows terminal
 type in....
   diskpart
  select disk 0
  clean  
  convert gpt
  create partition efi size=512
  format fs=fat32
  create partition msr size=128
  create partition primary size=102800
  format fs=ntfs quick label=Windows
  exit
complete normal windows 8.1 installation
go to windows support software 
go into bootcamp directory
run setup .exe and install drivers
turn off fastboot

(at this point the machines is a windows only MacBook pro)

insert ubuntu usb
power on with option key held down
boot to Ubuntu live install
choose install alongside windows (or custom)
install Ubuntu but DO NOT RESTART
When ubuntu finishes attach to network
open a terminal
  sudo apt-get install efibootmgr
  sudo efibootmgr
  sudo efibootmgr -o 0
In the same terminal we need to get rid of the hybrid mbr
  sudo gdisk /dev/sda
  x
  n
  w

That should be it....now the MacBook pro boots to grub by default and you can pick Ubuntu
If you want to book windows you do hold the option key and boot to windows.

-----

So part 2 is how to get both installation showing up in the options screen.
how to put a nice icon in for Ubuntu.
And how to get grub to just load straight to Ubuntu with not options.

---

### Post by oldfred on 2016-05-08
Still do not know Mac.
But with a PC in UEFI boot mode it does not create a hybrid MBR/gpt drive.
If installing in BIOS mode, but not getting grub installed, it would use MBR. And then maybe you installed the version of grub that is for UEFI?

If you want boot icons, that is rEFInd as linked above.

---

### Post by Robert_Jackson on 2016-05-08
I think this may be a bug. 

I kind of get the feeling that maybe the hybrid MRB issue has been attributed to prior use of bootcamp ... when maybe it was really ubiquity that is making the change.

I run gdisk in the live install before I laugh ubiquity...and MRB is protected..but the second I get past the past the partitioning screens in ubiquity...gdisk shows hybrid.

I even tried creating the partitions first in gparted. No issues. No change to mbr ... Until I go into ubiquity and tell it to use the partitions...then bang....I suddenly have a hybrid partition.

As long as I delete the hybrid using gdisk before reboot ... everything works fine afterward.

I follows the instructions to very I am in uefi mode during live and after a reboot into the actual installation. One thine to note...it returns apple uefi 1.1 ... while most examples shoe uefi 2.0.

Could there be logic in ubiquity code that gets tripped up by the 1.1 version and thinks it needs to create a hybrid mbr? You definitely would not see that on the PC side where it's always returning 2 or higher?

---

### Post by Robert_Jackson on 2016-05-08
Just noticed that the grub pick for Windows is also now working.

I had an issue with a failed patch on win 8.1 so I reformatted partition and then reloadeD Windows. Loaded up Ubuntu from USB and did sudo efibootmgr -o 0 and rebooted.

Not sure if the second install of Windows fixed this? Or if it worked to begin with. 

I'll wipe the drive clean and reinstall and test tomorrow.

---

### Post by oldfred on 2016-05-09
PCs use the newer UEFI version, but every vendor implements "standard" somewhat differently. Often hard coded to only boot "Windows Boot Manager" by description. And using description as part of boot is specifically not allowed in standard.

It is my understanding that Mac have not upgraded fully to the newest UEFI.
But Mac started using UEFI with the change to Intel chips and started long before PCs, so older UEFI. And they are really not 1.1 but include some newer features.

---

### Post by Robert_Jackson on 2016-05-09
How do I let the mactel team know about this issue? It really seems like a bug in ubiquity that is triggered by EFI v1.1

---

### Post by oldfred on 2016-05-09
You can create a bug here. 
I took a quick look and did not see anything similar, but you should review existing bugs.
Provide as much detail as possible, they will probably want logs from installer, if you saved them.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity](https://bugs.launchpad.net/ubuntu/+source/ubiquity)

---

### Post by Robert_Jackson on 2016-09-20
OK. 
Never did get the windows in grub working when unbuntu was in grub.
And never got Ubuntu to show up as a drive holding down the options.

But I am starting a new thread to replicate this with 16.04.1.


If I get that working I might have the bandwidth to get the last two bits going.

---

