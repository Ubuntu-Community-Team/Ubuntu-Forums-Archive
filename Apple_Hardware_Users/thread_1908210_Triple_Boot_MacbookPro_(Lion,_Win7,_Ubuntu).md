---
title: "Triple Boot MacbookPro (Lion, Win7, Ubuntu)"
date: 2012-01-13
forum: Apple Hardware Users
---

### Post by tgeulin on 2012-01-13
Alright, so I begin knowing that their are many such posts out their such as this. This however, is what worked for me, and so i thought i would share. My experience was mostly trial and error and my solution came from researching other fixes. For this guide I am assuming that you know your way around your mac fairly well. Although if i have posted this in the wrong place, i apologize. But i digress...

My hardware: MacbookPro8,2

The problems
[LIST]
[*]Lion recovery partition getting in the way
[*]Windows not booting after installing Ubuntu&#8230;. "missing operating system"
[*]refit not installing properly
[/LIST]

The solution:

download and install got fdisk for mac... [http://sourceforge.net/projects/gptfdisk/]("http://sourceforge.net/projects/gptfdisk/")
download rEFIt... [http://refit.sourceforge.net/]("http://refit.sourceforge.net/")

MAKE BACKUP: once gdisk is installed go to terminal and type 'sudo disk /dev/disk0'. it will take you to the disk menu. once there enter 'b', and type a file name (it will automatically save in your home folder). once finish quit by entering 'q'
 
installing refit... many people have difficulty installing refit. the trick is to install it manually (check out refit's documentation). reboot and you should see your new loader.

partition your disk... you need to create two new partitions for windows and linux (disk utility works just fine). format both of them to FAT.

install windows 7.... in the installer format the disk you want windows on as ntfs and finish through installation (note:your computer will reboot several times and each time it does make sure to boot from your new windows partition under refit). Once its all finished go ahead and install your boot camp drivers. your eject key won't work yet so you'll have to eject the setup disk from the control panel.

install ubuntu... for this you are going to need both a live usb and live cd. create live usb: [http://www.nightlion.net/guides/2011/burn-iso-to-bootable-usb-flash-drive-in-mac-osx-terminal-via-command-line-diskutil/]("http://www.nightlion.net/guides/2011/burn-iso-to-bootable-usb-flash-drive-in-mac-osx-terminal-via-command-line-diskutil/") and for the live cd simply burn the .iso with disk utility. with both the cd and the usb inserted in the computer, reboot and hold down the 'C' key on restart. It may take several minutes but you should get to the installer. In the installer select the advanced installation option. format and use the partition you set aside for linux. set the mount point to '/' and *install the grub boot loader to whatever partition your installing linux on. It will give you a warning about not having a swap partition, but you can ignore this for now and create a swap file inside your ubuntu later. install and reboot back into lion

At the moment you now have a screwed up hybrid mbr table (this is because most likely your lion recovery disk uses one of your precious mbr slots)
in order to fix this we are going to create a new hybrid mbr table. i have attached screenshots of this process.
reopen terminal and again type 'sudo gdisk /dev/disk0'. this time enter 'r'. and then 'p'. this will print your partitions. now you need to create your hmbr so type 'h'. it will now ask you for the partitions you wish to enter. referring to the printed partition list, add your lion, windows and linux partitions. (in my case 2 4 5). next it will ask you to place efi partition first, select 'y'. now it will ask you for the mbr hex code for each partition. the codes you want are 'AF' for lion, '07' for windows, and '83' for linux. don't set any of the bootable flags. once finish enter 'w' to write these changes to the disks. You can also enter 'q' if you want to quit without saving changes. reboot and now you should be able to boot into each of your OSes. 



Tip: if for some reason it doesn't work and you want to restore your gpt table, simply go back to gdisk, enter 'r', enter 'l', and then type your backup filename. reboot and you'll no longer have you win or linux partitions but your gpt will gpt table will be back to normal.

i hope this helps any and all of you. its not the prettiest guides and for that i apologize, but if you have any questions i'd be glad to answer them.

Cheers!

EDIT: if you want a 'common' partition, simply create three new partition at the beginning(one for win7, one for ubuntu, one for common).
         If you decide that you want a shared partition after you install win7 and ubuntu, simply create a new partition and the recreate your hybrid mbr as described above.

---

### Post by bhadotia on 2012-01-13
I think you should add the keywords: **how-to**, **macbook pro early 2011**, **ubuntu**, **multi boot**, etc. to your thread. And  also update the title of your thread to reflect that its a How-to and not a thread asking support to themulti-boot problems on macbook pro. This will help people to find your post better on both google and forums search.

Personally I'm also having problem booting up from the ubuntu (,Arch linux, openSuse and Fedora ;)) CD(s) on my macbook pro 8.1. Though, I haven't tried your suggestions yet, I will try them out when I get some free time and post back the outcome. Thanks, for the instructions though.. ;)

---

### Post by scognito on 2012-01-13
Nice work! (you should edit your first post: you wrote "sudo disk" instead of "sudo gdisk"). 
This is how I solved too (I'm writing an article for my blog).
The only problem is that you don't have a shared partition for data.
I had it but when a day I decided to resync the partition table using refit it disappeared from windows (works with Linux and OSX).
Still investigating...

> **tgeulin said:**
> Alright, so I begin knowing that their are many such posts out their such as this. This however, is what worked for me, and so i thought i would share. My experience was mostly trial and error and my solution came from researching other fixes. For this guide I am assuming that you know your way around your mac fairly well. Although if i have posted this in the wrong place, i apologize. But i digress...

My hardware: MacbookPro8,2

The problems
[LIST]
[*]Lion recovery partition getting in the way
[*]Windows not booting after installing Ubuntu&#8230;. "missing operating system"
[*]refit not installing properly
[/LIST]

The solution:

download and install got fdisk for mac... [http://sourceforge.net/projects/gptfdisk/]("http://sourceforge.net/projects/gptfdisk/")
download rEFIt... [http://refit.sourceforge.net/]("http://refit.sourceforge.net/")

MAKE BACKUP: once gdisk is installed go to terminal and type 'sudo disk /dev/disk0'. it will take you to the disk menu. once there enter 'b', and type a file name (it will automatically save in your home folder). once finish quit by entering 'q'
 
installing refit... many people have difficulty installing refit. the trick is to install it manually (check out refit's documentation). reboot and you should see your new loader.

partition your disk... you need to create two new partitions for windows and linux (disk utility works just fine). format both of them to FAT.

install windows 7.... in the installer format the disk you want windows on as ntfs and finish through installation (note:your computer will reboot several times and each time it does make sure to boot from your new windows partition under refit). Once its all finished go ahead and install your boot camp drivers. your eject key won't work yet so you'll have to eject the setup disk from the control panel.

install ubuntu... for this you are going to need both a live usb and live cd. create live usb: [http://www.nightlion.net/guides/2011/burn-iso-to-bootable-usb-flash-drive-in-mac-osx-terminal-via-command-line-diskutil/]("http://www.nightlion.net/guides/2011/burn-iso-to-bootable-usb-flash-drive-in-mac-osx-terminal-via-command-line-diskutil/") and for the live cd simply burn the .iso with disk utility. with both the cd and the usb inserted in the computer, reboot and hold down the 'C' key on restart. It may take several minutes but you should get to the installer. In the installer select the advanced installation option. format and use the partition you set aside for linux. set the mount point to '/' and *install the grub boot loader to whatever partition your installing linux on. It will give you a warning about not having a swap partition, but you can ignore this for now and create a swap file inside your ubuntu later. install and reboot back into lion

At the moment you now have a screwed up hybrid mbr table (this is because most likely your lion recovery disk uses one of your precious mbr slots)
in order to fix this we are going to create a new hybrid mbr table. i have attached screenshots of this process.
reopen terminal and again type 'sudo disk /dev/disk0'. this time enter 'r'. and then 'p'. this will print your partitions. now you need to create your hmbr so type 'h'. it will now ask you for the partitions you wish to enter. referring to the printed partition list, add your lion, windows and linux partitions. (in my case 2 4 5). next it will ask you to place efi partition first, select 'y'. now it will ask you for the mbr hex code for each partition. the codes you want are 'AF' for lion, '07' for windows, and '83' for linux. don't set any of the bootable flags. once finish enter 'w' to write these changes to the disks. You can also enter 'q' if you want to quit without saving changes. reboot and now you should be able to boot into each of your OSes. 



Tip: if for some reason it doesn't work and you want to restore your gpt table, simply go back to gdisk, enter 'r', enter 'l', and then type your backup filename. reboot and you'll no longer have you win or linux partitions but your gpt will gpt table will be back to normal.

i hope this helps any and all of you. its not the prettiest guides and for that i apologize, but if you have any questions i'd be glad to answer them.

Cheers!

---

### Post by tgeulin on 2012-01-13
> **bhadotia said:**
> I think you should add the keywords: **how-to**, **macbook pro early 2011**, **ubuntu**, **multi boot**, etc. to your thread. And  also update the title of your thread to reflect that its a How-to and not a thread asking support to themulti-boot problems on macbook pro. This will help people to find your post better on both google and forums search.

Personally I'm also having problem booting up from the ubuntu (,Arch linux, openSuse and Fedora ;)) CD(s) on my macbook pro 8.1. Though, I haven't tried your suggestions yet, I will try them out when I get some free time and post back the outcome. Thanks, for the instructions though.. ;)
thanks for the tip bhadotia. also the reason that just a live cd won't boot is because for some reason or another the macbook looses track of the cd which is why you get an error, but when you have the usb connected it detects that and reverts to it for the remainder of the boot session.

---

### Post by tgeulin on 2012-01-13
> **scognito said:**
> Nice work! (you should edit your first post: you wrote "sudo disk" instead of "sudo gdisk"). 
This is how I solved too (I'm writing an article for my blog).
The only problem is that you don't have a shared partition for data.
I had it but when a day I decided to resync the partition table using refit it disappeared from windows (works with Linux and OSX).
Still investigating...
did refit properly fix your tables? at first it gave me an error, but now that i manually fixed it with gdisk it says that it can sync my tables. everything is working fine now so I'm just leaving it. also, have you tried creating your common partition but not syncing it in you hybrid mbr? would that work? i haven't tried mainly because a common partition isn't really necessary for my needs

---

### Post by bhadotia on 2012-01-14
> **tgeulin said:**
> also the reason that just a live cd won't boot is because for some reason or another the macbook looses track of the cd which is why you get an error, but when you have the usb connected it detects that and reverts to it for the remainder of the boot session.

You mean to say that I should [FONT=Lucida Console]dd [FONT=Verdana]the image to a thumb drive and then try booting from that?

EDIT: Never mind, just went through the install ubuntu part of the How-to... ;)
[/FONT][/FONT]

---

### Post by tgeulin on 2012-01-16
> **mapperss said:**
> The only problem is that you don't have a shared partition for data.
This wasn't really a problem for me. but if you wanted to try, you could probably just create a new partition with disk utility and use that as your common partition. You shouldn't need to add it to your hybrid mbr, but by creating a new partition your hmbr could get messed up, so then you could just simply recreate it as described in my original post.

EDIT: this works, all you have to do is update the mbr. or just create a common partition from the very beginning.

---

### Post by scognito on 2012-01-16
I've created the shared partition at the beginning and it worked for win/lin/osx.
After some days Win7 sees OSX partition instead of the shared one, and I don't know the why.

My hybrid MBR is:
1) Reserved
2) OSX
3) WIN
4) LINUX

Also the hard disk has other 2 partition:
5) Shared partition (NTFS)
6) Linux swap

As said above, the shared is working on linux and osx. I think Windows can see *only* the Hybrid MBR partitions (indeed the reserved one is seen from win7 disk utility).
Still don't know why it worked initially, very confused.


> **tgeulin said:**
> This wasn't really a problem for me. but if you wanted to try, you could probably just create a new partition with disk utility and use that as your common partition. You shouldn't need to add it to your hybrid mbr, but by creating a new partition your hmbr could get messed up, so then you could just simply recreate it as described in my original post.

EDIT: this works, all you have to do is update the mbr. or just create a common partition from the very beginning.

---

### Post by MorganBauer on 2012-01-16
Made my day. I can confirm this works. Lion/W7/Arch here. Each boots up and functions.

---

### Post by scognito on 2012-01-17
> **MorganBauer said:**
> Made my day. I can confirm this works. Lion/W7/Arch here. Each boots up and functions.
Do you use shared partition too? I found a way to have a shered partition working on Windows too, sacrifing OSX parition visibility from it.

---

### Post by tgeulin on 2012-01-19
> **scognito said:**
> I've created the shared partition at the beginning and it worked for win/lin/osx.
After some days Win7 sees OSX partition instead of the shared one, and I don't know the why.

My hybrid MBR is:
1) Reserved
2) OSX
3) WIN
4) LINUX

