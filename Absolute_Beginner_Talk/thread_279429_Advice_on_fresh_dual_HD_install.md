---
title: "Advice on fresh dual HD install"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Henrythewound on 2006-10-18
I previously ran a dual boot machine (XP on a 160 Gb and Ubuntu on a 40) with GRUB loaded onto the 40. I set my BIOS to load the 40 gig hd 1st so grub would pop up and I could choose between linux and windows. Well my 40 gig hd died and I cant seem to boot into windows now either. I have decided to buy a larger hd and set up my system again. My main questions are listed below. If you think of anything else or have some suggestions please feel free to add your comment.

1) I would like to be able to access my windows drive with ubuntu, should I format them both with FAT32 or is this no longer an issue?

2) Is it easier to install each OS on a different HD as I did before or simply create a partition for linux? I want to keep my hard drives somewhat organized.

3) Lastly, is there a way to "ghost" my system, both XP and ubuntu so I could restore it if I have another bad crash or mishap? I have an external hd for backing up documents etc.

Thanks in advance, I appreciate any advice. My new HD will be here soon so I can get started.

~Joe

---

### Post by gustolove on 2006-10-18
1. Reading NTFS files from Linux/Ubuntu is not a problem. Writing NTFS files in Linux/Ubuntu is :-P

2. Partitions are fine. Different Hard drives are fine. its really up to you on how byou want to organize it. (Also the reason you were not able to get into windows was because of the fact that the Boot Loader "GRUB" was on the Ubuntu hard drive, and that was what was letting u select to get into windows.) 

3. A RAID 1 Setup will make 2 hard drives have exactly the same data on them.

---

### Post by aysiu on 2006-10-18
These two links should be helpful to you:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by anaconda on 2006-10-18
0. You should be able to boot to windows by removing the broken ubuntu hd, or by selecting from your BIOS that the windows drive boots first. Because you didn't put grub to the mbr of your windows disk it should boot to windows just fine...

---

### Post by ReaderRat on 2006-10-18
> 2) Is it easier to install each OS on a different HD as I did before or simply create a partition for linux? I want to keep my hard drives somewhat organized.
[**Dual-Booting (One HDD)**](http://users.bigpond.net.au/hermanzone/)
[**Dual-Booting (Two HDD)**](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by Dr. Nick on 2006-10-18
You may still be able to get into windows, remove the broken 40gig from the computer and plug the 160 into the master chanel of the ide and switch the jumpers on the 160 to match the 40, or you can just remove the jumper totally.

Then boot back up and make sure your BIOS is configured right. If it doesnt work then you can try to restore the mbr from a windows xp cd by using the recovery console and typing "fixmbr" and "fixboot"

Linux can natively read ntfs and can write to it with some workarounds, If you want the easiest read and write support it sort of depends

You can use fat32 and read/write natively or use ext3 and write natively in linux and use [this program]("http://e2fsprogs.sourceforge.net/ext2.html") in windows.

---

### Post by Henrythewound on 2006-10-18
Wow, great advice and links, many thanks. Dr. Nick, its funny, I tried exactly what you said prior to posting here. I attempted to use the fixmbr and fixboot from the XP cd with no better results. For some reason, windows must have been trying to look for SOMETHING where the old 40 gig hd had been plugged in, I'm not sure. 

The bright side is I have all my docs backed up and a fresh instll of both OSs will be fine, especially since I am purchasing a larger hd and may want to move most things to it. 

As for the FAT32 vs NTFS issue. I am thinking of just using FAT32 so I can switch to ubuntu, read and write easily. I have heard FAT32 has some security drawbacks though, I'm not sure if there are any other reasons not to use it. I want to make the choice now before I wipe the HDs and start over from scratch. I'll look up some info on this issue myself.

Once again, THANK YOU all

Joe aka Henry

---

### Post by Bigbluecat on 2006-10-18
I also had the problem that FIXMBR did not work when I tried it first time. I believe in my case it was beacuse I did something silly with grub and not only overwrote the MBR but also corrupted the boot sector.

To fix this I used the WinXP recovery console and entered three commands:

FIXBOOT               (this fixes the boot sector)
FIXMBR                (this replaces the MBR with WinXP MBR - Grub is eliminated)
BOOTCFG /rebuild


Perhaps if you use the last BOOTCFG /rebuild command in XP recovery as well you may get your windows back booting.

---

### Post by gn2 on 2006-10-18
There are limitations with Fat32 that can be avoided by using this driver with Windows: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Dr. Nick on 2006-10-18
gn2 that looks like a better version of the lik that I posted, Ill have to remember that for future refrence

IMHO i think some of the "security" risk come from the fact that fat32 doesnt do to well with the permissions. If  I am correct about it then any user could see anything on a fat32 partiton and owenerships of linux files would be non-existent

---

### Post by Henrythewound on 2006-10-19
Great tips. I re-installed XP on my new 400 Gig last night and I can access all my files on the old 160 Gig. My plan is to copy everything from the smaller drive onto the new larger drive and then wipe the 160 when I install ubuntu on it. I also used partition magic to create a 100 gig "common ground" FAT32 partition on my large HD where I can place files I want to access with both systems. I will look into those utilities mentioned above, thanks for the suggestions.

I'll be installing ubuntu tonight, the last install I did from CD was Breezy, hopefully this will go as easily.

Thanks for the tips all,
Joe aka Henry

---

### Post by Henrythewound on 2006-10-19
Wow, actually upon reading the windows plugin for windows suggested I think I'll try that 1st.

~Joe aka Henry

---

### Post by gn2 on 2006-10-19
Reader Rat has already suggested it, but here it is again, dual-boot on two drives: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

