---
title: "how do i remove ubuntu?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by CraniumDesigns on 2007-03-23
how can i remove ubuntu and reformat the hard drive. i dont want to use windows. i just want a blank formatted disk. thank you.

---

### Post by AndyCooll on 2007-03-23
For what purpose?

:cool:

---

### Post by mikewhatever on 2007-03-23
> **CraniumDesigns said:**
> how can i remove ubuntu and reformat the hard drive. i dont want to use windows. i just want a blank formatted disk. thank you.
Put in either ubuntu install cd or gparted live cd, reboot, delete all partitions, create new ones and format whatever you want.

---

### Post by seshomaru samma on 2007-03-23
boot from the liveCD run gaprted (if you cant find it in the menus . open a terminal and write : sudo gparted)
format all your partitions

---

### Post by IanGB on 2007-03-24
Tried this on my laptop but after using Gparted no windows set up disk would see the hard drive, why please?

Ian

---

### Post by halitech on 2007-03-24
how did you format the drive? did you use fat, fat32 or ext2?

---

### Post by Circus-Killer on 2007-03-24
i've had this problem before. if i remember correctly, creating partitions without formatting isnt good enough for windows, you need to format them with a specific filesystem (i dont even think they gotta be windows filesystems). 

and then once you start up the windows setup, it should give you the option to reformat partitions.

---

### Post by halitech on 2007-03-24
if you are booting from the windows setup disk, you should have an option to delete partitions from there and create them as needed. what version of windows?

---

