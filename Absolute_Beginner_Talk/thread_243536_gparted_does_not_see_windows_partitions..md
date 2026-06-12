---
title: "gparted does not see windows partitions."
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by hayati on 2006-08-25
[B]
i have acer aspire 1694wlmi and xp already installed on a partition. it has 2 more windows partitions. When i boot with Dapper LiveCD Disk-admin sees them all right but gparted says that it's all "unallocated". this is wrong info. when i press next without any allocation it sees partitions but this time it says "you need to specify a root directory". Specifying a root directory requires to write mbr which is very risky. [/B]

-----------------------------------------------------------------------------------
some body had the same problem before as below
-----------------------------------------------------------------------------------




Binary package hint: gparted

I've just installed DapperRC on an AMD box with two hard disk drives, I used the LiveCD and gparted to partition the first hard disk and I installed XP on it, then again I booted the LiveCD and installed Dapper on the second disk. The problem is that gparted doesn't recognize the Windows partitions and the swap partition it created on the first disk: it simply says "Type of disk: not recognized" and all the disk space is tagged as "unallocated". Note that disks-admin sees them all right, and in fact I successfully added them to fstab (can access them fine). Same goes for fdisk:

sudo fdisk -l /dev/hda

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot Start End Blocks Id System
/dev/hda1 * 1 2611 20972826 7 HPFS/NTFS
/dev/hda2 2612 5222 20972857+ 7 HPFS/NTFS
/dev/hda3 5223 19929 118133977+ 5 Esteso
/dev/hda4 5745 19929 113941012+ b W95 FAT32
/dev/hda5 5223 5744 4192902 82 Linux swap / Solaris

This is on an AMD Sempron 3100 box, the disks are two brand new SATA 160 GB Maxtor drives, CPU is an AMD Sempron 3100, GPU an ATI Sapphire Radeon 9550.

    * Edit description & tags

---

### Post by TFX360 on 2006-08-25
Did you check both disks? You need to open the button on the right for the next disk. Had this myself once...


Kind regards,


TFX

---

### Post by benfindlay on 2006-08-25
It could also be a problem with your mbr. If the mbr is damaged in certain ways, windows will still boot and everything, but progs like gparted will have difficulty recognising their existance. Try booting up your windows installation cd and going into the recovery console and typing "fixmbr" (no quotes obviously!)

This will repair any faults in your mbr and mean that gparted should be able to see it ok!

Hope this helps!

---

### Post by doodsangel on 2006-08-25
I have the exact same problem, but only one HDD though.

Partitioned as follows:
1. Windows
5. Linux root /
9. Swap
10. Linux /home
2. WinXP apps
3. Music partition
4. games partition.
6. Unallocated.
7. Linux work partition (where I store a lot of data and the like)

When I open GParted, I get the same error/message.

I have fixed mbr last night, but it stays the same...

I would also like more info on this.

---

### Post by hayati on 2006-08-25
yes you're right, i'll try this.
but amazingly disk-managers see them correctly but gparted doesn't. This sounds like a bug. Hopefully mbr was the problem. I'll report if i succeed. 

Thank a lot.

---

### Post by hayati on 2006-08-25
there is a misunderstanding. 
the first paragraph is mine, the other is a similar problem that i found from web which is left un-answered.
i also have exactly one HDD. it's configuration is about yours. but you said i had tried fixing mbr but it didn't worked. i'll try fixing mbr anyway. But i don't think the problem is mbr because disk -managers shows them correctly. 

thanks...

---

### Post by doodsangel on 2006-08-25
Like I said. I cannot get my Gparted to show anything except "unallocated". 

I had a mission installing Ubuntu, because I had to FDisk my partition to create install partition (/)as Ubuntu installer also did not pick anything up. The only option Ubuntu partition manager gave me was to wipe my whole HDD... yikes....](*,)  

Ended up having to manually **mount /dev/hda5 /target** before I could continue my install. Even downloaded Gparted live from the website and tried that. 

At the moment I'm flying without GParted as it does not work.... I'm rather sure it is not my MBR. 

If you need help installing without GParted I can help, otherwise I would also like any information on how to fix this (GParted)....

---

### Post by hayati on 2006-08-25
ok guys, after digging internet and ubuntu forums, some solutions is available. i haven't tried any but they sounds like they solved the problem. the link is 

