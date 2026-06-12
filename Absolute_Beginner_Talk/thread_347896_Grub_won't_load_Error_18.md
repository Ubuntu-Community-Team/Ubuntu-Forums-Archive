---
title: "Grub won't load Error 18"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Fanfayer on 2007-01-27
After 15 years of doing PC support for various companies, I finally am in a possition with my current employer to learn Linux. After doing some research and speaking with the network group at my office I decided on Ubuntu for simplicity. 
I have an older HP Netserver E45 and installed a 20G hdd in conjunction with the SCSI array. This was no brainer.

When I installed Ubuntu, everything seemed to go fine. When I restarted the system I get the following screen:

Grub Loading Stage1.5.
Grub Loading, Please Wait....
Error 18

The computer stops. It will not soft reboot or respond in any way to inputs. I have to power down and restart. 

I have a book about Ubuntu and it recommended restarting the install program but use the "REPAIR" option at the startup screen. I followed the steps, rebooted and still the same error.

I currently have Server 2000 on the SCSI Array, but that doesn't seemed to be affected. It seems that it did this when I tried to use Ubuntu's dual boot loader in order to select my server or Ubuntu.

Please help!:confused:

---

### Post by thelocust on 2007-01-27
[B]
I am no expert but I believe it has something to do with using SCSI HDD's. Does GRUB load up and let you select an OS or does it fault out as its loading.


[/B]

---

### Post by Fanfayer on 2007-01-28
I disconnected the SCSI drives and still get the same error message. I think it has more to do with the fact that I was trying to make it dual boot between Ubuntu & Win 2000 Server.

---

### Post by LKRaider on 2007-01-28
Google says error 18 means:
```
Selected cylinder exceeds maximum supported by BIOS
```

So it could be your partitioning scheme puts /boot beyond where your BIOS can read at boot time.

One solution would be to repartition and put a /boot partition preferably at the beginning of the disk.


