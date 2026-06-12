---
title: "Need more disk space for Ubuntu .... what are my options?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-06-05
I need more disk space for Ubuntu -- what are my options?

I've got a Windows NTFS partition followed with Ubuntu.  I like Ubuntu a lot and it is my primary partition.  I would like to keep my Windows partition just in case - but I must admit, I now rarely boot in Windows XP anymore -- I've about solved my Windows adiction :-)

What if:

  1- I install a dedicated Ubuntu hard drive.  How can I copy my current Ubuntu setup to it?  How about the Grub boot menu - what do I need to make it work with the new hard drive?

  2- Can I non-destructively shrink my NTFS partition and then non-destructively increase my Ubuntu partition?


I've gotten Ubuntu configured the way I want it and don't want to reinstall - the main reason is that I did not document what I have installed and how I configured things.

Thanks

Carl

---

### Post by DeadEyes on 2007-06-05
I was in the same position as you, and I went for option 2.
It is possible to non destructively shrink NTFS and grow ext3. I downloaded the GParted liveCD to do it.
Now I am not going to tell you how to do it becuase I am not 100% confident that I could. Even if everything is done properly there is still the chance of ruining one or both of your installations. When I did it I wasn't to pushed if I had to end up doing a reinstall.
What you want to do is quite common and you should be able to find plenty of help out there.

---

### Post by Zzl1xndd on 2007-06-05
had the same kinda problem, but I just set it up so I could write to NTFS and use the windows partition as I would anyother.

---

### Post by cwmoser on 2007-06-05
What would happen if I used Ghost to clone my 20GB Ubuntu partition to an 80GB hard drive?
I would think that Grub would need some tweaking.

Carl

---

### Post by dwblas on 2007-06-05
You don't really have to clone the Ubuntu Paritition.  Just use the 80 gig drive for /home or any other directory(ies) that contain a lot of data.

---

### Post by Inxsible on 2007-06-05
This poses a problem if you have the windows partition before the ubuntu partition. Even if you shrink your windows, the extra space will be between windows and ubuntu. If you are going to create a completely new partition out of the freed space..you will be OK. but if you plan to merge the freed space into an existing partition, i think it would be difficult and tedious.

Many ppl have had trouble merging free space to latter partitions

---

### Post by p_quarles on 2007-06-05
I'm looking into doing the same thing (never anticipated how rarely I would use Windows). I'm guessing, based on what Inxsible said, that the best thing to do would be to shrink the Windows partition and use the free space to create a separate ext3 file system? Are there any risks to this, beyond what would apply to all partition management? 

Also, I've only used gparted in guided mode, so perhaps someone would suggest an ideal way of doing this. Do I use the gparted boot disk, or can I do this from within linux?

---

### Post by goatflyer on 2007-06-05
dwblas has the right idea.  Forget monkeying with partition tables to try to squeeze more space, its only a matter of time before you fill what litttle you manage to steal from winxp.

get a 2nd hard drive, format it ext3, bring up ubuntu, mount the 2nd drive somewhere (/mnt/temp springs to mind), copy all your /home files to the new filesystem.  Then umount it and finally mount it on /home.  You can test this safely by not making any changes to /etc/fstab or any other of your system files until you prove that everything works fine with the 2nd drive.

sorry if the above description is too dense, I am trying to give an overview.   If you need help doing any of the steps, just ask.

---

### Post by Inxsible on 2007-06-05
You can use the GParted that comes on your install CD. or download a live CD of Gparted itself -- best partition program that i have come across !!!

---

### Post by cwmoser on 2007-06-06
I'm leaning toward the safer approach and just copy my Ubuntu to another Hard Drive.

What are the details to Ghost clone my current Ubuntu to another hard drive?

I would want a bigger paritition.  What would I have to do to the boot block on this new hard drive so that Ubuntu would boot?  Be nice to use the existing Grub so I can boot Windows when I want to.

One of the main reasons I want to go with a bigger partition is because I currently have 20GB with 1 GB free.  And, I want to play with vmplayer virtualization and I have no idea how much disk space that will take.

Thanks

Carl

---

### Post by kyphi on 2007-06-06
The option I would choose is to install a second hard drive and reinstall Ubuntu.

I was surprised to read that you have used nearly all of 20 Gb for Ubuntu.
One option you might like to consider to free up some space is to transfer some of your files to a CD or DVD or an external hard drive.  A collection of music files can get rather large as does a collection of video files.  Programme files are not large by comparison.

An installation of Ubuntu onto a second hard drive presents no problems with GRUB which will simply overwrite your existing boot menu (after asking you, of course).

I currently run two hard drives, one for Ubuntu and the other for XP.  The XP installation is for gaming only.
One reason for two hard drives is that if one hard drive fails (and they do sometimes and often without warning) I have access to another operating system.  As well as that, gaming is hard on hard drives and if a drive were to fail I would rather that it be the XP installation.

Unfortunately small hard drives are hard to find since capacities have reached outlandish levels.  A capacity of 12 Gb for XP if used solely for gaming is sufficient.  The installation of XP takes about 2 Gb, plus a few Gbs for the game, plus a few Gbs for the dynamic paging file (used to be called swap file in days of old).

---

### Post by Old Pink on 2007-06-06
9 months ago I shrunk my NTFS and it corrupted beyond repair, wouldn't even state free space etc. in GParted, never  mind mount/boot.

Reformatted entire hard drive and been 100% Ubuntu for 9 months now.

