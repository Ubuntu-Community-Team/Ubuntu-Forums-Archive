---
title: "Disk Utility internal error, need help."
date: 2009-01-14
forum: Apple Hardware Users
---

### Post by WA_Garrett on 2009-01-14
I have recently installed ubuntu on my macbook, and can boot from Mac OS 10.4.11 and Ubuntu using rEFIt. Both seem to be working alright so far, but. 

When trying to look at my partitioning scheme through Apples Disk Utility Application on Tiger by selecting my whole internal drive and clicking on my partition tab, DU throws the error, 

"Disk Utility has lost its connection with the Disk Management Tool and cannot continue. Please quit and relaunch Disk Utility."

Upon shutting it down and restarting, the error pops up again after clicking on the partition tab.

 I can still see my partitioning scheme with the Mac OS X terminal by calling "sudo diskutil list" and partition inspector (which was an OS X app supplied with rEFIt) can still detect my partitions, but Disk Utility throws the error. 

Does anyone know how to solve this problem?

---

### Post by cyberdork33 on 2009-01-14
try repairing the disk from the OSX install dvd.

---

### Post by WA_Garrett on 2009-01-17
> **cyberdork33 said:**
> try repairing the disk from the OSX install dvd.

I booted from my OS X install DVD, opened disk utilities from the installer, and verified my Macintosh HD disk, it revealed a minor error, So I proceeded to repair it. After repairing, Disk Utility said the volume appeared to be OK. However when selecting the entire disk and clicking on the partition tab Disk Utility still throws the error that is has lost its connection with the Disk Management tool. 

Do you or anyone reading this have any more ideas as to the cause of this and/or how to solve this problem?

---

### Post by cyberdork33 on 2009-01-17
can you post the content of the partition inspector tool?

---

### Post by WA_Garrett on 2009-01-17
> **cyberdork33 said:**
> can you post the content of the partition inspector tool?

I assume you mean the partition inspector tool that came with rEFIt

which is...

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    192645079  Mac OS X HFS+
 3      192645080    210613830  MS Reserved
 4      210613831    232440002  Basic Data
 5      232440003    234440003  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    192645079  af  Mac OS X HFS+
 3 *    192645080    210613830  c0  Unknown
 4      210613831    232440002  83  Linux

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

Partition at LBA 192645080:
 Boot Code: Unknown, but bootable
 File System: FAT32
 Listed in GPT as partition 3, type MS Reserved
 Listed in MBR as partition 3, type c0  Unknown, active

Partition at LBA 210613831:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 232440003:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

---

### Post by cyberdork33 on 2009-01-17
well, I don't know. Everything looks really good. I have gotten the error you are having a long time ago, but I don't know what I did about it. Maybe there is some preference file that you can delete or something.

---

### Post by WA_Garrett on 2009-01-17
> **cyberdork33 said:**
> well, I don't know. Everything looks really good. I have gotten the error you are having a long time ago, but I don't know what I did about it. Maybe there is some preference file that you can delete or something.

I've heard that this error could be the indication that there is something wrong with the disk and that problem would over time get worse, thus it might be necessary to nuke the drive and start over. Do you think that is the case here, or should I just leave this be and not worry about it?

---

### Post by cyberdork33 on 2009-01-18
Did you do a repair disk with the disk selected, or just the partition... make sure to do it with the whole disk.

---

### Post by WA_Garrett on 2009-01-18
> **cyberdork33 said:**
> Did you do a repair disk with the disk selected, or just the partition... make sure to do it with the whole disk.

It doesn't let me do a verify and repair on the entire disk, just the Macintosh HD partition.

---

### Post by WA_Garrett on 2009-01-19
> **cyberdork33 said:**
> Did you do a repair disk with the disk selected, or just the partition... make sure to do it with the whole disk.

Okay, here's an update with the problem. I've been doing alot of stuff with my computer lately, not only am I trying to run Ubuntu on my Macbook I'm also trying to triple boot Windows XP as well. 

