---
title: "Why doesn't Kubuntu recognize drives when ubuntu does"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Towerblock on 2007-06-27
Hi all...

I'm hoping someone can help me out a bit. I'm a complete noob and I've been playing around for the last cpl of weeks installing Ubuntu and Kubuntu (both Feisty) on a few machines to test it. I am having a cpl of issues though...

1. Kubuntu does not recognize an external usb hard drive and mount it when ubuntu does. Why would they be different?

2. On a totally different machine, running from the liveCD, Kubuntu does not show or recognize the internal HD of the machine from what I can see...but when I boot with the Live disk of ubuntu it DOES see the internal drive.

3. Neither OS seems to give me rights to change or write to internal partitions or external usb drives that are not the ones that the OS is loaded on..

Any help greatly appreciated!..

---

### Post by amsterdam on 2007-06-27
1: Are you running this through the live CD? If so, I am not sure how the live CD handles USB devices.

2. You may have to 'mount' the disk that is not being displayed. If it is a Windows installation on the disk try running this....
     sudo mkdir /mnt/disk
     sudo mount -t ntfs /dev/hda1 /mnt/disk
This is assuming that it is the first ide disk, and you want the first partition. If that does not work there are great tutorials on mounting disks. Try a forum search for 'mount hard drive'.

3. If you are trying to do something in the terminal (command) try putting a 'sudo' before the command.  Such as "sudo rm foo".

---

### Post by mickmade on 2007-06-27
For question 3, if you are talking about writing and editing stuff on your NTFS-formatted partition, you need to install ntfs-g3. Simply run:
sudo apt-get install ntfs-config
It will install ntfs-g3 and a GUI config tool under System Tools for you.

---

