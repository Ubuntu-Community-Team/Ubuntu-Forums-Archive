---
title: "Boot loader issue with MacBook Pro 5,1 Ubuntu install"
date: 2010-05-20
forum: Apple Hardware Users
---

### Post by wartron on 2010-05-20
I tried to install Ubuntu on my Macbook Pro 5,1 today. I had problems before, so I 0'd out my drive, reinstalled OS X, installed rEFIt, partitioned my HD, erased the windows partition with the disk utility, and got all the way to the installation. However, when I choose Advanced Options towards the end of the install dialogues, where I'm supposed to choose a dev/ option, there is a repeat.

ie.
Options:
dev/sda-1
dev/sda1
dev/sda2 <- I think this is the OS X partition
dev/sda-1

As a result, I can't choose sda-1. When I erased the boot camp partition through GParted, it was listed as dev/sda3. What should I do? I don't want to eff up my partition tables. Any suggestions?

---

### Post by 24601oxy on 2010-05-20
Wow, um, I'm having a pretty much identical problem, on a MBP 6,2

I followed [these]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation") instructions, and got hung up there, with the same dialog. Couldn't select install GRUB on sda3. 

I just continued installing without installing GRUB, but there is no option to boot into ubuntu. Anyone know a way of adding it now? Should I just delete that partition and try again?

---

### Post by wartron on 2010-05-21
this is totally driving me crazy. someone out there has to have an idea or SOME form of advice...

---

