---
title: "After using Ubuntu 8.04 live CD, unable to boot back to OS X"
date: 2008-05-22
forum: Apple Hardware Users
---

### Post by henji4 on 2008-05-22
After I tried Ubuntu 8.04 - the Hardy Heron Live CD on my macbook pro, I can't boot back to OS X. 
i have tried Restting the PRAM, Option booting, force OS X to start, but they don't work.
everytime i startup i see a folder icon with a ? mark inside.
I can still use Live CD and see my Macintosh HD but when I start up with OS X install CD, I cannot find Macintosh HD in startup disk option.

is there a way to get back to OS X?
I don't have any backups. Is there a way I can save my files that are in Document folder?

---

### Post by cyberdork33 on 2008-05-22
have you tried booting with CMD+S?

I don't know what you might have done, but simply booting the live cd doesn't make any kind of changes to your machine.

---

### Post by Playercoca on 2008-05-22
You can back-up the files on your HD with the Live-cd and a network interface/external hard-drive

---

### Post by maddojf on 2008-05-22
Backing up your files is definitely a good idea, but if it were me I would put in the Mac OS Install Disc which will boot into a live environment by holding down the c key during boot.  Once there, instead of using the installer, look in the menu bar and one of the menus will allow you to run disk utility.  See if your hard drive shows up.  If it does, then you may or may not be able to get it working again by repairing the disk, but you should at least be able to do an "Archive and Install".

An "Archive and Install" will save you entire system to a folder called "Previous Systems" or "Old Systems" or something like that.  You should then be able to boot into Mac OS X without losing any data.

Another possibility is that your hard drive has suffered a hardware failure and it just happened to occur around the time that you used the Live CD (This most often occurs when the hard drive is very new or very old).  If this has happened then you won't be able to see your internal hard drive with Disk Utility.  I recently had a hard drive failure: I only saw a blinking icon when I tried to boot it up and Disk Utility didn't show the drive at all.

A third possibility, with similar symptoms to the hardware failure is a corrupt files system that won't let you boot.  I have never had this happen to me so I can't say for sure what it would look like, but I would think that the drive would show up in Disk Utility but you wouldn't be able to browse its contents.  If you see the drive but can't mount the volume or partition on it then you may be able to use a recovery tool such as Disk Warrior, but I don't have any personal experience with that.

But, as was stated earlier, it seems unlikely that this was caused by the Ubuntu Live CD unless you explicitly mounted the hard drive and mucked around in the terminal.

---

### Post by henji4 on 2008-05-22
thanks for your inputs.
1. i have tried Cmd + S , but it doesnt go into os x
2. i tried to backup with the Live-cd, but it says i dont have permission to read some files.
3. i went in to disk utility, my 232.9G Hitachi showed up but under it there is a disk0s1(200mb microsoft reserved type)that i have never seen before.
and i dont see my Macintosh HD. repair disk option is not avaliable.  so i guess i cant "Archive and Install".
maybe it is a hardware failure but how come Macintosh HD shows within Ubuntu?
please help me...

---

### Post by damis648 on 2008-05-22
Well i have only bought a few Apple products (iPod and iPhone) but as long as you are still in warranty you should be able to set up an appointment at the apple store to have them look at it.

---

### Post by cyberdork33 on 2008-05-22
> **henji4 said:**
> thanks for your inputs.
1. i have tried Cmd + S , but it doesnt go into os x
It boots OSX into single-user mode. it goes to a shell where you can run the commands indicated to repair your filesystem... it is booting at all. What does it boot to?

> **henji4 said:**
> 2. i tried to backup with the Live-cd, but it says i dont have permission to read some files.
do it as root.
> **henji4 said:**
> 3. i went in to disk utility, my 232.9G Hitachi showed up but under it there is a disk0s1(200mb microsoft reserved type)that i have never seen before.
and i dont see my Macintosh HD. repair disk option is not avaliable.  so i guess i cant "Archive and Install".
maybe it is a hardware failure but how come Macintosh HD shows within Ubuntu?
please help me...That first partition is your EFI partion. That is ok. It seems that for some reason your partition table as become corrupted, and thus, your partition seems to be invisible (and unbootable). In ubuntu, what is the output of:
```
sudo parted /dev/sda print
```and
```
sudo fdisk -l /dev/sda
```

