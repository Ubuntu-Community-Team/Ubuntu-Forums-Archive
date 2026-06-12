---
title: "Reinstalled Jaunty, now 2 linux icons appear at rEFIt boot: Can I reinstall rEFIt?"
date: 2009-08-21
forum: Apple Hardware Users
---

### Post by swarup on 2009-08-21
I set up a dual boot with OSX/Jaunty on my MBP 5,2. But by mistake, I forgot to go to "advanced" during the install process and tell the installer to put the boot loader in sda3. So when it finished the install, I booted back up to the livecd, deleted the install, and reinstalled this time with the boot loader in sda3. But when it finished, I found on bootup that at the rEFIt screen, not one but two linux icons appears! rEFIt added a linux icon for each Jaunty install, and despite the fact that the first Jaunty install was deleted, rEFIt still kept that icon plus added a second one for the new Jaunty install. (Under one icon it says "Boot Linux from HD", and under the second icon it says "Boot Linux from partition 3".) Only one of the icons works (the one listed as booting Linux from partition3), and the second icon is useless (and confusing for anyone who uses the computer). What is the way to get rid of the excess linux icon on the rEFIt boot screen? Should I boot into OSX and re-download and install rEFIt? Would this bring about a clean setup of the rEFIt boot screen and solve the problem?

---

### Post by _mario_ on 2009-08-21
rEFIt always displays all boot loaders, it finds. your first try installed the boot loader grub into the disk's MBR (the one entitled "Boot Linux from HD"). it remained there despite the fact that you deleted your first installation. the second try was correct, installing grub into the root/boot partition (entitled "Boot Linux from partition 3").

so you should delete the superfluous instance of grub from the MBR, by running:

```

sudo dd if=/dev/zero of=/dev/sda bs=440 count=1

```

be aware: this command may entirely erase your hard disk if typed wrongly.

ciao,
Mario

---

### Post by swarup on 2009-08-21
All I'll do is copy what you've given and paste it into a terminal window. Are you certain what you've given is proper? In view of what you've written vis-a-vis the danger of putting an incorrect command here, I want to be sure what I'm pasting is correct. If you are certain I can paste what you've given and execute it, then I'll go ahead. I want to get rid of the unwanted icon, but I certainly don't want to end up deleting the entire HD! :)

---

### Post by produnis on 2009-08-22
thanks, I tried this one, and it leaves only the entries "Boot from Partition 3" and "OSX".

But:
If I try to boot from Partition 3, it just leaves a black screen with the word "GRUB" and a blinking cursor....

After reinstallation of the bootloader with the Ubuntu live-CD
(boot from live-cd, open a terminal and type in:```

sudo mount /dev/sda3 /mnt  # sda3 is my ubuntu-installation
sudo mount -o bind /dev /mnt/dev 
sudo mount -t proc /proc /mnt/proc 
sudo chroot /mnt /bin/bash 
grub-install /dev/sda 
update-grub 
reboot
```)

..rEFIt shows again 3 boot-option:
1) OSX
2) Boot Linux from HD
3) Boot Linux from Partition 3

The crazy thing:  both Linux-Options work!!
But after trying to delete the HD-option with your code 
```
sudo dd if=/dev/zero of=/dev/sda bs=440 count=1
```it again leaves the "Boot Linux from Partition 3" which is not able to boot
and again ends up showing a black screen with the word "GRUB" and a blinking cursor...

any suggestions?

---

### Post by _mario_ on 2009-08-26
> **produnis said:**
> thanks, I tried this one, and it leaves only the entries "Boot from Partition 3" and "OSX".

[...]

any suggestions?

yes. grub uses several stages to boot from. the first one may reside in the disk's MBR or a partition. the other ones are loaded off the linux boot/root partition.

if you choose to install grub to /dev/sda, it installs to the MBR, which is deleted with my command. but the grub installation in the linux partition is not actually working. hence, you should re-install to the partition, by running:
```

grub-install /dev/sda3

```
using the live CD (the other steps, you mentioned, seem to be ok).

