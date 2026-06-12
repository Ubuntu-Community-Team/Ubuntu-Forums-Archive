---
title: "Clean install of 10.04 boots to blinking cursor"
date: 2010-05-03
forum: Apple Hardware Users
---

### Post by pafufta503 on 2010-05-03
I have just installed Xubuntu 10.04, on my Mac pro.  I have OS X snow leopard on one hard drive (sd1), and I put lucid on another hard drive (sd2) (both SATA).  The installation went perfectly.

The issue is that I cannot boot Ubuntu, the screen briefly flashes some colors, and then displays a blinking cursor.  The screen is unresponsive to the keyboard, at this point I have to restart the computer.

My assumption is that there is a problem with my NVidia card and the drivers, but I am not even sure that grub loads as I cannot see anything until the blinking cursor comes up.  Is there a way that I can boot into safe mode, and then install the proper video drivers?  I would love some help, as this problem is keeping me from using Ubuntu, and I must use OS X for the moment.  Thanks.

---

### Post by linuxopjemac on 2010-05-04
Just try to chroot into your system to update the repository and to install the latest nvidia driver.

[http://mac.linux.be/content/chroot-system-livecd](http://mac.linux.be/content/chroot-system-livecd)

---

### Post by trusky5 on 2010-05-04
Hi,

i have the same problem, but my pc is a hp desktop using ubuntu. The funny thing is, it wouldn't boot before i installed the nvidia driver. i had to use the install cd, boot from it and then in the menu hit the "Boot from first hd" option. then it would boot.
Ive installed all variations of grub and allways run "sudo update-grub" or "sudo update-grub2" if neccessary.
This is a major problem, since the pc is not mine and i was just telling my cousin about the new and fast boot experience, when it happend.

If you need any more details about the computer, i will post the asap, just need to get access to his machine.

Regards from Germany

trusky5

---

### Post by linuxopjemac on 2010-05-04
[http://www.ubunturoot.com/2009/12/how-to-fix-problems-with-xorg-and.html](http://www.ubunturoot.com/2009/12/how-to-fix-problems-with-xorg-and.html)

---

### Post by pafufta503 on 2010-05-04
After a lot of attempts I have determined that the issue is grub related.  I have tried every imaginable key/s to boot into the grub menu on startup, and it will not load.  This leads me to believe that grub isn't loading.

---

### Post by Mills00013 on 2010-05-04
Macbook Pro 4,1 here. I have the same issue right now when booting. I do have grub installed correctly, although I had to do it manually since the grub is installed onto my sda4 partition (the linux boot) and I have the efi, osx, and win7 on the first 3 sda's. The first few times I booted my machine it worked fine, no issues whatsoever. I dont remember making any changes or updating something but I must have because last night i had to reboot (due to my backlight not resuming from sleep, another issue altogether) and found myself facing this problem.

I go through refit with no problem, then it hits the grub and again, no problem. but then once I select my main linux in the grub, it goes to that blinking white line in the upper left corner.

Now i havnt figured out a remedy for it just yet, but what I have found is that once at this screen, I can hold my power button on my MBP for about 1.5 seconds and it will flash the screen and i will be prompted with the login manager. I have no idea, i just know it works. This happens after every reboot now.

---

### Post by linuxopjemac on 2010-05-05
what about reinstalling grub from a liveCD?
Maybe this will help you:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Mills00013 on 2010-05-05
I really have an issue believing this is a grub issue. It might be, really im not ruling it out, I just had it not happen though. I uninstalled my nvidia proprietary drivers and it didn't do it once, then it did do it. So I'm not sure if its related or not.

Also, booted in recovery mode. In the recovery boot process, where you can see the verbose, it stopped after loading. I could still see the verbose but all that was left was a blinking white cursor. the same one. its got to be the same thing. pressing my power button brought me past it to the recovery menu...

---

### Post by pafufta503 on 2010-06-02
I am still experiencing the same issue.  Ubuntu used to boot fine for me, when I had OS X 10.4, since I've upgraded to 10.6 it will not boot.  Here's some specs:

Mac Pro 1,1
sda = OS X snow leopard 10.6.3 (boots fine)
sdb = xubuntu 10.04 64-bit (boots to "GRUB_")

I have rEFIt installed on my Mac drive.  I can pull up the rEFIt menu when I boot with no issues.  OS X boots perfectly fine.  Installation of 10.04 works flawlessly, LiveCD boots fine.  When I select Linux from rEFIt, it proceeds to boot, and then hangs at "GRUB_", becoming unresponsive and requiring me to hold the power button to shutdown.

I've tried 3 different versions of ubuntu, in both 64-bit and 32-bit, and they ALL boot to "GRUB_", where it hangs.  At this point I have given up, if anyone has a good solution I'd love to hear it because this is keeping me from using Linux atm.  I've spent nearly 6 hours just installing different versions, and chroot'ing to fix grub to no avail.  I'm stuck in OS X help!

---

### Post by linuxopjemac on 2010-06-02
I hope that this manual will help you:

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


Oh. And I just realized that I have my notes from my install, and they include a link to the thread where I originally found this. All credit goes to Jacques4x4 who originally developed this method.


Edit: I'm now on the Ubuntu partition, and realized that I forgot to mention one small thing. When you start up Ubuntu via rEFIt, the GRUB will assert itself and give you some additional boot options (straight Linux, safe Linux, shutdown, OSX, and something else, if I recall). GRUB will automatically boot into Ubuntu after 10 seconds, or you can just hit 'return' and boot right into Ubuntu. Not a big deal, to me, but those of you who really value your boot up times may want to search for a way to teach GRUB to shut up.
Last edited by jamesixgun; 1 Day Ago at 02:43 AM..

---

### Post by pafufta503 on 2010-06-02
I am quite familiar, after about 10 installations, with each of these steps.  Installation is not an issue for me, I can install it without problem.  The problem is with Grub, it will not load no matter what I've done.  [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) .  I've nearly memorized this page, done every relevant fix, nothing works.  It will only boot to "Grub_", and freeze there (yes every 32bit and 64bit version of Ubuntu between 9.04 and 10.04, in a bazillion fresh installations).

Your tutorial is not fully relevant to my setup.  I have OS X on sda, and Ubuntu goes on sdb.  Having 5 partitions on my OS X HD is less than ideal.  It is not a solution for me, but an entirely different setup.

Thank you for the reply, but it doesn't change my current problem, stuck at boot on "Grub_".  Reinstalling won't change anything, as 10 fresh installation confirms that Grub won't work for me.  Does anyone know why Grub would not load on my system?

---

### Post by pafufta503 on 2010-06-02
If it will help, I'll list the steps I took for installation.

1. Using Mac Disk utility I formatted /dev/sdb to free space.
2. Shut down, and booted using Xubuntu 10.04 amd64.
3. Once LiveCD loads it's menu I chose "try Ubuntu without changing your computer".
4. Xubuntu LiveCD boots, I choose "Install Ubuntu" from the desktop
5. When I get to the partition window, I select to install Xubuntu on HD sdb, using the "Format and use entire HD" option.
6. Installation proceeds without issue.
7. Installation finishes, prompting me to restart.
8. Upon reboot I run the partition sync tool in rEFIt, then boot into OS X, next I shutdown and reboot.
9. In the rEFIt menu I choose Linux, where it proceeds to begin to boot, but hangs at "GRUB_" with a blinking cursor.

I'm nearly a pro at installing ubuntu, fixing grub, and chroot'ing because of this experience.  But there is something I am missing, some piece of information, that accounts for Grub not working (more specifically it will not work at all from a fresh installation.)

Do I have a secret partition in some random location with grub on it?  Do I need to bless a partition?  Is an MBR table fuzzed up?  Is it an issue with X?  A video driver issue?

I wish I knew where to start...

---

### Post by wbm on 2010-06-09
I have the same exact issue on an HP desktop. I have clean install of Ubuntu 10.04 installed on one drive and a second drive for data only.
I have to press the power button and then it usually comes on.
My boot process is HP Blue screen where I can choose setup etc. then Grub where I can choose my Kernel, then a black screen with a blinking cursor.
Sometimes I get a message after waiting a looooong time that says:
"Gave up waiting for root device. COmmon problems:
- Boot args (cat/proc/cmdline)
- check rootdelay= (did the system wait long enough)
- check root= (did the system wait for the right device)
- Missing modules (cat /proc/modules; ls /dev)
Alert! /dev/disk/by0uuid/ ....(long number here) ... does not exist. Dropping to a shell

---

### Post by jamesgrant on 2010-12-19
I can hold my power button on my MBP for about 1.5 seconds and it will flash the screen and i will be prompted with the login manager.[/QUOTE]

im haveing the same issue whats an MBP?

---

### Post by arabis on 2010-12-20
MBP= MacBook Pro

---

