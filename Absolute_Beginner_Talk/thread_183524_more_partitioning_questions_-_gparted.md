---
title: "more partitioning questions - gparted"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by harperd on 2006-05-28
I am trying to move over from Windows to Ubuntu on my laptop and I need to resize the partitions. Windows currently has 34Gb (NTFS) and Ubuntu 4Gb. I want to take around 6Gb from Windows to give to Ubuntu.

I installed GParted and NTFSProgs. When I try to resize using GParted I get the message "A busy device is a device with at least one mounted partition. Because making changes to a busy device may confuse the kernel, you are advised to reboot your computer". After rebooting I get the same message.

hda1 Linux
hda2 Windows
hda3 extended
hda5 Linux-swap

I have searched other threads but cannot find a specific answer to this issue. 

Any help would be appreciated.
Dave, Madrid, Spain

---

### Post by simonn on 2006-05-28
Boot from a boot cd.

---

### Post by jorn on 2006-05-28
I think you can't resize while running your os on the same harddisk.
I would suggest to download gparted live cd and boot from that.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by harperd on 2006-05-28
Thanks for the responses. I tried the gparted live CD but it failed due to "unknown keyboard" - I have a Spanish keyboard.

---

### Post by catlett on 2006-05-28
That stinks because gparted live works great. But there is another way to get gparted running live.
Did you get an Ubuntu live cd? If not you can download one. Hopefully the live cd will recognise your keyboard since your ubuntu install did.
Then go into gparted like you did in your regular ubuntu system. The partition should be unmounted. If by some chance it is mounted check its mount point by ```
mount
``` Then unmount it with umount and run the partitioning

---

### Post by harperd on 2006-05-28
Thanks. I'll try that later. I'm downloading the Knoppix live CD at the moment so I'll try that first.

---

### Post by catlett on 2006-05-28
knoppix will work as well. knoppix is kde so it will have qtparted

---

### Post by harperd on 2006-05-28
Once again thanks for help. Knoppix worked and I freed up 4Gb (hda4). Now I need to make it useable. I tried editing fstab to add hda4 but must have screwed up as KDE crashed. Booted in recovery mode and reset fstab.

I'd like to mount the new partition as /home. This way I can keep my data and the OS seperate. I should know this but how do I do it?

---

### Post by aysiu on 2006-05-28
Try this:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by harperd on 2006-05-28
Great advice! Thanks.

---

