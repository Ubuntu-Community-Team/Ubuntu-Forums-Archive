---
title: "editing grub"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by rsnow on 2007-07-20
I have read the previous posts on this subject and once thought I had found my answer. However, I was interrupted and when I came back I could not remember the particular post that had the information I needed. So, here is my situation: I have W2K installed on the first partition of my master hard drive. I have fedora6 installed on the second partition of my master hard drive. I installed Ubuntu 7.04 on my slave hard drive. 

Grub now shows 4 iterations for Ubuntu, memtest, and W2K boot options. 

I commented out the older Ubuntu kernals. How do I get grub to include fedora6 as a boot option?

I know  to use sudo gedit /boot/grub/menu.lst. What data do I need to enter?

---

### Post by nitro_n2o on 2007-07-20
I think that your fedora is still bootable and is not a big problem 
go to /bool/grub/menu.lst and manually add the fedora entry 

title Fedora6
root (hd?,?)
kernel /boot/vmlinuz-??
initrd (if used) 

just copy and paste the ubuntu entry, and assuming that you can access your fedora files you can till exactly where to find the kernel and initrd

make a back up copy of your grub so in case you have something wrong you can easily recover by using the live cd, accessing the FS and using the back up copy

---

### Post by Big_Croc7 on 2007-07-20
I agree that it doesn't sound like a big problem, and the solution posted before should work fine.  However, with more than two operating systems I find it useful to use separate grub installations; this is more work to set up, but it has advantages.  I would recommend using a menu.lst in Fedora for Grub on the primary drive, and also installing Grub to the secondary drive (using the Ubuntu menu.lst).

From a live CD, install grub to (hd0) with the root as (hd0,1) - this will use Fedora's menu.lst and install to your primary disk; then, run install to (hd1) with the root as (hd1,0) - or whatever your Ubuntu boot partition is - this will install grub to the MBR of the second hard disk, using Ubuntu's menu.lst.  The final step is to add the following entry to Fedora's menu.lst:

title   Ubuntu bootloader
rootnoverify   (hd1)
chainloader +1
boot

---
Then, when you boot, you should see the following options:

Fedora kernel 2.....
Fedora recovery kernel ......
Fedora memtest...
Windows XP
Ubuntu bootloader
---
the last item will bring up another menu, with

Ubuntu kernel 2.....
Ubuntu recovery...
Ubuntu memtest...


Somewhat confusing perhaps, but it might save hassle later (e.g. with kernel updates in Fedora and Ubuntu). :)
Hope that all makes sense!

---

### Post by cotcot on 2007-07-20
Here is my menu entry for fedora as an example:

> 
title Fedora Core (2.6.19-1.2895.fc6)
root (hd1,0)
kernel /boot/vmlinuz-2.6.19-1.2895.fc6 ro root=LABEL=/ rhgb quiet
initrd /boot/initrd-2.6.19-1.2895.fc6.img


Of course adapt the kernel version and hd1,0 to what you have.

---

### Post by rsnow on 2007-07-20
Thanks to all for your help. I will see what I can accomplish. If I don't come back on this thread you can assume I was successful. Otherwise, I will be back to say what I did and what results I got.

---

### Post by rsnow on 2007-07-21
> **Big_Croc7 said:**
> I agree that it doesn't sound like a big problem, and the solution posted before should work fine.  However, with more than two operating systems I find it useful to use separate grub installations; this is more work to set up, but it has advantages.  I would recommend using a menu.lst in Fedora for Grub on the primary drive, and also installing Grub to the secondary drive (using the Ubuntu menu.lst).

From a live CD, install grub to (hd0) with the root as (hd0,1) - this will use Fedora's menu.lst and install to your primary disk; then, run install to (hd1) with the root as (hd1,0) - or whatever your Ubuntu boot partition is - this will install grub to the MBR of the second hard disk, using Ubuntu's menu.lst.  The final step is to add the following entry to Fedora's menu.lst:

title   Ubuntu bootloader
rootnoverify   (hd1)
chainloader +1
boot

---
Then, when you boot, you should see the following options:

Fedora kernel 2.....
Fedora recovery kernel ......
Fedora memtest...
Windows XP
Ubuntu bootloader
---
the last item will bring up another menu, with

Ubuntu kernel 2.....
Ubuntu recovery...
Ubuntu memtest...


