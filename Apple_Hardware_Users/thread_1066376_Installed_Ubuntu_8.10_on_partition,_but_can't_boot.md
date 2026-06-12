---
title: "Installed Ubuntu 8.10 on partition, but can't boot from it!"
date: 2009-02-10
forum: Apple Hardware Users
---

### Post by METC on 2009-02-10
Disk Utility thinks it's a FAT32 drive, and says it can't mount it.
It's also not available from the boot menu.
What should I do? I formatted it as a 30 GB ext3 partition.

---

### Post by METC on 2009-02-11
bump

hello?

---

### Post by JujuLand on 2009-02-11
You have perhaps made the same error as me.
 
On a Mac, there is two parts needed, not needed on other machines. First a specific Apple part and a part with the type NewWorld.
 
I have made this mistake and installed again many times. Not really entertaining :)
 
To make it easy, choose the automatic mode, and just before validating the partitionning, choose Go back.
 
You'll the see 4 parts. Don't touch to the two first I was talking about, and if needed, just delete ext3 part to make 2 parts (if you want to separate /home and / for security purpose) and create two ext2 parts, else validate and continue.
 
For example here are the parts on my system (HDD 20 Go):
 
Apple part           64 Ko ((if I remeber)
NewWord part     1 Mo
/ (ext3)              8.5 Go
swap                  1 Go
/home                11.5 Go (21.5 Go for a 30 Go HDD)
 
A+

---

### Post by METC on 2009-02-11
Would it help if I said I partitioned the drive with Gparted instead of the installer's partitioner?

---

### Post by avtolle on 2009-02-11
How did you install to the partition you created? That is, did you format the partition ext3, then (using manual partitioning) designate the entire partition with a mountpoint of / (for root)? Or, did you have the installation disk do an installation in the space?

The reason for the questions is that JuJuLand is correct; there needs to be two small partitions created for Linux to boot on a ppc mac. The first (which likely exists if you are dual booting with OSX) is a very small partition which holds the MacOS partition table (64 bytes, IIRC). The next, which must be formatted HFS, is an approximately 1 mb partition used as a boot partition, and is where yaboot looks to find the boot information. Then, the user may create at least two other partitions, one for root, mounted at /, the next for swap (mounted at /swap). Thus, the HDD should have at a minimum four partitions in total: one for the MacOS (if present; if not, the partition table); the boot partition; the root partition; and the swap partition (the last three for the Ubuntu installation).

Hopefully, this will not confuse you. My suggestion, absent someone with more knowledge than I, is to delete the 30gb partition you created, making it free space; then reinstall, choosing "install to largest continuous space) option, allowing the installer to create the needed boot (and possible partition table) partition(s), along with the root and swap partitions in that space.

---

### Post by METC on 2009-02-11
> **avtolle said:**
> How did you install to the partition you created? That is, did you format the partition ext3, then (using manual partitioning) designate the entire partition with a mountpoint of / (for root)?

yes! that was exactly what I did!

---

### Post by avtolle on 2009-02-11
> **METC said:**
> yes! that was exactly what I did!
I thought so. As earlier posted, you need to create a small partition, formatted HFS, for boot; and you should also create a swap partition as well. I presume you used the alternate install disk to install 8.10, given the lack of a "final" live cd for 8.10 ppc, so the "easier" fix for this won't work (unless you might happen to have a Live CD from 8.04). I still suggest deleting the 30 gb parition you created and installed to, and then doing the installation from the alternate CD I suggested. I believe that will work, but hopefully others will be along to suggest possible alternatives.

---

### Post by METC on 2009-02-11
I have an intel mac. I used the 8.10 live desktop cd to install. how do you make the swap partition?

---

### Post by avtolle on 2009-02-11
Sorry, misunderstood. Disregard the prior ppc related stuff.

Boot from the live cd. Once the desktop appears, go to System>Administration>Partition Editor. This will bring gparted up. Check to be sure that the partition you want to work on is not mounted; if it is, then select it and unmount it (under Partition in the top bar). Choose to resize/move that partition; resize it to create some unallocated room. Select the unallocated room, once it is finished, choose to make a new partition, and answer the questions to make it a swap partition. Size of swap is generally recommended to be 1.5 to 2x RAM; if you have >=1gb RAM, imho, 1gb is sufficient. Once the change is made, then exit. Make sure that swap is set on in the new partition.

However, that doesn't solve your booting problem. I'm not at all familiar with intel macs, but you might take a look in the help area for instructions for your particular mac. Good luck.

---

### Post by avtolle on 2009-02-11
Another read too fast; just noticed you have an 8.10 Live CD which, if I recall correctly, doesn't have gparted installed on it as a user application callable from the desktop. To get it, you need to install it in RAM; go to a terminal (Applications>Accessories>Terminal) and at the command prompt, do```
sudo apt-get update && sudo apt-get install gparted
```which will install it for you.

---

### Post by METC on 2009-02-11
It has gparted.

---

### Post by avtolle on 2009-02-11
> **METC said:**
> It has gparted.
That's good; you need to use it to work on the partition to get a swap partition as generally outlined before.

Found [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) while poking around a bit; I know you've already installed, but may I suggest looking at this, if you've not already done so, for some tips on how to install should you decide to reinstall. You might also take a look at the FAQ sticky for Mactel users at the top of the thread for other information on how to get your installation to boot.

---

### Post by cyberdork33 on 2009-02-11
> **avtolle said:**
> found [https://help.ubuntu.com/community/mactelsupportteam/appleintelinstallation](https://help.ubuntu.com/community/mactelsupportteam/appleintelinstallation) while poking around a bit; i know you've already installed, but may i suggest looking at this, if you've not already done so, for some tips on how to install should you decide to reinstall. You might also take a look at the faq sticky for mactel users at the top of the thread for other information on how to get your installation to boot.
+1

---

