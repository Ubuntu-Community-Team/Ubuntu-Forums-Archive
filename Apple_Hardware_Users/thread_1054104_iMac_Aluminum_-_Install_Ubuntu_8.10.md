---
title: "iMac Aluminum - Install Ubuntu 8.10"
date: 2009-01-29
forum: Apple Hardware Users
---

### Post by ov3rcl0ck on 2009-01-29
Many people have strugled to get Ubuntu setup on an iMac, mostly because of the EFI used in mac. In this little tutorial I will show you how to emulate a MBR and how to get the graphics drivers, wireless drivers, sound drivers, and bugs all up and running. So here are the steps:

1. Download the 8.10 ISO image from ubuntu.org. You can use 64bit or 32 bit if you have core 2 duo, but for single cores you can only use 32bit.

2. Insert blank disk, go to disk utilities, click on the disk drive then click Burn up above.

2.1 You could also order a Ubuntu disk free and wait about 3 weeks.

3. Now you need a MBR emulator/boot loader, for this we use [http://refit.sourceforge.net/](http://refit.sourceforge.net/) rEFIt is a MBR emulator for EFI based computers, even though rEFIt is a boot loader we still need GRUB.

4. Put in the disk and reboot, when rEFIt comes up choose to boot of the CD/DVD.

5. When you boot up go to System>>Admin>>Partions, in other words open gParted.

6. Now we shrink the HFS+ partion, LEAVE THE FIRST PARTITION ON THE DISK ALONE, now right click on the HFS+ partition, give at least 10GB for ubuntu, then create a new EXT3 or ReiserFS partition(reiserfs and EXT3 are the only linux filesystems supported by rEFIt), if you want to go ahead an make a swap partition.

7. Reboot, DO NOT INSTALL YET. On the rEFIt menu, go to partition editor on the bottom row, it will ask you if you want to automaticly edit your MBR, select yes(Y), after thats done, reboot again.

8. Boot from disk, Manually edit partitions. Select the Partition you made delete it make the SAME partition and mount your root(/) partition there. The rest of your install should be the same as any other install.

9. Restart, boot to linux, don't update quite yet we will remove some software and add some so update after we are done with that. First go to system>>Admin>>Hardware Devices, install both restricted drivers(wireless and graphics). If graphics don't work go to ATI's website get the drivers for the ATI Radeon 2600 XT or what ever card you have, then "chmod a+x" the BIN file run it in terminal install and your good to go, EX. "chmod a+x atidriver.bin" "./atidriver.bin".

10. Now if you tried running an program the uses OpenGL you might notice that everything is choppy, this is caused by Compiz which is installed by default on ubuntu, instead of using compiz we will use Metacity which runs off the CPU also saving you resources. First uninstall compiz, run "sudo apt-get remove compiz" go ahead and enter your password. Now lets enable metacity, run "gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true" in terminal. Now your good to go, if you want to disable metacity change true to false.

11. Now for the sound. Enter "sudo gedit /etc/modprobe.d/options" into terminal, this opens nano text editor, enter "options snd-hda-intel model=imac24" without the quotes to the end of the file, save exit, reboot.

12. Have fun and post any problems you might have.

Common problems:

1. Grub doesn't appear and I can't boot ubuntu.
  You have to instert your boot disk and install GRUB again.
2. Graphics are still choppy.
  Post your ATI configs.

---