Also the hard disk has other 2 partition:
5) Shared partition (NTFS)
6) Linux swap

As said above, the shared is working on linux and osx. I think Windows can see *only* the Hybrid MBR partitions (indeed the reserved one is seen from win7 disk utility).
Still don't know why it worked initially, very confused.
Unfortunately yes, Windows won't recognize the shared partition.

Personally I don't even use one since I have never really found a need to. Instead of a shared partition though, why not just have a "shared" folder in either the root of your windows or osx partition? this way you should have access to it from all partitions. It might work better in your windows partition though because in order for linux to write to your hfs partition you would have to disable journaling. 

So if you have this "shared" folder on your windows root, you could make a shortcut and put that on your desktop, in osx make an alias of that folder on your desktop as well, and do the same for linux. Although in linux you may even be able to mount the folder by editing your fstab.

---

### Post by andrix10 on 2012-01-20
Do u have to have the CD and USB for it to install?

And is it ok if I installed windows with bootcamp? Or I have to reinstall?

---

### Post by tgeulin on 2012-01-22
> **andrix10 said:**
> Do u have to have the CD and USB for it to install?

And is it ok if I installed windows with bootcamp? Or I have to reinstall?
For Linux you have to have both a live cd and live USB plugged in, and to boot it simply boot from the cd. I used bootcamp only for the drivers. If you partitioned your disk with bootcamp the process will still work. All you'll have to do after installing Linux is recreate your hybrid mbr.

EDIT: when you go to partition your disk for Linux, disk utility might give you an error about loosing your bootcamp. Ignore that and continue anyways. It will get fixed once you recreate your tables.

---

### Post by jherm on 2012-02-02
Thank you so much for this. It was exactly the information I needed. It applies to Fedora as well.

I tried with Fedora 16, 64-bit. I created a custom layout (thought I had already resized my NTFS partition, but I guess not). The install DVD wanted me to make a 2MB 'BIOS Boot' partition, so I did that. I used the rest of the disk to create a 25GB ext4 partition -- no swap, I just upgraded to 8GB of memory and an SSD, I can use a swapfile if I need to.

```

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640        76581511   36.3 GiB    AF00  Macintosh HD
   3        76581512        77851047   619.9 MiB   AB00  Recovery HD
   4        77852672       183236607   50.3 GiB    0700  BOOTCAMP
   5       183236608       183240703   2.0 MiB     EF02  
   6       183240704       234440703   24.4 GiB    EF00  ext4

```

I ended up using partitions 2, 4, and 6. I set none of them to bootable. I used the default partition type codes for each partition and everything works A-OK now! Thanks again.

---

### Post by ZERO_SHIFT on 2012-03-22
Which OS provides the smoothest experience on the mac?

---

### Post by tgeulin on 2012-03-26
> **ZERO_SHIFT said:**
> Which OS provides the smoothest experience on the mac?
OS X by far provides the smoothest experience on any apple hardware. OS X was made specifically by apple for apple products. Windows on Mac is improving, yet will not match the smoothness of OS X, partly because apple who makes the bootcamp drivers want you to stick primarily with OS X. Linux runs more as less as smoothly as windows, however installing the drivers you need is more difficult and not guaranteed to work on all apple hardware. I would recommend OS X for everyday use, and to use windows or Linux when you need them for specific tasks.

---

### Post by ias on 2012-03-31
Thanks very much. The main novelty is that you can finally install ubuntu! rEFIT has the option to restore the MBR, and I did that. It hung on the Penguin, grayed out, however. I restarted in mac, then restarted with the penguin and it worked. Great.

---

### Post by bbhome on 2012-04-19
Thank you.  This post helped me get my Triple Boot MacbookPro5,1 (Lion, Win7, Ubuntu 11.10) working!  

One simplification I found was I was able to use the Ubuntu Alternate CD (ubuntu-11.10-alternate-i386.iso) instead of the Ubuntu Live CD.  Using the Alternate CD I did not have to use a USB installer as well.

After initially installing ubuntu it would freeze after selecting the kernel from the grub menu.  I forced it to boot to a command line using info from this [thread]("http://ubuntuforums.org/showthread.php?t=1904347").  I then was able to see that it froze after printing:

> [drm] nouveau 0000:02:00.0: PRAMIN flush timeout

I found the solution from this [thread]("http://ubuntuforums.org/showthread.php?p=9036898").  Basically I had to add "nomodeset" to the kernel command-line by editing the grub boot line.

This allowed Ubuntu to boot in graphical mode.  I then installed "additional drivers" for nvidia and broadcom. Reboot and now Ubuntu 11.10 seems to be working.

I noticed [others]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Oneiric") had issues getting Ubuntu 11.10 running on MacBookPro5,1.  I'm guessing the nouveau issue is the problem.

---

### Post by perrya on 2012-06-01
> **tgeulin said:**
> Alright, so I begin knowing that their are many such posts out their such as this. This however, is what worked for me, and so i thought i would share. My experience was mostly trial and error and my solution came from researching other fixes. For this guide I am assuming that you know your way around your mac fairly well. Although if i have posted this in the wrong place, i apologize. But i digress...

My hardware: MacbookPro8,2

The problems
[LIST]
[*]Lion recovery partition getting in the way
[*]Windows not booting after installing Ubuntu&#8230;. "missing operating system"
[*]refit not installing properly
[/LIST]

The solution:

