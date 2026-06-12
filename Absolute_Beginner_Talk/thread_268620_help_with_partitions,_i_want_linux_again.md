---
title: "help with partitions, i want linux again"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2006-09-30
hi, i already used linux (a friend of mine made the installation for me), but i formated the pc and now i regret it big time.. and i don't have my friend to instal it this time for me!

so, i am trying to instal linux by myself but i am having some problems with the partitioning.. my version of linux is Ubuntu 6.06 LTS

ok, onto business, i hope you guys can help me..

i have 3 hard drives...one with 17Gb, other with 80Gb and another with 200Gb.

>i want to split the 80Gb in three partitions so:

in the first partition, 12Gb will be enough, i want to instal linux.
in the second partition, 12Gb will be enough, i want to instal windows XP so that i can have dualboot (i need to work with a certain program that only runs in windows!)
in the third partition, i want to have it for saving files.

>in the 17Gb hard drive i want to spit in two.. one partition for swap, the other for amule..so, will 1024mb be enough for swap?

>i don't want to mess up with the 200Gb hard drive, i have data there that i don't want to loose. like i said, i already used linux so this drive is ready to use with it because it was not formatted to use with windows.. it has 1024mb of space saved for the swap, can i delete these 1024 mb (i prefer using the 17Gb for swap) and keep the rest of the data?remember, i need that data so, i need to be sure if i delete the swap, i will not delete all the data of that hard drive!

i really need a detailed description on how to do this, i already tried different ways to install it but, after selecting the partitions, it always says:"no root file system"

i need help on how to make the partitions and what options should i choose in each case.. hope someone can help me, i really want linux again.

---

### Post by petri on 2006-09-30
Yes, of course you can partition it like that. But maybe it is better to study a little? ;) [Here's]("http://www.psychocats.net/ubuntu/index.php") a site which shows you how to plan and then how to do it.

---

### Post by cmaranhao on 2006-09-30
thanks for the link but even with that i don't think i can do it alone

---

### Post by bulldog on 2006-09-30
> **cmaranhao said:**
> thanks for the link but even with that i don't think i can do it alone

You have to learn sometimes :D 

You want a complete diskmanagement so you have to learn it yourself.

If you want to partition just one hdd for Ubuntu or even dual boot you've got plenty of help.

But your plans and your skills [no offence] cost a whole evening to explain.

---

### Post by orb9220 on 2006-09-30
First you need to insstall xp first so when ubuntu install it will see it.
And xp is picky and it is easier to have it on the first partition of first HD. Then install your root partition then swap.

You need to make sure your 80GB is master drive on primary IDE channel.

So first drive is 80gb first partition is ntfs xp ==== hda1
.                      second             ext3  / ==== hda2
.                      third              linux-swap== hda3

Second drive      17Gb  first partition is ext3 for amule and swap not needed

Third HD is your 200gb and deleting the swap on the 17gb will not do anything on the other partition.

Hope this help some.

---

### Post by petri on 2006-09-30
Did you read it allready? :mrgreen: 8) 


Partition sizes on 80GB seems good... but install XP first then Linux and the third partition format with FAT32 so you can use it from both OS.

Swap is usually twice your RAM. You might do the partitions with your LiveCD. At installation you have to choose manuell partitioning anyway to make the mountpoints to your partitions.

Read the guides about plan partitions and how to install. Good luck! :D

---

### Post by cmaranhao on 2006-09-30
the problem is that after making the partitions, it says "no root file system"

can you guys "make me a map" or something? lol

like in the 80Gb drive:

new partition, 12Gb, primary partition and ext3...and so on..

for the 17gb, how do i set the swap...

and after this how do i choose the options??

the reason i am asking this (and i know its a lot) is because i think i am doing something wrong and don't know where..i described the way i want the configuration of the drives, this way you can help me.

please?

