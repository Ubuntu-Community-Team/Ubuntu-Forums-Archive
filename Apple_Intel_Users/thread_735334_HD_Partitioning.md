---
title: "HD Partitioning"
date: 2008-03-25
forum: Apple Intel Users
---

### Post by jakejackjacob on 2008-03-25
I am buying a new HD for my MBP (long story) and plan on partitioning it (250gb) into several partitions to accomodate multiple OSs. My question is this: Would I be better off partitioning my drive in to 2 or 3 drives (then usung an external drive for ubuntu), or trying to partition it out into 4 to accomodate for a full triple-boot? I am not dealing with many large files, so total space isn't an issue.

I was thinking about breaking it up as follows:

1. EFI
2. Mac OS (50gb Mac OS J)
3. Common (150 gb FAT 32)
4. Win XP (50 gb NTFS)

(external) ubuntu

I think this will probably be my best bet, I don't use ubuntu as my primary OS-- honestly, for my purposes, it is more for fun.

<>< Jack

---

### Post by cyberdork33 on 2008-03-25
You will have issues with any legacy OS on an external drive. See the FAQ

I would propose:
[LIST=1]
[*]EFI
[*]FAT32 shared
[*]Ubuntu Root
[*]Windows
[*]OSX[/LIST]OSX doesn't care where it is located on the disk... and in this situation, you should be able to stretch the FAT32 partition to take up the Ubuntu space if you remove ubuntu.

---

### Post by jakejackjacob on 2008-03-25
So-- I'm pretty new to linux in general-- do I have to deal with a swap partition, or will I create a swap file on my linux (or FAT32) drive?

Maybe more concisely: I should partition my drive two ways FAT32 shared (including ubuntu space), NTFS , Mac OS. 

Install Mac OS (with rEFIt)
Install Windows on NTFS Drive
Use ubuntu installer to partition FAT32 drive to include a linux partition
Install ubuntu


<>< Jack

---

### Post by cyberdork33 on 2008-03-26
It is still generally recommended to have a swap partition, but you can also make a swap file on your main partition instead. If you have a good amount of RAM, you can even get away with no swap whatsoever. If you want to create a swap partition, you can also put it past #4 since Ubuntu can read the GPT and use partitions beyond #4 unlike windows.

If you have a complete plan, and have to install OSX, I would just create all the partitions off the bat with gparted or something. Even if the partition type is wrong, at least setup the boundries, then you can reformat the partitions to the desired type during the install.

You can also work around the 4 partition problem that is due to GPT by repartitioning the drive to a legacy msdos MBR style. OSX will not install to such a disk, but there are some tricks you can use to get it on there anyway. (install normally, clone to an external drive, repartition, clone OSX back to desired partition). Then you can place partitions wherever you like abiding by the legacy rules of the MBR using extended / logical partitions and such. You will lose the EFI partition this way though, and I think it is required for firmware (EFI) updates.

In the end, you want to avoid changing the partitioning after windows has been installed because you will likely have issues (hal.dll error). Checkout my multi-boot guide linked in my signature which will detail correct placement of Grub as well.

---

### Post by jakejackjacob on 2008-03-26
So perhaps

Install OSX on whole disk
Use disk utility to create the following drives:

OSX
Shared (FAT32)
Windows (NTFS)
Linux (whatever-TBD)
Linux swap (whatever-tbd)

Install Windows
Install LInux.

Also, your guide refers to placing GRUB in the root (/).
That is- the root for UBUNTU (partition #4), not the EFI partition, right?

Thanks for your patience...
<>< Jack

---

### Post by cyberdork33 on 2008-03-26
yes the Ubuntu root partition that is right.

---

### Post by madscientist032 on 2008-03-27
I'm currently trying to triple-boot OS X, Ubuntu 7.10, and the Hardy Heron 8.04 beta. I used Apple's bootcamp to partition the harddrive, and just recently I used the 8.04 beta cd to create another partition. Unfortunately the new partition is classified as "Free Space" (it's not formatted, i.e HFS+ or NTFS or Linux Swap) and I don't know where to go from here. 

Almost forgot - I have no extra backup hard drive. So I cannot just 'reinstall OS X' onto a single partition and go from there.

---

### Post by cyberdork33 on 2008-03-27
> **madscientist032 said:**
> I'm currently trying to triple-boot OS X, Ubuntu 7.10, and the Hardy Heron 8.04 beta. I used Apple's bootcamp to partition the harddrive, and just recently I used the 8.04 beta cd to create another partition. Unfortunately the new partition is classified as "Free Space" (it's not formatted, i.e HFS+ or NTFS or Linux Swap) and I don't know where to go from here. 

Almost forgot - I have no extra backup hard drive. So I cannot just 'reinstall OS X' onto a single partition and go from there.Install to the free space... I don't understand your problem. When you run the installer, you can run the manual partitioner to format it to whatever you like. You will want to install grub to the root partition of your new system though or else the two loaders will conflict and you might end up not being able to boot into the older Ubuntu system (not that it wouldn't be fixable).

---

### Post by madscientist032 on 2008-03-27
I remember from installing Gusty that the mount point was something along the lines of ext3. When I say free space I mean that as of right know, my 160 GB hard drive has 12 GB of free, unused and unformatted space. It's not HFS+ or NTFS or any of the FAT variations. It's just...there.
As for the potential boot problem, I have rEFIt installed, so I can choose between which OS I want to boot to. Won't matter until I install Hardy Heron over the weekend.

EDIT: I just installed Hardy heron but the problem is that I cannot boot into it, even though I can see two linux choices with rEFIt. Both selections boot up Gusty. Is there a workaround for this?

---

### Post by cyberdork33 on 2008-03-27
> **madscientist032 said:**
> I remember from installing Gusty that the mount point was something along the lines of ext3. When I say free space I mean that as of right know, my 160 GB hard drive has 12 GB of free, unused and unformatted space. It's not HFS+ or NTFS or any of the FAT variations. It's just...there.
ext3 is a filesystem format not a mount point. The mount point for your root partition is "/".

I understood what you meant by free space. You can choose to install to the free space. The installer will create the default filesystem in the space available.

> **madscientist032 said:**
> As for the potential boot problem, I have rEFIt installed, so I can choose between which OS I want to boot to. Won't matter until I install Hardy Heron over the weekend.

EDIT: I just installed Hardy heron but the problem is that I cannot boot into it, even though I can see two linux choices with rEFIt. Both selections boot up Gusty. Is there a workaround for this?You misunderstand the situation. rEFIt is just a menu that can see partitions with an OS on them. Grub is the actual Linux bootloader. Since the default is for Ubuntu to install Grub to the MBR, only one copy of Grub can exist there at a time... It will either point to your Gutsy install, or your Hardy install.... Apparently it is pointing to your Gutsy install. You need to install Grub separately to the partition that contains the operation system you want... for example, if you are installing Ubuntu to sda3, then you need to specify that Grub is installed to sda3, and the same goes for your other Linux install...

In reality, the way you have it is fine, but it is not setup to work that way properly. You can edit the menu.lst file on your gutsy install to contain the kernel entries for your Hardy install, and you can use it to boot both.

---

### Post by madscientist032 on 2008-03-27
How do I edit the menu.lst file? (I'm assuming it involved a terminal session)

---

### Post by cyberdork33 on 2008-03-28
you can edit it with whatever editor you like:
```
sudo gedit /boot/grub/menu.lst
```

---

