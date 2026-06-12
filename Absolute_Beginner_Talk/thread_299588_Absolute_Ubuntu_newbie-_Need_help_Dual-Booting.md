---
title: "Absolute Ubuntu newbie- Need help Dual-Booting"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by ShardOfNarsil on 2006-11-14
Ok, I want to install Ubuntu with my XP installation, and I understand that I will need to make a 10 gig and 500 mbyte partition, for the installation and swap (whatever that is). There are several problems, however.

1) My built in wireless card (Broadcom 802.11g WLAN) will not work when I boot Ubuntu from my LiveCD. Works fine in XP, though. Do I need special software?

2) Partitioning- Will it hurt my preexisting installation of XP? I don't really want to fudge that installation up. I have a 50 gig drive, and I want to cut off a 10 gig chunk for Ubuntu.

3) Walk me through the process again? I'm really scared by this but I want to do it. Guide me to the Super Ultimate Dual-Booting guide for complete retards. 

4) Media: I have 5 gigs of music that I would like to share between Xp and Ubuntu. Is that possible? What are the necessary steps?

---

### Post by scrooge_74 on 2006-11-14
> **ShardOfNarsil said:**
> Ok, I want to install Ubuntu with my XP installation, and I understand that I will need to make a 10 gig and 500 mbyte partition, for the installation and swap (whatever that is). There are several problems, however.

1) My built in wireless card (Broadcom 802.11g WLAN) will not work when I boot Ubuntu from my LiveCD. Works fine in XP, though. Do I need special software?

2) Partitioning- Will it hurt my preexisting installation of XP? I don't really want to fudge that installation up. I have a 50 gig drive, and I want to cut off a 10 gig chunk for Ubuntu.

3) Walk me through the process again? I'm really scared by this but I want to do it. Guide me to the Super Ultimate Dual-Booting guide for complete retards. 

4) Media: I have 5 gigs of music that I would like to share between Xp and Ubuntu. Is that possible? What are the necessary steps?


First of all, I will recommend you backup all your important data first, since you dont know much you may end up making a mistake that cost you your hard earn data, and then you will blame Linux for it.

Go slowly until you are more confident

1. Maybe your wireless card is not active at boot 
, Ubuntu is one of the best distro for detecting wireless cards.

2. Gparted at time of installing should take care of that just follow the instructions.

3. It is somewhere in the website [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows?action=show&redirect=SwitchingFromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows?action=show&redirect=SwitchingFromWindows)

4. You will be able to mount the NTFS partition from inside Ubuntu, you can do that right know from ADmin, Disks and asign it a folder in your system, so the drive with the files looks like a folder

---

### Post by ShardOfNarsil on 2006-11-14
Thatnks, but it didn't answer my biggest problem- does making a partition wipe my hard drive? If I choose "10 gigs" at the slider at the start, will my Windows XP installation be safe?

---

### Post by turbojugend_gr on 2006-11-14
I just write to inform you that what scrooge says is exactly my views also, so you can be more certain of his sayings.

In a hurry: 

1. You mioght need to search this forums for your broadcom, as I 've seen at least one how-to and some other threads, so you 'll get it working for sure, but it might need some work from your part.

2. Using the liveCD (or the alternate) you shouldn't have a problem, read the guide, and make sure you select custom partiotioning, so you can create some space for your ubuntu installattion, and also make sure that the remaining winxp partition is not to be formatted (there's a special sign showing this)

3. The official wiki guy scrooge mentions, is easy to use so go for it.

4. If you wish only to listen to that music it is very easy, while installing ubuntu just add a mount point to your winxp partition (I use /winxp). If you wish to be able to add music or modify it through ubuntu, you will have to create a new partition in fat32 format so that both windoz and ubuntu can read/write. Or if you wish to keep that files NTFS, you can follow a how-to (located in the how-to section on this forums) to read write NTFS filesystems.

I hope I was helpfull any questions, post back here.

Regards, TJ

---

### Post by turbojugend_gr on 2006-11-14
Yup the partition should be safe, I never seen any users posting about missing data following the gparted partitioning methods/tools, oh you should backup the most precious of your data, as you never know

---

### Post by ShardOfNarsil on 2006-11-14
I just can't do it. Every time I almost install it, I get scared and stop it. I'm too afraid it's going to cause irreversible damge to my laptop.

---

### Post by scrooge_74 on 2006-11-14
> **ShardOfNarsil said:**
> I just can't do it. Every time I almost install it, I get scared and stop it. I'm too afraid it's going to cause irreversible damge to my laptop.


I had that same felling 10 months ago....that is why it is better you backup your data...worst case scenario you only have to copy back from CDs all your important data

---

### Post by turbojugend_gr on 2006-11-14
Nobody can put you to make this m8, I suugest you to overcome your fears as the fun that follows will spoil you.

Anyway just get rid of your stupid windoz-created fears, and try it out, if you have the most important data in a couple of DVDs then no bad-no harm.

---

### Post by d3v1ant_0n3 on 2006-11-14
When I first installed Ubuntu with Windows present, I was afraid that it would kill my partitions. BUt the only thing it did to windows was let it gather dust:p

It *shouldn't* affect your windows partiton in any way apart from resizing it. But make sure any important data is backed up. Just to be on the safe side.

---

### Post by 3rdalbum on 2006-11-14
If you're still a bit scared, you could try installing Qemu (an emulator) on Windows. Create a large-ish disk image with qemu-img, install Windows into the emulator, then install Ubuntu into the emulator as a dual-boot.

Yeah, it'll be very very slow, but it will give you the ability to try the installer without affecting your existing data.

Otherwise, a utility like Norton Ghost will create a bit-for-bit copy of your existing data that you can split up onto DVDs. If anything goes wrong with your Ubuntu install, your Windows drive can be restored from the Ghost copy.

---