My 6 month story hit the top of Digg: [http://www.mbhoy.com/22-02-2007/six-months-on-pure-linux](http://www.mbhoy.com/22-02-2007/six-months-on-pure-linux)

Never looked back. Could've reinstalled XP fresh & legal any day since then. Don't want to. Don't even think about it.

---

### Post by tk03759 on 2007-06-08
> **goatflyer said:**
> dwblas has the right idea.  Forget monkeying with partition tables to try to squeeze more space, its only a matter of time before you fill what litttle you manage to steal from winxp.

get a 2nd hard drive, format it ext3, bring up ubuntu, mount the 2nd drive somewhere (/mnt/temp springs to mind), copy all your /home files to the new filesystem.  Then umount it and finally mount it on /home.  You can test this safely by not making any changes to /etc/fstab or any other of your system files until you prove that everything works fine with the 2nd drive.

sorry if the above description is too dense, I am trying to give an overview.   If you need help doing any of the steps, just ask.

How would you go about copying the home folder to the drive? I usually get an error about permissions:

"sudo cp /home /media/temp
cp: omitting directory '/home' "

or using nautilus: "/home/andr...Xauthority" cannot be copied because you do not have the permissions to read it."

Also, thinking ahead, would mounting the drive as /home be as simple as "sudo mount /dev/hdd1 /home" ?

---

### Post by Lakefall on 2007-06-08
> **cwmoser said:**
> I install a dedicated Ubuntu hard drive.  How can I copy my current Ubuntu setup to it?  How about the Grub boot menu - what do I need to make it work with the new hard drive?
Copying/moving the root of your Ubuntu system onto a different partition/drive is fairly simple. I did it recently. I think it's a good idea not to try to do it to a running system, so have a live-CD at hand. It probably can be done to a running system, but using the CD seems less hazardous to me. I had some difficulty with the Grub, otherwise it was a walk in a park.

**Preparation** (You do not need the live-CD yet.)
[list=1]
[*]Physically install the new drive into your system and figure out which device it shows up as.
[*]Partition it appropriately and take note of which devices the partitions show up as. (Use *cfdisk* or whatever to partition. Be absolutely certain you are partitioning the correct drive.)
[*]Create filesystems on the partitions. (Use *mke2fs -j* or whatever and *mkswap* if needed. Be absolutely certain you are operating on the correct partitions.)
[/list]
**Copying**
[list=1]
[*]Shut your system down cleanly (reboot is fine) and boot with the live-CD.
[*]Mount the partitions you are copying from and the partitions you are copying to.
[*]Use *cp -a* as root to copy everything. (It's recursive, see *man cp* for details.)
[/list]
**Configuration**
[list=1]
[*]Edit /etc/fstab on its new partition so that correct partitions will be mounted on the new system. (Try not to accidentally do this on the old partition. ;-)) Make sure you know how to edit the fstab.
[*]Edit /boot/grub/menu.lst on its new partition appropriately. (Try not to accidentally do this on the old partition, either.) Make sure you understand Grub and know how to edit the menu.lst. I don't. ;-)
[*]At this point your old system should still be fully operational and bootable, just pointing it out.
[*]Try to figure out a way to get the Grub use the menu.lst on the new partition instead the old one. One way which should work is to boot (without the CD) and hit Esc at the Grub to get the menu and hit e (AFAIR) to edit the boot parameters and change them to tell the kernel to use the new partition as root and then run grub-install and update-grub as root on the new partition, I think. You should know as you figured Grub out in step 2 above. ;-)
[*]Make sure Grub isn't using any of the old partitions and they are not mentioned in the new fstab before you get rid of the old partitions and reboot once more just to make sure everything still works.
[/list]

---

### Post by Lakefall on 2007-06-08
> **tk03759 said:**
> "sudo cp /home /media/temp
cp: omitting directory '/home' "
Your problem is that command isn't recursive. The command ```
cp -r /home /media/temp
``` would copy, but mess up the permissions and symbolic links (if any). You should use ```
cp -a /home /media/temp
``` which is the same thing as ```
cp -dpR /home /media/temp
```

See ```
man cp
``` for details.

---

### Post by tk03759 on 2007-06-08
I wound up loggin in as root in the GUI and doing it that way. Thank you. I'll probably use this on my other computer to make sure it doesn't run out of space.

---

### Post by stchman on 2007-06-08
> **cwmoser said:**
> I need more disk space for Ubuntu -- what are my options?

I've got a Windows NTFS partition followed with Ubuntu.  I like Ubuntu a lot and it is my primary partition.  I would like to keep my Windows partition just in case - but I must admit, I now rarely boot in Windows XP anymore -- I've about solved my Windows adiction :-)

What if:

  1- I install a dedicated Ubuntu hard drive.  How can I copy my current Ubuntu setup to it?  How about the Grub boot menu - what do I need to make it work with the new hard drive?

  2- Can I non-destructively shrink my NTFS partition and then non-destructively increase my Ubuntu partition?


I've gotten Ubuntu configured the way I want it and don't want to reinstall - the main reason is that I did not document what I have installed and how I configured things.

Thanks

Carl

How big is the hdd you have Ubuntu and XP installed on?

In my experinece Ubuntu only needs about 6G to work with.

Yes the liveCD can resize NTFS partitions.  Just boto up the liveCD, run gparted and select resize on the NTFS partition.

I woudl recommend you run a defrag chkdsk /f on all NTFS partitions.

---

