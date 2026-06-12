---
title: "Force USB-mount with a NTFS-error-disk"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Thorun on 2008-04-06
Hi. 

I have a recently new USB-harddrive but i have noticed, that it doesn't work wery well. For the 2.nd time now - it starts (on switch-on) to say "click-click" and the auto-mount function in Ubuntu 7.10 (nor Windows XP) can detect it. The Ubuntu gives me an error - and a description - like the one below. 

For 2 months ago i had the same problem but only in windows. When i put the USB-external harddrive in my Ubuntu, it "repaired" the drive, and it was auto-mounted wery well. Now i have tried the same thing - but without any success this time. 

My question is: can i somewho force the Ubuntu to mount the drive - and force it to read the partition - or maybe even better - to repair the partition??

(i have bought a new HD now - i just don't want to loose all of my stuff on the dying HD) 


```
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
root@x1lin1:/home/x1lina# mount -t ntfs-3g /dev/sda1 /media/disk1 -o
force
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
root@x1lin1:/home/x1lina# mount -t ntfs-3g /dev/sdb1 /media/disk1 -o
force
Record 6 has no FILE magic: Invalid argument
Failed to open inode: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
root@x1lin1:/home/x1lina# 
```

This code is from the Terminal in Ubuntu v7.10 I tried a hint from some google'ing somewhere. 

Another error code I've got was from a recovery-CD boot-up:

```
Warning
Failed to open incode: Input/output error
Couldn't mount devide /dev/sda1: Input/output error
NTFS resize v1.13.1.1 (libntfs 9:0:0)
Error(2): opening /dev/sda1 of NTFS failed:
No such file or directory
Unable to read the contents of this filesystem. 
```


If someone can tell me what this errors is all about - and maybe could help me to solve the que
stion above, I'll be wery happy!

---

### Post by shawnjones on 2008-04-06
You may want to try this:

mount -t ntfs-3g /dev/sda1 /media/disk1 -o force

Change to:

mount -t ntfs /dev/sda1 /media/disk1 -o force

I believe that the shell sees "-t htfs-3g" as two commands because of the dash before the 3. 

I hope this helps.

---

### Post by Thorun on 2008-04-06
I don't know if i should mount anything first...?
I wrote the code and did an fdisk -l afterwords, and this is the outcome:


```
root@x1lin1:/home/x1lina# mount -t ntfs /dev/sda1 /media/disk1 -o force
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
root@x1lin1:/home/x1lina# fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d2ffbfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        1431    11414182+   7  HPFS/NTFS
/dev/sda3            1432        7296    47110612+   f  W95 Ext'd (LBA)
/dev/sda5            1432        1680     2000061   82  Linux swap / Solaris
/dev/sda6            4054        5328    10241406    7  HPFS/NTFS
/dev/sda7            5329        7296    15807928+   7  HPFS/NTFS
/dev/sda8            1681        2896     9767488+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fe5f79f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801    7  HPFS/NTFS
root@x1lin1:/home/x1lina# 
```

---

### Post by Rocket2DMn on 2008-04-06
I think sdb1 is what you want, sda is your internal hard drive with lots of partitions on it.
In Windows, try going to Control Panel -> Administrative Tools -> Computer Management and click Disk Management on the left side.  If you can see the drive there, right click and select Properties if it's not grayed out.  Then go to the Tools tab and choose to check the volume for errors.
Alternatively if a drive letter is assigned in windows, you can go to Start->Run and type in "cmd", then in the DOS prompt run
```
chkdsk /f k:
```
where k is the drive letter.

If you must try from Ubuntu, you can install the packages ntfsprogs with
```
sudo apt-get install ntfsprogs
```
Then run
```
sudo ntfsfix /dev/sdb
```

---

### Post by Thorun on 2008-04-06
Windows cannot detect the USB-disk at all. It only continue to say *click-click* every 30. second (aprox.). When i turn on the USB-drive in Windows, the OS freeze and everything stalls. It doesn't get any drive-letter either. 

The reason I tried with Ubuntu once again was because of the last time i saw this problem. Ubuntu fixed it wery quick last time. I don't remember i did anything else than turn the harddrive on, after booting up on ubuntu. 
Maybe I did some force-mounting but I don't remember. 

I installed the program and run the command. Outcome:


```
root@x1lin1:/media# sudo ntfsfix /dev/sdb
Mounting volume... Failed to startup volume : Invalid argument
FAILED
Attempting to correct errors... FAILED
Failed to startup volume : Invalid argument
Volume is corrupt. You should run chkdsk.
root@x1lin1:/media# 
```

---

### Post by Rocket2DMn on 2008-04-06
Sounds like your drive may be busted.  If it is actually clicking at you, that could be signs of a hardware failure - the heads are damaged or misaligned and could be scratching the platters inside the drive, which means the drive is ruined.  I'd say if you can't figure out how to fix it in windows, then you're are out of luck.  Linux is not very good with ntfs partitions, only in the last year or so have we been able to write to them with the stable ntfs-3g driver.

---

### Post by Thorun on 2008-04-06
I am aware of my HD is dying. In windows it's clicking. But in Ubuntu it's not. It's just spinning and when I'm trying to mount it, it makes a little clicking noise. 

I think the problem is not the NTFS-volume - but rather how i can access the data at the disk - if it can be accessed. 
I have tried this problem before where ubuntu "fixed" the disk (i don't know if it hardware-failure or just some stupid table-stuff) with no problems at all. 

When I can see the partition table for the USB-drive I still think that there's some way to access the data on the disk. 
Ubuntu wants me to do a "chkdsk" but that command is not valid in the Terminal...

---

### Post by mister_pink on 2008-04-06
Dont try and mount it, this can only make things worse. You can use the dd command to copy bitwise the data from the drive to try and save it. Google around, I dont want to guess at the command you need in case i get it wrong  (which would be very bad).
It'll be along the lines of 
dd /dev/sdb destination

---

### Post by Rocket2DMn on 2008-04-06
chkdsk is a windows command, since ntfs is a windows native file system.  If I were you, I would focus my attempts on getting it to show in windows since linux is pretty bad with ntfs.  If you knew the hard drive is dying, I hope you backed up your data somewhere else, because honestly, the chances that you will be able to recover data from this drive are pretty slim.
You may want to consider getting some data recovery software for windows.

---

### Post by Thorun on 2008-04-06
Well. 

I'll try to google some windows-solutions. It just buggs me, that ubuntu did the "fix" last time - and without any problem. It just auto-mounted right away - even when the drive just click'ed away in windows. 

I have backup of 90% of my data which is acceptable. 
I will consider this thread as "solved".

---

### Post by mister_pink on 2008-04-06
I imagine that ubuntu managed to fix the corruption caused by physical disc damage before, but its probably worse this time so it isn't able to just fix things.
If you want to recover more of your data I suggest trying "dd". You can create an exact copy of the disc onto another as long as you have the space, then hopefully extract some data from that.

---

