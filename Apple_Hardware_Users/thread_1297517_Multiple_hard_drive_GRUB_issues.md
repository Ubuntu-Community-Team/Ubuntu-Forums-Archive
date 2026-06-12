---
title: "Multiple hard drive GRUB issues"
date: 2009-10-21
forum: Apple Hardware Users
---

### Post by macaholic on 2009-10-21
So I was attempting to clean install the karmic beta on my mac pro today, andthe installation itself went well, but now it seems there are some issues with my GRUB setup; first I'll briefly explain the hard drive setup on this computer. 
The "main" hard drive is sda, and it has leopard and an ubuntu (failsafe operating system) on it. The second hard drive, sdb, is devoted entirely to ubuntu (main linux operating system) a swap partition, and a /home partition.
Whenever I restart, rEFIt pops up and lists 3 options, osx, and two "legacy" operating systems. I select the first legacy operating system and it loads the GRUB that is installed to the sda drive. From here I can either choose to boot into the sda ubuntu, osx, or the sdb ubuntu. I want to primarily be booting into the sdb one, but when I try it says that the device is not found, followed by a hex code which I assume is the device identifier that it can't find. I press any key to return to the main GRUB menu.
I can boot into the sda ubuntu just fine, and have reinstalled GRUB just to be sure, and it still cannot find the sdb ubuntu partition.
Any help or input on this issue would be greatly appreciated.

---

### Post by ALLurGroceries on 2009-10-21
Have you ever been able to boot off of your 2nd hard drive? The full error message along with the code may be helpful.

Maybe the drive order is not what it was when you setup GRUB. You can edit the entry by selecting it with the arrow keys in the boot menu and then typing 'e' for edit. Then hit 'e' again on the line you want to edit. Then try changing the hard drive (hd0,1 for example) or partition. Hit enter to stop editing and 'b' to try booting.

If that doesn't do it more details about your system setup would probably help. Good luck!

---

### Post by macaholic on 2009-10-23
I used to be able to boot off the second hard drive just fine, but since repartitioned and clean installed it's stopped working entirely.
I have reinstalled GRUB multiple times, and have tried editing the entry from the boot menu, but nothing seems to be wrong. It's listed as hd1,2 which should be correct as it is the second partition on the second hard drive. The error message I am getting when I attempt to boot to it from the GRUB menu is something akin to ```
error device fa3f30b0-a301-4d37-a92a-0daedc511415 not found
Press any key to continue...
```
"fa3f30b0-a301-4d37-a92a-0daedc511415" is indeed the UUID of the drive I'm trying to boot to, as verified by running bkaid.

It should also be noted that when I try to boot to the second hard drive directly from the mac EFI boot menu (holding alt at startup) it comes up with a black screen which reads "Missing operating system". 

Maybe I need to reinstall GRUB to the second hard drive? If anyone could help me with this (I haven't done it in ages and the procedure seems to have changed) or has any other input it would be greatly appreciated.

---

### Post by ALLurGroceries on 2009-10-23
Do you have a **search --fs-uuid** option in your grub entry? Try removing that if you do...

Maybe you need to run grub-mkdevicemap and/or update-grub again since reconfiguring?

If you do run mkdevicemap it'd be smart to back up /boot/grub/device.map first in case anything goes wrong.

Also you can try swapping the drives at the grub prompt: [http://www.gnu.org/software/grub/manual/grub.html#map]("http://www.gnu.org/software/grub/manual/grub.html#map")

If that doesn't help then maybe post your device.map and menu.lst and maybe someone will spot an error.

Your second disk won't boot directly because you haven't installed a bootloader onto it and/or the partition is not set as bootable. You can install grub onto the second hard disk using a livecd or recovery mode on the installer CD. But you shouldn't need to.

Edit: Oops with Karmic you're probably on grub2, in that case check the UUID of the drive with **ls -l /dev/disk/by-uuid** and check that against your /boot/grub/grub.cfg entries.

---

### Post by macaholic on 2009-10-24
Thanks for your suggestions, I tried all of those and still nothing worked, the UUIDs matched and everything. I just decided to revert back to legacy grub on the first hard drive, grub2 doesn't have anything that spectacular as far as I can tell, and I have fairly simple needs from my bootloader.

---

