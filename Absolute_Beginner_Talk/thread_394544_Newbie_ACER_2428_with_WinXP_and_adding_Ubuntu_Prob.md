---
title: "Newbie: ACER 2428 with WinXP and adding Ubuntu Problems"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by gerrymoth on 2007-03-27
Okay after much reading on here I decided to try adding Ubuntu to my ACER laptop as a dual boot system, but I've got stuck at the first hurdle in trying to partition as Ext3.
The laptop at the moment has the following
/media/hda1 6MB FAT32
/media/hda2 29GB FAT32
/media/hda3 29GB FAT32

hda2 is my C: drive and hda3 is my D: drive.

First question (remember I'm a newbie) is should I not have a NFTS partition which WinXp is installed on? WinXP is on C: drive and D: is just storage.

When I boot from the Ubuntu CD it will not allow me to partition the drives using Gparted.

---

### Post by seshomaru samma on 2007-03-27
windows can live on a FAT32 file system though I would expect ACER to install it on an NTFS
what is the output of :
```
sudo fdisk -l
```
(put that in a terminal when you boot from the live Cd , you can find the terminal in the top menu , I'm not on Ubuntu right now so I don't remember)

---

### Post by gerrymoth on 2007-03-27
> **seshomaru samma said:**
> windows can live on a FAT32 file system though I would expect ACER to install it on an NTFS
what is the output of :
```
sudo fdisk -l
```
(put that in a terminal when you boot from the live Cd , you can find the terminal in the top menu , I'm not on Ubuntu right now so I don't remember)

Was tring to post from memory, so booted up and did the fdisk and got the following:-

Disk /dev/hda: 60.0GB 60011642880 bytes
255 heads 63 sectors/track 7296 cylinders
Units = cylinders of 16005 * 512 = 8255280 bytes

Device Boots	Start	End	Blocks		Id	System
/dev/hda1	1	510	4096543		12	Compaq diagnostics
/dev/hda2	511	3871	26997232	c	W95 FAT32 (LBA)
/dev/hda3	3872	7295	27503280	c	W95 FAT32 (LBA)

---

### Post by slayerboy on 2007-03-27
also, are you sure that acer didn't put a "recovery partition" on the disk? These are made so that you can easily recover back to Windows in the event of mass destruction to your registry.

If you have CD's that say "Windows Recovery" or something like that then you shouldn't have any problems unless your disks are NTFS, in which case you might have an issue.

I would grab Ultimate Boot CD ([http://www.ultimatebootcd.com)](http://www.ultimatebootcd.com)), just the regular version and you can use one of the partitions from there if gparted gives you issues and you are not using a recovery partition.  Just make sure you have those cds.  If you don't, I think there should be a program that each manufacturer installs that lets you make these cds in case of hard drive failure.

---

### Post by gerrymoth on 2007-03-27
> **slayerboy said:**
> also, are you sure that acer didn't put a "recovery partition" on the disk? These are made so that you can easily recover back to Windows in the event of mass destruction to your registry.

If you have CD's that say "Windows Recovery" or something like that then you shouldn't have any problems unless your disks are NTFS, in which case you might have an issue.

I would grab Ultimate Boot CD ([http://www.ultimatebootcd.com)](http://www.ultimatebootcd.com)), just the regular version and you can use one of the partitions from there if gparted gives you issues and you are not using a recovery partition.  Just make sure you have those cds.  If you don't, I think there should be a program that each manufacturer installs that lets you make these cds in case of hard drive failure.

Only disk which came with the laptop was a Windows XP Home Edition installation CD, still in the wrapper, never had the misfortune of having to use it.

---

### Post by seshomaru samma on 2007-03-27
It seems like your Windows was installed on a FAT partition(hda2)
I believe you have to defrag it several times before you can resize it

hda1 is some sort of a rescue partition , I'm not sure if you need it or not

did you try running gparted from the liveCd ?
what errors did you get?

---

### Post by gerrymoth on 2007-03-29
I resized /dev/hda3 to 15GB using gparted and then rebooted to the LiveCD and let Ubuntu install in the free space. Now have a dual boot system, when I power up it has a list of operating systems for me to select (WinXP, Ubuntu, Ubuntu-Graphicsafe mode).

Now all I need to do is sort out how I can view the /dev/hda3 from Ubuntu as this is where I have stored all my music and videos. Think I haven't set the mounts correctly, so will be reading up on this.

Also haven't connected to the internet yet, will try tomorrow at home, away working at the moment and only have wifi connection, will connect via cable to my sky broadband (netgear router) and download ndiswrapper to sort out the wifi connection.

---