There was a fat 32 partition squished in between my Linux partition and my Mac OS X partition which I was planning to put windows on (I made the fat 32 partition when I originally installed ubuntu). After acquiring an MS WIN XP SP2 disk I tried to install windows on the fat 32 partition, but I couldn't for some reason, so I tried to delete it, and create a new partition, the disk wouldn't let me create any more partitions because it said that I already had "the maximum number of partitions on the disk," so restarted my mac, booted from the OS X install cd, ran disk utility and converted the free space, where the fat 32 partition was, into MS-DOS formated space. 

After that, upon selecting the entire disk and pressing on the partition tab in Disk Utility, _Disk Utility no longer reports the error that it lost connection with the disk management tool. _

Upon rebooting, in rEFIt, rEFIt only showed the option of booting from Mac OS X or booting from the FAT partition (which appears as a windows icon). 

I inserted the windows disk and booted from it. It detected my partitions, and WAS able to say it could go onto the new partition I reformatted for it, I began to install it, it wrote alot of files to the partition, and at the end it said it needed to reboot to continue. 

It rebooted in rEFIt, I booted from the windows partition, but it reported that there was a "Disk error" which means I can't continue installing windows, (Or I at least I don't know how to)

Also rEFIt still can't detect the linux partition and boot from it, I don't know why. Which means that I can't boot in Ubuntu currently. I tried to update the partition table in partitioning tool, but that didn't help.

Does anyone know how I can continue the windows installation? And does anyone know how I could boot in Ubuntu again as well?

Thank you to anyone who reads and responds to this post.

---

### Post by cyberdork33 on 2009-01-19
> **WA_Garrett said:**
> Also rEFIt still can't detect the linux partition and boot from it, I don't know why. Which means that I can't boot in Ubuntu currently. I tried to update the partition table in partitioning tool, but that didn't help.
Your attempt to install Windows probably placed the windows bootloader in the MBR which is where grub installs by default. You need to reinstall grub to the Ubuntu partition.

See:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

---

### Post by WA_Garrett on 2009-01-20
> **cyberdork33 said:**
> Your attempt to install Windows probably placed the windows bootloader in the MBR which is where grub installs by default. You need to reinstall grub to the Ubuntu partition.

See:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

Ah, thank you for that link, the instructions on it worked. 

I know this isn't the place for it, but do you have any ideas about my windows problem?

Thank you.

---

### Post by flaggh on 2009-01-20
Could it be a problem with the partitioning scheme?  Doesn't Windows dislike drives with more than four partitions?

---

### Post by cyberdork33 on 2009-01-20
> **WA_Garrett said:**
> Ah, thank you for that link, the instructions on it worked. 

I know this isn't the place for it, but do you have any ideas about my windows problem?

Thank you.
Not sure.

---

### Post by WA_Garrett on 2009-01-20
> **flaggh said:**
> Could it be a problem with the partitioning scheme?  Doesn't Windows dislike drives with more than four partitions?

Infact when I first tried to install windows, it didn't like the fat 32 partition I made for it with my Ubuntu disk. When I deleted it with the windows installer and tried to create a new partition in the free space with the windows disk it said that there were too many partitions to create a new one. I already had my EFI partition, My Macintosh HD partition, My Linux partition and a Linux swap space partition. So I rather sneakily booted up from my OS X install cd opened disk utility and converted the free space to MS-DOS disk format. I rebooted again with the windows disk and it liked the partition created from Disk Utility enough to do the first part of the installation where it wrote the OS files onto the partition. After that it rebooted and when booting on the windows disk, it reported a "disk error please press any key to restart," pressing the any-key did nothing, the system was unresponsive, I restated with the power button and can still boot in OS X and Ubuntu. :confused:

---

