---
title: "New to the Game..."
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by raydanator on 2007-09-06
Hi, I have a laptop that I would like to dual boot Ubuntu on, but I"m wondering what version I need, and how to set it up. Its a Dell running Windows Xp. Any advice would be appreciated. 

Thanks.

---

### Post by oilchangeguy on 2007-09-06
please advise your computers specs.
and see this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by linux noooob on 2007-09-06
I know it can be confusing at first but i got the hang of it. all you have to do is download ubuntu 7.04 burn the iso to a cd *not as a data cd but as and iso!!* when done restart comp with cd in drive if it does not auto start then reboot hit the botton it tells you to hit to go into the bios when in change the boot options so the cd if first. and last use safe graphics mode it is alot faster!! then you install it and you are done * when resizing partition use the gpart first then install!!

---

### Post by oilchangeguy on 2007-09-06
this may be more helpful in regard to an iso how to:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by raydanator on 2007-09-06
It is a Dell with Sp2, and 1.7 Proccesor, as well as a 60 gb hard drive and integrated graphics. And for RAM, 512. 

 Thanks for the article, I think that 's where I need to get started. Would you reccomend downloading the latest Ubuntu version, or is that too much for my machine?

---

### Post by oilchangeguy on 2007-09-06
> **raydanator said:**
> It is a Dell with Sp2, and 1.7 Proccesor, as well as a 60 gb hard drive and integrated graphics. And for RAM, 512. 

 Thanks for the article, I think that 's where I need to get started. Would you reccomend downloading the latest Ubuntu version, or is that too much for my machine?

version 7.04 should be fine. one thing however. how much free space is left on the hard drive?

---

### Post by Harpoon on 2007-09-06
If by "the latest version" you mean Feisty, the answer is yes.  It fixed a lot of problems that plagued Edgy.  I have not yet tried Gutsy, myself, so it's hard for me to give you an opinion on that one.

---

### Post by raydanator on 2007-09-06
Well,  I'm actually going to wipe it and start over with a fresh copy of Windows and Ubuntu, so I think I should be alright. How much is recommended to run smoothly?

---

### Post by oilchangeguy on 2007-09-06
> **raydanator said:**
> Well,  I'm actually going to wipe it and start over with a fresh copy of Windows and Ubuntu, so I think I should be alright. How much is recommended to run smoothly?

i'd just split the drive in half, 30gb for each os. or do a 40/20. 40 for windows.

---

### Post by SOULRiDER on 2007-09-06
Its also a good idea to install Windows first that way you wont have to recover GRUB.

---

### Post by parvinder on 2007-09-06
You don't need to wipe out the windows installation.... just pop in the Feisty 7.04 disk and boot from cd. 

you will get option to Run/Install ubuntu hit <Enter>
* it will boot to desktop and if you are lucky will detect your wireless and you are ready to test  it before installing it on your system.
* Next use the partition manager from the menu System->Admin->gnome partition manager to resize your disks.
* click the install icon on the desktop to install ubuntu.


You are ready to go with dual-boot system. WIndows and Ubuntu.

---

### Post by joshier on 2007-09-06
> **raydanator said:**
> Well,  I'm actually going to wipe it and start over with a fresh copy of Windows and Ubuntu, so I think I should be alright. How much is recommended to run smoothly?

how much in what respect?.. disk space?.. ram size?

For ubuntu, I'd recommend atleast 5GB HD space because you'll really get into lots of applications and find lots of stuff to do... 

You may want to play around using the live CD first.

---

Also, you'll want to first boot linux, format HD using Gnome partition editor, which is a friendly GUI HD partitioner.  This can be launched on the live CD and it is placed in the top menu > system > administration.

Format the HD (make sure you backed up everything).. you then will want to create an NTFS partition for windows.. you can use the whole of the HD if you like, because after a few more steps - ubuntu will resize it for itself.

OK, so, once you've formatted your HD with at least one NTFS partition on it (and nothing else at this point in time depending on what option you chose in the last paragraph).

You then commence edit, it will format plus make ntfs partition, you then restart, install windows the best way (boot from cd)... make sure to tell it to ue the ntfs partition and you can let it do a quick format if you like.

Upon finalizing windows instillation, you will then want to boot ubuntu disc again, select to install ubuntu. Ubuntu will then ask you how you want to install it... now, you can either setup partition for it manually, or do it automatically and tell it to use X amount of HD space taken from the NTFS partition (it will just resize the ntfs partition and create an ext3 partition, which is the equalivant to ntfs in linux world, and *also* a 'swap' partition, which is used for temporary storage.

It will set it all up and add windows to grub so you can select which OS you want to go into upon boot.

Hope this helps

---

### Post by jimrz on 2007-09-06
if your XP install is in need of a re-install then I would suggest downloading the G-parted live cd and use it to delete the current XP partition and then create new partitions for your new installs. Remember that you will need a separate partition for swap (for a laptop 1.5 x amount of RAM - in your case = 768) + you probably do not want to mess with your Dell restore partition + you are only permitted 4 primary partitions on your drive, but one of them can be an extended partition which can contain any number of partitions within itself. suggest 1 primary as XP + 1 primary as Ubuntu root + 1 primary as your Dell restore + 1 extended into which you put your swap + possibly a separate Ubuntu /home partition and maybe a small FAT32 partition to share data between the OS's.

if your current XP is ok then just do the partitioning with your Ubuntu install disk, but remember to defrag your XP partition AT LEAST twice before resizing it. always back up important date before doing any of these type operations.

---

### Post by raydanator on 2007-09-08
You know something, I'm afraid I have the wrong specs on the laptop I wanted to use.  The Dell I was thinking of using has 256 mbs of ram and a 30 gb hdd. Do you think that is still enough for the 7.04 or do I need to go to a different version?

Thanks very much,

---

### Post by raydanator on 2007-09-08
Wow, thanks for all the help, I didn't see the second page. You guys rock!!

---

### Post by BrendanM on 2007-09-08
7.04 should still be fine, but I would go with Xubuntu (which has a lighter GUI) and use the alternate text-based installer. The live CD is going to be really slow on only 256 MiB of RAM.

---

### Post by Kedster on 2007-09-08
for the partitions make sure u put a partition that both Ubuntu and windows can read (FAT 32) so that u can share files between the two and the swap u could make 512 or more because i find that the more virtual memory u have the better the hibernation works i made the swap 266 and it sied that it had a hard time to hibernate so.  ohhh and i like ask is there a way to delete a bios and if so can grub be used as a bios or is there a linux bios

---