download and install got fdisk for mac... [http://sourceforge.net/projects/gptfdisk/]("http://sourceforge.net/projects/gptfdisk/")
download rEFIt... [http://refit.sourceforge.net/]("http://refit.sourceforge.net/")

MAKE BACKUP: once gdisk is installed go to terminal and type 'sudo disk /dev/disk0'. it will take you to the disk menu. once there enter 'b', and type a file name (it will automatically save in your home folder). once finish quit by entering 'q'
 
installing refit... many people have difficulty installing refit. the trick is to install it manually (check out refit's documentation). reboot and you should see your new loader.

partition your disk... you need to create two new partitions for windows and linux (disk utility works just fine). format both of them to FAT.

install windows 7.... in the installer format the disk you want windows on as ntfs and finish through installation (note:your computer will reboot several times and each time it does make sure to boot from your new windows partition under refit). Once its all finished go ahead and install your boot camp drivers. your eject key won't work yet so you'll have to eject the setup disk from the control panel.

install ubuntu... for this you are going to need both a live usb and live cd. create live usb: [http://www.nightlion.net/guides/2011/burn-iso-to-bootable-usb-flash-drive-in-mac-osx-terminal-via-command-line-diskutil/]("http://www.nightlion.net/guides/2011/burn-iso-to-bootable-usb-flash-drive-in-mac-osx-terminal-via-command-line-diskutil/") and for the live cd simply burn the .iso with disk utility. with both the cd and the usb inserted in the computer, reboot and hold down the 'C' key on restart. It may take several minutes but you should get to the installer. In the installer select the advanced installation option. format and use the partition you set aside for linux. set the mount point to '/' and *install the grub boot loader to whatever partition your installing linux on. It will give you a warning about not having a swap partition, but you can ignore this for now and create a swap file inside your ubuntu later. install and reboot back into lion

At the moment you now have a screwed up hybrid mbr table (this is because most likely your lion recovery disk uses one of your precious mbr slots)
in order to fix this we are going to create a new hybrid mbr table. i have attached screenshots of this process.
reopen terminal and again type 'sudo gdisk /dev/disk0'. this time enter 'r'. and then 'p'. this will print your partitions. now you need to create your hmbr so type 'h'. it will now ask you for the partitions you wish to enter. referring to the printed partition list, add your lion, windows and linux partitions. (in my case 2 4 5). next it will ask you to place efi partition first, select 'y'. now it will ask you for the mbr hex code for each partition. the codes you want are 'AF' for lion, '07' for windows, and '83' for linux. don't set any of the bootable flags. once finish enter 'w' to write these changes to the disks. You can also enter 'q' if you want to quit without saving changes. reboot and now you should be able to boot into each of your OSes. 



Tip: if for some reason it doesn't work and you want to restore your gpt table, simply go back to gdisk, enter 'r', enter 'l', and then type your backup filename. reboot and you'll no longer have you win or linux partitions but your gpt will gpt table will be back to normal.

i hope this helps any and all of you. its not the prettiest guides and for that i apologize, but if you have any questions i'd be glad to answer them.

Cheers!

EDIT: if you want a 'common' partition, simply create three new partition at the beginning(one for win7, one for ubuntu, one for common).
         If you decide that you want a shared partition after you install win7 and ubuntu, simply create a new partition and the recreate your hybrid mbr as described above.

_**Dual Boot Snow Leopard OS X 10.6 (Late 2009 iMAC Core 2 Duo) & Ubuntu 11.10 (32-bit) Successful !!!**_
*June 1st, 2012*

There were a couple things I had to do in addition to this post.

> At the moment you now have a screwed up hybrid mbr table (this is because most likely your lion recovery disk uses one of your precious mbr slots)
in order to fix this we are going to create a new hybrid mbr table. i have attached screenshots of this process.
reopen terminal and again type 'sudo gdisk /dev/disk0'. this time enter 'r'. and then 'p'. this will print your partitions. now you need to create your hmbr so type 'h'. it will now ask you for the partitions you wish to enter. referring to the printed partition list, add your lion, windows and linux partitions. (in my case 2 4 5). next it will ask you to place efi partition first, select 'y'. now it will ask you for the mbr hex code for each partition. the codes you want are 'AF' for lion, '07' for windows, and '83' for linux. don't set any of the bootable flags. once finish enter 'w' to write these changes to the disks. You can also enter 'q' if you want to quit without saving changes. reboot and now you should be able to boot into each of your OSes. 

The latest version of gdisk has an additional question before you select 'w'. I don't remember the question now but I said 'no' to it. [I found gdisk here]("http://download.opensuse.org/repositories/home:/srs5694/xUbuntu_11.10/i386/"). (I had to learn how to install using the deb command, I think the command went something like *sudo deb --install gdisk*.deb*) From the Ubuntu 11.10 Live CD (In "Try Ubuntu" mode) I issued the following;

***sudo gdisk /dev/disk0***

After that I ran [gptsync_014]("http://packages.debian.org/sid/i386/gptsync/download") (download the latest version as only 014 or above was capable of fixing this issue) just to see what it had to say. It indicated that it had to perform a resync. I did just that and it worked just fine. (Install command for gptsync is something like *sudo deb --install gpts*.deb*, please check on how to use deb properly, that's just from recollection).

I think the command was something like

***sudo gptsync /dev/sda***

[URL="http://mac.linux.be/content/problems-refit-and-grub-after-installation"]more on how to use gptsync here
[/URL]

Once I ran that I shutdown the system as per the instructions of rEFit. When I rebooted however the Ubuntu installation did NOT initially run. When I was about to give up I happened to remember an instruction to run a 'bless' command on the partition. I did this from OS X. (I did not reinstall grub however I did make an attempt and it didn't work, so I took a chance on not doing that) (also, I had to *manually* install [rEFit]("http://refit.sourceforge.net/doc/c1s1_install.html") and tested to make sure it was working before I did anything !!! rEFit comes with a readme on how to that)

***bless --device /dev/disk0s4 --setBoot --legacy***

[More on how to setup a dual-boot Snow Leopard / Ubuntu style here!]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation")

in my case Ubuntu was installed on /dev/sda4 (yours may be different so the /dev/disk0s4 has to be logically in reference to your setup)

After I 'bless'ed the partition I did a shutdown I think then rebooted and just happened to check one more time for the Linux partition to work. It did!!!!

So....

Special thanks to everyone that helped make this possible. In my particular case Snow Leopard was fine for a development environment but given that my servers are running Ubuntu 11.04 I needed to setup a Ubuntu development environment on my desktop in order to *resolve* differences.

Thank you very much for taking the time to post the above and all the other pages on the web, you really helped me out on this. Your time and efforts are greatly appreciated !!!

Perry

Ps.
In my case I had a fresh Snow Leopard install on 1/2 of the 1 trig drive. So I could have reinstalled should something go wrong but I didn't have to. I did not have to repartition however I did have to use **[gparted]("http://gparted.sourceforge.net/")** off the Ubuntu 11.10 install Live CD to add a new partition and swap drive. I then had to manually make sure that this partition would be used during the install. (Also, i recommend using an earlier version of Ubuntu than the very latest as it is sure to have it's kinks worked out and also selecting the 32-bit version turned out to be a really good idea!) Good Luck !!!

-------
Perry Anderson
Software developer
St. John's, Newfoundland
[www.unifiedobjects.net](www.unifiedobjects.net)

---

### Post by nmante on 2012-06-01
> **tgeulin said:**
> Alright, so I begin knowing that their are many such posts out their such as this. This however, is what worked for me, and so i thought i would share. My experience was mostly trial and error and my solution came from researching other fixes. For this guide I am assuming that you know your way around your mac fairly well. Although if i have posted this in the wrong place, i apologize. But i digress...

My hardware: MacbookPro8,2

The problems
[LIST]
[*]Lion recovery partition getting in the way
[*]Windows not booting after installing Ubuntu…. "missing operating system"
[*]refit not installing properly
[/LIST]

The solution:

download and install got fdisk for mac... [http://sourceforge.net/projects/gptfdisk/]("http://sourceforge.net/projects/gptfdisk/")
download rEFIt... [http://refit.sourceforge.net/]("http://refit.sourceforge.net/")

MAKE BACKUP: once gdisk is installed go to terminal and type 'sudo disk /dev/disk0'. it will take you to the disk menu. once there enter 'b', and type a file name (it will automatically save in your home folder). once finish quit by entering 'q'
 
installing refit... many people have difficulty installing refit. the trick is to install it manually (check out refit's documentation). reboot and you should see your new loader.

partition your disk... you need to create two new partitions for windows and linux (disk utility works just fine). format both of them to FAT.

install windows 7.... in the installer format the disk you want windows on as ntfs and finish through installation (note:your computer will reboot several times and each time it does make sure to boot from your new windows partition under refit). Once its all finished go ahead and install your boot camp drivers. your eject key won't work yet so you'll have to eject the setup disk from the control panel.

install ubuntu... for this you are going to need both a live usb and live cd. create live usb: [http://www.nightlion.net/guides/2011/burn-iso-to-bootable-usb-flash-drive-in-mac-osx-terminal-via-command-line-diskutil/]("http://www.nightlion.net/guides/2011/burn-iso-to-bootable-usb-flash-drive-in-mac-osx-terminal-via-command-line-diskutil/") and for the live cd simply burn the .iso with disk utility. with both the cd and the usb inserted in the computer, reboot and hold down the 'C' key on restart. It may take several minutes but you should get to the installer. In the installer select the advanced installation option. format and use the partition you set aside for linux. set the mount point to '/' and *install the grub boot loader to whatever partition your installing linux on. It will give you a warning about not having a swap partition, but you can ignore this for now and create a swap file inside your ubuntu later. install and reboot back into lion

At the moment you now have a screwed up hybrid mbr table (this is because most likely your lion recovery disk uses one of your precious mbr slots)
in order to fix this we are going to create a new hybrid mbr table. i have attached screenshots of this process.
reopen terminal and again type 'sudo gdisk /dev/disk0'. this time enter 'r'. and then 'p'. this will print your partitions. now you need to create your hmbr so type 'h'. it will now ask you for the partitions you wish to enter. referring to the printed partition list, add your lion, windows and linux partitions. (in my case 2 4 5). next it will ask you to place efi partition first, select 'y'. now it will ask you for the mbr hex code for each partition. the codes you want are 'AF' for lion, '07' for windows, and '83' for linux. don't set any of the bootable flags. once finish enter 'w' to write these changes to the disks. You can also enter 'q' if you want to quit without saving changes. reboot and now you should be able to boot into each of your OSes. 



Tip: if for some reason it doesn't work and you want to restore your gpt table, simply go back to gdisk, enter 'r', enter 'l', and then type your backup filename. reboot and you'll no longer have you win or linux partitions but your gpt will gpt table will be back to normal.

i hope this helps any and all of you. its not the prettiest guides and for that i apologize, but if you have any questions i'd be glad to answer them.

Cheers!

EDIT: if you want a 'common' partition, simply create three new partition at the beginning(one for win7, one for ubuntu, one for common).
         If you decide that you want a shared partition after you install win7 and ubuntu, simply create a new partition and the recreate your hybrid mbr as described above.

When you are creating this common partition on the Mac, what format should it be in?  FAT, Free Space, ExFAT?  Also, is there a hex code for the common partition or is it not necessary?

---

### Post by jvcleave on 2012-06-03
> **tgeulin said:**
> 

My hardware: MacbookPro8,2

what version of linux was this? Did video work out of the box? I have tried just about everything from 10 - 12.10 and can only get video with nomodeset. I eventually endup with a system that can boot to the CLI but that is it

---

### Post by markthekdeguy on 2012-06-23
Tried all this, didn't work for me on my Macbook Pro 5.1,
during install, it recommended separate (min 20mb) boot thingy, so i did as advised.(it said its not same as a seperate /boot partition)
just get a flashing cursor top left :(

---

### Post by Chazzer on 2012-06-29
Thank you for this post, it saved me a lot of time. The only thing I am not clear about is the need for 2 Ubuntu install sources. I only needed the DVD, no USB install drive.
My existing triple boot with Snow Leopard fell apart after upgrading to Lion and I was left with only Ubuntu working.

This is the order that I reinstalled with no need of a second Ubuntu install media...
[B][LIST=1]
[*]Format the HDD to HFS+ and install Lion.
[*]Update Lion.
[*]Download and install rEFIt.
[*]Create two FAT32 partitions using Disk Utility.
[*]Reboot the Macbook with Windows Install Disk.
[*]Reformat one FAT32 partition to NTFS and install Windows 7 on it.
[*]Reboot Macbook with Windows 7 and install Apple drivers from USB drive.
[*]Reboot Macbook with Ubuntu Install Disk.
[*]Reformat remaining FAT32 partition to Ext4 and install Ubuntu 12.04 on it.
[*][COLOR="Red"]After rebooting Macbook, Ubuntu will not load, "Missing Operating System"![/COLOR]
[*]Reboot to OSX, download and install gdisk.
[*]Follow gdisk partition modification instructions provided by "tgiulin".
[/LIST]
[/B]Everything works fine, thanks again.

---

### Post by alchemistry on 2012-07-06
Hello, 

the Tutorial works fine on my System (Macbook 7.1, Lion, Win7, Precise). I followed it except of installing Windows straight via Bootcamp software and resizing the Macintosh HD via disk utility. 
Besides I have created a Data HD
After installing Ubuntu and reconfiguring the hMBR via gdisk GRUB2 starts on both partitions Win7 and Ubuntu. While installing Ubuntu I chose to install the bootloader into the same partition unless I err. 
I would like to boot Win7 without GRUB 2 (and afterwards set the boottime delay to zero)

Aside from this I am not sure if it is really necessary to insert OS X into the MBR, according to the shortage of this hybride partitioning I would to put my data partition into the MBR partition table instead.


My Partition:
```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    293378383  Mac OS X HFS+
 3      293378384    294647919  Mac OS X Boot
 4      294647920   1719747431  Mac OS X HFS+
 5     1720010752   1835665407  Basic Data
 6     1835665408   1953523711  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    293378383  af  Mac OS X HFS+
 3     1720010752   1835665407  83  Linux
 4 *   1835665408   1953523711  07  NTFS/HPFS

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 293378384:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot

Partition at LBA 294647920:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 4, type Mac OS X HFS+

Partition at LBA 1720010752:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 5, type Basic Data
 Listed in MBR as partition 3, type 83  Linux

Partition at LBA 1835665408:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 6, type Basic Data
 Listed in MBR as partition 4, type 07  NTFS/HPFS, active

```

---

### Post by tgeulin on 2012-07-11
> **alchemistry said:**
> Hello, 

the Tutorial works fine on my System (Macbook 7.1, Lion, Win7, Precise). I followed it except of installing Windows straight via Bootcamp software and resizing the Macintosh HD via disk utility. 
Besides I have created a Data HD
After installing Ubuntu and reconfiguring the hMBR via gdisk GRUB2 starts on both partitions Win7 and Ubuntu. While installing Ubuntu I chose to install the bootloader into the same partition unless I err. 
I would like to boot Win7 without GRUB 2 (and afterwards set the boottime delay to zero)

Aside from this I am not sure if it is really necessary to insert OS X into the MBR, according to the shortage of this hybride partitioning I would to put my data partition into the MBR partition table instead.


My Partition:
```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    293378383  Mac OS X HFS+
 3      293378384    294647919  Mac OS X Boot
 4      294647920   1719747431  Mac OS X HFS+
 5     1720010752   1835665407  Basic Data
 6     1835665408   1953523711  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    293378383  af  Mac OS X HFS+
 3     1720010752   1835665407  83  Linux
 4 *   1835665408   1953523711  07  NTFS/HPFS

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 293378384:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot

Partition at LBA 294647920:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 4, type Mac OS X HFS+

Partition at LBA 1720010752:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 5, type Basic Data
 Listed in MBR as partition 3, type 83  Linux

Partition at LBA 1835665408:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 6, type Basic Data
 Listed in MBR as partition 4, type 07  NTFS/HPFS, active

```
hi alchemistry,

If you don't insert OS X into the mbr, I don't think you'll be able to access your OS X HD, but if you have a data HD i guess that won't be a problem. Are you using refit? you're correct, grub2 should be installed on the same partition as ubuntu, so it sounds like for some reason booting windows, actually boots into ubuntu. my guess is that its because your ubuntu partition is listed before windows, i would try recreating your mbr so that windows is first. 

tgeulin

---

### Post by alchemistry on 2012-07-17
Hello,
I solved the problem guessing that grub2 was written to the mbr. so i used boot-repair to delete grub2 from mbr and wrote it to the partition. the results are a bit confusing:

1. afterwards mbr-partitiontable was screwed up again (first four gpt partitions were listed in mbr), so i modified it as before. afterwards:

2. using refit everything works fine - ubuntu boots via grub2, windows boots as if there were no linux. using the native bootmanager (pressing alt-key while start) it gives me the rEFIt, a Windows and a Recovery partition. booting from Windows results in grub2...

3. on OS X Lion Disk Utility there are not any Linux and Bootcamp partitions but a unmounted and not mountable disk0.5. with an invalid sector size=0.

4. the protective-mbr-data read out via gdisk on ubuntu and on os x vary in boot-flags (ubuntu-gdisk shows linux hd boot-flagged, macintosh-gdisk shows bootcamp boot-flagged). refit partitioning tool also shows bootcamp boot-flagged.

5. maybe the gpt-partition-code of linux hd or bootcamp is wrong? it differs from yours, tgeulin.


Partition Inspector Results

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    293378383  Mac OS X HFS+
 3      293378384    294647919  Mac OS X Boot
 4      294647920   1719747431  Mac OS X HFS+
 5     1720010752   1835665407  Basic Data
 6     1835665408   1953523711  EFI System (FAT)

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    293378383  af  Mac OS X HFS+
 3 *   1720010752   1835665407  83  Linux
 4     1835665408   1953523711  07  NTFS/HPFS

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 293378384:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot

Partition at LBA 294647920:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 4, type Mac OS X HFS+

Partition at LBA 1720010752:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 5, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 1835665408:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 6, type EFI System (FAT)
 Listed in MBR as partition 4, type 07  NTFS/HPFS

```

---

### Post by YannBuntu on 2012-07-18
Hello
Has anyone managed to use grub-efi instead of Refit ?

---

### Post by supermario87 on 2012-07-23
this would work also with debian according to you??

---

### Post by seandgibbonsy on 2012-07-23
> **Chazzer said:**
> Thank you for this post, it saved me a lot of time. The only thing I am not clear about is the need for 2 Ubuntu install sources. I only needed the DVD, no USB install drive.
My existing triple boot with Snow Leopard fell apart after upgrading to Lion and I was left with only Ubuntu working.

This is the order that I reinstalled with no need of a second Ubuntu install media...
[B][LIST=1]
[*]Format the HDD to HFS+ and install Lion.
[*]Update Lion.
[*]Download and install rEFIt.
[*]Create two FAT32 partitions using Disk Utility.
[*]Reboot the Macbook with Windows Install Disk.
[*]Reformat one FAT32 partition to NTFS and install Windows 7 on it.
[*]Reboot Macbook with Windows 7 and install Apple drivers from USB drive.
[*]Reboot Macbook with Ubuntu Install Disk.
[*]Reformat remaining FAT32 partition to Ext4 and install Ubuntu 12.04 on it.
[*][COLOR="Red"]After rebooting Macbook, Ubuntu will not load, "Missing Operating System"![/COLOR]
[*]Reboot to OSX, download and install gdisk.
[*]Follow gdisk partition modification instructions provided by "tgiulin".
[/LIST]
[/B]Everything works fine, thanks again.

After installing, is the Recovery HD still available (either in the rEFIt loader or bootcamp loader) or detectable by OS X?

---

### Post by Nikki1993 on 2012-07-24
> After installing, is the Recovery HD still available (either in the rEFIt loader or bootcamp loader) or detectable by OS X?
yea I also want to know that. Planning to install ubuntu as 3 operating system on Mac and my first attempt (before this guide) ended in destroying my Recovery HD partition.

---

### Post by seandgibbonsy on 2012-07-25
> **Nikki1993 said:**
> yea I also want to know that. Planning to install ubuntu as 3 operating system on Mac and my first attempt (before this guide) ended in destroying my Recovery HD partition.
I'll be trying it out today, as I'm doing a fresh install for Mountain Lion and also wanted to change the sizes of some of my partitions.  I will report back with my findings.

---

### Post by Nikki1993 on 2012-07-25
>  			 		 	 	 I'll be trying it out today, as I'm doing a fresh install for  Mountain Lion and also wanted to change the sizes of some of my  partitions.  I will report back with my findings. 	
Oh cool thanks I'll be waiting for your reply!

---

### Post by seandgibbonsy on 2012-07-26
> **Nikki1993 said:**
> Oh cool thanks I'll be waiting for your reply!

I've now finished the installation procedures. I can confirm that Chazzer's instructions (coupled with tgiulin's gdisk instructions) now have all three operating systems working, as well as a working recovery partition when using the BootCamp bootloader (holding alt on startup).
Success!

---

### Post by Nikki1993 on 2012-07-26
> **seandgibbonsy said:**
> I've now finished the installation procedures. I can confirm that Chazzer's instructions (coupled with tgiulin's gdisk instructions) now have all three operating systems working, as well as a working recovery partition when using the BootCamp bootloader (holding alt on startup).
Success!
That's awesome to hear, thank you for your reply. I'm glad that the recovery partition is on its place because the first time it was wiped out by the Ubuntu installation.

---

### Post by eatfoodnow on 2012-07-29
I have a MBP from early 2011, with the 2.2ghz i7 and 6750m, and I've had it since late 2011.  As soon as I got it, I used bootcamp to install Windows 7. That's been working fine up until now, when I want to also install Ubuntu 12.04 and triple boot the three OS. I want to keep my data intact and not have to reinstall anything.

I went through all the steps in the tutorial and everything seemed to go along fine, nothing is broken and I can still boot into OSX and Windows7. Also, rEFIt is working fine. However, rEFIt doesn't include the option to boot into Ubuntu (which I installed without any errors). Holding down the option key to bring up the bootcamp startup menu lets me choose from rEFIt, windows, and the recovery partition. I tried windows through that and it brought me into windows (I had read somewhere that some people set that up as the way to boot into linux). After I did that, I tried booting into windows through rEFIt and it didn't work.

So, obviously something went wrong along the way. I started the partitioning tool in rEFIt on startup and it displayed something like this (typing in the information since I can't copy/paste and I don't have a good camera to take a readable photo).

--------

Current GPT partition table:
# | start | end | type
1 | 40 | 409639 | EFI System (FAT)
2 | 409640 | 488996303 | Mac OS X HFS+
3 | 488996304 | 490265839 | Mac OS X Boot
4 | 823945216 | 1465147391 | Basic Data (side-note: this is my windows partition)
5 | 490265840 | 823943574 | Basic Data (linux partition)

Current MBR partition table: (this is what I changed it to be, like the tutorial said to do)
# | start | end | type
1 | 1 |409639 | EE | EFI Protective
2 | 409640 | 488996303 | AF | Mac OS X HFS+
3* | 823945216 | 1465147391 | 07 | NTFS/HPFS (* on screen indicates a change?)
4 | 490265840 | 823943574 | 83 | Linux

Status: MBR table must be updated

Proposed new MBR partition table:
# | start | end | type
1 | 1 |409639 | EE | EFI Protective
2 | 409640 | 488996303 | AF | Mac OS X HFS+
3 | 488996304 | 490265839 | AB | Mac OS X Boot
4* | 490265840 | 1465147391 | 07 | NTFS/HPFS

--------
Then it asks me if I want to update the MBR as printed above. I have not said yes, since it seems like that would cause a loooot of problems. Should I redo the hybrid MBR and set up four partitions (osx boot, osx, linux, windows)? What can I do to fix this?

My linux partition is in-between my osx and windows partitions because i shrunk the size of my osx partition using disk utility to make room for the new partition.


So, my main problem is linux not showing up in rEFIt. How can I fix this? I also can't boot into windows through rEFIt now, but that problem will probably be fixed when this main issue is solved, and it's not an issue since booting through bootcamp still works. Thanks!

UPDATE: nevermind about booting into windows from rEFIt, it's working now. I didn't change anything, it just worked though.

---

### Post by Rutto on 2012-08-06
I had no clue what to do to fix Windows 7, this guide made my day! Thanks!

---

### Post by pratnala on 2012-08-28
> **tgeulin said:**
> Alright, so I begin knowing that their are many such posts out their such as this. This however, is what worked for me, and so i thought i would share. My experience was mostly trial and error and my solution came from researching other fixes. For this guide I am assuming that you know your way around your mac fairly well. Although if i have posted this in the wrong place, i apologize. But i digress...

My hardware: MacbookPro8,2

The problems
[LIST]
[*]Lion recovery partition getting in the way
[*]Windows not booting after installing Ubuntu…. "missing operating system"
[*]refit not installing properly
[/LIST]

The solution:

download and install got fdisk for mac... [http://sourceforge.net/projects/gptfdisk/](http://sourceforge.net/projects/gptfdisk/)
download rEFIt... [http://refit.sourceforge.net/](http://refit.sourceforge.net/)

MAKE BACKUP: once gdisk is installed go to terminal and type 'sudo disk /dev/disk0'. it will take you to the disk menu. once there enter 'b', and type a file name (it will automatically save in your home folder). once finish quit by entering 'q'
 
installing refit... many people have difficulty installing refit. the trick is to install it manually (check out refit's documentation). reboot and you should see your new loader.

partition your disk... you need to create two new partitions for windows and linux (disk utility works just fine). format both of them to FAT.

install windows 7.... in the installer format the disk you want windows on as ntfs and finish through installation (note:your computer will reboot several times and each time it does make sure to boot from your new windows partition under refit). Once its all finished go ahead and install your boot camp drivers. your eject key won't work yet so you'll have to eject the setup disk from the control panel.

install ubuntu... for this you are going to need both a live usb and live cd. create live usb: [http://www.nightlion.net/guides/2011/burn-iso-to-bootable-usb-flash-drive-in-mac-osx-terminal-via-command-line-diskutil/](http://www.nightlion.net/guides/2011/burn-iso-to-bootable-usb-flash-drive-in-mac-osx-terminal-via-command-line-diskutil/) and for the live cd simply burn the .iso with disk utility. with both the cd and the usb inserted in the computer, reboot and hold down the 'C' key on restart. It may take several minutes but you should get to the installer. In the installer select the advanced installation option. format and use the partition you set aside for linux. set the mount point to '/' and *install the grub boot loader to whatever partition your installing linux on. It will give you a warning about not having a swap partition, but you can ignore this for now and create a swap file inside your ubuntu later. install and reboot back into lion

At the moment you now have a screwed up hybrid mbr table (this is because most likely your lion recovery disk uses one of your precious mbr slots)
in order to fix this we are going to create a new hybrid mbr table. i have attached screenshots of this process.
reopen terminal and again type 'sudo gdisk /dev/disk0'. this time enter 'r'. and then 'p'. this will print your partitions. now you need to create your hmbr so type 'h'. it will now ask you for the partitions you wish to enter. referring to the printed partition list, add your lion, windows and linux partitions. (in my case 2 4 5). next it will ask you to place efi partition first, select 'y'. now it will ask you for the mbr hex code for each partition. the codes you want are 'AF' for lion, '07' for windows, and '83' for linux. don't set any of the bootable flags. once finish enter 'w' to write these changes to the disks. You can also enter 'q' if you want to quit without saving changes. reboot and now you should be able to boot into each of your OSes. 



Tip: if for some reason it doesn't work and you want to restore your gpt table, simply go back to gdisk, enter 'r', enter 'l', and then type your backup filename. reboot and you'll no longer have you win or linux partitions but your gpt will gpt table will be back to normal.

i hope this helps any and all of you. its not the prettiest guides and for that i apologize, but if you have any questions i'd be glad to answer them.

Cheers!

EDIT: if you want a 'common' partition, simply create three new partition at the beginning(one for win7, one for ubuntu, one for common).
         If you decide that you want a shared partition after you install win7 and ubuntu, simply create a new partition and the recreate your hybrid mbr as described above.


After installing Ubuntu, can I just run rEFIt's tool to fix the partition table?

---

### Post by Armaeddon on 2012-09-24
This is great! I can confirm that it works on a Macbook Pro 6,2 with Ubuntu 12.04, Windows 7 x64, and Mac OSX Mountain Lion.

One thing though, if you plan on restoring a Windows Partition from a system restore image, it will not work.

---

### Post by bastienb11 on 2012-10-09
Triple boot with windows 8 is working. I made it (not with this tuto but I think it will work too). Drivers for trackpad get by Bootcamp working well.

Here a video I made just to show the booting time of every OS : [http://youtu.be/9GX3J1kAj1k](http://youtu.be/9GX3J1kAj1k)

---

### Post by Sargatanus on 2012-10-14
It... it works!! I can't believe it works! Do I need to install drivers for my machine on my Ubuntu 12.04 partition?

---

### Post by dimtarsp on 2012-12-27
Hello, and thank you for posting this thread!

I am successfully triple booting with Mac OS 10.6.8, Win 8 Pro, and Ubuntu 12.10 on Macbook Pro 4.1 (Early 2008) with all drivers working properly following this thread. Ubuntu boot loader is installed on the same partition as Ubuntu, and I have created and extra swap partition.

I have also created a FAT shared data partition that I can see and edit in both Mac and Ubuntu, but I cannot see in Windows. When I view the drive/partition tool in windows, it displays the shared FAT partition as unallocated space. 

I also tried to recreate the shared partition within Ubuntu, by erasing the partition, making a new FAT partition and then fixing the MBR table with gdisk in Mac OS, but with the exact same result (seeing the partition in both Mac and Ubuntu but not seeing it in Win) as before. And now I also have the drive showing up in refit. 

Any suggestions will greatly be appreciated on getting the shared partition to mount on windows.

Here is my MBR and GPT layout:

> 
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     98065895  Mac OS X HFS+
 3       98328576    293640191  Basic Data [win8 partition]
 4      293640192    342466363  Basic Data [ubuntu partition]
 5      342466364    467394294  Basic Data [shared data partition]
 6      467433472    468860927  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     98065895  af  Mac OS X HFS+
 3 *     98328576    293640191  07  NTFS/HPFS
 4      293640192    342466363  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 98328576:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 07  NTFS/HPFS, active

Partition at LBA 293640192:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 342466364:
 Boot Code: Unknown, but bootable
 File System: FAT32
 Listed in GPT as partition 5, type Basic Data

Partition at LBA 467433472:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 6, type Linux Swap



---

### Post by Super Man on 2013-01-08
> **dimtarsp said:**
> Hello, and thank you for posting this thread!

I am successfully triple booting with Mac OS 10.6.8, Win 8 Pro, and Ubuntu 12.10 on Macbook Pro 4.1 (Early 2008) with all drivers working properly following this thread. Ubuntu boot loader is installed on the same partition as Ubuntu, and I have created and extra swap partition.

I have also created a FAT shared data partition that I can see and edit in both Mac and Ubuntu, but I cannot see in Windows. When I view the drive/partition tool in windows, it displays the shared FAT partition as unallocated space. 

I also tried to recreate the shared partition within Ubuntu, by erasing the partition, making a new FAT partition and then fixing the MBR table with gdisk in Mac OS, but with the exact same result (seeing the partition in both Mac and Ubuntu but not seeing it in Win) as before. And now I also have the drive showing up in refit. 

Any suggestions will greatly be appreciated on getting the shared partition to mount on windows.

Here is my MBR and GPT layout:

I have the same problem and I don't know what to do.

---

### Post by superchuckinator on 2013-01-25
I'm stuck looking at a pretty purple and orange background with a cursor and a status bar. There are volume and gear icons in the task bar, but clicking them does nothing. Any ideas?
[IMG]http://i.imgur.com/dkhxXXGl.jpg[/IMG]
I was stuck looking at this for forever

EDIT: FIXED! Turns out it was just taking forever, I left to go out to dinner with my family and when I came back I was on the desktop!

---

### Post by rohitdewani on 2013-03-06
Hi,

I had installed windows with the help of bootcamp and then later on I partitioned my mac HD to install linux and linux swap partitions.
Then my windows 7 stopped loading. Give some boot loader error.But my mac OSX and linux work perfectly.
Now i came across your article and after printing the partitions this is what i got


Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640      1167552039   556.5 GiB   AF00  Macintosh HD
   3      1167552040      1168821575   619.9 MiB   AB00  Recovery HD
   4      1168822272      1227413503   27.9 GiB    0700  LINUX
   5      1227415552      1228242943   404.0 MiB   8200  LINUX SWAP
   6      1228242944      1465147391   113.0 GiB   0700  BOOTCAMP

I have a lot of homework saved on my linux and mac. And I really dont want to lose any of the partitions.
So should i go ahead and do the procedure you have mentioned?
I am skeptical because you did not have a linux swap partition.

---

### Post by tgeulin on 2013-03-11
> **dimtarsp said:**
> Hello, and thank you for posting this thread!

I am successfully triple booting with Mac OS 10.6.8, Win 8 Pro, and Ubuntu 12.10 on Macbook Pro 4.1 (Early 2008) with all drivers working properly following this thread. Ubuntu boot loader is installed on the same partition as Ubuntu, and I have created and extra swap partition.

I have also created a FAT shared data partition that I can see and edit in both Mac and Ubuntu, but I cannot see in Windows. When I view the drive/partition tool in windows, it displays the shared FAT partition as unallocated space. 

I also tried to recreate the shared partition within Ubuntu, by erasing the partition, making a new FAT partition and then fixing the MBR table with gdisk in Mac OS, but with the exact same result (seeing the partition in both Mac and Ubuntu but not seeing it in Win) as before. And now I also have the drive showing up in refit. 

Any suggestions will greatly be appreciated on getting the shared partition to mount on windows.

Here is my MBR and GPT layout:

Hi Dimtarsp and SuperMan,

Windows cannot recognize any partition not included in the hybrid mbr, and linux needs to be included in the mbr in order to boot, otherwise you'll get the "missing os" error at boot. this is because Ubuntu automatically installs itself with an emulated BIOS on mac... hence the hybrid mbr.
 
Something I have not tried that you may look into to, is installing Ubuntu in (U)EFI mode. Take a look here [http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/) and here [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting). If you succeed this way, then theoretically you could have OSX, WIN, and a shared partition in your hybrid mbr, and ubuntu as (U)EFI, so all partitions would boot and all they would all be visible to one another (except ubuntu within windows).

I would be interested in the result, share anything you come across :).

Cheers!

---

### Post by tgeulin on 2013-03-11
> **rohitdewani said:**
> Hi,

I had installed windows with the help of bootcamp and then later on I partitioned my mac HD to install linux and linux swap partitions.
Then my windows 7 stopped loading. Give some boot loader error.But my mac OSX and linux work perfectly.
Now i came across your article and after printing the partitions this is what i got


Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640      1167552039   556.5 GiB   AF00  Macintosh HD
   3      1167552040      1168821575   619.9 MiB   AB00  Recovery HD
   4      1168822272      1227413503   27.9 GiB    0700  LINUX
   5      1227415552      1228242943   404.0 MiB   8200  LINUX SWAP
   6      1228242944      1465147391   113.0 GiB   0700  BOOTCAMP

I have a lot of homework saved on my linux and mac. And I really dont want to lose any of the partitions.
So should i go ahead and do the procedure you have mentioned?
I am skeptical because you did not have a linux swap partition.

Hi rohitdewani,

Simply add your OSX, WIN and LINUX partitions to your hybrid mbr to make them all boot correctly. However, to make them all play nice with one another, I would add your WIN partition in front of LINUX. So when prompted, enter "2 6 4" as the partitions to add to your mbr. This process adds your partitions to the hybrid mbr, and does not touch the data inside the partitions.

Cheers!

---

### Post by tgeulin on 2013-03-11
**Update to my original thread: I now use rEFInd as an alternative to rEFIt. rEFInd is an open source fork of rEFIt and provides better support. From Rod Smith, the same guy who provided GPT fdisk. Check it out here! [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)**

---

### Post by rvb3n on 2013-03-11
Hi and first of all thank you for your guide!

I am finally able to triple boot my MacBook Pro 8.2!

The only difference for me is that after the last step of your guide I had to install one more time rEFInd to see my partition again: is this normal?

Now I'm trying to make everthing working and I'm folliwing this guide: [https://help.ubuntu.com/community/MacBookPro8-2/Oneiric](https://help.ubuntu.com/community/MacBookPro8-2/Oneiric)

I started with the wi-fi related problem but I have a problem. The guide says that I have to install "[COLOR=#333333][FONT=Ubuntu]linux-backports-modules-cw-3.2-oneiric-generic", but I'm not able to find it anywhere: can you tell me how did you solved this problem (since you have the same MacBook Pro)?[/FONT][/COLOR]

---

### Post by tgeulin on 2013-03-18
> **rvb3n said:**
> Hi and first of all thank you for your guide!

I am finally able to triple boot my MacBook Pro 8.2!

The only difference for me is that after the last step of your guide I had to install one more time rEFInd to see my partition again: is this normal?

Now I'm trying to make everthing working and I'm folliwing this guide: [https://help.ubuntu.com/community/MacBookPro8-2/Oneiric](https://help.ubuntu.com/community/MacBookPro8-2/Oneiric)

I started with the wi-fi related problem but I have a problem. The guide says that I have to install "[COLOR=#333333][FONT=Ubuntu]linux-backports-modules-cw-3.2-oneiric-generic", but I'm not able to find it anywhere: can you tell me how did you solved this problem (since you have the same MacBook Pro)?[/FONT][/COLOR]

I used the same guide to get my wifi card working except I just skipped the "[COLOR=#333333][FONT=Ubuntu]linux-backports-modules-cw-3.2-oneiric-generic" [/FONT][/COLOR]step.

---

### Post by d4m1r on 2013-04-10
For anyone else interested, I was successfully able to triple boot my  2012 13" MBP with OS X 10.8.3, Windows 7 x64, and Ubuntu 12.04.02 x64  using this thread and the one linked below. It was fairly tricky and especially time  consuming but it does work! Now with reFIT, I get a prompt and can boot  into either three OS's [IMG]http://cdn.macrumors.com/vb/images/smilies/smile.gif[/IMG]

[http://www.lifehacker.com.au/2010/05/how-to-triple-boot-your-mac-with-windows-and-linux-no-boot-camp-required/](http://www.lifehacker.com.au/2010/05/how-to-triple-boot-your-mac-with-windows-and-linux-no-boot-camp-required/)

Note: I installed both Windows 7 and Ubuntu via MBR and NOT EFI.  Possibly might work under EFI as well but I haven't personally tried it.  Went with MBR for simplicity but I don't know if installing them via  MBR and not EFI has any benefits **or** downsides for that matter....

---

### Post by gjf7 on 2013-04-28
Thanks for putting this guide up. I've followed the instructions but have ran into some problems and was hoping someone might be able to point out if I'm doing something wrong.

I'm running OSX 10.8.3 and would like to set up a triple boot with Windows 7 and Linux Mint Debian edition. I realize I'm on an Ubuntu forum, but I haven't been able to find any fix with my searches.

Here's my process:

1. Install rEFInd manually. Confirmed working on reboot.

2. Create one 40GB FAT32 partition for Windows 7 with Disk Utility. If I create both a partition for Windows and Linux, I am not able to format the Windows partition to NTFS with the Windows installer CD. The option is greyed out.

3. Boot from Windows CD, format to NTFS, install Windows 7, install Bootcamp drivers taken from Apple website. Reboot. Confirmed working.

4. Reboot into OSX and create one 30GB FAT32 Linux partition.

5. Reboot from LMDE CD with nomodeset option as per this guide: [http://forums.linuxmint.com/viewtopic.php?f=197&t=94579](http://forums.linuxmint.com/viewtopic.php?f=197&t=94579)

6. Partition ext4 and linux-swap as per the guide above. Install. Reboot into OSX!

7. Follow gdisk instructions from this guide. I have to use 2 5 4 for OSX, Windows and Linux respectively. No boot flags set. AF for OSX, 07 for W and 83 for Linux. This is what it looks like after typing "w".
```

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       819253591   390.5 GiB   AF00  Macintosh HD
   3       819253592       820523127   619.9 MiB   AB00  Recovery HD
   4       820525056       874926079   25.9 GiB    0700  
   5       879118336       976773119   46.6 GiB    0700  BOOTCAMP
   6       874926080       879118335   2.0 GiB     8200  


```

8. Reboot to rEFInd. I now have the boot to OSX option, two boot from vmlinuz options, a boot Linux from HD option and a boot Windows from partition 3 option. So first I want to check if Windows is running.

I choose the Windows option and GRUB begins to load! So I quickly press e and boot with nomodeset option. Install the nvidia drivers as per the linux mint debian guide above. I get a warning during the installation saying: "Conflicting nouveau kernel module loaded", "The free nouveau kernel module is currently loaded and conflicts with the non-free nvidia kernel module. The easiest way to fix this is to reboot the machine once the installation has finished."

Ok, so I let it finish. Then I reboot (through the strange windows from partition 3 option). The resolution is now even smaller and I can't even see the menu bar along the bottom. So I reboot into rEFInd again and try to see if choosing boot linux from HD option boots me into Windows. Nope. It says it can't find the operating system.

I managed to dual-boot OSX 10.6.8 (Snow Leopard) with rEFInd and Linux Mint Debian Edition, and never got the kernel module conflict error and everything worked fine. Upgraded to Mountain Lion and triple boot refuses to work. Tried doing everything from scratch a second time - same problem. Windows rEFInd icon boots Linux and Linux icon boots nothing, Linux nvidia drivers won't work. 

Any ideas?

---

### Post by gjf7 on 2013-04-29
Ok, I realized I was installing grub2 to the mbr. This was "breaking" the windows boot option.

(see: [http://refit.sourceforge.net/help/windows_boots_linux.html](http://refit.sourceforge.net/help/windows_boots_linux.html))

So I booted from CD, mounted my linux partition with 

```
sudo mount /dev/sda4 /mnt
```

 and tried manually installing grub2 via terminal after the installation but I ran into this error: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, ..."

So I tried a force install by typing:
```

sudo grub-install --root-directory=/mnt /dev/sda --force
```

Same problem.

I didn't try installing to /dev/sda4 because of the warnings and because I doubt that would make things any better...

8 hours later, I think I'm going to sleep...

---

### Post by gVes on 2013-05-10
check this method. doesnt require any refit or refind.


[http://www.youtube.com/watch?v=O40UG1guLeo](http://www.youtube.com/watch?v=O40UG1guLeo)

---

### Post by gVes on 2013-05-10
second part of the video also shows how to virtualise the OSes with VMware fusion! enjoy!!!

---

### Post by benfro6 on 2013-06-29
Joined up just to say thanks to all that contributed here. Exceptionally well written and clear, not to mention useful!

I appreciate all the help.

---

### Post by thetermonkao on 2013-07-04
[FONT=Verdana]> **scognito said:**
> I've created the shared partition at the beginning and it worked for win/lin/osx.[/FONT]> **scognito said:**
> 
[FONT=Verdana]After some days Win7 sees OSX partition instead of the shared one, and I don't know the why.[/FONT]

[FONT=Verdana]My hybrid MBR is:[/FONT]
[FONT=Verdana]1) Reserved[/FONT]
[FONT=Verdana]2) OSX[/FONT]
[FONT=Verdana]3) WIN[/FONT]
[FONT=Verdana]4) LINUX[/FONT]

[FONT=Verdana]Also [[COLOR=#222222]the data recovery of hard disk[/COLOR]]("http://www.iphone-mac.com/recover-data-from-macbook-hard-drive.html") has other 2 partition:[/FONT]
[FONT=Verdana]5) Shared partition (NTFS)[/FONT]
[FONT=Verdana]6) Linux swap[/FONT]

[FONT=Verdana]As said above, the shared is working on linux and osx. I think Windows can see *only* the Hybrid MBR partitions (indeed the reserved one is seen from win7 disk utility).[/FONT]
[FONT=Verdana]Still don't know why it worked initially, very confused.[/FONT]
If you remove the paritions you made, and leave the space as unallocated or combine it with an existing drive, it should return the BMR to the original number of partitions.  However I had tried this once with nothing but problems..
 
I think your only hope would be a Windows backup, providing you had made one of your windows system.  You can then boot with a Windows Rescue disk and restore the data.. but that all depends if you used Window's backup system to made a system image.
One word of caution though: Using the Windows's built-in recovery system also restors the partition that you had installed Windows.  This would be great in your case.. however if you had changed the partitions anyhow, windows with just copy its installation in the same spot, regardless of if you have another OS on that spot in the disk.. somewhat careless of MS actually.

---

### Post by tele51 on 2013-07-08
This guide worked for me, I can now triple boot OS X ML, Win7, Ubuntu 12.04 on my macbook pro 9,2 :D Much appreciated!!!

---

### Post by BiggerestAl on 2013-07-10
[COLOR=#000000]I am VERY new to all of this stuff and I have done everything correctly (to my knowledge) and there is just one last thing that I need to complete. I have triple booted my MacBookPro and I customized my ReFIT menu to have only three emblems in this order OS X (Mountain Lion), Ubuntu, and Windows 8. I want to boot straight into each OS when I select it from the ReFIT menu, but instead a purple GRUB menu comes up (if I choose Ubuntu or Windows) and I have to scroll through a bunch of different options to start up the OS I desire. My OS X (Mountain Lion) boots straight from ReFIT (without the GRUB menu) which is what I want for each OS but I don't know how to do so. So this is where I need help. Is it possible to boot into Windows 8 without having to select the OS from the purple GRUB menu. I just want everything to look clean and professional and if there is no way to do what I am asking still let me know. Remember, I am new to this and your advice and solutions would be much appreciated. [/COLOR]

[COLOR=#000000]Thank you,[/COLOR]

---

### Post by tgeulin on 2013-07-16
> **BiggerestAl said:**
> [COLOR=#000000]I am VERY new to all of this stuff and I have done everything correctly (to my knowledge) and there is just one last thing that I need to complete. I have triple booted my MacBookPro and I customized my ReFIT menu to have only three emblems in this order OS X (Mountain Lion), Ubuntu, and Windows 8. I want to boot straight into each OS when I select it from the ReFIT menu, but instead a purple GRUB menu comes up (if I choose Ubuntu or Windows) and I have to scroll through a bunch of different options to start up the OS I desire. My OS X (Mountain Lion) boots straight from ReFIT (without the GRUB menu) which is what I want for each OS but I don't know how to do so. So this is where I need help. Is it possible to boot into Windows 8 without having to select the OS from the purple GRUB menu. I just want everything to look clean and professional and if there is no way to do what I am asking still let me know. Remember, I am new to this and your advice and solutions would be much appreciated. [/COLOR]

[COLOR=#000000]Thank you,[/COLOR]

Did you install grub to /dev/sda or /dev/sdaX? (X being the ubuntu partition number)

---

### Post by dysonsphere232 on 2013-12-17
hi.
Using this guide (thanks BTW) I had a quite functional triple boot macbook pro (OSX Lion, Ubuntu,  Windows7), with all OSes sharing a common data storage partition, until I  upgraded to Mavericks via the apple store.  After that, Windows would  not recognize the common data disk as being formatted (the other OSes we  fine with it).  It seems that Windows changed the drive number of the  Mac HD to the one that was identifying the data HD (see image file).  In  my attempts to fix that problem (including using disk recovery  software) I inadvertently erased GRUB.  So then of course Ubuntu would  not boot up when I selected the Linux icon in rEFIt (windows booted up  in its stead).  I then reinstalled Ubuntu in the same location.  Then  rEFIT had a bunch more options for me to select from (see image file for  reference):


[LIST=1]
[*]"Boot EFI\ubuntu\shimx64.efi from EFI" - Boots grub. Ubuntu works fine
[*]"Boot EFI\ubuntu\grubx64.efi from EFI" - Boots grub. Ubuntu works fine
[*]"Boot EFI\ubuntu\MokManager.efi from EFI" - Opens uefi key management.
[LIST=1]
[*]Continue boot - does not boot
[*]Load key
[*]Load hash
[/LIST]

[*]"Boot Mac OS X from Macintosh HD" - Boots into OSX. Works fine.
[*]"Boot Mac OS X from Recovery HD" - Recovery disk. Don't even want to go there.
[*]"Boot Windows from Partition 3" - Boots windows. Works fine.
[*]"Boot Linux from Partition 4" - Boots grub. Ubuntu works fine.
[*]"Boot Windows from HD" - Boots grub. Ubuntu works fine.
[*]
[/LIST]
I  then noticed that rEFIt was no longer being updated, so I installed  rEFInd.  I installed as per the instructions on the developer's website  and all went well.  Now the first 2 options have Ubuntu icons and boot  up the GRUB screen (options for Ubuntu, Mac x32, Mac x64, and advanced)  and I can start Ubuntu from there.  The MokManager is now on the next  row (small icons).  The Mac OS X from Macintosh  works fine. The Mac OS X from Recovery is now on the next row (with a  life jacket icon). The first Windows icon boots into windows just fine.   The Linux (Tux) icon brings up the GRUB and I can start Ubuntu from  there.  The final Windows icon loads up Windows (unlike in rEFIt where  it brought up GRUB).  The hybrid MBR has been unchanged with the  upgrade.



The issue with Windows not recognizing the data partition persists.



At this point I am wondering:

[LIST=1]
[*] what are the extra boot options on the rEFIt screen?
[*]how can I get rid of them?
[*]should I reformat the data partition in Windows to have it recognized?
[/LIST]

Thanks in advance if anybody can help out.  Following are screenshots and terminal output:

[SIZE=1][FONT=arial][ATTACH=CONFIG]248690[/ATTACH][/FONT][/SIZE][SIZE=1][FONT=arial][ATTACH=CONFIG]248689[/ATTACH][/FONT][/SIZE][SIZE=1][FONT=arial][ATTACH=CONFIG]248691[/ATTACH][/FONT][/SIZE]From gdisk:
[SIZE=1][FONT=arial]kenneths-MacBook-Pro:~ dysonsphere$ sudo gdisk /dev/disk0[/FONT][/SIZE][SIZE=1][FONT=arial]Password:[/FONT][/SIZE]
[SIZE=1][FONT=arial]GPT fdisk (gdisk) version 0.8.6[/FONT][/SIZE]
[SIZE=1][FONT=arial]
[/FONT][/SIZE]
[SIZE=1][FONT=arial]Partition table scan:[/FONT][/SIZE]
[SIZE=1][FONT=arial]  [/FONT][/SIZE][SIZE=1][FONT=arial]MBR: hybrid[/FONT][/SIZE]

[SIZE=1][FONT=arial]  BSD: [/FONT][/SIZE][SIZE=1][FONT=arial]not present[/FONT][/SIZE]

[SIZE=1][FONT=arial]  APM: not present[/FONT][/SIZE]
[SIZE=1][FONT=arial]  GPT: present[/FONT][/SIZE]
[SIZE=1][FONT=arial]
[/FONT][/SIZE]
[SIZE=1][FONT=arial]Found valid GPT with hybrid MBR; using GPT.[/FONT][/SIZE]
[SIZE=1][FONT=arial]
[/FONT][/SIZE]
[SIZE=1][FONT=arial]Command (? for help): r[/FONT][/SIZE]
[SIZE=1][FONT=arial]
[/FONT][/SIZE]
[SIZE=1][FONT=arial]Recov[/FONT][/SIZE][SIZE=1][FONT=arial]ery/transformation command (? for help): p[/FONT][/SIZE]

[SIZE=1][FONT=arial]Disk /dev/disk0: 1465149168 sectors, 698.6 GiB[/FONT][/SIZE]
[SIZE=1][FONT=arial]Logical sector size: 512 bytes[/FONT][/SIZE]
[SIZE=1][FONT=arial]Disk identifier (GUID): 000052DF-3C5E-0000-4F13-0000225D0000[/FONT][/SIZE]
[SIZE=1][FONT=arial]Partition table holds up to 128 entries[/FONT][/SIZE]
[SIZE=1][FONT=arial]First usable sector is 34, last usable sector is 1465149134[/FONT][/SIZE]
[SIZE=1][FONT=arial]Partitions will be aligned on 8-sector boundaries[/FONT][/SIZE]
[SIZE=1][FONT=arial]Total free space is 3413 sectors (1.7 MiB)[/FONT][/SIZE]
[SIZE=1][FONT=arial]
[/FONT][/SIZE]
[SIZE=1][FONT=arial]Number  Start (sector)    End (sector)  Size       Code  Name[/FONT]
[/SIZE]
[SIZE=1][FONT=arial]   1              40          409639   200.0 MiB   EF00  EFI system partition[/FONT][/SIZE]
[SIZE=1][FONT=arial]   2          409640       195722135   93.1 GiB    AF00  Customer[/FONT]
[/SIZE]
[SIZE=1][FONT=arial]   3       195722136       196991671   619.9 MiB   AB00  Recovery HD[/FONT][/SIZE]
[SIZE=1][FONT=arial]   4       196993024       685271039   232.8 GiB   0700  WINDOWS HD[/FONT][/SIZE]

[SIZE=1][FONT=arial]   5       685271040       880583535   93.1 GiB[/FONT][/SIZE][SIZE=1][FONT=arial] 0700 [/FONT][/SIZE]
[SIZE=1][FONT=arial][/FONT][/SIZE]
[SIZE=1][FONT=arial]   6       880583536      1464886983   278.6 GiB   0700  Storage[/FONT][/SIZE]
[SIZE=1][FONT=arial]   7      1464887296      1465147391   127.0 MiB   0700  [/FONT][/SIZE]





From Partition Inspector:
 *** Report for internal hard disk ***

Current GPT partition table:
  #      Start LBA      End LBA  Type
  1             40       409639  EFI System (FAT)
  2         409640    195722135  Mac OS X HFS+
  3      195722136    196991671  Mac OS X Boot
  4      196993024    685271039  Basic Data
  5      685271040    880583535  Basic Data
  6      880583536   1464886983  Basic Data
  7     1464887296   1465147391  Basic Data

Current MBR partition table:
  # A    Start LBA      End LBA  Type
  1              1       409639  ee  EFI Protective
  2         409640    195722135  af  Mac OS X HFS+
  3      196993024    685271039  07  NTFS/HPFS
  4      685271040    880583535  83  Linux

MBR contents:
  Boot Code: Unknown, but bootable

Partition at LBA 40:
  Boot Code: None (Non-system disk message)
  File System: FAT32
  Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
  Boot Code: None
  File System: HFS Extended (HFS+)
  Listed in GPT as partition 2, type Mac OS X HFS+
  Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 195722136:
  Boot Code: None
  File System: HFS Extended (HFS+)
  Listed in GPT as partition 3, type Mac OS X Boot

Partition at LBA 196993024:
  Boot Code: Windows BOOTMGR (Vista)
  File System: NTFS
  Listed in GPT as partition 4, type Basic Data
  Listed in MBR as partition 3, type 07  NTFS/HPFS

Partition at LBA 685271040:
  Boot Code: GRUB
  File System: ext4
  Listed in GPT as partition 5, type Basic Data
  Listed in MBR as partition 4, type 83  Linux

Partition at LBA 880583536:
  Boot Code: Windows BOOTMGR (Vista)
  File System: NTFS
  Listed in GPT as partition 6, type Basic Data

Partition at LBA 1464887296:
  Boot Code: None (Non-system disk message)
  File System: FAT16
  Listed in GPT as partition 7, type Basic Data

---

### Post by simon16 on 2014-02-01
Works perfectly! 


I installed Backtrack 5 R3 GNOME instead of Ubuntu and it worked out all fine!

Thanks for this tutorial!
I appreciate it!

 :popcorn: 
=d>=d>=d>

---

### Post by hendrik4 on 2014-03-30
For me the last step does not work... I get this message: Is this alright?

[FONT=Menlo]Do you want to proceed? (Y/N): y[/FONT]
[FONT=Menlo]OK; writing new GUID partition table (GPT) to /dev/disk0.[/FONT]
[FONT=Menlo]Warning: Devices opened with shared lock will not have their[/FONT]
[FONT=Menlo]partition table automatically reloaded![/FONT]
[FONT=Menlo]Warning: The kernel may continue to use old or deleted partitions.[/FONT]
[FONT=Menlo]You should reboot or remove the drive.[/FONT]
[FONT=Menlo]The operation has completed successfully.[/FONT]

---

### Post by rafaelvega on 2014-06-18
I can confirm this works with MacBookPro8,1, Debian 7, Windows 7 and Mountain Lion. Thanks!

---

### Post by jake_hewitt on 2015-02-05
You sir are a saint. I about S*** my pants when I booted (or attempted to rather) into windows and got that stomach wrenching "No OS" message. Thank you!!

I should also mention this will do the same for the refind boot loader as well as refit.
I am using iMac 27' Late 2012 (sorry don't know the number off the top of my head), OS X Yosemite, Windows 10 Tech preview, and Ubuntu 14.10.

---

### Post by tekboi2 on 2015-05-27
Following the guide, for some reason my iMac late 2011 boots directly into ubuntu after rebooting. I have been unable to figure out why it is still doing this.

---

