---
title: "Install Windows 7 from Ubuntu without CD or USB"
date: 2011-07-31
forum: Any Other OS
---

### Post by LionelTabre on 2011-07-31
Hello Ubuntu Forums, I was wondering how I could re-install Windows 7 from Ubuntu(or GRUB2).
Here is my current situation:
I was using GParted (I knew the risk), and I was removing a partition. And I accidentally removed my Windows Partition(It was mostly filled with junk.). Now I want to reinstall it from a ISO Backup on my Ubuntu Partition. The problem is that I have a 2GB usb (So I can't install from USB), And no blank DVD's. How would I go about installing from the iso? I'm using Natty.
By the way, is this the correct category to post this in?
Anyway, thanks for any help!

---

### Post by blane2 on 2011-08-01
unknown, probably can't be done.

Go buy DVD's

---

### Post by drawkcab on 2011-08-01
Whoops.  Time to go Ubuntu only?

---

### Post by varunendra on 2011-08-01
> **blane2 said:**
> unknown, probably can't be done.

Go buy DVD's
+1
Cheap and best option. :)

---

### Post by mips on 2011-08-01
You could always try creating a small FAT32 partition and extracting the ISO to it and boot with some dos bootable usb media to gain access to the partition and then just run setup/install.

---

### Post by CharlesA on 2011-08-01
> **mips said:**
> You could always try creating a small FAT32 partition and extracting the ISO to it and boot with some dos bootable usb media to gain access to the partition and then just run setup/install.
Might work, but I doubt it - worth a shot tho.

---

### Post by varunendra on 2011-08-01
Well, one blank DVD could make life much easier. :D

Else this lengthy but much more easy to follow method can be adapted:


[LIST=1]
[*]Install VirtualBox
[*]Create a Win7 VM on the HDD with its virtual HDD being at least 60GB
[*]Boot the VM from the iso and make two equal sized partitions in it
[*]Install Win7 in the first partition
[*]after the installation is finished, reboot the VM - this time from clonezilla live iso
[*]create the image of the installed partition placing it on the second partition
[*]copy the image over to the actual hard drive
[*]reboot your physical machine from clonezilla live USB (the 2GB USB)
[*]restore the image on the first physical partition
[*]reboot from hard disk. This time it should boot into Win7. Let it install drivers for the actual hardware.
[/LIST]
I haven't tried it myself, but given the fact that Vista/Win7 are capable of adapting themselves to changed hardware, I'm sure this should work.

I just thought that getting a blank DVD would be much more easier.. ;)

---

### Post by mips on 2011-08-01
> **CharlesA said:**
> Might work, but I doubt it - worth a shot tho.

Never tried it with Win7 but I did use this method with WinXP many times.

---

### Post by LionelTabre on 2011-08-01
I'll try varunendra's method. The reason why I can't use DVD's is because I would have to get one from my brother, and he would ask why, I would have to tell him the truth ,and then he would get My mom to take away my laptop(Which I don't want). Anyway, thanks for helping me!

---

### Post by varunendra on 2011-08-01
> **LionelTabre said:**
> I'll try varunendra's method. The reason why I can't use DVD's is because I would have to get one from my brother, and he would ask why, I would have to tell him the truth ,and then he would get My mom to take away my laptop(Which I don't want). Anyway, thanks for helping me!
Ouch..!! :D

---

### Post by christopher.wortman on 2011-08-02
This is a simple thing, mount the ISO file, and launch setup.exe from wine. Make sure you have a blank partition to format to NTFS, and choose it from the setup and away you gooooooo. I have done it with XP I suppose it shouldnt be that different from 7.

---

### Post by varunendra on 2011-08-02
> **christopher.wortman said:**
> This is a simple thing, mount the ISO file, and launch setup.exe from wine. Make sure you have a blank partition to format to NTFS, and choose it from the setup and away you gooooooo. I have done it with XP I suppose it shouldnt be that different from 7.
Sounds really interesting - even with XP.
Looks like you've just given me the recipe to waste my day today experimenting with this stuff ;).
The only thing I doubt (besides w7 installer's compatibility with wine) is partition/entire drive's mount status (exclusive access required??). I'll post back results with XP and Win7 both.

---

### Post by varunendra on 2011-08-02
> **christopher.wortman said:**
> This is a simple thing, mount the ISO file, and launch setup.exe from wine. Make sure you have a blank partition to format to NTFS, and choose it from the setup and away you gooooooo. I have done it with XP I suppose it shouldnt be that different from 7.
Hmm.. okay, I got some time to try that out, and as expected, setup (both xp and win7) couldn't find a valid hard-drive partition to even start the setup process.

It was a two-partition virtual hard drive, with iso and extracted files being on partition2, partition-1, after 1st failure, mapped as E: drive in wine, tried both with mounted and unmounted status, VM was booted from a live CD (yes, I installed wine just for the experiment, on a volatile environment!!). Oh, did I mention- the setup files could not be executed while being on the iso (no executable bit, no permission change allowed on a read-only media :)), so i had to extract them to a folder. On execution from the extracted files, the setup screen came up well and good! But on clicking the "Install" button - "no valid partition" (or something similar) message greeted me.... ;)


So I'd really appreciate if you could tell us how exactly you managed to do that 'simple thing' with XP.. :-k


Although the method suggested by mips surely works with XP, not sure about Win7 (another 'experiment day'?), I've done it myself in the past. In fact, I wrote kinda tutorial for it once: [http://ubuntuforums.org/showpost.php?p=9190079&postcount=11](http://ubuntuforums.org/showpost.php?p=9190079&postcount=11)

---

### Post by zero244 on 2011-08-03
Watch it, you might toast your Ubuntu install.

I agree with drawkcab this might be a good time to go Ubuntu Only!

---

