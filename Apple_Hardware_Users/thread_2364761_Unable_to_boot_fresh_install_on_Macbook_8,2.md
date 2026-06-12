---
title: "Unable to boot fresh install on Macbook 8,2"
date: 2017-06-27
forum: Apple Hardware Users
---

### Post by bullman on 2017-06-27
Yesterday I installed Xubuntu from a USB stick. I used the following image: xubuntu-17.04-desktop-amd64
I followed the Machine [specific guide]("https://ubuntuforums.org/archive/index.php/t-2157775.html") I found on the forums and have successfully installed Xubuntu to my second hard disk on my machine. 

After a reboot I am able to see the Xubuntu install in rEFInd along side the OSX install on my other HDD. But when I try to boot from the Xubuntu install I am unable to get any further than a black screen. 
The OSX partition loads perfectly and doesn't have any issues.

When checking the partitions from the terminal I noticed the following:
```
diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *250.1 GB   disk0
   1:                        EFI EFI                     209.7 MB   disk0s1
   2:          Apple_CoreStorage                         193.3 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
   4:       Microsoft Basic Data LXPART                  55.9 GB    disk0s4
/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:                  Apple_HFS Naamloos               *193.0 GB   disk1
/dev/disk2
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.1 GB   disk2
   1:                        EFI NO NAME                 536.9 MB   disk2s1
   2:                  Linux LVM                         499.6 GB   disk2s2
```

To me it seems disk0 and disk1 are the same drives. 

Did I install Xubuntu in a wrong way or did something mess with the partitioning on disk2?

---

### Post by kevin160 on 2017-06-27
Your disk1 is a "virtual" or "synthesized" disk and is the contents of the (disk0s2) CoreStorage "container" volume on disk0.  Looks normal although I wonder why it would be set up with CoreStorage on only 1 disk.  It it a fusion drive?  

As long as you are getting a rEFInd screen and are able to select linux/grub, I don't think the CoreStorage volume is related to your linux boot issues.  

Are you getting a grub screen or is it going black immediately after you pick the option in rEFInd?

---

### Post by bullman on 2017-06-27
After i select linux at the de refind screen the screen goes black immediately. No error message what so ever. 

Could it be related to the dual gpu that this MacBook Pro has?

I have been doing some testing and noticed that I don't see GRUB at all. Did I forget to install GRUB? 

This is completely unfamiliar grounds for me, so bear with me if I am asking the wrong questions.

---

### Post by johndough2 on 2017-06-29
Hi

rEFIt is similar and may be worth trying, I prefer it to rEFInd.

There are / is a config file in refind that is supposedly editable, but I struggled.

---

### Post by bullman on 2017-06-29
> **johndough2 said:**
> Hi

rEFIt is similar and may be worth trying, I prefer it to rEFInd.

There are / is a config file in refind that is supposedly editable, but I struggled.

I've tried your suggestion of rEFIt but that doesn't seem to help booting the system either. As far as I have been able to see is that neither of the EFI firmwares seem to be the problem. It's after I select the Ubuntu from the selection menu that the Mabook Pro's screen goes black.

From what I have seen of videos I should be getting a GRUB screen like the one I had when I was installing right?

---

### Post by oldfred on 2017-06-29
You have LVM on your disk2 partition 2, but partition one say EFI.
Normally LVM has a separate /boot partition. And if UEFI normally uses the ESP - efi system partition on the first drive.

Or is disk2 partition 1 really an ESP with FAT32 formatting or a /boot partition with ext2 formatting. If ext2 formatted remove boot flag.

---

