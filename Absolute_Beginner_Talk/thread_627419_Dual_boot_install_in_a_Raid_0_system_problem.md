---
title: "Dual boot install in a Raid 0 system problem"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by maggus76 on 2007-11-30
Hello 

I have an XP system with a Raid 0 (2x120 gm disks) and another 120 FAT32 hard disk which is not used in Raid and works more like a storage of music etc.. I always tried to have a working linux and i heard really good comments on ubuntu about its user-friendliness. 

So after doing a defragmentation of the FAT32 HD i used the ubuntu installer to install ubuntu. After using the automatic partition i chose to give 60GB to ubuntu. The installer did the partition and installed all that had to install. Then it went to a reboot and since then i cannot gain access into linux since i go straight to xp like i have never done any partitioning or linux installing. The seperate FAT32  HD is now shown as a 60GB disk since the other 60GBs are given to ubuntu. However i dont get any Lilo-style way to choose to which system should i go when i start the PC. In no point of the installation process was i given an option to choose if i was going to have a dual boot system or anything.

I should note that the windows are installed in the Raid 0, while the Linux on the seperate FAT32

Any thoughts or solutions?

---

### Post by zero-9376 on 2007-11-30
i had a similar issue (without the raid) where ubuntu installed grub to a different HD than the bios was using, sounds like you have a similar issue. Try changing your bios to boot from the other disk

---

### Post by maggus76 on 2007-11-30
so is there so way or some dual boot loader that checks all disks? cause its kind of a problem to change bios settings whenever i want to go to linux

---

### Post by zero-9376 on 2007-11-30
so i assume it worked when you booted from the other disk?

if grub didn't have windows in the list of boot options my guess would be that is to do with the raid array which is probably a hardware/software type.

you might want to look at info on grub and raid arrays and maybe chainloading which may be of use in this situation.

---

### Post by maggus76 on 2007-11-30
damnit .. i always heard that linux people were so help full ... :) ... 2good2btrue... 

so i guess chainloading is telling grub to check more than one HDs to load from .. will try that thanx

---

### Post by zero-9376 on 2007-11-30
unfortunately not everyone is an expert and that includes me. but we do try to help where we can and thats what makes this such a great community.

were you able to boot into ubuntu when you changed the bios settings?
was windows presented as an option?

reading this: 

[http://www.overclock3d.net/articles.php?type=3&id=51&page=2&desc=dual_boot_raid_windows_and_linux](http://www.overclock3d.net/articles.php?type=3&id=51&page=2&desc=dual_boot_raid_windows_and_linux)

it seems grub doesn't handle the software raid very well but it mentions that lilo may work for you although i would think that windows would have installed its own bootloader in one of the MBRs of the array in which case you may want to experiment with grub configs such as this old post mentions

[http://ubuntuforums.org/archive/index.php/t-300586.html](http://ubuntuforums.org/archive/index.php/t-300586.html)

If you feel like your not getting the help you need I apologise but once again I am no expert.  If you are willing you might want to try the IRC channel plenty of knowledgable people hang out there.

This page has some info on grub which may be useful:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
and [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) talks about  lilo and other things that may be useful.

---

### Post by zero-9376 on 2007-11-30
i asked on IRC for you and it seems more info is needed about your setup. this is the conversation:
zero-9376: can grub boot an xp install on a software raid 0?

ampex_: zero-9376: it may be possible with dm-raid, what type of software RAID is Windows using?

zero-9376: ampex_: im not really sure im trying to help this guy [http://ubuntuforums.org/showthread.php?p=3866522#post3866522](http://ubuntuforums.org/showthread.php?p=3866522#post3866522)

ampex_: zero-9376: we would need to know more about his hardware

ampex_: zero-9376: what type of chipset he is using for his RAID

ampex_: zero-9376: if the ubuntu installer doesn't see the software RAID array or sees it as two disks, it probably wouldn't have installed grub to it. He may just have to change his boot order to get the second drive to boot before the RAID array.

zero-9376: ampex_: yeah i thought as much i will post again and ask him/her to provide more information

ampex_: that is what i suspected, he has not clarified whether ubuntu would boot once he changed the order in the bios but i wanted to know whether grub would have seen the windows install (assuming its software only)

 zero-9376: ampex_: i dont know how windows handles the MBR/boot when its in raid, does it still install to the MBR of the disk like normal?
zero-9376: i guess that depends on the hardware

ampex_: zero-9376: I assume it depends on the hardware

So it seems more information would be needed to assist with your problem. Specifically what chipset you are using for your raid array and I think it would also be good to know how ubuntu 'sees' your raid array - as one partition or two separate partitions?

---

### Post by kosmic on 2007-11-30
First things first.

1 - You say you are using RAID 0, ok it is RAID 0 but is  your motherboard that give you RAID option ?? if yes then you ARE NOT using a real RAID system, but a SOFT RAID...

SOFT RAID is not a good solution, avoid instaling OS in a Soft RAID system if you don't want to have troubles

Second you installed your boot loader (GRUB) to the second disk of the Soft ARRAY, this hapened because Ubuntu installer sees 2 disks and not 1 has it should in an array.

So keep things simple, find your Master disk, create in that disk a partition for ubuntu, and when it gives the option to save grub choose to save to the MBR (Master Boot Record).

Happy now :) ?

---

