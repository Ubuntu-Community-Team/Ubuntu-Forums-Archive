---
title: "Setting up winXP/ubuntu dual boot"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by KentS on 2006-11-26
I want to set up a winXP/Ubuntu dual boot on a PC. I have read som guides on doing this, but being new to hard drive partitions and Linux I have gotten a bit confused. I would be very grateful if someone could take the time to answer my questions. I thing most of them are yes/no-questions.

The situation:
I have a new PC that I want to install Ubuntu on. I still want to keep Windows. The hard drive has two partitions. The first is an NTFS partition with Windows XP installed. The second is the PC recovery partition. I have tested the Ubuntu Dapper live CD on the system, and it appears to be working well. I have created PC recovery CDs.

The questions:
1. If something goes wrong when I make a new partition, will I be able to boot and recover the original system from the PC recovery CDs? Or do I need something else to make the partitions in a safe way? I did not recieve a Windows CD with my PC.

2. Should I make a boot CD as described on the following web page?
[http://old.bink.nu/xpbootcd/](http://old.bink.nu/xpbootcd/)

3. Would you recommend me to use the partition manager included on the Ubuntu CD (live version), or should I use a third party manager, f.ex cute partition manager, or one included on Ultimate Boot CD, or Ultimate Boot CD for Windows?

4. How many partitions should I make? Do I have to change from NTFS into f.ex FAT32? Will the Linux partition manager let me do this? Which partitions should have the different file systems?

5. How do I know if what is described on the following page applies to me?
[https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid)

6. From 
[http://www.ubuntu.com/download/releasenotes/606](http://www.ubuntu.com/download/releasenotes/606)
"If you are installing from the Desktop CD on a system that already has one or more RAID arrays or LVM volume groups set up, you must disable the arrays (sudo /etc/init.d/mdadm stop; sudo mdadm --stop --scan) and volume groups (sudo vgchange -a n) before starting the installer. "

How do I know if this applies to me? Does this paragraph tell me to type in f.ex. "sudo /etc/init.d/mdadm stop;" in the terminal?

7. My PC has a "AMD Turion 64"-mark. Should I use the version for "64-bit PC"? Iv'e tested Intel x86 version.

8. When testing, the "&", f.ex., is in the wrong place (above "7", it should be above "6"). Is that corrected during installation?

---

### Post by xyz on 2006-11-26
Have you checked this one out:
[Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

### Post by missmoondog on 2006-11-26
the simplest way is to create 3 partitions beforehand, if possible. one for windows, one linux native and one linux swap (1.5-2 times bigger than the amount of memory). install windows first on the ntfs windows partition. then install ubuntu on the other partitions. the ubuntu install disk will automatically install it to the linux partitons. let ubuntu install grub to where it says by default and you will be fine.

---

### Post by Bosonator on 2006-11-26
1. Not sure, but the install usually goes very smoothly. 

2. As far as I know, no. Ubuntu comes with a boot loader by default (called GRUB) and should automatically detect your Windows partition.

3. Yes, use the partition manager included on the Ubuntu CD. It's so simple to use, it'll make you shake your head in disbelief. You can even resize partitions without destroying them.

4. It's up to you. XYZ's comment is a good one on this point. 

5. 99.999% chance it doesn't. LVM and RAID are used when you extend a single drive across multiple physical hard drives, and are not used by most casual users. 

6. See question 5.

7. It's up to you. Performance will be better with the AMD64 install, but it's missing a couple pieces of important software (which *are* under development, but not available yet). An example is that the AMD64 version doesn't include Flashplayer, and it's a bugger to get working. Personally, I'm sticking with the i386 version until all the finiky little things get worked out. 

8. Not sure, myself.

I think you'll be surprised at how easy the install goes. Good luck!

---

### Post by seshomaru samma on 2006-11-26
1. If you paid for your Windows you should demand a Windows CD. You should be able to recover your Windows with that recovery-CD but then you would lose all your data and settings. If you have Windows activation number and a serial number (maybe it's the same thing) you could restore your Windows with somebody else's Windows CD.
2. no
3.any partition manager you are comfortable with will do, don't forget to back up all your data first. also Windows need to be defraged before it can be resized ( start>control panel>admin tools>computer managment>disk defragmenter)
4. i dont think you can change windows from NTFS to FAT without reinstalling it. what you could do is resize it (defrag first) and leave the rset of the disk unparted. Ubuntu will make the partitions for you. If you want to share files between Linux and Windows you could create a FAT32 partition so your disk will look like this:
Windows -NTFS
Files- FAT32
Linux -ext3
Swap -swap
The ubuntu Cd will create the Linux partition and the swap partition for you. You can create a /home partition on Linux where you will put all your personal things and settings , this way when you upgrade Ubuntu you keep all your settings and documents.
5.you can test it with the live CD
i think 
> sudo fdisk -l
will show you whether you have an LVM volume there but it's quite rare
this is the output of the  fdisk command on my desktop:
> Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3824    30716248+  83  Linux
/dev/hda2            3825        5401    12667252+  83  Linux
/dev/hda3            5402        5472      570307+  82  Linux swap / Solaris
/dev/hda4   *        5473        9726    34168832    7  HPFS/NTFS
if you have an LVM it should show together with the system name like 
But im not 100% sure...cause i dont use LVM or RAID

7 probably better to install the i386 version first , the 64bit seems to be more buggy 
8 dont know...sorry

---

### Post by moshuptrail on 2006-11-26
8. Most keyboards I've seen have & above 7 and ^ above 6.  Maybe you've got a different keyboard.  Once installed there are ways to pick alternate keyboards.

---

### Post by KentS on 2006-11-26
Ok, a couple of more questions.

I wrote 
> sudo fdisk -l
in the terminal using the live CD. There was no mention of LVM volume. Except from different partition the output looked almost identical to the output seshomaru samma got. However when I shut down my system from Ubuntu I got some output about shutting down LVM volumes. I also get some output concerning RAID. Do I have to assume my system has LVM/RAID? Can I use the live CD and just type in the commands I quoted under 6.? Or should I use the alternate CD?

If I don't create a \home partition, will I still be able to upgrade Ubuntu without loosing my documents?

I think my preferred strategy for installation is to adapt the procedure from the link XYZ gave me to the desktop CD, and use the included partition manager.

I'm using a Norwegian keyboard. We have three more letters compared to the English alphabet. I guess that's the reason for the misplacements, so I'm guessing it will be corrected during installation.

Thank you so much for your help, all of you.

---

### Post by seshomaru samma on 2006-11-26
If your fdisk shows no LVM then you are OK
What you see when Ubuntu boots and shutdown are all the services that it starts and end , even if you dont have LVM it will start the service when it boots and end it when it shuts down (you can later configure it to only starts the services you need so boot/shut down time is shorter)
There are several ways of upgrading , many of them will leave your documents and setting in tact, but I found that the safest way of upgrading is reinstalling. If you reinstall you must have a /home partition set in order to keep your docs+settings.
You can choose your keyboard setting during installation.
Welcome to Ubuntu!

---

### Post by KentS on 2006-11-27
Thank you very much!

---

