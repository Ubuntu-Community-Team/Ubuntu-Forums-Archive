---
title: "[SOLVED] Cant install ubuntu (failed to unmount partitions)"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by SnapyGapi on 2007-08-15
Hello, i downloaded ubuntu live cd (7.04) from ubuntu website. I boot from it, and everything is fine. When i try to install it, when it comes to end, it shows a popup:  

when selecting partitions i select guided, and select external wd drive (usb) where i wont ubuntu to install.


screenshot:
[IMG]http://www.freewebs.com/snapygapi/Screenshot.png[/IMG]


my hardware:
1gb ram
250gb external drive, 250 hard drive
intel core 2 duo
asus p5b motherboard

what can i do to fix this and install ubuntu?

---

### Post by LinuxLoserr on 2007-08-15
Are you dual booting your computer?

---

### Post by Hazmat. on 2007-08-15
As long as you have a recovery disk, i'd just wipe your drive. That way if you don't like ubuntu at any time you can go back to windows ( the bad thing is i can't go back because i don't have one, i have a windows update disc which until tonight i didn't know i couldn't go back with it. )

---

### Post by SnapyGapi on 2007-08-15
i dont realy know what is dual booting

i wont on external drive to have ubuntu, and on main drive to have windows

theres no files in my external drive

---

### Post by meierfra on 2007-08-15
On the bottom of the screen it says "My Book File -Browser".

 Close the file browser and try again.

---

### Post by SnapyGapi on 2007-08-15
allredy tryed to close all tabs and install and its the same...

---

### Post by defconoii on 2007-08-15
while your in the installer open up the home folder below places and right click all partitions and click unmount and proceed with the installation, this is a bug, u just got to keep force unmounting the partitions, if that dont work do it in the terminal sudo umount /media/"partitionname"

---

### Post by bodhi.zazen on 2007-08-16
In case anyone else runs across this thread, it is a "feature" of gnome 

To disable, Go to System > Preferences > Removable Drives and Media and uncheck the box about automatically mounting drives

---

### Post by SnapyGapi on 2007-08-16
ok this time it didnt show popup. The install finished normal, but now i cant load windows, neither ubuntu... i can just now use live cd if i boot from it...

---

### Post by bodhi.zazen on 2007-08-16
Sounds like you need to either remove the CD and boot from hard drive (which I assume you hav edone, but just checking ;) ) or install grub.

Follow this how to for installing grub (to the MBR):

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Follow the "quick start" section

---

### Post by SnapyGapi on 2007-08-16
in fourth step, when i press tab key, it doesnt complete line, instead it just says possible disks are hd0 hd1

*should i make another thread, because this is not the problem with install anymore?

---

### Post by SnapyGapi on 2007-08-18
srry for double post, but i have managed to complete the tutorial and its still the same...

i will make another thread, becouse this thread is about install problem not grub problem

---

