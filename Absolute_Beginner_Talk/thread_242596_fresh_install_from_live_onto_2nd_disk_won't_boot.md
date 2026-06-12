---
title: "fresh install from live onto 2nd disk won't boot"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by generica on 2006-08-23
Hi everyone!

I'm by no means completely a newbie when it comes to Linux, however I rarely step outside of Debian/GNU console-based world, as most of my experience comes from managing servers at work.

However, I downloaded the Dapper Drake Live CD for PowerPC (6.06) and liked it enough on the CD that I decided to give it a try on a partition!  So I freed up some space on my secondary hard drive, repartitioned to free up space, and rebooted off the Live CD again to begin my install.  The installation went perfectly, and I must commend you on how smoothly the process went.  

To my delight, I rebooted, holding down the option key, to see that Ubuntu was now showing up in the Open Firmware boot manager, along with my OS X partition.  Clicking on the icon for Ubuntu, however, brought me to a second menu (presumably the MBR from the second hard disk) which gave me the option of choosing Linux or OSX.  I press L, and instead of booting, the machine loops back into a slightly-distorted-video'd OpenFirmware boot menu, which then re-loads the list of bootable devices like it was just rebooted.

I thought the problem would have something to do with my system's main hard drive being /dev/sda, which is where OSX was installed, and Ubuntu residing on /dev/sdb.  I booted with Command-Option-OF to access the Open Firmware command line, and did my best to boot the 'ultra1' device, which represented the second hard drive in my system, but I couldn't get it to boot from there, either.  I kept getting the error message "LOAD-SIZE is too small" but had no idea how to change that setting.

Then, I tried booting from the Live CD a third time, opened a terminal, and mounted the /boot filesystem (located at /dev/sdb2) on my hard drive.  In it there were three files, including yaboot.conf.  I took a look in there and thought that maybe, just maybe, the problem was because the device= line was set to disk@0, and who knows if that refers to my secondary hard drive or not?  I read the man page for the yaboot.conf file, to see that I could in fact specify "ultra1:" as the device to boot from in that file as well.  I did so, rebooted yet again, however still nothing (the machine just boots straight away into OSX unless I hold down option, in which case I can see the Ubuntu partition, but the behavior is still the same as previously described).

The furthest I think I've gotten was when I booted from the Live CD a fourth time, and tried to specify the ultra1: device (as well as its fully expanded Open Firmware device id string) as a boot device.  Doing so yielded the error message "incorrect or corrupt file" (or something very similar along those lines, I don't remember the exact error message from memory and didn't have anything to write it down on at the time.

I specified "ultra1:/yaboot" as the boot device, and it read in an Elf32 kernel, and then said "could not malloc()" along with a few hexadecimal memory addresses.

Is the problem that my machine is 64 bit and the installed kernel is 32 bit?  Or is the problem with the default, auto-configured yaboot.conf settings?  Or with the way the installation process partitioned my hard drive (I allowed it to do so automatically since I had already made 5GB of free space on the drive)?  The root partition got put onto /dev/sdb4, the boot partition /dev/sdb2.  SDB2 shows up as a NewWorld partition in fdisk, and there is also a swap at /dev/sdb5.

Any advice from where I should go from here?  :confused: 

Thanks,
generica

---

