---
title: "Moving Ubuntu to a new drive."
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-02-05
After installing Ubuntu (plus KDE) and deciding I'd like to stay with it, I want to transfer the system to another larger partition. I originally created a 9GB system partition, a 4gb /home partition (both are close to half used and I've only had Ubuntu for 4 weeks!), and a 750mb /swap partition. I have a 36gb Fat32 partition that I can dedicate around 30gb to Linux (which I would reformat to EXT3) , keeping about 6gb for files registered with Windows. Eventually, I want to use Linux for most everything and shrink windows down to the bare minimum need for the few apps that need it. 

So, can I keep the present installation and move it to the new drive? Or will I need to install to the new partition and reinstall and reconfigure Ubuntu from scratch? 

Also, I was thinking of give the existing ext3 partitions to /home for ~16gb and give 29GB to the system with a 1gb swap. Or would it be better to give /home the larger partition and run the system off the 15-16gb partition? In other words, which needs more space, /home or the system files?

---

### Post by kebes on 2007-02-05
It can be done, and you have different options.


1. One way would be to install Ubuntu onto the bigger drive. Once that's done, you can then overwrite it with your previous install. This will mean that all the config files and installed software will be back in place. As long as you are careful to maintaing ownership and permissions during the copy, it should work.

2. You could also just copy the old partitions to the new partitions, making sure to maintain permissions. You would then have a nearly functional system... but you would have to manually install the bootloader onto your new hard drive.

3. You could also boot into a LiveCD and use partimage to make backup images of your partitions ([System Rescue CD]("http://www.sysresccd.org/Main_Page") has partimage installed automatically). Then you could restore these images to the appropriate partitions on the new hard drive. This makes sure that things like permissions are maintained. You will still have to install the grub bootloader manually.

4. You could install Ubuntu on the new drive, and then just copy over your "/home/" folders. This directory keeps all your personal files and most config settings (at least for user software). You would still have to re-install missing apps, but once done your preferences would already be set (including firefox bookmarks, etc.).


Hope that helps.

---

### Post by click4851 on 2007-02-05
I did something similar, in that I basically moved my entire system on to a bigger drive. I used the Gparted Live cd. Worked very slick, very intuitive. When I was done copying partitions I physically swapped the drives making sure to set the drive as master with those little jumpers. I would try that first.

---

### Post by kebes on 2007-02-05
> **Patrick K said:**
> Also, I was thinking of give the existing ext3 partitions to /home for ~16gb and give 29GB to the system with a 1gb swap. Or would it be better to give /home the larger partition and run the system off the 15-16gb partition? In other words, which needs more space, /home or the system files?

Obviously it depends on your usage habits. (Do you tend to accumulate lots of big data, like video files? ... or do you tend to install tons and tons of software?)

I personally would make /home/ bigger than the system files (the root directory, /). On my computer, the root directory is only taking up 5 Gb, even after installing lots of software. My /home/ directory contains all my music, videos, personal files, etc. These take up **much **more space, at least for me.

So I would invert them: 15 Gb for /, 1Gb swap, and 30 Gb for /home/

---

### Post by Patrick K on 2007-02-05
> So I would invert them: 15 Gb for /, 1Gb swap, and 30 Gb for /home/

Since I'm recording live music and those files get huge, I think I'll go with your recommendation. Of course, they can be saved to the FAT32 partitions, of which I have a number. But keeping them on EXT3 has some advantages. 

> I did something similar, in that I basically moved my entire system on to a bigger drive. I used the Gparted Live cd. Worked very slick, very intuitive. When I was done copying partitions I physically swapped the drives making sure to set the drive as master with those little jumpers. I would try that first.

I was thinking Gparted would work for doing this. However, the drives are installed and swapping them is not happening. Given the above partition usage, I figure I can move /home to the new partition and give the existing /home and swap space to / (the system). Of course, the partitions will likely get renamed so I'll probably have to edit Grub's files.

> 3. You could also boot into a LiveCD and use partimage to make backup images of your partitions (System Rescue CD has partimage installed automatically). Then you could restore these images to the appropriate partitions on the new hard drive. This makes sure that things like permissions are maintained. You will still have to install the grub bootloader manually.

This looks like the best option. Since I have decided to keep the system on it's existing partition, hopefully expanding it to include the now /home partition, I'd be moving the /home files only. Unless, of course, something keeps me from combining the /home and / partitions. IIRC, swap lies between them so this might be an issue. I'll just have to fire up gparted and take a look.

---

### Post by Patrick K on 2007-02-08
I had mixed results with revamping the partition structure to give Ubuntu more room to grow. After backing up / and /home and the relevant windows partitions (this took quite a while, maybe two hours), I loaded up the livecd and went to work with gparted. A quick tip before backup a system, make sure the trash is dumped (I had some 1.1gb setting there) and uninstall any apps you don't want. 

I was unable to shrink the size of the partition I want to use. I kept getting errors about the file system reporting the incorrect size. I planned on shrinking a 36gb FAT32 partition to 6gb and use the new space for /home. Then giving the existing /home space to / for a total of about 13gb. After several attempts, no go.

On to plan 2. This time I was able to shrink the partition that I stole space from for the original Ubuntu installation. Instead of having a 30gb /home partition I now have a 15gb partition. The / partition ended up around the same sized as planned. I also enlarged swap to 1gb from 750mb. 

However, I didn't think about gparted give the new partitions different names and, AFAIK, there was no way in advance to know what those names might be, so there was no way to pre-edit menu.lst. / changed from hda8 to hda11, which caused GRUB to choke. After spending an hour or more with SuperGrub I finally got the system up and running with, so far, everything working as before. Windows seems happy, too.

Man-O-man, that livecd is slow!!!!!!!!! Total time for a rank beginner, about 6 hours. 

Thanks for all the help. I hope to reciprocate as I learn more.

---

### Post by vascotia on 2008-06-25
The easiest way to do this is with a dump/restore action.

Just put the new harddrive in the system, boot your Ubuntu installation as usual, then partition (e.g. cfdisk or any other partitioner) and create new filesystem of the new harddrive as planned.

*mkfs.ext3 /dev/sdX * 

Where X is the partition number and assuming you have a SATA drive, use hdaX in case of IDE.

Mount the new harddrive's root partition to /target

then change directory to the newly mounted harddrive
*cd /target*
*/sbin/dump 0ufb - 10 /dev/sda1 | restore -rf -*

Where sda1 is the current harddrive's root partition containing the current/existing installation (Could be different in your case ofcourse).

When you execute this command WHILE being in the newly mounted (/target) harddrive's root partition, it will mirror the content to the new harddrive.

After this, just reconfigure your GRUB bootloader..

*grub-install --root-directory=/target /dev/sdX*

Where X is the new harddrive.

Reboot and enjoy.

Cheers,
Vascotia

---

