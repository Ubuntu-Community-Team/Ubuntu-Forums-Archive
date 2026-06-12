---
title: "Installing ubuntu without destroying my computer"
date: 2007-04-21
forum: Apple Intel Users
---

### Post by cybergoldfish on 2007-04-21
Sorry if this has been posted before, I've had a look around but can't seem to find it. I've got to the point of installing ubuntu 7.04 on my macbook, and got to stage 4 of 7, where i have to select partitions and stuff. I've already used boot camp to partition 15gb off for what i intend to use for ubuntu, so i select /dev/sda3 , which is 16610mb and presumably the right one. But then apparently i have to select another partition as well? But this one needs to be only about 256mb or something.

I'll try it again and write down all the details, but I thought someone here might know what I have to do at this point, and how to do it. I'm a bit* scared that I'll totally destroy my precious new computer.

Thanks,
james

*very very very very very

---

### Post by ronocdh on 2007-04-21
> **cybergoldfish said:**
> Sorry if this has been posted before, I've had a look around but can't seem to find it. I've got to the point of installing ubuntu 7.04 on my macbook, and got to stage 4 of 7, where i have to select partitions and stuff. I've already used boot camp to partition 15gb off for what i intend to use for ubuntu, so i select /dev/sda3 , which is 16610mb and presumably the right one. But then apparently i have to select another partition as well? But this one needs to be only about 256mb or something.

I'll try it again and write down all the details, but I thought someone here might know what I have to do at this point, and how to do it. I'm a bit* scared that I'll totally destroy my precious new computer.

Thanks,
james

*very very very very very
What's happening is that Ubuntu is taking the 15GB slot and intending to install on it. It wants, however, an additional partition, about 1-2GB, for use as "swap." Swap space helps the computer better manage RAM usage; it's like a place where data can be "on deck" for use in RAM. 

IIRC, you can install without specifying swap space, although it will caution you about it. You can also create a swap file later, once the system is installed. If you have 1GB of physical memory, you'll be just fine, because Linux doesn't really hog it. ;)

Make sure the large partition you've created is set as "/". That means it'll be the root space, and then although the installer requests you have a "/swap" partition too, just ignore that for now. Good luck!

---

### Post by cybergoldfish on 2007-04-22
Thanks. I've got 2gb of RAM so I think I'll leave the /swap partition for now. But when I try to edit my 15gb partition, it comes up with 'use as' and 'mount point'. If I don't select 'use as' then when I set the mount point to "/" then nothing really happens, and I can't move on. So. which of the 10 'use as' options should I select? ext3. ext2. reiserfs, jfs, xfs, fat16, fat32, swap [i'm guessing not that one], efi or dontuse [i'm presuming not that one either. But I can only guess...]

Thanks for your help :D

---

### Post by ronocdh on 2007-04-22
> **cybergoldfish said:**
> Thanks. I've got 2gb of RAM so I think I'll leave the /swap partition for now. But when I try to edit my 15gb partition, it comes up with 'use as' and 'mount point'. If I don't select 'use as' then when I set the mount point to "/" then nothing really happens, and I can't move on. So. which of the 10 'use as' options should I select? ext3. ext2. reiserfs, jfs, xfs, fat16, fat32, swap [i'm guessing not that one], efi or dontuse [i'm presuming not that one either. But I can only guess...]

Thanks for your help :D
All those options are the file systems available to you; I recommend you use ext3. It is to NTFS as Linux is to Windows, or to HFS+ as Linux is to OS X. It's also possible to set up OS X and Windows XP with read/write capability on ext3, and it is also the most flexible.

You could of course use FAT32, but ext3 won't leave you with the limitations of that. I have my Windows partition formatted to FAT32 so I can read and write from anywhere (Linux and OS X have innate read capabilities for NTFS, but neither has write). This allows me to keep my music on the Windows part and listen in any operating system. =)

Good luck to you!

---

### Post by cybergoldfish on 2007-04-22
Thanks, that's great. I think something went wrong though. I finished installing, and it said it had to restart, but then sort of... broke. A black screen came on and some error-type messages were displayed, and wouldn't go away on their own so after a while I held down the off button on my macbook until it turned off. Then, just incase, I tried holding down option when turning it on, but it only displayed osx. So I tried it with the ubuntu disc again, and tried reinstalling it, but now it gets to the partitioning part and says that my 15gb partition has /media/Untitled 2, and 2300mb is being used on it. And I have no idea what to do.

And now I'm feeling like I may have broken it. Damn.

---

### Post by oskarloko on 2007-04-23
( I'm assuming you use rEFIt )

You won't be sent to hell for this. ;-)

It's just happen to me: GRUB - the linux loader - doesn't load onto Linux partition. 
Restoring grub you'll fix it

Ok, let's go

Insert LiveCd and boot on it.
When desktop is loaded, open a terminal and:
```

su
mkdir /target 
mount /dev/sda3 /target   [FONT="Arial"]*(*)*[/FONT]
cd /target/usr/local/sbin     [FONT="Arial"]*(**)*[/FONT]
./grub

```
You'll be onto grun shell
then type
```

root (hd0,2)  [FONT="Arial"]*(***)*[/FONT]
setup(hd0,2)

```
reboot and now try !!

pd. do not write the [FONT="Arial"]*(*)*[/FONT]
(*) You must know what is your linux partiton, mine is /dev/sda3
(**) Maybe /usr/sbin, /usr/local/sbin.... just look it with ls
(***) renember that hd0,2 references to sda3 (  a second hd on first partition will be (hd1,0)

Tell us !!

---

### Post by cybergoldfish on 2007-04-24
thanks! i seem to have a new problem - there's no ./grub in the /sbin folder

actually, all of the folders in the /target/usr/local are empty.

---

### Post by oskarloko on 2007-04-27
Excuse me 

grub will be under 
```
**/target/usr/sbin/**
```

...I don't know if ```
/target/usr/local
```may be empty just after installation Maybe it's right.

Try and tell us.

---

