---
title: "Ubuntu: Breath of Life for Sick Computer, but How?"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by ArmyPunk on 2006-02-20
Well I recently got a virus (I think) on my computer, (AMD64 3000+  Compaq Labtop) and well I simply cant get windows open. So I was talking to a friend and he suggested I could save my computer and files by using Linux. He was using Ubuntu so I figured id try it too. Now my friend got a Ubuntu Live Boot CD and we were going to use the partition editor and make 10GB of my 40GB HD a Linux partition. So I could then install Ubuntu and then transfer over the music files I wanted and then clear off the rest (in hopes of getting rid of the virus). But when we tried to use the partition editor, it would not work. It simply started to work, and then flashed a progress screen for a seocnd and then reverts back to the origional partition editor screen without changing anything. It wont even tell me why it wont work. Any ideas of what i can try? Or what I am doing wrong? Is there a different editor I need for an AMD64? 

Now I have been thinkin of Linux for a while but I never have a reason to switch, and well this seems like the perfect opertunity, but I might have waited too long. Can I save my computer and files from their early grave? Or am I simply stuck like a fish out of water?

Thanks in advance for any help!

---

### Post by carlosqueso on 2006-02-20
sometimes the partitioning tools don't like to resize things.......if you want to try to get your files, try using a live CD and copying your files to a USB stick....that may allow you to save your files.

---

### Post by jjf on 2006-02-20
I can't help you with the partitioning problem, but if you do get it working, be sure to copy your files then burn them to a CD.  When (if?) you reinstall Windows, it hoses your Master Boot Record so that your hard drive forgets where it put Ubuntu, so to speak.  In other words, once you reinstall Windows, you won't have access to your Ubuntu partition again.  Perhaps the pros know ways to fix your MBR, but I'd rather just get the data onto a CD-R.

---

### Post by jjf on 2006-02-20
carlosqueso's idea is good.  Use your Live CD, then follow the instructions here to mount your Windows partition:

[http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

Copy what you need onto a flash drive.

---

### Post by aysiu on 2006-02-20
Your best bet is to actually do the following:

1. Get ahold of a Knoppix CD--these are perfect for recovery, as they'll put your Windows partition as an icon on your desktop ready for the clicking. You can then copy your Windows files (the important ones) to some external media (blank CDs, iPod, whatever).

2. Reinstall Windows.

3. Possibly install Ubuntu as a dual boot.

4. Copy your files back.

---

### Post by ArmyPunk on 2006-02-21
Ok, so ill try to find both a Knoppix CD and  a bootable windows CD.

I think i heard rite, that if i install say Ubuntu and erase my virus-ridden windows partition, and then later want to re-install windows, i will lose my Ubuntu partition? (sounds like somehting Windows would do....)

Well I have 10-DVD-R's so i could probably back up my good music and stuff on to them, and then start on a clean slate, and install a Linux flavor, then if i want to install WIndows again later I will still have my music backed up on DVD. (Does this makes sence to you smart computer people? It seems to work in my little head :oP )

I guess im off to find me some CD's then.

Thanks All.

---

### Post by Zeroangel on 2006-02-21
Well, you could make three partitions.

1x Windows partition (at least 15GB NTFS, or FAT32 only if you can't get NTFS to work), 1x Linux Partition (at least 10GB EXT3), 1x Shared Partition (FAT32, largest since you might eventually want to store media on it and be able to access it from both Linux and Windows). If you have a very big hard drive (like 100GB) then adjust these numbers somewhat.

Once you have the partitions set up, then you can access the shared drive as a different drive in windows (ie: Drive D:) and you will be able to symbolic link it in Linux. Basically, you will be able to make linux believe that there is a **[COLOR="DarkGreen"]&#65378;Media&#65379;[/COLOR]** folder and files on your /home/username directory, even though the files are physically on the other partition. It is very easy to do in nautilus and you should pick it up very quickly.

---

### Post by ArmyPunk on 2006-02-21
Humm thanks ZeroAngel, I havent even heard of Nautilus, ill look it up and read about it.

---

### Post by Zeroangel on 2006-02-21
Oh, Nautilus is comparable to Windows Explorer (the window with all of the icons and folders that pops up ie: when you click on a folder on the desktop). Except in linux, its called Nautilus (or Konqueror, for those who use the KDE desktop style)

---

### Post by aysiu on 2006-02-21
[QUOTE=ArmyPunk]
I think i heard rite, that if i install say Ubuntu and erase my virus-ridden windows partition, and then later want to re-install windows, i will lose my Ubuntu partition? (sounds like somehting Windows would do....)[/QUOTE] What you should do, after you save your files, is reinstall Windows first; then instal Ubuntu.

---