alternatively, instead of the previous command you may also run *grub* to open a grub-shell and issue the commands:
```

root (hd0,2)
setup (hd0,2)

```

ciao,
Mario

---

### Post by _mario_ on 2009-08-26
> **swarup said:**
> All I'll do is copy what you've given and paste it into a terminal window. Are you certain what you've given is proper? In view of what you've written vis-a-vis the danger of putting an incorrect command here, I want to be sure what I'm pasting is correct. If you are certain I can paste what you've given and execute it, then I'll go ahead. I want to get rid of the unwanted icon, but I certainly don't want to end up deleting the entire HD! :)

it is correct. bs=440 selects a blocksize of 440 bytes. count=1 transfers exactly 1 block of the specified size. hence, this command overwrites the first 440 bytes of your disk with zeros. these bytes usually contain the standard MBR boot loader not needed by EFI machines. if rEFIt recognizes no boot loader, it displays no icon.

do not attempt to delete the remaining bytes (up to 512) of the first sector, as this is the MBR partition table, although the MBR can be rebuild using rEFIt's partitioning tool. the second sector and consecutive ones contain the GPT. this is why you should not accidentally mis-type this command.

ciao,
Mario

---

### Post by swarup on 2009-09-01
> **_mario_ said:**
> it is correct.

I see. Whereas for produnis (above), it did not work because his grub was not properly installed to the linux partition, right? That is why he got the problem when he used your method?

Ok, so assuming I have understood correctly that this is why it didn't work for produnis, then, since my grub is correctly installed to the linux partition, so your method should work for me. I'll back up all my data carefully, and then try what you suggest. Let us cross our fingers and hope it goes well! It took me a long time to get my Ubuntu install configured the way I want it on this machine. :p

---

### Post by Raveon on 2009-09-02
I ran the command below as was mentioned.  Feeling comfortable as I am used to using dd and its different versions.

     ```
sudo dd if=/dev/zero of=/dev/sda bs=440 count=1
```Unfortunately I still have an extra icon.  Luckily nothing was ruined though.  Any other ideas on how to get rid of the second Linux icon?

---

### Post by imdacrocker on 2009-09-02
Not to thread jack, but I tried your command

sudo dd if=/dev/zero of=/dev/sda bs=440 count=1

and it gives me this error:

dd: /dev/sda: Operation not supported

I'm having a similar problem, except I'm running a triple boot system with EFI on partition 1, Mac OS 10.5 on partition 2, Ubuntu on 3 and windows on 4.  What happens is that I get 4 icons in this order: Mac OS from Macbook HD, Windows from Macbook HD, Linux from sda3, and Windows from ______.    Everything works except for the Windows from Macbook HD.  Here's a copy of the partition table via refit's tool for reference.


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    488777991  Mac OS X HFS+
 3      488777992    558258460  Basic Data
 4      558258750    625137344  MS Reserved

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    488777991  af  Mac OS X HFS+
 3      488777992    558258460  83  Linux
 4 *    558258750    625137344  0b  FAT32 (CHS)

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: Windows NTLDR
 File System: FAT12
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 488777992:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux

Partition at LBA 558258750:
 Boot Code: Windows NTLDR
 File System: FAT32
 Listed in GPT as partition 4, type MS Reserved
 Listed in MBR as partition 4, type 0b  FAT32 (CHS), active

---

### Post by Raveon on 2009-09-02
> Not to thread jack, but I tried your command

sudo dd if=/dev/zero of=/dev/sda bs=440 count=1

and it gives me this error:You need to determine the device name for your hard drive.  Once you have booted into the Linux live CD open a terminal and type:

```
sudo fdisk -l
```This will give you some output and I am betting it will have different partitions on /dev/hda.  If it is "hda" then use that in place of sda.  Your command would look like:
```

sudo dd if=/dev/zero of=/dev/hda bs=440 count=1
```The difference is between using a SATA/SCSI/USB device (sda, sdb, etc) or an IDE device (hda, hdb, etc).