links:
[http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)
[http://www.debianhelp.org/node/1479](http://www.debianhelp.org/node/1479)

---

### Post by Fanfayer on 2007-01-28
That is entirely possible. I did get a message when loading Ubuntu that it wanted to know if I wanted to keep the information that was on the hard drive, etc. I thought I selected for it to wipe the hard drive and use the whole drive as 1 partition. It may not have. I will try to reinstall tomorrow and remove all the old partitions and let Ubuntu use the entire hard drive.

---

### Post by tagginannie on 2007-01-28
> **Fanfayer said:**
> After 15 years of doing PC support for various companies, I finally am in a possition with my current employer to learn Linux. After doing some research and speaking with the network group at my office I decided on Ubuntu for simplicity. 
I have an older HP Netserver E45 and installed a 20G hdd in conjunction with the SCSI array. This was no brainer.

Grub Loading Stage1.5.
Grub Loading, Please Wait....
Error 18

The computer stops. It will not soft reboot or respond in any way to inputs. I have to power down and restart. 

I have a book about Ubuntu and it recommended restarting the install program but use the "REPAIR" option at the startup screen. I followed the steps, rebooted and still the same error.

I currently have Server 2000 on the SCSI Array, but that doesn't seemed to be affected. It seems that it did this when I tried to use Ubuntu's dual boot loader in order to select my server or Ubuntu.

Please help!:confused:


 GRUB does not distinguish between ide and scsi drives. it number drive in this order
(hd0,0) for hda1 and so on. To fix the problem you don't have to reinstall you can try 
_[Super Grub]("http://supergrub.forjamari.linex.org/")_ or the [U][Grub live CD]("http://gparted.sourceforge.net/livecd.php")
[/U]. 

Suzy:KS

---

### Post by Fanfayer on 2007-01-29
I tried as you suggested the Super Grub and Grub Live CD. Neither one worked. I have tried to reinstall Ubuntu after deleting all partition, letting Ubuntu automatically partition and work with the hard drive, but to no avail. I get the same error message. I was going to try and flash my BIOS, but apparently the FDD Controller has expired over the years and no longer recognizes the floppy. I may work on this some more and see if I can get it working somehow.

I am about ready to try it on a different system, but the funds have to be there first.
I guess I am just going to have to wait awhile.:(

---

### Post by petroskhan on 2007-01-29
Just yesterday, I was installing 6.06 on a friends computer, and after the install I got the same error.  I looked it up and found that error 18 is caused when your BIOS does not or can not recognize a disk size greater than 8 GB.  What I did then was re-installed, making the boot sector of the drive 5.5 GB, and then set the rest of the drive as an extended partition.  Now, the system WILL boot up, and I can get to the desktop, ie, a full boot, the OS starts, etc.  The only problem is, I can't see the "extended" partition.  Not sure what is going on there, but I am still checking; so I think the solution is to set a boot sector of a small size, then some how set up the rest of the drive as another Ubuntu-recognizable partition...just not sure how to do the second part there.  Anyone else know how?  I've solved the first part of the problem, just need to get the second part done.  :)  Thanks...

---

### Post by Afoot on 2007-01-29
> **petroskhan said:**
> What I did then was re-installed, making the boot sector of the drive 5.5 GB, and then set the rest of the drive as an extended partition.
What? You made a 5.5 GB /boot partition?

---

### Post by petroskhan on 2007-01-29
Well, yeah.  The info I found said that with the BIOS not recognizing the large drive (160 GB), I needed a partition smaller than 8 gigs, which I did.  Before doing this, on boot up, the BIOS was only recognizing 8 gigs anyway, so I needed to do something.  That part worked, Ubuntu now starts, I just can't access the rest of the drive.  I need to figure that part out.

---

### Post by petroskhan on 2007-01-29
Possible correction...is there a difference between the boot sector and the root sector?  That's the one I made 5.5 gigs...the root.  That's the one the info I found said had to be less than 8.

---

### Post by LKRaider on 2007-01-30
That is what I was trying to say on my previous post: the **/boot** needs to be at the beggining of the disk. It won't work to create one huge partition (as the installer does by default), because you don't know where the kernel is going to land inside that huge space (that's the critical part).

Try this partition layout:

**/boot** (~100mb)
**/**  (the root partition - as much as you need, 10gb is good default)
**/home** (user storage, can take rest of disk, except for swap space which is next)
**swap space** (1gb is a good default. change as needed)

The really important part here is the /boot at the start of the disk, where will be placed the system kernel that grub needs to access on boot.

After the kernel is initialized, you should have no more problems with BIOS access limitations, since it takes over from there.


Oh, and just to be sure, enter your BIOS and enable the LBA option for the harddrives (if it isn't already, and if available at all).

---

### Post by Fanfayer on 2007-01-31
At the end of your message you mention one of the most important BIOS Setups for this kind of problem, LBA! For those who don't know what this is, it is Large Block Access. It was a work around for most BIOS manufacturers in the mid to late 90's when hard drive sizes started growing exponentialy. The problem I have is my BIOS doesn't support LBA mode for IDE devices. This is mainly because it is a server that is designed to run SCSI Drives which don't use LBA. This is where I am running into problems. I do have a smaller hard drive that I am going to give a try loading Ubuntu on and see how things go from there. Since the floppy controller on my server has died and won't recognize the floppy any more so I have no way to flash the BIOS even though there is a newer version that could resolve everything available from HP.

---

### Post by dru2 on 2007-01-31
I got the same problem.

Also when I went to install, 2nd step, change time.  If I try to adjust the time, the install program gets frozen and the buttons on step 2 dont work.  Cant close that proggy, just reboot.

Now error 18.

WTF.

This is the same sh*t I got when I first used redhat 5.0 about 9 years ago.  Nothin has changed. what a goddam waste of time.:( :( :( :( :(

---

### Post by LKRaider on 2007-01-31
If you have a BIOS update available, focus on getting that working. It is really the best way to deal with these kind of issues. It is a waste of time trying to find workarounds when the best solution is already available.

If you can't boot from a floppy, make a boot CD with Grub (you already have this), get [memdisk]("http://syslinux.zytor.com/memdisk.php") from syslinux and a floppy image from [bootdisk.com]("http://s93616405.onlinehome.us/bootdisk/drdflash.zip"). With this you can boot into DOS and use the flash utility you have.

---

### Post by Fanfayer on 2007-02-01
> **LKRaider said:**
> If you have a BIOS update available, focus on getting that working. It is really the best way to deal with these kind of issues. It is a waste of time trying to find workarounds when the best solution is already available.

If you can't boot from a floppy, make a boot CD with Grub (you already have this), get [memdisk]("http://syslinux.zytor.com/memdisk.php") from syslinux and a floppy image from [bootdisk.com]("http://s93616405.onlinehome.us/bootdisk/drdflash.zip"). With this you can boot into DOS and use the flash utility you have.

The problem is that the system doesn't support this method of flashing the BIOS. Per HP, the system has to be booted from the floppy that contains the BIOS upgrade. It is a self installing program and can't be run from a DOS prompt. If that were the case, I would have already made a bootable rescue CD and updated the BIOS. If you remember from my initial post, I have been a hardware tech for 15 years now and also a certified HP Technician. There are some workarounds that just don't work in certain circumstances and this is one of them. I have installed a 4.3GB HDD and I am working on installing Ubuntu on it right now.

---

### Post by LKRaider on 2007-02-03
You could probably try making an image (dd) of the HP BIOS flashing disk and booting it through memdisk.

---

### Post by dudz5150 on 2007-02-04
Hey guys, I've got the same error 18, and I'm sited in front of the computer something about 3 hours...

And, I know it will sound very strange, but in a anger flash moment I was pressing anything in the keyboard... suddenly  the Grub started to run fine, and the Ubuntu is running. 

I think that I've pressed something like alt+1, or ctrl+alt+1. Something like we do to access the others desktops in linux. 

Well, I'm just telling this, cause it could help. Or could not. But it was interestanting... I'll try it again tomorrow, to put here the real-magic-key-combination. Now, I need rest!  

That's I've not followed in the computer career... There's some strange stuff like that! 
:)

---

### Post by rumli on 2007-02-14
Try booting into recovery mode (via the GRUB menu) and then commenting out the "savedefault" line in your /boot/grub/menu.lst.  That's what worked for me.  
[http://ubuntuforums.org/showpost.php?p=2156493&postcount=3]("http://ubuntuforums.org/showpost.php?p=2156493&postcount=3")

---