### Post by flaggh on 2009-01-21
Perhaps the easiest approach would be to remove the swap partition, install windows by deleting the fat partition and have the installer do all the work formatting.  It shouldn't have any problems since there are not already four partitions.  You can always re-add the swap partition, or just use a swap file which will accomplish the same thing.

Read the Swap FAQ for information on disabling your swap before you actually delete the partition.  It also has info on using a swapfile.
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by cyberdork33 on 2009-01-21
> **flaggh said:**
> Perhaps the easiest approach would be to remove the swap partition, install windows by deleting the fat partition and have the installer do all the work formatting.  It shouldn't have any problems since there are not already four partitions.  You can always re-add the swap partition, or just use a swap file which will accomplish the same thing.

Read the Swap FAQ for information on disabling your swap before you actually delete the partition.  It also has info on using a swapfile.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
yea, just boot the ubuntu CD and start gparted, unmount the swap partition (swapoff) and delete it. Try to let Windows create the partition again and it should allow it. When you are done there, you can boot the Ubuntu CD again and recreate the swap in the same place.

---

### Post by flaggh on 2009-01-21
If he boots into the ubuntu CD, will the swap drive even be mounted?  I would think he should boot up the computer as usual, disable the swap partition, comment it out in fstab, delete it with gparted, then try the windows installation.

---

