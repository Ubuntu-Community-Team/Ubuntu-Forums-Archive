---
title: "usb hard drive mount"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by steve789 on 2006-04-19
hi i need help mounting a laptop HD that has win3.1 and i would like to erase
everything :files,partitions. so I wont have to burn a cd for a 5mb file and yes i know pendrives exists but for now i would like to use this hard drive.

---

### Post by McLogic on 2006-04-20
If the hard drive is in a usb enclosure, then Ubuntu should mount it automatically. It will be fat16 or fat32 -- I bet it will be fat16. 

Use Synaptic to install "gparted" it is a program to manage your disk partitions. Then type "sudo gparted" and give your password.

gparted is a nice GUI app that should be easy to understand. You want to pull down the menu on the right, and select the little disk. Then you want to erase the partitions that you will see and make a new one that is fat32.

Hope this helps.

---