It could also be that you have more than one hard drive and your triple boot drive is sdb.

---

### Post by imdacrocker on 2009-09-02
I'm only using 1 hard drive, it's in a macbook pro.  

I'm out of town with no ubunti live cd, just a mac os 10.5, 10.6, and a windows xp sp2.  Anyway to find the name with any of those?

---

### Post by _mario_ on 2009-09-03
> **swarup said:**
> I see. Whereas for produnis (above), it did not work because his grub was not properly installed to the linux partition, right? That is why he got the problem when he used your method?

yes.

> **swarup said:**
> 
Ok, so assuming I have understood correctly that this is why it didn't work for produnis, then, since my grub is correctly installed to the linux partition, so your method should work for me. I'll back up all my data carefully, and then try what you suggest. Let us cross our fingers and hope it goes well! It took me a long time to get my Ubuntu install configured the way I want it on this machine. :p

yes. it's very unlikely that you'll have to reinstall and reconfigure your system ... because:

with respect to safety, erasing the Linux boot loader is not a big issue, since you can always recover using the live CD. erasing the MBR partition table is no problem either. just use rEFIt to recreate it. 

erasing the GPT would be a serious problem, but fortunately there are 2 of them, one stored at the beginning of the disk and another one at the end. and it's very unlikely to erase both at the same time.

ciao,
Mario

---

### Post by _mario_ on 2009-09-03
> **imdacrocker said:**
> I'm only using 1 hard drive, it's in a macbook pro.  

I'm out of town with no ubunti live cd, just a mac os 10.5, 10.6, and a windows xp sp2.  Anyway to find the name with any of those?

if you're using OSX, the command looks very similar. only the disks' device names are different. OSX uses */dev/disk0*, */dev/disk1*, ... for disks, and */dev/diskXs1*, */dev/diskXs2*, ... (where X is the disk number) for partitions.

you can get a list of available disks and partitions (column IDENTIFIER) by running:
```
diskutil list
```

finally, run:
```
sudo dd if=/dev/zero of=/dev/disk0 bs=440 count=1
```
to erase the MBR boot code on the first disk (*disk0*).

ciao,
Mario

---

### Post by Raveon on 2009-09-03
Sorry for reposting but like I said yesterday I ran the command but I still have my 4th icon.  Its a second Linux icon which says "boot linux from hd" and boots into grub just like the other linux icon.

I am half tempted to try running fixmbr again on my Windows partition....

Just a recap.  I have 4 icons in refit for OSs.  OS X, Linux, Windows, Linux.

---

### Post by _mario_ on 2009-09-03
> **Raveon said:**
> Sorry for reposting but like I said yesterday I ran the command but I still have my 4th icon.  Its a second Linux icon which says "boot linux from hd" and boots into grub just like the other linux icon.

actually i didn't answer your question. according to my experience, "Boot Linux from HD" refers to the master boot record. otherwise rEFIt states "Boot Linux from Partition X". so by running this command, you should have got rid of this superfluous icon. however, rEFIt doesn't state which disk this icon refers to. do you have more than one disk? does the additional icon still appear after cleaning the other disks as well?

> **Raveon said:**
> 
I am half tempted to try running fixmbr again on my Windows partition....


well, if you like. but fixmbr writes a standard boot code to the MBR, that, by default, chainloads an OS from the partition marked active. this one will certainly get an icon by rEFIt.

ciao,
Mario

---

### Post by Raveon on 2009-09-03
> **_mario_ said:**
> according to my experience, "Boot Linux from HD" refers to the master boot record. otherwise rEFIt states "Boot Linux from Partition X". so by running this command, you should have got rid of this superfluous icon. however, rEFIt doesn't state which disk this icon refers to. do you have more than one disk? does the additional icon still appear after cleaning the other disks as well?

