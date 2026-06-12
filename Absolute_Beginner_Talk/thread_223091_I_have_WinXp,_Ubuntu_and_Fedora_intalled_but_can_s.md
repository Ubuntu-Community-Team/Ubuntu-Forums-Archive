---
title: "I have WinXp, Ubuntu and Fedora intalled but can see fedora help on GRUB"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Arijua on 2006-07-25
I intall winxp ubuntu in first hd (hd0) and fedora in second drive but grub is on first drive's mbr or primari partition, I don't know but fedora was the last installation and it says can not intall (mbr or the program how load it)  in a secundary disc, how do I edit grub and fix it.

---

### Post by catlett on 2006-07-25
I can't tell what OS you are in but if you are in Ubuntu, reinstall grub. Then go into fedora's partition and get the entry for fedora from it's grub menu.
Add that entry to Ubuntu's grub menu and your all set.

To install grub to the  mbr use this command.(this assumes you have an ide hard drive)
```
sudo grub-install /dev/hda
```Then update grub ```
sudo update-grub
```
Hopefully Ubuntu mounted fedora's partition. (If not mount it by going to System<Administration<Disks) When you can get in fedora's partition, go to the boot folder. Inside it go to the grub folder. Open the grub folder and open up the file menu.lst. Copy out the entry for Fedora.

Now open Ubuntu's menu.lst so you can edit it.```
 sudo gedit /boot/grub/menu.lst
```Add Fedora's entry, that you copied out, to the end of the file. Make sure to hit save at the top of gedit.

If all went well, Ubuntu installed grub to the mbr and automatically added windows to the grub menu. Then you found fedora's grub menu, copied it to ubuntu's grub menu and saved it. Now when you boot you will have ubuntu, windows and grub.

If you are in fedora things are a little different so those commands won't work, fedora doesn't use sudo.

---

