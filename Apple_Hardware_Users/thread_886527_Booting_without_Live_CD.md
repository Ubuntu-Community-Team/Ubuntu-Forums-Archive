---
title: "Booting without Live CD"
date: 2008-08-11
forum: Apple Hardware Users
---

### Post by ems5311 on 2008-08-11
Hey,
This might be a real stupid problem, so please bear with me.  I can't boot into Ubuntu from just the hard drive alone, I have to use the Live CD.  When I try with just the Hard Drive, I get a little flashing cursor every time.

I don't know why this is exactly, but I have a hunch.  When I partitioned my HD i set up not one but THREE swap partitions... it's kind of a long story but trust me, it looked like a good idea at the time.  Could this be the reason I can't boot from my hard drive alone?  I can tear down the two (superfluous?) swap partitions easily, or tear down all three and still run fine if that will make the booting process easier.

Thanks in advance, sorry for another dumb question.

---

### Post by ajgreeny on 2008-08-11
> This might be a real stupid problem, so please bear with me. I can't boot into Ubuntu from just the hard drive alone, I have to use the Live CD. When I try with just the Hard Drive, I get a little flashing cursor every time.Do you mean that you can not boot your installed version at all, or simply that it boots to a console after login.  Or perhaps you just boot to the live CD and not your hard disk install.

From the live CD (or whatever it is you can boot to) run```
 sudo fdisk -l
``` in terminal and let's see the output from that.  Then in the live CD, mount the installed hard disk version and let's see the output of ```
cat /mountpoint/boot/grub/menu.lst
```  Where I use the word mountpoint, you will need to add the mountpoint path of your hard disk.  Once we know all that it may be possible to put things right.

---

### Post by cyberdork33 on 2008-08-11
In the LiveCD, run these commands and post the output please:
```
sudo fdisk -l /dev/sda
``````
sudo parted /dev/sda print
```
or if you have refit installed, you can use the partition inspector application in your Utilities folder to give this information.

My guess is that grub is broken and this can be easily fixed so hold tight.

---

### Post by ems5311 on 2008-08-11
Sorry if I was unclear in my post, but I can boot into my hard drive local install from the Live CD.  I'm not just booting up the Live CD run of Ubuntu.  I have it installed, just can't boot that install without the disk.

Result of```
sudo fdisk -l
``` output:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19458   156290903+  ee  EFI GPT

```

Here's more:
```
erich@erich-laptop:~$ sudo parted /dev/sda print

Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name      Flags
 1      17.4kB  209MB   209MB   linux-swap                  
 2      210MB   79.5GB  79.3GB  hfs+         Customer       
 6      79.5GB  79.7GB  137MB   linux-swap                  
 3      79.7GB  159GB   79.7GB  ext3         Untitled       
 5      159GB   160GB   685MB   linux-swap                  

Information: Don't forget to update /etc/fstab, if necessary.             

```

---

### Post by cyberdork33 on 2008-08-11
You need to install refit and sync your partition tables...

[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by ems5311 on 2008-08-11
Okay, got rEFIt going, and it froze on the Tux logo like you said it might.  Given that you posted that a few months ago, is there a common fix for this problem yet?  I'll try powering down first, last time I just restarted.

---

### Post by cyberdork33 on 2008-08-11
> **ems5311 said:**
> Okay, got rEFIt going, and it froze on the Tux logo like you said it might.  Given that you posted that a few months ago, is there a common fix for this problem yet?  I'll try powering down first, last time I just restarted.yep do that first. before you do the other fix though, you need to try to fix your partition situation:
> **ems5311 said:**
> Here's more:
```
erich@erich-laptop:~$ sudo parted /dev/sda print

Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name      Flags
 1      17.4kB  209MB   209MB   linux-swap                  
 2      210MB   79.5GB  79.3GB  hfs+         Customer       
 6      79.5GB  79.7GB  137MB   linux-swap                  
 3      79.7GB  159GB   79.7GB  ext3         Untitled       
 5      159GB   160GB   685MB   linux-swap                  

