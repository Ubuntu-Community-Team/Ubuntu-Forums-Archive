---
title: "NEED ADVICE: Installation errors"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by 999.michael on 2006-04-11
:confused: Im new to Linux :oops: , so would appreciate any help here! thanx. :confused: 

I have quite an old pc, and am trying to install ubuntu linux (breezy badger? 5.10 i think) on it. it used to have windows xp on, but i repartitioned the hard drive (partitions #1 and #5 as the guided partitioner recommended)and hopefully its gone :-? . it had a boot virus aswell, but i think that went aswell.

everything in the install works fine, except for the "install base system" part. i partitioned the drives how it recommended, and the cd is fine as i used the checking utility on the installer. the ubuntu live cd also works on that pc so i know its compatible, i just cant install it ](*,) . whenever it gets to the install base system part, the following error message comes up about 50-60% through every time i try:

> Base system installation error

The debootstrap program exited with an error (returned value 139).

Check /target/var/log/bootstrap.log for details.

Then when i press continue, it says:

> The base system installation into /target/ failed.

Check /target/var/log/bootstrap.log for details.

then it tells me that the installation failed *again* (in case i hadnt realised, i guess :p ) and takes me back to the installation steps box.

This happens every time i try to install. i tried reinstalling the base system only from the box that comes up, it asks me if im sure i want to install to an unclean system and then sometimes it comes up with the same error messages above, just with value 1 instead of 139. however, most of the time it just comes up with 139 again. i really need to know what value 139 actually is!

i have tried repartitioning the disks and restarting the whole installation, but this does not work. I tried using the option to copy the log files to a floppy disk, but it didnt even access the drive. i then tried opening the log files directly from /target/var/log with the shell but this wont work either. i do not have a network connection on that pc so i cannot do anything web or network based.

please help! i really need ideas :idea: but as i said, i am a newbie so cant really do much! thanx a lot ;)

---

### Post by YuHoo on 2006-04-11
Check the integrity of the disk, I don't have to time right now to check the exact process, but it may be a slightly corrupted disk. Reburn it at a lower burn rate to solve the problem (hopefully). I'll research it a bit, but I have to fly right now. List what you're using to install/partition. Is it LVM or something else? I would also recommend making sure that you completely wipe the hard drive of everything. Also try again with completely automated process if possible. If that doesn't work then you'll have to start working with some of the manual options.

Once again, sorry for being so brief, but I'll make sure to get to it in the next few hours with a better analysis.

----ok, I think I see a possible problem...
It asks if you're sure that you want to install to an unclean system. This could be the source of the error. Make sure that you use LVM and that you let it automatically set up the partitions and GRUB. After that make sure that you have your hard drive formatted. This will ensure that your system does not have the virus, old installs, etc on it. That's the best I can figure since I do not know what the code value 139 either means or where it is showing up.

---

### Post by 999.michael on 2006-04-14
Thanks i checked the integrity of the disk and it was fine, i burned 3 copies at 4x (lowest possible on my pc) and it still didnt work. However, i swapped a few bits around with another pc i had spare and installed it on that one along with win98 on another partition and it worked fine! so i now have ubuntu. thanks anyway :p

---

