---
title: "Error : Unknown file system Grub Rescue&gt;"
date: 2011-11-11
forum: Any Other OS
---

### Post by nlkasyap09 on 2011-11-11
Hi friends,
 
I searched a lot but couldn't find a thread which addressed my problem exactly. 
The Problem : I had Win Vista and Ubuntu 11.04 in different partitions. I wanted to try linux mint so i deleted and formatted the partition that had ubuntu in NTFS and installed Mint(I don't know if deleting the partition was required. I'm just new). Then when i rebooted there was this error.
Error : Unknown file system 
Grub Rescue>
 
I thought my machine was useless untill i found SuperGrubDisk. Using SDG I can boot into windows and mint. But without SDG the error still comes up. I want to boot without the help of SDG. I found a way to fix windows MBR which involves using Vista Recovery Disk, but i dont have one.
 
So thats the end. I'd be grateful if someone helps me getting into windows/mint without having to use SDG. I'm ok with uninstalling or reinstalling grub as long as it helps the matter.
 
P.S. : I also used EasyBCD. It gives the error Opening BCD Registry.

---

### Post by coffeecat on 2011-11-12
It looks as though you've installed Mint to a different partition from where Ubuntu used to be, but that Ubuntu's grub in the mbr is still looking for the Ubuntu partition. Some of the grub code needed for booting is in /boot/grub in the root partition. If this is right, then re-installing grub to the mbr but pointing to the Mint root partition should be enough. This can be done with a Mint live CD. But before you try anything, let's see if this is so and get an overview of your system.

Boot up into Mint using SGD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. You can use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar for this.

---

