---
title: "Dual Boot (2 HD)"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by bparham on 2006-08-17
Okay I'm attempting to dual boot using two hard drives, the original SATA drive has Windows XP, the new IDE drive contains Dapper. In an effort to prevent installing grub on the Windows drive I need to make the new IDE drive the Master and the Windows Drive the slave. Problem is that I can't get the Windows drive to load.

Any ideas?

---

### Post by confused57 on 2006-08-17
This thread may help you:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

You may just need to add this to your /boot/grub/menu.lst:

```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

---

### Post by bparham on 2006-08-17
Thanks, however that's not the problem. Have already manipulated grub, checked fdisk to make sure I was pointing it to the correct partition on the hard drive as well. From what I can tell everything is cool.

---

### Post by bparham on 2006-08-17
Ok, after a little more research I realized that my original drive is an ATA/IDE drive and not a SATA drive as labeled. 

The problem that I keep running into is that the system doesn't see/recognize the secondary drive. The jumper pins have been set per drive instructions. 

Help...

---

### Post by confused57 on 2006-08-17
Is the slave drive controller set to auto or enabled in bios?
That's the only thing I can think of at the moment.

---

### Post by bparham on 2006-08-17
It is, a friend of mine pointed out that perhaps the Jump Pins on the Master as set in such a manner that prevents the second drive from being seen. 

He suggested using Cable Select on the slave drive rather than the slave setting as well. So I have a couple of options to try this evening when I get home.

---

### Post by bparham on 2006-08-17
For whatever reason, my original HD won't act as a slave, fortunately though I have the option to boot from the slave drive. What I'm not sure about is what sort of command changes need to be made to grub to allow Dapper to boot from the slave drive.

---

### Post by confused57 on 2006-08-17
> **bparham said:**
> For whatever reason, my original HD won't act as a slave, fortunately though I have the option to boot from the slave drive. What I'm not sure about is what sort of command changes need to be made to grub to allow Dapper to boot from the slave drive.


 Did you install Dapper connected as the master drive?  You would probably have needed to, to get the dualboot method I described to work.
I'm not sure what's going on...if you don't mind switching drives to have Dapper as the master drive and Windows as the slave drive.
Then try to see what Dapper sees as far as your hard drive configurations by booting into Dapper(if you're able), then run:
```
sudo fdisk -l
```
The -l is a small "L".
You could also boot into the Desktop Live CD and run the above command from terminal.

Can you boot the Dapper & Windows drives when each is the only drive connected (as the master drive)?

Usually IDE drives are pretty straightforward and work pretty well dualbooting with 2 harddrives...

---

### Post by bparham on 2006-08-18
Yeah, each drive boots fine when connected as primary. However I can't get the Windows drive to boot as a slave drive. Originally I had planned on making the Dapper drive Primary and Windows slave, however that doesn't seem like it is going to work. What I would like to do is change the grub settings so that dapper will boot from the slave position. 

My thoughts are that all I need to do is change the drive numbers in grub so that Dapper realizes that it is now on the slave drive. 

Does that make sense?

---

### Post by confused57 on 2006-08-18
Does the output of fdisk -l show both your hard drives when connected as I mentioned, especially the partition table of your Windows drive as hdb?

Yes, I'm not sure if you can just change the grub entry to get Dapper to boot as the slave drive(hdb), since Dapper was evidently installed when the drive was connected as hda...I'm not sure if Dapper would automatically recognize and change the mountpoints in /etc/fstab from hda to hdb.  If not, you "may" be able to manually change it and get it to work, I don't know.

Possibly, if you set bios to boot first from the slave drive, that may maintain Dapper as hda?

Don't suppose there is a problem with the IDE cable?

Good luck...wish I could assist more.  It may help if you could possibly post the output of *fdisk -l*...someone may be able to diagnose what could be wrong if you can.

You might want to try GAG bootloader:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)
or Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by bparham on 2006-08-18
This gives me some ideas, I thought about the cable, but it recognizes the Dapper drive as slave when connected, the system just won't see the XP drive when connected as slave. I just can't get grub to load when it is hooked up as slave.  

I have not tried booting from the Live CD yet. I was hopeful that I could simply change all the registry entries from (HD 0,0) to (HD 1,0), but that didn't work. My next step is booting from the Live CD to check fdisk. I'm hopeful that I will be able to see the Dapper Drive that way. 

I'm not familiar with GAG Bootloader and Super Grub Disk, what do they do?

---

### Post by confused57 on 2006-08-18
I have Dapper as the master drive and Windows as the slave drive, here's the output of "sudo fdisk -l":

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+  83  Linux
/dev/hda2            1217       19331   145508737+  83  Linux
/dev/hda3           19332       19457     1012095    5  Extended
/dev/hda5           19332       19457     1012063+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1           4       32098+   6  FAT16
/dev/hdb2   *           5       14589   117154012+   7  HPFS/NTFS

Here's the /boot/grub/menu.lst I need to boot Windows:
```
title           Windows
rootnoverify    (hd1,1)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