### Post by linuxopjemac on 2010-05-22
Just read a few installation manuals, which worked for other people. There is much info about this subject on [http://mac.linux.be](http://mac.linux.be), a place to bookmark.

---

### Post by jamesixgun on 2010-05-22
Here's the work-around (cross-posted from another thread on Page 1). I hope this helps!

Ok. I had the same problem as all of you seem to have, but fixed it thanks to another thread in this forum. 

Rather than link directly, I'll post the workaround here, though your mileage may vary.

1. Start out by backing up your mac to an external drive. 
2. Install ReFIT. (restart two times, and it will take effect).
3. Open Boot Camp and set up a windows partition.
4. Shut down and boot into the Lucid install disk.
5. Select the option to try linux without installing (ie. boot into the live CD).
6. Open gparted (System > Administration)
7. Use gparted to delete the boot camp partition. 
8. Remain in gparted, and create a tiny partition just after the mac partition (512M should be plenty). Name it BOOTCAMP or something memorable and set the file system as NTFS.
9. Apply changes. (BE SURE TO APPLY CHANGES.) Then exit gparted.
10. Start the Lucid installer from the desktop. Follow the locations and language and whatnot. When it asks you to prepare the disk, choose "Specify partitions manually."
11. Select the partition you just created (which should be /dev/sda3) , choose Change --> use as NTFS. At Check Format choose mount point = /windows. 
12. Select the free space. You'll need to create two partitions here, one for Ubuntu, and one for Swap at the end. I set upFor the first partition, choose Use as Ext4, mount point = / . In the remaining section (I used 4096 bytes, ie. 4 Gig) choose Add --> use as Swap. Click ok.

If everything worked as expected, you'll have 5 partitions: sda1 (EFI); sda2 (OSX); sda3 (NTFS); sda4 (where Ubuntu will go); and sda5 (the swap).

13. Go through the rest of the installation. On the last screen (screen 8, iirc) click the Advanced button and choose to install the boot loader to /dev/sda3, which should now appear. 

Click Install and wait 20 or 30 minutes while Ubuntu installs.

14. when the installation is complete, restart. In the rEFIt menu, choose the partition tool and resync. 
15. Power down your computer.
16. Power up and you should be just fine.

If you're not dual-booting, you should still choose to set up a special partition for GRUB, since it will whack out your EFI even if Ubuntu is the only thing there. (Get into the live CD, go gparted, wipe the drive, set up a partition for GRUB, one for Ubuntu, and one for the swap, and be sure to install GRUB in dev/sda2/ instead.)

Good luck! I hope this works out for everyone. It worked brilliantly on my revA Macbook (1,1), and I'm typing this from the Mac partition.


Oh. And I just realized that I have my notes from my install, and they include a link to the [thread]("http://ubuntuforums.org/showthread.php?t=1468240&page=5") where I originally found this. All credit goes to Jacques4x4 who originally developed this method.


Edit: I'm now on the Ubuntu partition, and realized that I forgot to mention one small thing. When you start up Ubuntu via rEFIt, the GRUB will assert itself and give you some additional boot options (straight Linux, safe Linux, shutdown, OSX, and something else, if I recall). GRUB will automatically boot into Ubuntu after 10 seconds, or you can just hit 'return' and boot right into Ubuntu. Not a big deal, to me, but those of you who really value your boot up times may want to search for a way to teach GRUB to shut up.

---

### Post by wartron on 2010-05-24
Oh my god, worked perfectly. Thank you sooooooooooooooooo much. :P

---

### Post by GreenLeafz on 2010-07-17
Baffles me, i thought the boot-loader had to always be installed on the same partition as ubuntu. In-fact i have successfully dual booted Hardy Heron on mac and when installing i put the Boot-loader onto the same Partition as Hardy Heron and it worked a treat. Although i discarded Hardy in the end. Then i switched to Lucid Lynx hoping for a better distro, but it wouldn't boot into it after the install, it just said GRUB in the top left of a black screen with a flashing cursor.

Frustrated but not going to give up, i wiped my whole hd and just installed Lucid Lynx to see what it was like. Now i have wiped my HD all over again and am back on just snow leopard but even more determined to try again and dual boot. I have just tried again but this time hit the same snag you guys have had, being, after selecting install on largest continuous free space (which it stated in the ubuntu guide) and then clicking the advanced button i was unable to select /dev/sda3 as the bootloader, /dev/sda3 wasn't even in the list, which thinking about it makes sense because it hasn't been assigned to anything, it is just free space. SO WHY ON EARTH WAS THAT TUTORIAL EVEN WRITTEN AND PUBLISHED? GOD only knows.

---

### Post by JohnAtilano on 2010-07-18
I had the same problem as you.  First time I installed Lucid I shose /dev/sda and nuked my hard drive.  Decided to try a different distro because I was so pissed at Ubuntu.

I did a full write up with pics on my blog.  Although it outlines installing Linux Mint, the process is exactly the same for Ubuntu.  Hope it helps.

[http://johnatilano.com/dual-boot-mac-os-x-and-linux-mint-9-on-a-macb]("http://johnatilano.com/dual-boot-mac-os-x-and-linux-mint-9-on-a-macb")

---

### Post by nadams1073 on 2010-10-07
> **jamesixgun said:**
> Here's the work-around (cross-posted from another thread on Page 1). I hope this helps!

Ok. I had the same problem as all of you seem to have, but fixed it thanks to another thread in this forum. 

Rather than link directly, I'll post the workaround here, though your mileage may vary.

1. Start out by backing up your mac to an external drive. 
2. Install ReFIT. (restart two times, and it will take effect).
3. Open Boot Camp and set up a windows partition.
4. Shut down and boot into the Lucid install disk.
5. Select the option to try linux without installing (ie. boot into the live CD).
6. Open gparted (System > Administration)
7. Use gparted to delete the boot camp partition. 
8. Remain in gparted, and create a tiny partition just after the mac partition (512M should be plenty). Name it BOOTCAMP or something memorable and set the file system as NTFS.
9. Apply changes. (BE SURE TO APPLY CHANGES.) Then exit gparted.
10. Start the Lucid installer from the desktop. Follow the locations and language and whatnot. When it asks you to prepare the disk, choose "Specify partitions manually."
11. Select the partition you just created (which should be /dev/sda3) , choose Change --> use as NTFS. At Check Format choose mount point = /windows. 
12. Select the free space. You'll need to create two partitions here, one for Ubuntu, and one for Swap at the end. I set upFor the first partition, choose Use as Ext4, mount point = / . In the remaining section (I used 4096 bytes, ie. 4 Gig) choose Add --> use as Swap. Click ok.

If everything worked as expected, you'll have 5 partitions: sda1 (EFI); sda2 (OSX); sda3 (NTFS); sda4 (where Ubuntu will go); and sda5 (the swap).

13. Go through the rest of the installation. On the last screen (screen 8, iirc) click the Advanced button and choose to install the boot loader to /dev/sda3, which should now appear. 

Click Install and wait 20 or 30 minutes while Ubuntu installs.

14. when the installation is complete, restart. In the rEFIt menu, choose the partition tool and resync. 
15. Power down your computer.
16. Power up and you should be just fine.

If you're not dual-booting, you should still choose to set up a special partition for GRUB, since it will whack out your EFI even if Ubuntu is the only thing there. (Get into the live CD, go gparted, wipe the drive, set up a partition for GRUB, one for Ubuntu, and one for the swap, and be sure to install GRUB in dev/sda2/ instead.)

Good luck! I hope this works out for everyone. It worked brilliantly on my revA Macbook (1,1), and I'm typing this from the Mac partition.


Oh. And I just realized that I have my notes from my install, and they include a link to the [thread]("http://ubuntuforums.org/showthread.php?t=1468240&page=5") where I originally found this. All credit goes to Jacques4x4 who originally developed this method.


Edit: I'm now on the Ubuntu partition, and realized that I forgot to mention one small thing. When you start up Ubuntu via rEFIt, the GRUB will assert itself and give you some additional boot options (straight Linux, safe Linux, shutdown, OSX, and something else, if I recall). GRUB will automatically boot into Ubuntu after 10 seconds, or you can just hit 'return' and boot right into Ubuntu. Not a big deal, to me, but those of you who really value your boot up times may want to search for a way to teach GRUB to shut up.
Golden ticket after an arduous search. Willy Wonka's factory finally opens to me! Thank you.

---

### Post by xlollie106 on 2011-01-05
this worked great for me too.

weird thing though...when i run reffit, it gives me the option to boot either mac, ubuntu, or windows...i haven't installed windows on my comp so this seems odd to me. i haven't tried to see what happens if i choose to boot this imaginary windows.

but since ubuntu seems to be running fine, i don't plan to try to fix this until maybe i know something about partitions lol. 


thanks!


edit: ok when i boot in "windows on partition 3" it just boots into ubuntu..weird. anyone know why this happens?

---

### Post by mustinet1900 on 2012-11-06
> **jamesixgun said:**
> 

13. Go through the rest of the installation. On the last screen (screen 8, iirc) click the Advanced button and choose to install the boot loader to /dev/sda3, which should now appear. 




Exactly this point is my problem on my macbook pro 5.5 and Ubuntu 12.04

When i install the bootloader in the root partition then i get later a black screen with blinking cursor and nothing happen , no boot.

But when i install the bootloader on my default main hard disk i can boot without problems.

I dont know if this is also right.

Can someone help me?

Must i use gparted before i start the installation or can i make the partition things also in the normal partition menu form the installer?

---