There is only one hard drive in the system.  The first Linux icon in rEFIT does say "Boot Linux from Partition 3" but the second one says "from HD".

Based off of what you are saying I am not quite sure what to do.  I may try to run the dd command again.

---

### Post by imdacrocker on 2009-09-03
When I run the command, I get this list:
   0:      GUID_partition_scheme          *298.1 Gi    disk0
   1:      EFI                                              200.0 Mi      disk0s1
   2:      Apple_HFS Macbook Pro        232.9 Gi      disk0s2
   3:      Microsoft Basic Data               33.1 Gi         disk0s3
   4:      Microsoft Reserved                 31.9 Gi         disk0s4
  
So am I modifying disk0 or disk0s1?

---

### Post by _mario_ on 2009-09-04
> **imdacrocker said:**
> 
So am I modifying disk0 or disk0s1?

you'll have to use */dev/disk0*. */dev/disk0* is the first hard drive and */dev/disk0s1* (slice 1) is its first partition.

ciao,
Mario

---

### Post by _mario_ on 2009-09-04
> **Raveon said:**
> There is only one hard drive in the system. The first Linux icon in rEFIT does say "Boot Linux from Partition 3" but the second one says "from HD".

Based off of what you are saying I am not quite sure what to do. I may try to run the dd command again.

this is strange. i'd expect those icons in reverse order ("... from HD" before "... from Partition 3"). running the dd command again shouldn't harm. we can also double-check the result by running:
```
sudo hexdump -n 440 /dev/sda
```

however, if that doesn' help, i don't know how to get rid of that extra icon.

ciao,
Mario

---

### Post by imdacrocker on 2009-09-04
> **_mario_ said:**
> you'll have to use */dev/disk0*. */dev/disk0* is the first hard drive and */dev/disk0s1* (slice 1) is its first partition.

ciao,
Mario

when I try to run the command I get:


sudo dd if=/dev/zero of=/dev/disk0 bs=440 count=1                   
Password:
dd: /dev/disk0: Resource busy
davids-macbook-pro:~ davidcrocker$ 

I tried doing it from the terminal after I booted from the 10.6 instal disk, no dice. Says the sudo command isn't recognized.

---

### Post by _mario_ on 2009-09-07
> **imdacrocker said:**
> when I try to run the command I get:

sudo dd if=/dev/zero of=/dev/disk0 bs=440 count=1                   
Password:
dd: /dev/disk0: Resource busy
davids-macbook-pro:~ davidcrocker$ 

I tried doing it from the terminal after I booted from the 10.6 install disk, no dice. Says the sudo command isn't recognized.


looks like OSX disallows to modify the disk (to protect the partition table) while the disk is being used. did you try to unmount all volumes first? and to close the graphical disk utility? 

in contrast, the install disk might not need sudo, as it opens a root shell by default. (i've never tried that.)

however, downloading and burning a Linux disc might be much easier after all.

ciao,
Mario

---

### Post by imdacrocker on 2009-09-07
Ok, I'll try running it without the sudo command just to see what happens, but i'm back home tomorrow anyways, so if that fails, I'll just get it done from Linux.

Hey, thanks for all your help!  I'm still figuring out this ubuntu and Linux, but it's a pretty cool program...

---

### Post by imdacrocker on 2009-09-10
well, I finally got that command to run, and it didn't change a damn thing... I still have 4 icons.  I tried running the partitioning tool from refit, it says there is no need to run them

---

### Post by X5-655 on 2009-10-06
Not to bring up a couple weeks old thread but I'm having the same problem.  My Mac has got two HD's, one with OS X, the other with Linux.  I too had dual icons in refit.

I tried the first command to remove grub, and it just says "Legacy OS" in refit.  I try to run that and get a blank screen with a blinking cursor.  I tried to run "grub-install /dev/sda1" as my linux is on the 1st, but got permission denied.  Ran it as sudo and got an error about /boot and not a block device.

Now I'm stuck and can't even boot my linux install.

---

