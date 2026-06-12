---
title: "Missing OS"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by ohnnyj on 2006-07-23
Hi all:

I really would like to try ubuntu but am at a road block.  I currently have four hard drives in my system.  Two are in a RAID array and have Windows on them.  Another is a storage drive and the last is the one I would like to dedicate to Linux.  I tried to run the installer for ubuntu after burning the iso to a cd and the setup went fine but when I try to boot it does not load the GRUB boot loader and booting directly off of the Linux hard drive (by changing the drive order in the motherboard BIOS) gives me a Missing Operating System error (as if it did not install).

Is there something special I need to do in order for my config to work?  I'm sure my RAID array has something to do with the problem as it shows up as two logical drives during the ubuntu setup when it should show as one.  This leads me to believe that it has no idea if Windows is installed or not.  I still don't know why it would not at least allow me to boot directly off of the Linux hard drive.

Any help would be greatly appreciated.

Thanks.

John

---

### Post by Ziox on 2006-07-23
do you have a live cd? perhaps you can reinstall grub on your linux drive...

---

### Post by catlett on 2006-07-23
The issue is where you installed grub. If you used the live cd installer then there wasn't too much you could configure.
Anyways if grub installed to the mbr then grub won't be on your linux drive, so booting to the linux drive won't start grub.
If you used the Alternate Install CD then you could have chosen to install grub to the linux drive.
If you have the ability to select the hard drive to boot from then I would do it like this.
Disconnect the other drives and have only the one linux drive setup as master. Install Ubuntu. You do not have to do anything fancy. Let grub install to the mbr (this will be the default)
Then put all the drives back in. Now when you select the linux hard drive, it will boot into grub.
Can you boot into windows alright or are you not able to because of the ubuntu install? If you can still boot to windows, I would do it this way. If you can't get into windows, that can be fixed.
So what is the status? Can you boot to windows? If not , do you get a grub menu?

---

### Post by ohnnyj on 2006-07-23
My Windows drives are just fine and bootable.  Would it be easier to simply install with the alternate and tell grub to install on the Linux drive or is it better to disconnect all the other drives?  Either way it seems as though I will have to use my BIOS to switch between booting to Windows or booting to Linux as ubuntu cannot see the Windows install on the RAID array.

---

### Post by catlett on 2006-07-23
I only mentioned unhooking the other drives because Ubuntu has been having issue with sata and grub. There doesn't seem to be any logic to it. Just appears to be a bug.
I don't know what the last install showed but if it showed the Linux drive without a problem, then go ahead and leave everything attached. Just make sure to select that drive for install and when you get to grub, so no to install on mbr. It will then ask you where you want to install grub. You will then have to type in the drives label. i.e. /dev/hdac or /dev/sdd whatever the drive is labeled as when you select it to install to, remember the label and use that.
If you just had the 1 drive attached, it takes away any chance of error or corruption of the other drives. But your way will work, just make sure you are selecting the correct drive and that you know the drives label when you get to the installing grub part.

---

