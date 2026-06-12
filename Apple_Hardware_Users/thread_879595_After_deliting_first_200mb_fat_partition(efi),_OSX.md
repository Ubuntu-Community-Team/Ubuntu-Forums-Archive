---
title: "After deliting first 200mb fat partition(efi?), OSX reinstallable?"
date: 2008-08-04
forum: Apple Hardware Users
---

### Post by Nikolai D. on 2008-08-04
Hi all.

Im stuck with this Tux icon in rEFIt. Also other Tux icons not bootable to. And all that after trying to install elilo. While installing Debian GRUB failed and i tried elilo. So now i havent found any way to uninstall elilo. And i tough, ohh lets just reinstall OSX. And no result. So i guess elilo is stored on that first 200mb partition. Iguess its EFI there. So if i delete it and reinstall, is it no problem anyone? =] Why i get this question, Disk Utility dont show it, is it because it dont see fat or dont want me to see it or anything else.. No idea.

Okay. Any suggestions are welcome. =]
Have a nice day.
Nikolai

---

### Post by Kobalt on 2008-08-04
Hello,

Can you insert your Mac OS DVD, press C to force booting on it and then, from here, completely wipe your disk before performing a clean Mac OS install. This should restore your EFI I believe.

---

### Post by cyberdork33 on 2008-08-04
> **Kobalt said:**
> Can you insert your Mac OS DVD, press C to force booting on it and then, from here, completely wipe your disk before performing a clean Mac OS install. This should restore your EFI I believe.
Yes, you can do a complete erase of the disc, then the installer should recreate the partition. If you think the files are on the EFI partition, boot the Ubuntu LiveCD, mount sda1, and see what files are there, and remove them if needed...

---

### Post by Nikolai D. on 2008-08-05
Hi guys.

Re Kobalt, thats what i did. But somehow EFI partition wasnt restored. But now ive booted into Ubuntu LiveCD and deleted it with grub.

Re Cyber, logically that was the thing to do. Ive booted into a livecd and have gone trough /dev and such. But i guess i was to lazy to go check a command for manual mount. So ive just deleted it and reinstalled. Now it's perfect. Checked with livecd that its there :)

Now i need to find a good Debian/OSX Dual Boot how to. Have been googling but from the view isaw it wasnt very clear on what to do with grub. I expect that it's going to be.Basic install without installing of grub. And then manually installing grub on root partition. But im not sure whats Debian installer going to do. I want to know it for sure.

Have a nice day.
Nikolai

---

### Post by cyberdork33 on 2008-08-05
> **Nikolai D. said:**
> Re Cyber, logically that was the thing to do. Ive booted into a livecd and have gone trough /dev and such. But i guess i was to lazy to go check a command for manual mount. So ive just deleted it and reinstalled. Now it's perfect. Checked with livecd that its there :)
The mount command is an important one that you should learn. First you have to have a folder created that you want to mount on. I will use /mnt/efi. (We have to use sudo to create a folder in this location).```
sudo mkdir /mnt/efi
``` Next you mount the partition you want onto the folder. You can explicitly state the filesystem type, but the mount command can detect it automatically.```
sudo mount /dev/sda1 /mnt/efi
``` At this point the contents of your EFI partition are in /mnt/efi. Then after you are done looking, you can unmount: ```
sudo umount /mnt/efi
``` (No, that is not a typo, the command is 'umount'.)

> **Nikolai D. said:**
> Now i need to find a good Debian/OSX Dual Boot how to. Have been googling but from the view isaw it wasnt very clear on what to do with grub. I expect that it's going to be.Basic install without installing of grub. And then manually installing grub on root partition. But im not sure whats Debian installer going to do. I want to know it for sure.From what it sounds like, the instruction you were following was attempting to show you how to boot from EFI (rather than through the emulated BIOS). This doesn't work well at all yet. You got it mostly right though, but you can install GRUB to the MBR. The only time this really becomes troublesome is if you also install windows. So basically, just create you root and swap partitions, then tell the installer to use that partition and go. There shouldn't really be a need for anything special.

---