On my slave drive, hdb1 is a dell utility and hdb2(hd1,1 in grub) is my Windows partition.
Hope this helps.

---

### Post by bparham on 2006-08-19
I live CD to boot and ran fdisk, here was my output.

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131   de  Dell Utility
/dev/hda2   *           6        4392    35238577+   7  HPFS/NTFS
/dev/hda3            4393        4862     3775275   db  CP/M / CTOS / ...

Disk /dev/hdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4676    37559938+  83  Linux
/dev/hdb2            4677        4863     1502077+   5  Extended
/dev/hdb5            4677        4863     1502046   82  Linux swap / Solaris

---

### Post by confused57 on 2006-08-19
I'm running out of ideas here, but if you're able to boot both the Windows and Dapper drives when each is connected as the master drive by itself...you "should" be able to connect the Dapper drive as master and Windows drive as slave and boot Windows with the exact same /boot/grub/menu.lst Windows entry that I use(see my last reply).

You might want to read back over the link I gave you previously:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by bparham on 2006-08-19
You are right, I should, however, the BIOS for my Dell simply doesn't see the Windows XP drive when it is connected as a slave. I thought it was the cable, but when the drives are connected the other way, the Windows as the Primary, Dapper as slave it sees the drive. 

I have thought that my jumper pins were set incorrectly, and have tried every combination I can think of, and am simply out of ideas.  I'm going to try another post under the installation area, hopefully someone will have an idea. I'm beginning to get tired of switching cables everytime I want to boot Dapper.

---

### Post by baylorbear on 2006-08-19
I realize I'm jumping in on a well-ongoing thread here -- BUT, thought I'd offer my two cents worth.

I just recently set my box up the same way you're wanting to do.  At first I was concerned about letting Ubuntu (slave) re-write the boot record on my Windows drive (master).  I went ahead and let it do a "regular" install on the slave drive though, because I realized I could just pop in my Windows XP CD and repair the boot record (and boot to Ubuntu via floppy for the repair) in the case that it failed.  

Install went flawlessly, though, and I can successfully boot to either Ubuntu or Windows from GRUB at system start.

---

### Post by bparham on 2006-08-20
The problem is that I don't have a restore disk for XP. There used to be a way of creating your own Restore Disk/CD, however I can't seem to find that in XP Pro. Any ideas?

---

### Post by bparham on 2006-08-20
Hallelujah!!! I got it figured out.

---

### Post by confused57 on 2006-08-20
> **bparham said:**
> Hallelujah!!! I got it figured out.

Good to hear you got it working...what was the solution, if I may ask?  May help someone else with the same problem.  Thanks for checking back in with the good news.

---

### Post by bparham on 2006-08-21
I'll post the solution later this evening.

---

### Post by bparham on 2006-08-21
I'm not really sure why it is that this worked, but it did. 

```
title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot
```

Even though the Dapper drive is clearly in the slave position I had to leave the root location as (hd0,0). The change occurred in the kernel line where I changed the device to hdb1 from hda1.

---