[http://www.ubuntuforums.org/showthread.php?p=1420541#post1420541](http://www.ubuntuforums.org/showthread.php?p=1420541#post1420541)

the title is "where are my partitions!!"
in  Ubuntu Forums > Dapper Drake 6.06 Release  > General Support  > Installation and Upgrade Help

unfortunately the problem is in the windows installer.

but anyway i want to hear the other solution "installing without gparted"

thanks to all.

---

### Post by doodsangel on 2006-08-25
Alright, here goes:
*Working from memory :-k *

Alright. 
1. Instert CD, and boot in  to ***expert***. If expert is not selected my installer blatantly refused to copy base system.
2. I then clicked through all options for cdrom, copy packages and the like going down the list till where I got the partition manager.
3. I clicked on partition manager **as well **to go into Partition manager, and it told me that I can wipe my whole 120GB and start from scratch. Then I skipped that step for wiping the 120GB, and just said [COLOR="red"]write partition to disk.[/COLOR] Obviously it gives an error and returns to the expert menu. [COLOR="Red"]<-but it is an important step.[/COLOR]

*Now you might wonder why go into partition manager only to get the error after doing nothing and then saving the information. To be honest I don't know exactly why, but I do know what happens if you don't. If you do not go through that motion you will receive an error messages later when trying to install the base system that the target is not defined or something of the kind.*

So you are right. Up to here nothing happened of interest and the partition tool failed and there is no mount point.

4. Then I browsed to the bottom of the list and selected [COLOR="red"]execute shell command[/COLOR].
5. In shell I did:
5.1. mkdir /target
5.2. mount /dev/hda5 /target
5.3. exit

Note that my root partition is /dev/hda5, obviously you would change it to your own root partition if you would like to use it.

5. Now I think it jumps back to partition manager in the list again, but don't run it. Skip the Partition Manager, LVM and the like till you get to [COLOR="red"]Install base system[/COLOR]. Do this and go down the list doing the options one by one again installing grub and the like.

6. When the installation is completed, your system will restart, and present you with GRUB. But grub is not neccesarily going to be configured correctly. So try it, and if it fails do the following: 
Select the boot ubuntu option, but press [COLOR="red"]'e'[/COLOR] for edit.
7. Edit the list according to your machine setup:
```
title Ubuntu, kernel 2.6.12-9-386
root (hd0,4)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot
```
My root is on /dev/hda5 and thus **root (hd0,4)** if your root is located on /dev/hda3 it will look more like this: [COLOR="red"]root (hd0,2)[/COLOR]
**kernel /boot/vmlinuz-2.6.12-9-386 [COLOR="red"]root=/dev/hda5[/COLOR] ro quiet splash** because I have /dev/hda5 is root.

If this is configured as you want it press [COLOR="red"]'b'[/COLOR] to boot.

8. Ubuntu should start now. After booting into UBUNTU I opened **terminal **and did a **[COLOR="red"]su[/COLOR]**
9. Then I fixed the menu.lst for GRUB.
9.1 cd /boot (i think this is where I got it)
9.2 [COLOR="red"]vi menu.lst[/COLOR] and changed it to reflect the settings I have @ point 7 and saved.
9.3 exit terminal

And that is it if I remember correctly.

---

### Post by doodsangel on 2006-08-25
Oh, just one thing that precedes all this:

As I said before, I downloaded GParted live from their website. I booted into this first of all only to be dissapointed by "unallocated" message and could not configure my partitions.

What I was able to do with it was however to setup the partitions with FDisk.

> 
**birdbrain** from thread: [http://www.ubuntuforums.org/showthread.php?t=241274](http://www.ubuntuforums.org/showthread.php?t=241274)

You may need to partitions, 1 small parition for your swap drive and another for your root install. It is also possible that you may need to boot into the live cd, umount the paritions you want and use fdisk

WARNING, if you use the wrong parition, eg your windows partition you could loose data. Just starting fdisk won't do any harm but the later steps may if you choose the wrong partition.

1. fdisk /dev/hda
2. type p to get a listing
3. note the number of the parition you want and then press t (for type)
4. set the type to 83
5. press w to write the changes to disk

P.S you should also have a smaller partition of between 512 and 1024MB for your swap space. If you setup you swap space then change the type of that partition to 82

Now you can format your paritions
Lets say that /dev/hda2 is swap then typing:
mkswap /dev/hda2 would setup hda2 for swap

# WARNING - This is the step that would stuff your data up if you have the wrong partition.
If you wanted reiserfs for say /dev/hda3 you could type
mkreiserfs /dev/hda3

You could then try and reboot and use /dev/hda3 for root i.e / and /dev/hda2 for swap.

---

### Post by hayati on 2006-08-25
perfect!!!

really attractive solution. your steps reaches to an alternate solution. But it's a **solution**. :) 

thanks to all
regards...

---

### Post by doodsangel on 2006-08-25
Blood sweat and tears I tell ya... 

But I have to give the community credit as well. If it wasn't for birdbrain's advice on how to use fdisk, and anaconda's help on GRUB, I would have been screwed... As well as to the guys I didn't mention.....

:D

---