---

### Post by henji4 on 2008-05-23
> **cyberdork33 said:**
> It boots OSX into single-user mode. it goes to a shell where you can run the commands indicated to repair your filesystem... it is booting at all. What does it boot to?


do it as root.
That first partition is your EFI partion. That is ok. It seems that for some reason your partition table as become corrupted, and thus, your partition seems to be invisible (and unbootable). In ubuntu, what is the output of:
```
sudo parted /dev/sda print
```and
```
sudo fdisk -l /dev/sda
```

1.could you explain a little bit how to do it as root? im a linux newbie

2. ```
ubuntu@ubuntu:~$ sudo parted /dev/sda print 
 
Disk /dev/sda: 250GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
 
Number  Start   End    Size   File system  Name                  Flags   
 1      20.5kB  210MB  210MB  fat32        EFI system partition  msftres 
 2      210MB   250GB  250GB  hfs+         Customer              boot    
 
Information: Don't forget to update /etc/fstab, if necessary.
```

```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda 
 
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted. 
 
 
Disk /dev/sda: 250.0 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x00000000  Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1       30402   244198583+  ee  EFI GPT  
```

hope these helps

---

### Post by cyberdork33 on 2008-05-23
> **henji4 said:**
> 1.could you explain a little bit how to do it as root? im a linux newbieLet's skip this for now as I think I have a solution.

> **henji4 said:**
>  2. ```
ubuntu@ubuntu:~$ sudo parted /dev/sda print 
...
``````
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda
...
```
Upfront information: Your Mac has two different ways of determining the partition status on your hard drive. The "real" table is called the GPT. This table is used by OSX and the Mac firmware. 

The information that the GPT contains is the output of the 'parted' command. As you can see the 'boot' flag is set on your second partition. This is incorrect according to [this]("http://www.macosxhints.com/article.php?story=20080130022147512"). So what you need to do is startup Ubuntu (livecd) and use gparted to set the boot flag to the EFI partition rather than the OSX partition. Hopefully that will fix the booting issue.

There is another problem in that your MBR table (shown in the output of the second command) is not synced with your GPT. Of course, this doesn't really matter unless you need it for anything, which you don't if you are not installing Ubuntu or Windows, and can be fixed when you do one of those things.

---

### Post by henji4 on 2008-05-23
> **cyberdork33 said:**
> Let's skip this for now as I think I have a solution.


Upfront information: Your Mac has two different ways of determining the partition status on your hard drive. The "real" table is called the GPT. This table is used by OSX and the Mac firmware. 

The information that the GPT contains is the output of the 'parted' command. As you can see the 'boot' flag is set on your second partition. This is incorrect according to [this]("http://www.macosxhints.com/article.php?story=20080130022147512"). So what you need to do is startup Ubuntu (livecd) and use gparted to set the boot flag to the EFI partition rather than the OSX partition. Hopefully that will fix the booting issue.

There is another problem in that your MBR table (shown in the output of the second command) is not synced with your GPT. Of course, this doesn't really matter unless you need it for anything, which you don't if you are not installing Ubuntu or Windows, and can be fixed when you do one of those things.

Thank you Cyber,
My problem is solved.

---

### Post by cyberdork33 on 2008-05-23
Great!
Can you mark this thread as solved?

---

### Post by kumarldh on 2008-05-29
Hi,
I am reopening the thread, sorry as nothing mentioned here helped me. Here is the scenario.
a) I have 8.04 disk and using boot preferences from system pref pane I selected disk as target boot option. I really didnt bother to read, my mistake, what all options were there
b) My mac booted into ubuntu
Now, I have shut down the machine pressed all the key combinations but my mac just boots into Ubuntu 8.04. Any help?

Regards,
Kumar

---

### Post by kumarldh on 2008-05-29
Hi,
Please mark the thread closed. I just found a way out. Hope it helps some one like me 
a) Switch off the machine
b) Press the options button
c) Switch on the machine
d) Screen will show 2 boot options, choose the desired one


Thanks again.

Regards,
Kumar Chetan Sharma

---