Somewhat confusing perhaps, but it might save hassle later (e.g. with kernel updates in Fedora and Ubuntu). :)
Hope that all makes sense!
I need a little more help understanding this...when you say "From a live cd install grub...", do you mean like I need to reinstall fedora core 6? Otherwise, I don't know how to just install grub. I looked at the install process again and I didn't see an option to install grub.  I tried the other two suggestions (Nitro & Cotcot) but was not successful with them. One did get fedora on the grub menu but it would not boot fedora. I guess I need more hand holding. Also, I can't figure out how to access fedora to see what keranl version I have.

If all this sounds like more than you want to fool with, I understand. I don't mind reinstalling Ubuntu because I have just started with it, but I would like to avoid starting over with fedora because it is so slow downloading updates (even over my dsl). I appreciate any help you care to give.

---

### Post by confused57 on 2007-07-21
You can install Fedora's grub to the mbr, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Then you can add an entry to Fedora's grub to boot Ubuntu:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

I would recommend using a configfile entry:
```
title        Feisty
configfile   (hd1,0)/boot/grub/menu.lst
```

---

### Post by rsnow on 2007-07-23
Well, things have not gone as I hoped. After trying the things posted here plus some things from the Super Grub Disk page, I finally resorted to using Partition Magic in W2K to clean both Fedora and Ubuntu off the hard drives. I then set up a 20GB partition after c: and installed Ubuntu 7.04 there. Upon rebooting grub looked O.K. and I was able to boot to either Ubuntu or W2K. Next I used the partition program in Fedora's installer to set up a 20GB partition following Ubuntu and installed Fedora there. During the Fedora install I got a message saying that the swap file (set up during Ubuntu install) was smaller than my ram and might cause problems. So, after Fedora install, I rebooted back into W2K and used Partition Magic to increase the size of the swap file.

After that, I was unable to boot into anything except the bash shell with the grub> prompt. Eventually I was able to setup grub into (hd0,5) and get Ubuntu's menu.lst working. So now I can boot into Ubuntu or W2K but not Fedora. 

I was going to use Partition Magic to look at the drive setup to see how much free space I had left on hd0 but when I try to activate PM I now get the following messages:

error 110: partition starting at sector 63 on disk 1 - The CHS length is 77561820, the LBA length is 77561820 and the file system length is 78140097. 

PartMagic then goes on to say that it can fix this, do I want to? I click yes and get a message saying that the problem was successfully fixed.

But, then, I get another error message (113) which says partition starting at sector 63 overlaps another partition or the end of the disk. PM has determined that the partition can be truncated from 78140097 to 77561820 should it be fixed? I click yes and get the message saying it was successfully fixed.

Then I get the message: init failed: error 117 Partition's drive letter cannot be identified. Then PM closes.

Can anyone tell me how to get into a partition editor and fix this?:confused:

---

### Post by Big_Croc7 on 2007-07-27
By the sound of it the partition table has become corrupted.  I suspect that this is a result of using partition magic; it also happens sometimes with Windows' in-built partitioning program.  The partition table is where a record of the layout of partitions on the disk is stored.  Details of each partition are also stored within the partition itself.  For some reason I don't know, the Windows method of partitioning (and by the sound of things, Partition Magic too - I've heard of other people having problems with it) has written the wrong values to the partition table.

That's the problem; now, how to fix it.  There is an easy-but-long way, and a complicated-but-quick way.  The easy way is to use a GParted liveCD to create a new partition table - this is drastic and will delete all your data.  You then have a blank disk on which to partition (with GParted) and install things as yyou like.  The hard way is to use a partition table recovery program - I would recommend testdisk (you can download this using Synaptic during a recovery CD session).  This will read the partition table data from the disk and create a new (correct) partition table.  You can then write this new table to the disk, which will be readable by Windows, Ubuntu & Fedora.  It's fairly self-explanatory, but you do need to a think a bit; it will likely 'see' all the partitions you've deleted over the past few days, so you will have to select the correct ones to recover.  Usual warnings about backing up all user data etc. apply!

PS. Sorry for the slow reply - I'm also not going to check for another week or so after this weekend, but I'll check back after that (feel free to PM me if I don't!).

EDIT: By the way, most distros can mount more than one swap partition, so you can create a new partition at the end of the disk without moving/resizing others.

---

### Post by rsnow on 2007-07-27
I have decided not to try working with two distros. For the time  being, and until I learn more, I am going to use Feisty by itself.

I have already reinstalled using the entire hard drive.

Thanks for all the help. I'll probably be back with more questions as I try to master the learning curve.

---

