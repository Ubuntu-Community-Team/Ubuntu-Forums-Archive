---
title: "Sharing swap space with XP"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-11-30
Hi,

Since linux has a swap partition, I'd like to use it to put the XP pagefile too. XP cannot read the Linux swap but what about the following:

Create 2 scripts:
1) When Ubuntu is booting, one linux script format the swap partition with filesystem "linux swap" to make it available to Ubuntu once started.

2) When the computer boots on XP, a windows script format the swap partition as NTFS. This partition will be recognized by XP and it can store the pagefile on this partition.

It sounds great especially since these scripts would run during startup and not shutdown so if either XP or Ubuntu crash at some point, it will still be OK on next reboot. 

Now as I have absolutely no skills in script writing, I ask you if this is possible? Is it possible to make scripts that run during boot and format a partition with a specific format BEFORE Linux or XP need to access the swap space??

---

### Post by deadgobby on 2006-11-30
I think this is what you are looking for.
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

### Post by Bachstelze on 2006-11-30
Do you have *such* a small drive ?

---

### Post by kilou on 2006-11-30
> **HymnToLife said:**
> Do you have *such* a small drive ?

No it is to solve the /tmp and FAT32 issue that we are discussing on the other thread. I have enough space but this would just be perfect and would make sense. I could also create another separate NTFS partition only for the XP pagefile but sharing swap space appears as a more elegant solution...if it's possible to write these scripts. Any ideas? What kind of scripts can be run during boot?

I know that for XP we can run vbs or *.bat scripts during startup but I don't know if these would run before XP needs to access pagefile. Probably the best would be ascript that run right after GRUB and before either OS is launched. Any such possibility?

---

### Post by kilou on 2006-11-30
Is it possible to add a command to menu.lst (GRUB) that would format swap space in NTFS if XP is selected and format swap space as linux-swap if Ubuntu is selected? That would be awesome!

---

### Post by b1g4L on 2006-11-30
I'm not sure if this is feasible, but consider the time it will take to format your swap space during boot. It would increase boot time considerably, because you would have to wait for the format to complete before the system would be ready.

I would consider having separate swap space for XP and Ubuntu. If you have a "Gig" of RAM, then swap space consumed by Windows and Linux would be minimal (say 2 GB).

---

### Post by shin on 2006-11-30
Firstly, it is preferable to use fat32 on XP swap partition, instead of NTFS. It just works better for this cause.

About those scripts - I think it is doable. But it lacks sense. As b1g4L said, it would increase boot time and just for saving like 1-2gbs? Anyway, experiment if you like. I doubt that anyone is going to give you complete solution for this, as probably noone does it this way.

Now while formatting swap partition on linux boot would be relatively easy - I think that modifying /etc/init.d/mountall.sh do_start part would do it. You should just add there mkswap /dev/<whatever is hour swap partition from fstab>

Formatting ntfs/vfat partition for windows is not that easy as there is probably no way to add this to grub, so you should add this script for windows, autoexec or something like that. Dunno how to do it. If this partition is normally visible (even with swap FS) then probably just format <drive letter>: /q /fs:fat32 (or for ntfs, skip this option) would do.

---

### Post by kilou on 2006-11-30
I could also make 2 linux scripts, one that create the linux-swap when Ubuntu is launched and another that format it back to NTFS or FAT32 when Ubuntu is shutting down. The only problem is if Ubuntu crashes I will have to resart it and shut it down again to recreate the FAT32 for XP...... 

You're right, I didn't think about the increased boot time it would induce :-? Also as shin mentioned it's true that the linux-swap would simply not be visible when booting in Windows so the autoexec.bat script would probably not work (unless I used specific drivers to read swap partition but this really starts to be way too complicated). So probably I'll simply do a separate partition for XP pagefile then...in FAT32.

Anyway thanks to everyone for having provided me some feedback on this topic! ;)

---

### Post by PacShady on 2006-12-03
The other alternative might be to make a FAT32 partition and put the Windows swapfile and a Linux swapfile (as opposed to a swap partition) on it, splitting the space between the two. It wouldn't allow them to use the SAME space, but it would allow them both to be on one partition to keep things neat and tidy, and it would save the need for scripts.

'Shady

---

### Post by kilou on 2006-12-03
That could be a solution too yes but I read somewhere that it's not recommended to use a swap file for Linux. A partition is much better apparently (I don't really know why).

---

