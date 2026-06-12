---
title: "Make sure ubuntu is fully uninstalled"
date: 2010-09-10
forum: Apple Hardware Users
---

### Post by ZeldaFan on 2010-09-10
How do I make sure Ubuntu is fully uninstalled from my system? 
I have removed the corresponding partitions and only remain with the EFI and OS X partition. However, when I load refit, the option to load linux from the HDD still remains. I can't remember if that was always there or if its still there after I installed it.

---

### Post by Tylerjd on 2010-09-11
I would suggest booting into a Ubuntu live CD, starting gparted, and making sure there are only 2 partitions, the EFI protected partition, and HFS+ partition. Make sure there are no ext2, ext3, ext4 or swap partitions. rEFIt is weird in reporting the partitons. If you still need rEFIt, try reinstalling rEFIt (uninstalling, and installing again) and that *may fix the problem.

---

### Post by lisati on 2010-09-11
When you've removed the Ubuntu partition(s) you will need to reset the bootloader. If you plan to (re)install Ubuntu, that should be taken care of automatically by the installer.

I'm going to have to all "pass" on how to do it on an Apple if you don't plan to reinstall Ubuntu: someone else might need to step in and offer suggestions.

---

### Post by ZeldaFan on 2010-09-11
Yes there are only two partitions available through the LiveCD. I do not have rEFIt installed, I run it via a bootable CD. Would such an issue with messed up boot options still exist then? I can boot into OS X totally fine, but it's just that when I had a PC, if I simply removed the OS partitions, it wouldn't have necessarily removed GRUB, and I would have had to reset the MBR. I don't think Macs have an MBR, however, so I wasn't sure if the phantom linux boot option in rEFIt was rEFIt's fault or me not resetting the bootloader as lisati mentions.

---

### Post by linuxopjemac on 2010-09-12
You can zero out the code in the MBR.
sudo dd if=/dev/zero of=/dev/sda bs=440 count=1

or from within OSX (safer):
[http://mac.linux.be/content/remove-grub-under-osx-if-osx-wont-boot-anymore](http://mac.linux.be/content/remove-grub-under-osx-if-osx-wont-boot-anymore)

---

