---
title: "2gb live usb - why would I NOT use all available space for persistence?"
date: 2013-07-15
forum: Any Other OS
---

### Post by Phateless on 2013-07-15
Mods feel free to move this if I posted in the wrong location.

My goal is to use a 2gb flashdrive to have an extremely fast and lightweight installation with Chrome and Java so I can run it on any computer.

I've been fiddling with this over the past two days and have tried a few distros for a few mins each. Some report not enough space when trying to install java, some run a bit laggy, Ubuntu was very slow.

I guess I don't know exactly what I'm doing. Can someone help out a noob?

---

### Post by ibjsb4 on 2013-07-15
Have you checked out Puppy?

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

---

### Post by oldfred on 2013-07-15
Have you turned on persistence?

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

   [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by Phateless on 2013-07-15
> **ibjsb4 said:**
> Have you checked out Puppy?

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

Not yet, but I read a bit about it and it's on my list.

> **oldfred said:**
> Have you turned on persistence?

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

   [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Are you saying that "persistence" is different than a "direct install to a flashdrive?" I'm just looking for Chrome Sync and Java so I can use my screensharing software for work.

Apologies, I am an extreme noob at Linux. Thanks for your help!

---

### Post by oldfred on 2013-07-15
With only a 2GB flash you can only use persistence, you probably need an 8GB as a minimum for a full install to a flash drive. But a full install has more update capabilities. With persistence you can save some things, but the installer still installs the original downloaded version which you are always booting.

---

### Post by sanderj on 2013-07-15
> **Phateless said:**
> Mods feel free to move this if I posted in the wrong location.

My goal is to use a 2gb flashdrive to have an extremely fast and lightweight installation with Chrome and Java so I can run it on any computer.

I've been fiddling with this over the past two days and have tried a few distros for a few mins each. Some report not enough space when trying to install java, some run a bit laggy, Ubuntu was very slow.

I guess I don't know exactly what I'm doing. Can someone help out a noob?

In my experience, a USB stick install is not suitable for doing updates or installing (big) software packages. 
IMHO, A USB stick install is suitable for running that, and keeping some of your own files on the persistent part of the stick.

Easy check: do a fresh install to a stick (I would use netbootin for that), and then run "df -h" to see how much space is left.

HTH

---

### Post by Phateless on 2013-07-15
> **oldfred said:**
> With only a 2GB flash you can only use persistence, you probably need an 8GB as a minimum for a full install to a flash drive. But a full install has more update capabilities. With persistence you can save some things, but the installer still installs the original downloaded version which you are always booting.

Ahh yes, that makes sense. I already made the mistake of trying to update Zorin, and of course it failed, which is exactly what I suspected.

> **sanderj said:**
> In my experience, a USB stick install is not suitable for doing updates or installing (big) software packages. 
IMHO, A USB stick install is suitable for running that, and keeping some of your own files on the persistent part of the stick.

Easy check: do a fresh install to a stick (I would use netbootin for that), and then run "df -h" to see how much space is left.

HTH

That's fine, that functionality is actually exactly what I had in mind - the only thing I want to install is Java support. Can anyone help me with that? I posted another thread.

Thanks all! I know I'm a noob but I'm loving Linux so far. It's amazing how multiple machines seem to run better than with their stock windows drivers. LOL.

---

### Post by kurt18947 on 2013-07-15
I think for what you want to do, a 'real' install might be your best choice.  Flash drives are pretty cheap these days; I bought a 16 GB. USB 3 store brand for $10.99.  I formatted it to ext4 and did a 'real' install from a live DVD.  I unplugged my hard drive just so nothing got  installed to the hard drive by accident but that isn't necessary.  Just pay attention during the install process that the O.S. *and GRUB* are written to the proper drive.  Writing to flash drives is much slower than reading so installing takes more time than installing to a hard drive.  I bought a USB 3 flash drive thinking write speeds might be faster than USB 2 even on a USB 2 port.  I don't know if I wasted $3 or not :).  I installed PCLinuxOS on it and can update and install additional software just like on a hard drive.  Even though installing takes quite some time, using the flash drive install while slower than an internal hard drive, isn't too slow.  Everyday functions - web browsing, office stuff etc. work pretty well.  Any proprietary software such as video or network adapter drivers should install and work normally.

---

### Post by Phateless on 2013-07-15
> **kurt18947 said:**
> I think for what you want to do, a 'real' install might be your best choice.  Flash drives are pretty cheap these days; I bought a 16 GB. USB 3 store brand for $10.99.  I formatted it to ext4 and did a 'real' install from a live DVD.  I unplugged my hard drive just so nothing got  installed to the hard drive by accident but that isn't necessary.  Just pay attention during the install process that the O.S. *and GRUB* are written to the proper drive.  Writing to flash drives is much slower than reading so installing takes more time than installing to a hard drive.  I bought a USB 3 flash drive thinking write speeds might be faster than USB 2 even on a USB 2 port.  I don't know if I wasted $3 or not :).  I installed PCLinuxOS on it and can update and install additional software just like on a hard drive.  Even though installing takes quite some time, using the flash drive install while slower than an internal hard drive, isn't too slow.  Everyday functions - web browsing, office stuff etc. work pretty well.  Any proprietary software such as video or network adapter drivers should install and work normally.
Thanks for your reply. So how do I go about doing a full install on a usb? I've been using Univeral USB Installer and so far the only issue I've encountered is that I can't figure out how to get Java working.

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Thanks!

---

### Post by C.S.Cameron on 2013-07-15
In answer to the title, if you use all available space for persistence , you will not be able to use the drive to move files to/from a windows machine. For drives larger than 8GB you would need to use a persistent partition as max size of the persistence file, (casper-rw), is 4GB, (being FAT32).