Information: Don't forget to update /etc/fstab, if necessary.             

```

OK, you are going to need a little revamp here... You seem to have formatted over your EFI system partition. The first partition (sda1) needs to be formatted back to an EFI system partition if you can. Otherwise you will run into problems later.

You probably want to try and backup as much stuff from your OS X partition as you can as if push comes to shove, you are going to have to do a complete wipe and reinstall.

Boot from the Ubuntu Live CD and start the Partition Editor in the Administration Menu (gparted). and see if you can select sda1 right-click and select format to and see if EFI comes up as an option... If it is locked you will have to unmount it first.

I would just select and delete the second swap partition (sda6) as it is not going to help any.

---

### Post by ems5311 on 2008-08-11
Got it to boot by shutting down... now giving this partitioning change a go.  Thanks a lot for all your help, by the way.

---

### Post by cyberdork33 on 2008-08-11
> **ems5311 said:**
> Got it to boot by shutting down... now giving this partitioning change a go.  Thanks a lot for all your help, by the way.
Well that's good. Your system should "work" anyway now, but you might have a problem updating firmware in OS X.

---

### Post by ems5311 on 2008-08-11
Sorry but just one more... how do I access the admin menu in the Live CD?

---

### Post by cyberdork33 on 2008-08-11
> **ems5311 said:**
> Sorry but just one more... how do I access the admin menu in the Live CD?
It is under System... System > Administration > Partition Editor...

You can also just run "gksudo gparted" in a terminal.

---

### Post by ems5311 on 2008-08-11
Okay, major problems.  Maybe.

It is NOT POSSIBLE to create EFI partitions in gparted (from ubuntu live cd).  What I did was delete my sda6 partition and moved the unallocated space (~130 megs) into my sda5 partition.  So I consolidated the two swap partitions into one.  This involved moving the sda6 into my ext3 partition, then shrinking it out and growing it into my sda5 swap partition.

So that's all I did.  No creation of an EFI partition from sda1.  When I tried to boot back into ubuntu through rEFIt, it was not possible (linux icon did not show up at all).  Tried the partition repair function in rEFIt, then it called the operating system something else (not linux...).  Completely unbootable.  I insert the live CD to boot into my local disk from there, and I get the message "no operating system found".

Three things from this:
1. How do I make an EFI partition out of my sda1?  Anyone got a program that can do this?
2. Repair partition in rEFIt tells me it's missing a "gptsync.efi" file.  I have this exact file in /efi/tools in mac OSX... do I need one in linux?

Thanks in advance to anyone who still cares about this, it'll really help me out.

---

### Post by cyberdork33 on 2008-08-11
> **ems5311 said:**
> Okay, major problems.  Maybe.

It is NOT POSSIBLE to create EFI partitions in gparted (from ubuntu live cd).  What I did was delete my sda6 partition and moved the unallocated space (~130 megs) into my sda5 partition.  So I consolidated the two swap partitions into one.  This involved moving the sda6 into my ext3 partition, then shrinking it out and growing it into my sda5 swap partition.

So that's all I did.  No creation of an EFI partition from sda1.  When I tried to boot back into ubuntu through rEFIt, it was not possible (linux icon did not show up at all).  Tried the partition repair function in rEFIt, then it called the operating system something else (not linux...).  Completely unbootable.  I insert the live CD to boot into my local disk from there, and I get the message "no operating system found".

Three things from this:
1. How do I make an EFI partition out of my sda1?  Anyone got a program that can do this?
2. Repair partition in rEFIt tells me it's missing a "gptsync.efi" file.  I have this exact file in /efi/tools in mac OSX... do I need one in linux?

Thanks in advance to anyone who still cares about this, it'll really help me out.

You just messed up grub. Follow the second part of that thread I linked to. It will show you how to reinstall it.

I would try reinstalling refit. (you can sync partitions in linux too though. "sudo apt-get install refit" then run "gptsync")

---

### Post by ems5311 on 2008-08-12
Sweet, thanks to the thread linked to in that thread you linked to, my Ubuntu is back up and running again.

> I would try reinstalling refit. (you can sync partitions in linux too though. "sudo apt-get install refit" then run "gptsync")

Does this suggestion pertain to getting an EFI partition established over my sda1?

---

### Post by cyberdork33 on 2008-08-12
> **ems5311 said:**
> Does this suggestion pertain to getting an EFI partition established over my sda1?
no

Unfortunately this is an issue. The information you posted does seem to indicate that you have a GPT though... Basically, all you have to do is format it as FAT32 and then set the appropriate flag on the partition in the GPT. I am unsure of how to go about that though.

Apple really isn't any help:
[http://support.apple.com/kb/HT2434?viewlocale=en_US](http://support.apple.com/kb/HT2434?viewlocale=en_US)
I am looking around.

[COLOR=Red]**EDIT:**[/COLOR]

OK, this seems to go through the steps (post 4). If you have issues with a portion, post the output of the commands in the first few steps, and we can help. It is focused on dual-booting with Vista, but just ignore that. It doesn't make a difference. Please be very careful! [http://forum.insanelymac.com/index.php?showtopic=19522](http://forum.insanelymac.com/index.php?showtopic=19522)

---

### Post by ems5311 on 2008-08-12
Wow, that's huge.  Thanks again dude.  I won't try that now, but pretty soon.

---

### Post by ems5311 on 2008-08-17
Alright, I tried editing my fdisk... edited partition 1 (my 200 meg swap partition) that should be turned into an EFI.  Again, I can't boot into linux.  According to refit partitioning tool, my MBR table does not match my GPT partition.  It will not let me "repair" these in that screen.  Anything else I can do to get linux running again?  (It just stops at the tux screen when booting off the hard disk, and I cannot boot off the live CD either.)

Here's an output from terminal:
```
erich-stoekls-macbook:~ erichstoekl$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *149.1 Gi   disk0
   1:                 Linux Swap                         199.3 Mi   disk0s1
   2:                  Apple_HFS Macintosh HD            73.9 Gi    disk0s2
   3:       Microsoft Basic Data                         74.2 Gi    disk0s3
   4:                 Linux Swap                         784.4 Mi   disk0s4