### Post by cyberdork33 on 2009-01-21
> **flaggh said:**
> If he boots into the ubuntu CD, will the swap drive even be mounted?  I would think he should boot up the computer as usual, disable the swap partition, comment it out in fstab, delete it with gparted, then try the windows installation.
yes, it automatically finds swap and mounts it if available. (why wouldn't it? It can only increase the performance of the CD-based OS).

Why do all those config edits that you have to edit back later? just delete the partition, install, then create a new partition in the same location. All the config files point to the same partition still.

Actually, I don't know if letting the windows installer create its own partition is a good idea anyway... It cannot edit the GPT, so it will likely end up problematic. This is why you use Disk Utility or BootCamp to make the partition for you.

---

### Post by WA_Garrett on 2009-01-21
> **flaggh said:**
> Perhaps the easiest approach would be to remove the swap partition, install windows by deleting the fat partition and have the installer do all the work formatting.  It shouldn't have any problems since there are not already four partitions.  You can always re-add the swap partition, or just use a swap file which will accomplish the same thing.

Read the Swap FAQ for information on disabling your swap before you actually delete the partition.  It also has info on using a swapfile.
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

So do we have consensus that deleting my swap partition will allow windows to finish installing? I sort of have doubts about deleting that partition because I have gotten past the stage where you create the partition for windows with the windows CD, where windows failed so I used the OS X install CD to create a FAT partition which windows liked. As a result I have the first step of installation for windows complete. But because of windows being partially installed, how could deleting a partition be helpful? I already passed the partitioning stages and I am just trying to finish up windows installation on the windows partition. Is that extra partition the cause of the "disk error" and need to reboot? If I were to try to delete the swap partition should it just be made as free unpartitioned space?

---

### Post by cyberdork33 on 2009-01-22
> **WA_Garrett said:**
> So do we have consensus that deleting my swap partition will allow windows to finish installing? I sort of have doubts about deleting that partition because I have gotten past the stage where you create the partition for windows with the windows CD, where windows failed so I used the OS X install CD to create a FAT partition which windows liked. As a result I have the first step of installation for windows complete. But because of windows being partially installed, how could deleting a partition be helpful? I already passed the partitioning stages and I am just trying to finish up windows installation on the windows partition. Is that extra partition the cause of the "disk error" and need to reboot? If I were to try to delete the swap partition should it just be made as free unpartitioned space?

put the windows disc in your drive, boot and select the windows partition to boot from. If you still get the error, verify that the partition tables are in sync and try again. If you STILL get the same error then I am not sure what the issue might be at all, and it might be easiest to start again with a clean partition.

I really don't think that the swap partition is an issue, mainly because windows can't even see it. (It can only see 4 partitions). Windows does act weird though sometimes if it is not the last partition on the disk (as far as it can tell... i.e. #4).

---

### Post by WA_Garrett on 2009-02-08
> **cyberdork33 said:**
> put the windows disc in your drive, boot and select the windows partition to boot from. If you still get the error, verify that the partition tables are in sync and try again. If you STILL get the same error then I am not sure what the issue might be at all, and it might be easiest to start again with a clean partition.

I really don't think that the swap partition is an issue, mainly because windows can't even see it. (It can only see 4 partitions). Windows does act weird though sometimes if it is not the last partition on the disk (as far as it can tell... i.e. #4).

I temporarily nuked Ubuntu and cleared the partition. Now there are just 3 partitions on the disk, the 200mb EFI Partition, 90 GB Mac HD, and a 20 GB FAT 32 volume. There is no unpartitioned space. I tried installing XP SP2 and still it throws that "disk error - press any key". Partitioning tool says tables are in sync. Any ideas? 

Sorry it's been a while, school's been being ridiculous.

---

### Post by cyberdork33 on 2009-02-09
> **WA_Garrett said:**
> I temporarily nuked Ubuntu and cleared the partition. Now there are just 3 partitions on the disk, the 200mb EFI Partition, 90 GB Mac HD, and a 20 GB FAT 32 volume. There is no unpartitioned space. I tried installing XP SP2 and still it throws that "disk error - press any key". Partitioning tool says tables are in sync. Any ideas? 

Sorry it's been a while, school's been being ridiculous.
Windows apparently doesn't like your partition layout. I don't know what to tell you. Might be better to remove the FAT partition, resize the OSX partition to take up the space, and start over from the beginning.

Take a look at this thread for installation options:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by WA_Garrett on 2009-02-09
> **cyberdork33 said:**
> Windows apparently doesn't like your partition layout. I don't know what to tell you. Might be better to remove the FAT partition, resize the OSX partition to take up the space, and start over from the beginning.

Take a look at this thread for installation options:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I looked up some information and found out that I needed to make windows re-format the drive when you install it to fat file system (quick).

After alot of trouble I was able to get both Ubuntu back up and working (for the most part, wireless access still isn't working) and I was able to install windows as well (far from working though, wireless and sound don't work, it can't even connect to the internet via ethernet)

Anyways long story short, OS X, Ubuntu and Windows have all been crammed onto my macbook. I can now triple boot, thanks for all the help. :guitar:

One more thing though, I'm thinking the reason I'm having so much trouble with windows is because I don't have that drivers disk that I would have created if I used bootcamp. But since I didn't use bootcamp I don't have the divers disk for windows. I'm wondering if there is a disk image of it somewhere on the internet.

---

### Post by cyberdork33 on 2009-02-09
> **WA_Garrett said:**
> 
One more thing though, I'm thinking the reason I'm having so much trouble with windows is because I don't have that drivers disk that I would have created if I used bootcamp. But since I didn't use bootcamp I don't have the divers disk for windows. I'm wondering if there is a disk image of it somewhere on the internet.
the drivers are on the Leopard DVD.

---

### Post by WA_Garrett on 2009-02-22
> **cyberdork33 said:**
> the drivers are on the Leopard DVD.

I couldn't find the win drivers on the Leo DVD, but I found the drivers online and burnt them to a CD and was able to install them. So windows is working well enough now. 

I can triple boot rather nicely now, I'd like to thank you and flaggh for all the help.:D

---

### Post by cyberdork33 on 2009-02-23
> **WA_Garrett said:**
> I couldn't find the win drivers on the Leo DVD, but I found the drivers online and burnt them to a CD and was able to install them. So windows is working well enough now.
I placed my Leopard DVD in the drive in Windows, and all the drivers are in a folder named "Boot Camp". Anyway, glad you got it working.

---

