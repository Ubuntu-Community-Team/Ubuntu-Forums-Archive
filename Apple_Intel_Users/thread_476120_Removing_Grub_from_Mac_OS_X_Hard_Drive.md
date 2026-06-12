---
title: "Removing Grub from Mac OS X Hard Drive"
date: 2007-06-16
forum: Apple Intel Users
---

### Post by kitki83 on 2007-06-16
I cannot figure out why i had this problem for weeks now unable to fix it. I installed Ubuntu in windows XP hard drive(Hard drive #2) but I kept Mac OS X(hard drive #1) untouched. Removing Ubuntu and doing fdisk repair on MBR on windows. I still get two windows Boot Icons. One is windows while the other gives me "GRUB GRUB GRUB GRUB GRUB" spam. I was told as a solution to clean install Mac OS but I think there is similar procedure to reset MBR for apple. I installed Parallels to use Ubuntu in more safe environment but I get an error I do not have a Boot Camp MBR. I really need someone who can help me figure out what is wrong with mac os x boot record. Also I tested it out and grub was on apple by removing windows xp hard drive and seeing windows (Grub Spamming boot icon).

This is Boot Record information in Apple if it helps.
(From Partition Inspector)


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    976773127  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    976773127  0b  FAT32 (CHS)

MBR contents:
 Boot Code: None

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 2, type Basic Data
 Listed in MBR as partition 2, type 0b  FAT32 (CHS)



From Terminal
/dev/disk0
   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *465.8 GB disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:   Microsoft Basic Data HORUS              465.5 GB  disk0s2
/dev/disk1
   #:                   type name               size      identifier
   0: FDisk_partition_scheme                    *279.5 GB disk1
   1:           Windows_NTFS Windows XP         279.5 GB  disk1s1
/dev/disk2
   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *232.9 GB disk2
   1:                    EFI                    200.0 MB  disk2s1
   2:              Apple_HFS Macintosh HD       232.6 GB  disk2s2
rene-martins-computer:~ Horus$

---

### Post by kitki83 on 2007-06-18
Can any one help me with this only solution was to format the Mac Hard drive but if someone can give me a guide on how to remove GRUB where ever its located I would appreciate it.

---

### Post by ronocdh on 2007-06-19
What exactly was the procedure you used to try to restore the MBR? I see you mentioned "fdisk" but as I recall, the command was **fixmbr** when booted to the Windows XP installation disc, although I could be mistaken here. Is this the procedure you're describing?

I have no experience using Parallels, but if it's saying you do not have a Boot Camp MBR, perhaps you should reinstall  Boot Camp (which would likely necessitate reinstalling Windows, too). Can you transcribe the error message for us?

If these options fail you, I say try reformatting the entire drive as an HFS+ OS X volume and starting fresh from there.

---

### Post by kitki83 on 2007-06-19
Yes sorry Fixmbr was the process,  I just assume fdisk is same as fixmbr. This procedure was to fix my Windows Boot, which worked it. Yes the Boot Camp I tried, well thought, it can fix the boot drive for me but failed and got the error of unrecognized or unable to initialize partition. Was seeing creating a partition on Mac OS X HD might reset it or make it non Grub.

I am using parallels as a safe mean to use Ubuntu and not ruining my Boot Information. I cannot use this software since its claiming I have a third party or non boot camp partition setup.

I want to format Mac OS X but I am trying to find a way to back up my information, I tried making a iso in Disk Utility but got "File to Large". I have a third hard drive I can make duplicate without destroying whats already backed up in the hard drive. Last option is the fire wire migration but I do not have an external firewire just USB 2.0.

Thank you so much for responding.

---

### Post by ronocdh on 2007-06-19
> **kitki83 said:**
> I am using parallels as a safe mean to use Ubuntu and not ruining my Boot Information. I cannot use this software since its claiming I have a third party or non boot camp partition setup.
Have you tried VMWare Fusion beta? I understand that if you've already shelled out cash for Parallels, you won't want to ditch that software, but from what I've read (my actual experience with virtualization is extremely limited), VMWare Fusion beta handles Ubuntu much better. It's worth a shot if nothing else.
> I want to format Mac OS X but I am trying to find a way to back up my information, I tried making a iso in Disk Utility but got "File to Large". I have a third hard drive I can make duplicate without destroying whats already backed up in the hard drive. Last option is the fire wire migration but I do not have an external firewire just USB 2.0.
First, I am unfamiliar with the term "Firewire migration." Can you elaborate a little on that, perhaps post some links? My Googling wasn't very fruitful. Next, I do think a reformat would treat you very well... I keep an external drive on hand just for the purpose of imaging and drive I need to wipe! It's very handy like that. ;)

---

### Post by kitki83 on 2007-06-19
> First, I am unfamiliar with the term "Firewire migration." Can you elaborate a little on that, perhaps post some links? My Googling wasn't very fruitful. Next, I do think a reformat would treat you very well... I keep an external drive on hand just for the purpose of imaging and drive I need to wipe! It's very handy like that. 


Basically when installing Mac OS X all over again it gives you the option to transfer all your data from an old computer or HD into the new setup. I just do not know it would work with USB. 
I just want to make a simple clone of my Mac os X then clean the HD make it nice and clean then load the clone onto the HD. Do you know anyway of doing this with USB HD?

---

### Post by ronocdh on 2007-06-19
> **kitki83 said:**
> Basically when installing Mac OS X all over again it gives you the option to transfer all your data from an old computer or HD into the new setup. I just do not know it would work with USB. 
I just want to make a simple clone of my Mac os X then clean the HD make it nice and clean then load the clone onto the HD. Do you know anyway of doing this with USB HD?
Sure, that's a simple image making process. I think Disk Utility can do this, no? You should be able to declare the external drive as the directory to which the ISO be saved, and then proceed. If that doesn't work, I've heard good things about [Carbon Copy]("http://www.versiontracker.com/dyn/moreinfo/macosx/13260"), although that is not free software. I'm sure some people here can mention some OSS applications for this purpose!

---

### Post by kitki83 on 2007-06-19
I tried doing that from Booting off the Disk and in the operating system both times I got an error of some sort.
I just need a way to back up my computer (at very least my mail setup) and be able to reload the system onto a cleaned hard drive.

Anyone?

---

### Post by kitki83 on 2007-06-19
OK I found a guide
[http://tomster.org/geek/mac/clone-howto](http://tomster.org/geek/mac/clone-howto)


seems to explain all my questions on backing up everything and using Disk Util to restore it, thanks for the help and I hope this post helps another person. 

Also Google it makes a big difference between clone and cloning just fyi.

---

