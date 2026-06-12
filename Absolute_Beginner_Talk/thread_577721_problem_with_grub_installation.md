---
title: "problem with grub installation"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by zaprenki on 2007-10-16
Hi there...
After an installation of Ubuntu 7.04 with unsufficient partitioning (too little available space - see [the thread here]("http://ubuntuforums.org/showthread.php?t=574404") for info), I decided to repartition and re-install, and so I did.
The second installation completed successfully and I got to the part where the installer asked for reboot. I removed the LiveCD and rebooted the PC, but WinXP started loading with no sign of GRUB asking me which OS to boot. I formatted and reinstalled Ubuntu once more but again no GRUB available at all. The system boots directly to WinXP without even showing the GRUB menu, I doubt that it even runs.
This did not happen at the very first installation where GRUB ran normally at boot time. Also I checked (using Partition Magic) that data were actually written in the linux partition. I should note that when I repartitioned the hard disk, I erased the linux partitions and was left with GRUB not working and an unbootable system. So I had to boot with WinXP installation CD, run recovery console and restored the MBR with the fixmbr command. Maybe that has some relation to the problem?
So how can I fix GRUB so that the OS choice menu appears at boot time?
Thanx in advance...

---

### Post by Diabolis on 2007-10-16
You can reinstall grub from the live cd. Once I messed up grub because I installed 3 different distros in my hard drive. When I got tired of them, I just deleted their partitions. What happens is that grub keeps the info from the last installation and when it can't find any of that information, it won't boot. I fixed it by typing this in the terminal:
```
sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit
```

you  must change "x" for the desired location

I'm not sure if you can do this from a live CD. I did it from another ubuntu installation on a removable hard drive.

---

### Post by Duck2006 on 2007-10-16
Yes you can do it from the live cd in the terminal
You can also get super grub and install grub with that

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