```
However, here's what my fdisk looks like:
```
erich-stoekls-macbook:~ erichstoekl$ sudo fdisk /dev/disk0
Password:
Disk: /dev/disk0	geometry: 19457/255/63 [312581808 sectors]
Signature: 0xAA55
         Starting       Ending
 #: id  cyl  hd sec -  cyl  hd sec [     start -       size]
------------------------------------------------------------------------
 1: EE    0   0   2 - 1023 254  63 [         1 -         33] <Unknown ID>
 2: 82 1023 254  63 - 1023 254  63 [        34 -     408204] Linux swap  
 3: AF 1023 254  63 - 1023 254  63 [    409640 -  154927104] HFS+        
*4: 83 1023 254  63 - 1023 254  63 [ 155336744 -  155633461] Linux files*

```

Viable solutions I can see:
re-build my grub
re-install refit
I screwed up editing the EFI in the first place and it did nothing, but for some reason I still can't boot back into ubuntu?

---

### Post by cyberdork33 on 2008-08-17
> **ems5311 said:**
> Alright, I tried editing my fdisk... edited partition 1 (my 200 meg swap partition) that should be turned into an EFI.  Again, I can't boot into linux.  According to refit partitioning tool, my MBR table does not match my GPT partition.  It will not let me "repair" these in that screen.  Anything else I can do to get linux running again?  (It just stops at the tux screen when booting off the hard disk, and I cannot boot off the live CD either.)

Here's an output from terminal:
```
erich-stoekls-macbook:~ erichstoekl$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *149.1 Gi   disk0
   1:                 Linux Swap                         199.3 Mi   disk0s1
   2:                  Apple_HFS Macintosh HD            73.9 Gi    disk0s2
   3:       Microsoft Basic Data                         74.2 Gi    disk0s3
   4:                 Linux Swap                         784.4 Mi   disk0s4