i am trying different partitions for over 3.5 hours :( with no results

---

### Post by petri on 2006-09-30
Anyone? Ok, Donkey does it :mrgreen: 

On your 17GB install XP.

On your 80GB make 20GB ext3 for root (linux) 2GB swap and +50GB ext3 to your **/home** folder. With that you can install linux how many times you want and not losing your files from your own folder.

Partition for sharing files? You are not going to use XP for anything else than playing games. I'm quite sure about that ;) 

Amule? There's a room for them in your /home.


EDIT: You did know that you can browse internet (the guide) while you install Ubuntu?

---

### Post by Javier_Electrico on 2006-09-30
Why dont you try to installing xp in the 80Gb CLEAN?(i mean with no partitions).  Then try some like Partition Magic to make all the divisions that you want(advice: dont make an extra partition for swap, let Linux does it). After that, run the miracle Linux cd =).  On the installation Linux will tell you "hey, i've found some partitions. Which one do you want to use?".
One last advice: you HAVE to install windows before installing linux, because if you install Linux and then Windows. Win is gonna take the control of PC, leaving grub into a second place.
and read the link that petri gave to you. Always is better to learn by your own

---

### Post by cmaranhao on 2006-09-30
lets forget windows for now.. i can instal vmware later and have it.. i need windows because i need to use a certain software that only works with windows.

i will give you my partitions and i want to know what is wrong with them.

-- on the 80 Gb drive, i did it like this:

-create primary partition #1 (ext3, 20000MB) on /dev/hda 

this way i can install linux here and vmware with windows.

-create extended partition #2 (extended, 60000MB) on /dev/hda 

after setting this it appeared like this:

- /dev/hda1   filesystem: unknown   size:20 Gb
  /dev/hda2   filesystem: extended  size:60 Gb
    unallocated   filesystem: unallocated  size:60 Gb

-- on the 17Gb drive, i did it like this:

-create primary partition #1 (linux-swap, 2048MB) on /dev/hdd

-create extended partition #2 (extended, 15000MB) on /dev/hdd

i want to put amule in this hard drive

after setting this it appeared like this:

- /dev/hdd1   filesystem: unknown   size:2 Gb
  /dev/hdd2   filesystem: extended  size:15 Gb
    unallocated   filesystem: unallocated  size:15 Gb

--on the 200Gb drive i am afraid to mess up, because it has important files. it is like this:

  unallocated   filesystem: unallocated  size:1 Gb
  /dev/hdb1   filesystem: extended   size:188 Gb
  /dev/hdb5   filesystem: ext3      size:188Gb

after setting this up i go to mount points menu. i set it like this:

mount point       size          partition          reformat

    /              20              hda1               yes
   swap            2               hdd1               yes
 /multimedia       189             hdb5                no
 
the hdb1 drive, it says it only has 1Kb of size, what should i do with it? also, where are the other partitions? i don't have the hda2 (50Gb) and i don't have the hdd2 (15Gb) to mount.

after this detailed post, i hope someone can help me to install now :)  please??? :)


i need to know if i am doing the partitioning right!

---

### Post by cmaranhao on 2006-09-30
ok, i've done it, finally!!!!

now i just need to know how to mount all the partitions.. any tips are very welcomed!!:p 

side note: i have tons of things to do like install codecs, java, flash, rar, ace, etc, etc, etc

i'm doomed lol

---

### Post by petri on 2006-09-30
Congratulations!

They will be mounted automaticly at your ubuntu installation when your choose "partition manually".

