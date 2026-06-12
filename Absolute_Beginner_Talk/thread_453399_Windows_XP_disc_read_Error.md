---
title: "Windows XP disc read Error"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by coderK on 2007-05-24
Hi,
I installed Ubuntu a few days ago. I had Windows XP. It was fine but I had very little RAM: 256 MB (-32MB of which is shared with the video card) with which Feisty would run really slow. So my friend suggested I use a live CD of GNOME Partition Editor, create the partitions and turn the swap on before I started installing Ubuntu. I created 3 partitions of ext3 format on my 160GB Hard disc (it's SATA) for Root, Home and Swap which were 20GB, 10 GB, and 1 GB respectively. I had not yet installed Ubuntu.
 After that I could not boot with XP, It gave me and error saying:
```
A disc read error had occurred.
Press Alt+Ctrl+Del to restart.
```So I tried the recovery Console in the XP CD and tried fixboot and fixmbr.
It still gave me the error. So I was like, what the heck and installed Ubuntu. The GRUB boot loader screen gives me an option to start XP but I keep getting the same error. I have all the partitions mounted on Ubuntu and can access them. The data is all fine. What is wrong?

I forgot to mention that after the partitioning, I booted with the live CD and tried installing Ubuntu but quit on step 6 where I wasn't sure if I should import my XP account. I planned to ask a friend later. He has been on Ubuntu for nearly six months now and he has no idea what is wrong with Windows.

I just installed ntfs-3g but it said I could not write to it due to a scheduled disc check. I should boot into windows twice to enable this. So I just forced a remount and i can write to the drive. I hope I haven't done more damage. Can somebody please help?

---

### Post by coderK on 2007-05-24
I really need to fix this before my dad gets back!!! He'll be back tomorrow. He won't be very happy to know I couldn't fix it. And I'm pretty sure he would hate switching to another interface. Please please help guys.

---

### Post by dhruva023 on 2007-05-24
this is xp error.

i had many time, when i was sing xp.

just try to reboot few time, it might start.

i had to reboot 6 to 7 time to get that error fixed.

---

### Post by Outrunner on 2007-05-24
Can you try hitting F8 continually during startup, and see if you can boot into safe mode at least.

---

### Post by coderK on 2007-05-24
I have already booted some 15 times since yesterday. No luck yet. And I tried F8 just now for the safe mode. Same error. I just can't figure out why the XP CD couldn't fix this. Is it a problem with GRUB?

I forgot to mention that after the partitioning, I booted with the live CD and tried installing Ubuntu but quit on step 6 where I wasn't sure if I should import my XP account. I planned to ask a friend later. He has been on Ubuntu for nearly six months now and he has no idea what is wrong with Windows. :(

---

### Post by CrucifiedEgo on 2007-05-24
Unfortunately resizing partitions, especially NTFS, always comes with a risk. IF you boot to the recovery console, can you read from the windows device(i.e. read directories with dir?)?  Try running chkdsk to check the filesystem for errors.

---

### Post by Terl on 2007-05-24
Can you post the output of:  ```
fdisk -l
```?

I am assuming you are in Ubuntu.  Is that correct?

I am afraid the partitioning may have "broken" xp but I am not sure how badly.  Did you defragment the drive before you partitioned it?  

If there were a problem with grub (do you see grub when you boot?) you would get a grub error.

EDIT:  Yes, as mentioned above run chkdsk.  Many times if you resize a windows partition it goes wonky on the first start.  You might get lucky.

---

### Post by Zzl1xndd on 2007-05-24
It will write over you MBR but might i suggest doing a repair install it. It should solve this problem.

---

### Post by coderK on 2007-05-24
I can read directories with dir in the recovery console. But how can I run chkdisc? I'm not on Windows. I am on Ubuntu. I did defragment my hard drive - both the partitions I had at the time. When I boot I see three options for Ubuntu and one for XP. I think that is the GRUB screen... but i'm sure. I did try a repair befor Ubuntu was installed and it did not work. But now wouldn't it overwrite my GRUB configs? And fdisk -l does not seem to give any output. I just get the prompt back. Am I doing something wrong?

---

### Post by Terl on 2007-05-24
the l is a small L.  Is that what you entered fdisk -l (with the l being lower case L)?

Yes, if you did fixmbr it would overwrite grub.  I am not sure if repair will.  I think you can run chkdsk from the recovery console if you restart with your windows xp disk.

---

### Post by coderK on 2007-05-24
Yes that was a small L, I just copy pasted. I don't have the XP CD right now ( my vendor keeps it - Although Microsoft says My windows is genuine)
I'll try the chkdisc tomorrow then but I think the discs are okay since I can access and modify them. Here is the fdisk:
```
kush@k-Ubuntu:~$ fdisk -l
kush@k-Ubuntu:~$ fdisk -l
kush@k-Ubuntu:~$ fdisk -l
kush@k-Ubuntu:~$ fdisk -l
kush@k-Ubuntu:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
kush@k-Ubuntu:~$ 
```

---

### Post by CrucifiedEgo on 2007-05-24
coder: run it from the Windows XP Repair console.  chkdsk C: <enter>

---

### Post by coderK on 2007-05-24
What is wrong here?
```
fdisk -l
```
Why don't I get an output? Is an Output expected?

---

### Post by dstew on 2007-05-24
Try **sudo fdisk -l**

---

### Post by coderK on 2007-05-24
Yes sudo did it. Thanks. Here is the output:
```
kush@k-Ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8296    66637588+   7  HPFS/NTFS
/dev/sda2            9732       19456    78116062+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            8297        9601    10482412+  83  Linux
/dev/sda4            9602        9731     1044225   82  Linux swap / Solaris
/dev/sda5            9733       16845    57135172+   7  HPFS/NTFS
/dev/sda6           16846       19456    20972826   83  Linux

Partition table entries are not in disk order
kush@k-Ubuntu:~$ 
```
Is it any help?

---

### Post by Terl on 2007-05-24
I am not an expert but it does not look good to me.  sda2 looks like it overlaps sda5 and sda6.  I will have to defer to someone else on this.

Sorry, I forgot about the sudo part in the fdisk command....

---

### Post by coderK on 2007-05-24
I am a newbie but I remember GParted displayed sda2 was the extended partition under which sda5 and sda6 were created because you cannot have more than four primary partitions - At least that's what GParted said anyway. And I had used version 0.3.3 if that makes any difference.

---

### Post by Terl on 2007-05-24
What is sda5?  It is formatted ntfs.  It looks like windows is on sda1.

---

### Post by gbesso on 2007-05-24
/dev/sda2 is indeed your extended partition and that is why it seems to overlap, I don't think that's the problem.
What partition is your windows install on? You have 2 NTFS filesystems, sda1 and sda5

Did you move partitions around?

---

### Post by coderK on 2007-05-24
sda5 is my D drive in windows, I have mounted it as softwares in Ubuntu. sda1 is the Windows Partition. sda5 was already under sda2 when I used GParted so I just resized it to get sda6 which is the Root in Ubuntu. C drive was resized to obtain the sda3 which is the Home and sda4 which is the swap.

---

### Post by coderK on 2007-05-24
Er, is anybody still online? Bump.

---

### Post by Happy_Man on 2007-05-24
Oh jeez... here's my take on this:

For some reason, GParted has *completely* messed up your HDD partitions, and so now Ubuntu can boot (its partitions are fine) but Windows cannot (you did something MESSED UP here, bud, and I don't know what). What I suggest? Get an install CD, and reinstall Windows. Let it use the whole drive. Get Windows up and running, then come back here. Do some RESEARCH. Many people will just assume they can use Linux like Windows and proceed to go all happy-go-lucky and BAM! They're left with an expensive doorstop. 

But, I'm not blaming you. In any case, do as I say. Perhaps we can get this straightened out soon. 

Remember to back up anything important.

---

### Post by coderK on 2007-05-24
But won't a reinstall erase the grub configs? I might not be able to boot into Ubuntu and With windows I can't be sure of anything. Besides, a reinstall will leave me lost for good. I would have to sit for a week to reconfigure and reinstall all the important and other not so important but useful softwares.

I'm also worried about the GRUB configs. In any case if there is a way out I would like to avoid a reinstall of Windows as far as possible. I have a feeling GRUB can help me fix it because this here guy managed to although I don't have the same lines in my configuration file.
[http://forums.devshed.com/windows-help-34/a-disk-read-error-has-occurred-after-ubuntu-dual-boot-444515.html](http://forums.devshed.com/windows-help-34/a-disk-read-error-has-occurred-after-ubuntu-dual-boot-444515.html)

---

### Post by confused57 on 2007-05-24
You could download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

It's a small download(5-7 Mb) & maybe it will be able to boot your Windows.

It's probably a Windows problem, but it wouldn't hurt to post your menu.lst:
```
gedit /boot/grub/menu.lst
```
you probably just need to post the entries to boot Ubuntu & Windows

---

### Post by coderK on 2007-05-24
I'll try the Super Grub disc in a minute. Meanwhile, here is menu.lst. I hope it helps. thanks.
```

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=c2bb5e03-5050-4f88-82a8-a77b25f328c0 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=c2bb5e03-5050-4f88-82a8-a77b25f328c0 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

---

### Post by coderK on 2007-05-24
Damn. I couldn't boot into **or** fix windows. I keep getting the same error. Do I have to Reinstall? Surely, there must be another way Out. If grub works, the MBR is not physically damaged right?

---

### Post by Terl on 2007-05-24
Your grub file looks fine.  I think the partitioning is hosed and somehow windows is seriously confused.  There may be no other way out other than to reinstall windows and then ubuntu.

---

### Post by coderK on 2007-05-24
Why do I have to reinstall Ubuntu? Can't I use the Super GRUB disc to bring back grub on the Windows Partition?

---

### Post by Happy_Man on 2007-05-24
No, because this isn't a GRUB problem. It never was. This is a partition and Windows problem, and reinstalling is the only way you're gonna fix it. Sorry.... :(

---

### Post by STREETURCHINE on 2007-05-24
just out of curiosity do you have the gparted live disk,if not can you download it then run it and take a screen shot of how it displays your partition setup.
i dont know if it will help but it will show what is going on better.

---

### Post by Terl on 2007-05-24
> **STREETURCHINE said:**
> just out of curiosity do you have the gparted live disk,if not can you download it then run it and take a screen shot of how it displays your partition setup.
i dont know if it will help but it will show what is going on better.

He did in this thread:  [Check here.]("http://ubuntuforums.org/showthread.php?t=453743")

It is bad.

---

### Post by STREETURCHINE on 2007-05-24
yep sorry did not see that yes it is fried,seems to have split windows in two,i think i would reformat the whole disk make two partitions install windows on the first one,then install ubuntu on the second.
takes a while to get the hang of manually partitioning a hard drive.
i know i stuffed mine several times before i learnt

---

### Post by Terl on 2007-05-24
> **STREETURCHINE said:**
> yep sorry did not see that yes it is fried,seems to have split windows in two,i think i would reformat the whole disk make two partitions install windows on the first one,then install ubuntu on the second.
takes a while to get the hang of manually partitioning a hard drive.
i know i stuffed mine several times before i learnt

Me too.  Nothing you can do but laugh about it and move on.  I've learned a lot making my share of boo-boos.

---

### Post by STREETURCHINE on 2007-05-24
> **Terl said:**
> Me too.  Nothing you can do but laugh about it and move on.  I've learned a lot making my share of boo-boos.

yes but what an exciting way to learn,lol

---

### Post by coderK on 2007-05-25
Hey sorry guys, I've been so paranoid. My head was not working well yesterday - lack of sleep!!
Anyway, none of the data is lost. Today, I booted into Ubuntu and C: drive was also gone. I called up a friend about what was up and he figured that the drives aren't mounted properly. He told me to go to /etc/fstab and change the device names. did it and the drives were mounted back. All the data is there! I can now backup and reinstall Windows. But I don't get why I need to reinstall Ubuntu. I can just Reinstall GRUB right? Here is a copy of fstab in case anyone is curious:
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=c2bb5e03-5050-4f88-82a8-a77b25f328c0 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=81e08a99-4eb6-4a45-a700-ed27c0c2e2c5 /home ext3 defaults 0 2
# Entry for /dev/sda5 :
#UUID=E8E010EBE010C1AC /softwares ntfs-3g defaults,locale=en_IN 0 1
sda5 /softwares ntfs-3g defaults,locale=en_IN 0 1
# Entry for /dev/sda1 :
#UUID=262C22392C220501 /windows ntfs-3g defaults,locale=en_IN 0 1
sda1 /windows ntfs-3g defaults,locale=en_IN 0 1
# Entry for /dev/sda4 :
UUID=24dbedcc-6d14-45b6-a166-d1bf7dd9a419 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
```

---

### Post by Terl on 2007-05-25
Remember, when you reinstall windows it will over write the mbr and you will have to reinstall grub.

I would recommend you consider reinstalling both windows and ubuntu (windows first of course) becuase you can set up a cleaner partition arrangement from the beginning.  The structure you have now is not clean to me.

Yes, you could leave it as it is and reinstall windows and reinstall grub while leaving Ubuntu as it is.  In my opinion I think it would be good to repartition the drives and reinstall fresh.

I am very happy you did not lose any data :)  Always a good thing.

---

### Post by coderK on 2007-05-25
I will think about the reformatting of the whole drive when I get the XP Disc. If I have to do that, I'll need to take at least 20GB of backup which isn't very encouraging. But there is a new problem right now. I can't write to ntfs partitions although I have ntfs-3g. Was it because of the fstab change?

---

### Post by Terl on 2007-05-25
It probably is due to the fstab change.  Have you tried using the ntfs-config tool?

---

### Post by Sef on 2007-05-25
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

From Test Disk:

> TestDisk is a powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting your Partition Table). Partition table recovery using TestDisk is really easy.

---

### Post by Terl on 2007-05-25
> **Sef said:**
> Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

From Test Disk:


Thanks for that link!  That is a great tool.

---

### Post by coderK on 2007-05-25
Checking out testdisk right now. Looks like a great app. Thanks. Any idea about the ntfs-3g problem. I tried this: ```
kush@k-Ubuntu:~$ sudo gksu ntfs-config
Password:
kush@k-Ubuntu:~$ sudo gksu ntfs-config
kush@k-Ubuntu:~$ sudo gksu ntfs-config
```
But nothing seems to happen! What is wrong???

---

### Post by dstew on 2007-05-25
I think you just want```
gksu ntfs-config
```

---

### Post by Happy_Man on 2007-05-25
Are you sure you did 
```
sudo apt-get install ntfs-3g ntfs-config
```
?

Copy and paste that into a terminal, and make sure it installed EVERYTHING. Then try again. Above all, be patient. Some stuff takes a while on older hardware.

EDIT: NVM. Sudo and Gksu do the same thing... you don't need to use them both.

---

### Post by coderK on 2007-05-26
I'll tried the command:
```
kush@k-Ubuntu:~$ sudo ntfs-config
Password:
sudo: ntfs-config: command not found
[EMAIL="kush@k-Ubuntu:~$"]kush@k-Ubuntu:~$[/EMAIL]
```.
Nothing seems to happen
I can't try the install again because, I can't connect to the net. My service provider says his "server is down". I'm using my dad's laptop right now and also backing up for the XP reinstall.
I'll try reverting back the fstab file. It might help. And I'll give testdisk a try before I reinstall.

---

### Post by coderK on 2007-05-28
Thank you all so much. Windows is up and running again. I used the Testdisk Utility on Ubuntu and it worked like a charm. Restored the NTFS partitions MFT and Boot sector with it. Now I'll just reinstall ntfs-3g. Thanks again everyone.

---