```However, here's what my fdisk looks like:
```
erich-stoekls-macbook:~ erichstoekl$ sudo fdisk /dev/disk0
Password:
Disk: /dev/disk0    geometry: 19457/255/63 [312581808 sectors]
Signature: 0xAA55
         Starting       Ending
 #: id  cyl  hd sec -  cyl  hd sec [     start -       size]
------------------------------------------------------------------------
 1: EE    0   0   2 - 1023 254  63 [         1 -         33] <Unknown ID>
 2: 82 1023 254  63 - 1023 254  63 [        34 -     408204] Linux swap  
 3: AF 1023 254  63 - 1023 254  63 [    409640 -  154927104] HFS+        
*4: 83 1023 254  63 - 1023 254  63 [ 155336744 -  155633461] Linux files*

```Viable solutions I can see:
re-build my grub
re-install refit
I screwed up editing the EFI in the first place and it did nothing, but for some reason I still can't boot back into ubuntu?

fdisk only shows the MBR table, not the GPT. You should post the output of 'sudo parted /dev/sda print' as well. Or you can use the Partition Inspector Tool that comes with refit (In Applications/Utilities

---

### Post by ems5311 on 2008-08-17
Alright, here's a more accurate report:
```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             34       408237  Linux Swap
 2         409640    155336743  Mac OS X HFS+
 3      155336744    310970204  Basic Data
 4      310970205    312576704  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1           33  ee  EFI Protective
 2             34       408237  82  Linux swap / Solaris
 3         409640    155336743  af  Mac OS X HFS+
 4 *    155336744    310970204  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 34:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 1, type Linux Swap
 Listed in MBR as partition 2, type 82  Linux swap / Solaris

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 3, type af  Mac OS X HFS+

Partition at LBA 155336744:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active

Partition at LBA 310970205:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
```

---

### Post by cyberdork33 on 2008-08-17
OK I didn't realize the first output was OS X terminal commands.

It looks like you got your partitions one place off when you followed the previous instructions... either way, you cannot sync the MBR to the GPT only GPT > MBR. The key is editting the GPT table appropriately, which looks right, except for the first partition (EFI) is marked as swap for some reason. AH, I see that you have extra space at the beginning of the drive...

```
Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1           33  ee  EFI Protective
 2             34       408237  82  Linux swap / Solaris
 3         409640    155336743  af  Mac OS X HFS+
 4 *    155336744    310970204  83  Linux

```That says that partition #1 starts at block 1 and goes to 33 and the second goes from 34 to[FONT=monospace] [/FONT]408237 ... I think it should start at 1 and go to [FONT=monospace][/FONT]408237.
See my output as an example:
```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    321034647  Mac OS X HFS+
 3      321034648    482460429  Basic Data
 4      482460430    488397134  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    321034647  af  Mac OS X HFS+
 3      321034648    482460429  83  Linux
 4      482460430    488397134  82  Linux swap / Solaris

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
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 321034648:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux

Partition at LBA 482460430:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris
```

---

### Post by ems5311 on 2008-08-18
Wow.  Looking at your tables, it looks like I've got to do some complete re-arranging.  Here's a changed output:

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             34       408237  Linux Swap
 2         409640    155336743  Mac OS X HFS+
 3      155336744    310970204  Basic Data
 4      310970205    312576704  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       408237  ee  EFI Protective
 2             34       408237  82  Linux swap / Solaris
 3         409640    155336743  af  Mac OS X HFS+
 4 *    155336744    310970204  83  Linux
```

Obviously a useless change, as the start LBA for linux swap is overlaps with the entire EFI section in my MBR.  I can't make the Linux swap tiny though.  How can I completely rearrange my MBR to look like yours?

---

