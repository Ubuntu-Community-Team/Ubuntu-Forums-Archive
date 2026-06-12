---
title: "how can I save boot logs when recovery mode hangs?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by ginestre on 2008-01-25
Having upgraded from ubuntustudio/feisty to gutsy, now the pc generally doesn't boot cleanly: I need to go into recovery mode and then start the desktop. 

However, even in recovery mode boot, it often hangs at initramfs. This doesn't always happen, just 3 times in 4- and I can't work out what the variable is. When the machine does manage to boot, I've checked disks and memory (1GB) and they are reported as error free. When it happens, I just have to keep rebooting until it sorts itself out- and this is a right royal pain in the ....

Is there some way to make a file copy of all of the info that flashes by on screen, while the boot is taking place? If this info were saved somewhere, when I do get the machine running I could sit down and analyse what had happened at the bad boots, and try to find out just where the problem is. 

TIA

---

### Post by petteriIII on 2008-01-25
If you can boot into Ubuntu give the command: dmesg that displays those messages.
 
If you cannot boot with your hard-drive boot with live-CD. There go to System/applications/terminal and give commands:
sudo mount -t auto /dev/<the device name of your Ubuntu-partition, for example hda1> /mnt
sudo chroot /mnt
- and now you can give the command: dmesq

---

