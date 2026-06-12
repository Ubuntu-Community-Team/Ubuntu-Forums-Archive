---
title: "xubuntu 6.06.1 installation..stuck!!!"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by subrat_shrivastava2000 on 2007-09-21
stuck!!!
dear friends,

hello
i attempted to install xubuntu 6.06.1 on my 128 MB RAM P4 1.99 Ghz desktop.
i reached upto the alternate cd ii installed it
----?>>>>>>>>>>>>>>>>>
1) chosen language,country & keyboard layout as american english.
 cd rom hardware pcmcia everything was detected.
2) when ireached the partitioning i selected the manual partitioning.
3) i selected not to use the the c & d drives bcoz windows was installed on it.
4) i selected the e drive selected the journaling file ext2 system.
resized it to 5 GB created a wsap of 4 GB
5) rest space a few more partions as ext3 & thats all 
6) i feel that the errore was in the partitioning.
7)the installation then proceeded..........after the 548 files were retrieved and the add softwares etc installed.
8) i saw a black c\screen for over 15 minutes with tao small rectangled on the screen black in background...
9)computer thenm froze........
10)i turned it off bcoz no keys were working 
11)oh boot up windows home was loaded..
12) e & f drives disappeared.
13)can please someone help??
14)
about setting the values for partitions in the partition manager??
about...........boot up or bootloader configurations???

plz reply.

---

### Post by kagashe on 2007-09-21
Following parameter is required:
boot: install debian-installer/framebuffer=false

Please note that you don't type the word "boot:" it is a prompt which will appear when you press Escape key on first screen and select "ok" when it tells you that you are leaving graphical boot menu.

Type "install debian-installer/framebuffer=false" at boot: prompt and press enter.

kagashe

It is 200th post for me!

---