If you have installed Ubuntu to USB using Startup Disk Creator, (from the Live CD), or UNetbootin, using the extra space options you should be able to install Java in the normal manner.
See:
[http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html](http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html)

---

### Post by Phateless on 2013-07-15
> **C.S.Cameron said:**
> In answer to the title, if you use all available space for persistence , you will not be able to use the drive to move files to/from a windows machine. For drives larger than 8GB you would need to use a persistent partition as max size of the persistence file, (casper-rw), is 4GB, (being FAT32).

If you have installed Ubuntu to USB using Startup Disk Creator, (from the Live CD), or UNetbootin, using the extra space options you should be able to install Java in the normal manner.
See:
[http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html](http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html)

Thanks for your help. I set it to maximum size persistence available (just over 1gb I think), because I figured I use DropBox for everything anyway, so what's the difference? I'll probably get a larger usb drive at some point for the purpose you mentioned.

I finally did get Java working, it was just a matter of adding the right packages in Synaptic Package Manager (derp). Not sure which ones finally did the trick, lol, but I tested it and my screenshare works, so I can use this live usb for work, which was my original purpose.

I'm still a little fuzzy on the practical difference between a live usb with persistence and a full install - can you break it down for me in super-noob terms? I'm comfortable with computers in general and would consider myself a "power-user" in Windows, but I'm so new to Linux that I don't think I have a full context to grasp what you're saying.

Is it as simple as with a live usb the entire OS is running in RAM, whereas with a full install it will be running directly from the usb drive?? Again, thanks for your patience! This is a great forum, and at the risk of invoking Murphy's Law, I haven't once been yelled at to search, even though I'm sure this has been covered before. (I did search, just couldn't find an answer I could understand)

Also, what exactly is the difference between UNetBootin and Universal USB Installer? Or are they just different programs that do essentially the same thing?

Thanks again!

---

### Post by oldfred on 2013-07-15
The install process is the same regardless of the tool used. It extracts/converts the ISO to the flash drive and adds boot capability to the MBR. You do not just copy ISO to flash drive. Some distributions have modified ISO so dd will work, but I do not suggest that as any use of dd can be dangerous. Any typo and you permanently damage the data on another drive.

See pros & cons of each type of install in post #3.

Flash drives are slower writing, but all Linux caches your activity into RAM. So if you have a system with a fair amount of RAM and do not run lots of different apps at once, system speed will be similar regardless of how you boot except for writes. You do have to change some settings to reduce writes with slower devices like flash drives which makes them a bit better.

---

### Post by C.S.Cameron on 2013-07-16
A Persistent install extracts the files from the Live DVD to the USB drive, adds a persistence file or partition named casper-rw and makes the drive bootable usually using syslinux.
A Full install is doing a normal install to USB just like installing to internal drive, as most newer computer BIOS see a USB drive as just another HDD.
Both styles have advantages and disadvantages, The benefit of a Persistent install for you is that it does what you want, on a drive you already own.
You can soup up a Persistent drive by adding your user name, removing the try/install screen and adding a persistent partition or drive, (formatted ext2 and named casper-rw).

It seems that with recent versions USB drives mostly run in RAM.

Many people report problems with Universal. I prefer SDC.

---

### Post by Phateless on 2013-07-16
> **oldfred said:**
> The install process is the same regardless of the tool used. It extracts/converts the ISO to the flash drive and adds boot capability to the MBR. You do not just copy ISO to flash drive. Some distributions have modified ISO so dd will work, but I do not suggest that as any use of dd can be dangerous. Any typo and you permanently damage the data on another drive.

See pros & cons of each type of install in post #3.

Flash drives are slower writing, but all Linux caches your activity into RAM. So if you have a system with a fair amount of RAM and do not run lots of different apps at once, system speed will be similar regardless of how you boot except for writes. You do have to change some settings to reduce writes with slower devices like flash drives which makes them a bit better.

No I definitely didn't just copy the ISO, I used to program to "install" to the flash drive, but I'm not sure if it's a "live cd" or a "full install."

> **C.S.Cameron said:**
> A Persistent install extracts the files from the Live DVD to the USB drive, adds a persistence file or partition named casper-rw and makes the drive bootable usually using syslinux.
A Full install is doing a normal install to USB just like installing to internal drive, as most newer computer BIOS see a USB drive as just another HDD.
Both styles have advantages and disadvantages, The benefit of a Persistent install for you is that it does what you want, on a drive you already own.
You can soup up a Persistent drive by adding your user name, removing the try/install screen and adding a persistent partition or drive, (formatted ext2 and named casper-rw).

It seems that with recent versions USB drives mostly run in RAM.

Many people report problems with Universal. I prefer SDC.

That helps a bit more, but I still don't fully understand how to do a full install to a usb instead of the live usb I think I'm currently running with Zorin.

---

### Post by C.S.Cameron on 2013-07-17
Following is step by step for installing 12.04 on a 8GB flash drive on an Intel machine.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system".
And "Mount point" = /windows.
Select "OK"

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4000 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hibernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.

Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.

Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can revise grub later, if you wish.

---

### Post by Phateless on 2013-08-18
> **C.S.Cameron said:**
> Following is step by step for installing 12.04 on a 8GB flash drive on an Intel machine.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system".
And "Mount point" = /windows.
Select "OK"

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4000 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hibernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.

Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.

Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can revise grub later, if you wish.
Thanks for that! Some of it is still a bit above my head, but I can google and learn. So I'm assuming I can't boot from a live usb and then perform a full install to that same live usb? Like asking a pencil to write on itself.

After reading up a bit more, it also appears that  might be better off with a live usb than a full install because I intend to use this on multiple different machines.

Thanks again, everyone, for all your help, and especially your patience.

---

