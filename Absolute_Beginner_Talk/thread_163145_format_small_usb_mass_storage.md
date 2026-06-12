---
title: "format small usb mass storage"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-20
I have an mp3 player that uses a 256 mb flash memory card. The player plugs into the usb port - shows as a usb drive -  and I am able to transfer files back and forth. It would seem that if I delete files they show up in a .trash directory on the "drive" and I am able to go to that directory and delete them - however the drive space seems to diminsh each time I do this - and I have to boot into windows and re-format the card (FAT).

**My objective is to be "Windows-free"  one day :)  and so I wonder how I can format the memory card on this little palyer with Ubuntu Linux ?**

---

### Post by 5-HT on 2006-04-20
If you are using GNOME, a graphical way would be to go to System > Administration > Disks, and format from there if it's listed.

From the command line, 'fdisk' can edit the partition tables and 'mkfs' can format.
To learn their syntax and options, 'man fdisk' & 'man mkfs'.

Be careful with these though, it would not be a pleasant experience if the wrong device is selected.

About deleted files getting sent to the .trash directory, if you are using nautilus, you can go into nautilus' preferences menu and select the option to add a delete command that bypasses the trash (other file managers should have a similar option).

HTH

---

### Post by cliff0108 on 2006-04-20
Thanks kindly - I'd forgotten about the GUI disks interface.

---

