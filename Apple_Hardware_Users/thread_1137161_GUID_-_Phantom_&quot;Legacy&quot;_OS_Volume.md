---
title: "GUID - Phantom &quot;Legacy&quot; OS Volume"
date: 2009-04-25
forum: Apple Hardware Users
---

### Post by poddus on 2009-04-25
Hi all,

(system details below)
I attempted to install 9.04 recently on my system, but along the way I did some stupid things and messed up the boot sectors on my HDDs somehow. First I installed Ubuntu on the 250GB drive via the LiveCD, which worked great, but it didn't show up in the standard apple boot loader. The last time I installed Ubuntu was 8.04 a year or so ago, and I used BootCamp to start the installation, which somehow made that work (I ended up loosing the OS to a hibernation bug and didn't bother reinstalling). However BootCamp doesn't like my RAID for some reason, so that didn't work. I figured I'd use rEFIt, but attempting to install it on my RAID failed, so I used a thumb drive instead. that worked great, but I wanted to 1up, so I wiped the drive and made a 1GB HFS+ partition for rEFIt, a 32GB FAT partition for sharing files between OSes, and made the rest freespace for the Ubuntu partitioner to easily recognize where to install. Once again the install itself worked without a hitch, but for some reason my dedicated rEFIt partition wasn't bootable from the apple boot loader, so I popped in my flash drive and opened rEFIt, opened the partition fixer (or whatever it's called) and synced the GTP with the MBR. This is where thigns started to go downhill. After a quick restart I noticed a new "bootable" "windows" volume in the apple bootloader. I attempted to boot from it but it gave me a "missing operating system" error, forcing me to do a hard shutdown of the system. Loading rEFIt upon restart showed "boot Legacy OS from" (didn't say "hard drive" and wasn't bootable either) and the linux volume. Ubuntu was bootable, but I figured I should wipe the drive and go back to my old setup again. However after wiping the drive and installing Ubuntu on the entire volume it doesn't show up in rEFIt and the phantom legacy volume is still in both the apple boot loader and rEFIt. Wiping the drive yielded the same results, so it must be appearing somewhere on my RAID's GPT and/or MBR. I had this problem before when I tried installing Fedora (attempt was a complete mess btw) and couldn't get an answer from anybody, which left me no choice but to clean install. I don't want to have to go through that again, so does anybody have any ideas of how to get my machine back to how it was?

-poddus


Mac Pro 8-core
2 500GB OSX HDD, soft RAID 1
1 250GB Ubuntu HDD
*more info upon request*

---

### Post by cyberdork33 on 2009-04-25
please get the report from /Applications/Utilities/Partition Inspector (part of rEFIt).

Some notes:

rEFIt on your HFS+ partition needs to be blessed. You can do this manually, or use the enable.sh script in the refit directory

The Partition sync tool in the rEFIt menu can only sync the partition tables on the primary hard drive. You can install 'gptsync' in Ubuntu and use that to sync partition tables on other drives.

---

### Post by poddus on 2009-04-25
```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    976510983  Apple RAID
 3      976510984    976773127  Mac OS X Boot

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    976510983  ac  Apple RAID
 3      976510984    976773127  ab  Mac OS X Boot

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Apple RAID
 Listed in MBR as partition 2, type ac  Apple RAID, active

Partition at LBA 976510984:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot
 Listed in MBR as partition 3, type ab  Mac OS X Boot
```

I blessed the thumb drive and that worked just fine, but for some reason or another it didn't work on the RAID or the partition I made for it.

In the case of a soft RAID, which one is the primary drive? How can I tell?


-poddus

---

### Post by cyberdork33 on 2009-04-25
> **poddus said:**
> ```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    976510983  Apple RAID
 3      976510984    976773127  Mac OS X Boot

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    976510983  ac  Apple RAID
 3      976510984    976773127  ab  Mac OS X Boot

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Apple RAID
 Listed in MBR as partition 2, type ac  Apple RAID, active

Partition at LBA 976510984:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot
 Listed in MBR as partition 3, type ab  Mac OS X Boot
```I blessed the thumb drive and that worked just fine, but for some reason or another it didn't work on the RAID or the partition I made for it.

In the case of a soft RAID, which one is the primary drive? How can I tell?


-poddus
Well, I thought you were saying you got rid of the RAID... I am not really sure how to go about working with it there... They should really BOTH be the primary as they are seen as one device, but don't quote me there... I don't know if any of the tools are equipped to handle raid devices.

---

### Post by poddus on 2009-04-25
no I wiped the 250GB drive, the one with ubuntu on it. I tried my best not to touch my OSX volumes at all, but that didn't work so well :/

well, I've got some related questions that I've been trying to figure out to work on the problem myself.

1. When a device, folder, or file is blessed, what exactly happens to it and how is it handled by the system?

2. If I understand correctly, the MBR is only supported by apple for legacy reasons and isn't directly used by the system. could I purge the MBR without touching the GPT and retain my data?

3. What exactly does the system look for when I access the apple bootloader? Is there a place where a list of all known bootable devices is kept?


-poddus

---

### Post by cyberdork33 on 2009-04-27
> **poddus said:**
> 1. When a device, folder, or file is blessed, what exactly happens to it and how is it handled by the system?
Not real sure, but I think the machine stores something as a variable in firmware or something.

> **poddus said:**
> 2. If I understand correctly, the MBR is only supported by apple for legacy reasons and isn't directly used by the system. could I purge the MBR without touching the GPT and retain my data?sort of, and yes you can wipe out the MBR. I have a thread I started about this here:
[http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

> **poddus said:**
> 3. What exactly does the system look for when I access the apple bootloader? Is there a place where a list of all known bootable devices is kept?
Nothing accessible to you to look at that I know of.

---