There is Automatix which cna install codecs etc att [http://www.getautomatix.com](http://www.getautomatix.com)

Otherwise there is RestrictedFormats on wiki [https://help.ubuntu.com/community/RestrictedFormats#head-2491078b7f3fdd9ad37ffe23e43eeafdebf4187b](https://help.ubuntu.com/community/RestrictedFormats#head-2491078b7f3fdd9ad37ffe23e43eeafdebf4187b)
if you want to do some pasting in terminal.

---

### Post by cmaranhao on 2006-09-30
i want to have a shortcut in my home folder of the 200 and 17 hard drives.. how can i create a shortcut of them?

i want these hard drives to appear like a folder inside my home folder.. can you give me any tip?

thanks for the codec link

---

### Post by devils_casper on 2006-09-30
create sym link (shorcut)

ln -sf path_of_hard_drive /home/user_name/drive_name




casper

---

### Post by cmaranhao on 2006-09-30
just did it with my 17Gb hard drive but i cannot open it because its locked (it shows a briefcase with a lock on it )and it says it has 0 bytes of space.. 

i tried to click on it with the right button of the mouse to enable writting, reading, etc but i cannot do that.all the options are greyed.. what should i do to have the shortcut?

thanks

---

### Post by devils_casper on 2006-09-30
post the output of fdisk -l ( its small 'L')

sudo fdisk -l





casper

---

### Post by cmaranhao on 2006-09-30
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2550    20482843+  83  Linux

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1             132       24792   198089482+   5  Extended
/dev/hdb5             132       24792   198089451   83  Linux

Disk /dev/hdd: 17.3 GB, 17340000256 bytes
255 heads, 63 sectors/track, 2108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1         261     2096451   82  Linux swap / Solaris



i want shortcuts for the 200GB hard drive and the 17GB, both shortcuts inside my home folder.

---

### Post by cmaranhao on 2006-09-30
almost forgot, i partitioned my 80GB hard drive in 20GB for the OS and 60 for backup.. i also want these 60GB to appear inside my home folder

---

### Post by devils_casper on 2006-09-30
your 17 GB harddisk has only SWAP partition. you can't mount that... there is not data, no other partition.
whats the format of 60 GB partition. hda2 or hda5 is not listed in fdisk's  output.





casper

---

### Post by cmaranhao on 2006-09-30
when i partitioned my drives i made it like this:

-- on the 80 Gb drive, i did it like this:

-create primary partition #1 (ext3, 20000MB) on /dev/hda

this way i can install linux here and vmware with windows.

-create extended partition #2 (extended, 60000MB) on /dev/hda

after setting this it appeared like this:

- /dev/hda1 filesystem: unknown size:20 Gb
/dev/hda2 filesystem: extended size:60 Gb
unallocated filesystem: unallocated size:60 Gb

-- on the 17Gb drive, i did it like this:

-create primary partition #1 (linux-swap, 2048MB) on /dev/hdd

-create extended partition #2 (extended, 15000MB) on /dev/hdd

i want to put amule in this hard drive

after setting this it appeared like this:

- /dev/hdd1 filesystem: unknown size:2 Gb
/dev/hdd2 filesystem: extended size:15 Gb
unallocated filesystem: unallocated size:15 Gb

--on the 200Gb drive i am afraid to mess up, because it has important files. it is like this:

unallocated filesystem: unallocated size:1 Gb
/dev/hdb1 filesystem: extended size:188 Gb
/dev/hdb5 filesystem: ext3 size:188Gb

now, i want to have a shortcut of the hda2, hdd2 and the hdb (not sure if it is the 1 or 5).

is it more clear now?i am noob in this :(

---

### Post by devils_casper on 2006-10-01
Hi !

hda2 and hdd2 are Extended partitions. you have create Logical(s) partitions in it. new partitions will be hda5/hdd5...

hdb5 can be mounted... but, create logical partitions in hda and hdd first.



casper

---

### Post by cmaranhao on 2006-10-01
hooo, i get it.. to mount the extended partitions i must create logical partitions first.. i already have a logical partition for the 200Gb so this one can be visible right?

how can i create logical partitions now? do i have to re-install linux again?

keep in mind i am a total noobie here ](*,)

---

### Post by cmaranhao on 2006-10-01
i decided to install linux all over again, this time i created logical partitions, lets see if they show up inside home.

thanks for your help.. i still have plenty of stuff to do.. maybe you will see another posts of mine :mrgreen: 

thanks a lot guys, without you i would be stuck in partitioning drives like yesterday

---

### Post by cmaranhao on 2006-10-01
ok, just typed "sudo fdisk -l" in the terminal and i had this:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2550    20482843+  83  Linux
/dev/hda2            2551        9729    57665317+   5  Extended
/dev/hda5            2551        9729    57665286   83  Linux

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1             132       24792   198089482+   5  Extended
/dev/hdb5             132       24792   198089451   83  Linux

Disk /dev/hdd: 17.3 GB, 17340000256 bytes
255 heads, 63 sectors/track, 2108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1         261     2096451   82  Linux swap / Solaris
/dev/hdd2             262        2108    14836027+   5  Extended
/dev/hdd5             262        2108    14835996   83  Linux


i want to have a shortcut of the hda5, hdb5 and the hdd5 inside my home folder. how can i do that?

---

### Post by devils_casper on 2006-10-01
so you reinstalled... 

check /media folder. all partitions hda5, hdb5 and hdd5 should be there..
you can create shorcuts using 'ln' command.

ln -sf /media/hda5 /home/user_name/hda5




casper

---

