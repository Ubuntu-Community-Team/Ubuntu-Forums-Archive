---
title: "change ownership of folder"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by ken123 on 2007-10-14
i have come to a predicament, having gotten my first virus on windows in years, i couldn't get rid of it. i used to use ubuntu all the time, so i decided to set up a dual boot system on my laptop. i have a windows partition, ubuntu 6.06 partition, and an FAT32 partition for inter-operating system storage. i sert it all up and i can read/write to the storage partition fine, except when i made my windows operating system make the partition be the default for "My documents". the fold shows up and is able to be read on Ubuntu, but i can't write to it. i tried my basic skills in the terminal to change the ownership from root to myself, but nothing seems to work, any suggestions?

---

### Post by aysiu on 2007-10-14
You can't *chown* a FAT32 partition. You have to mount it with the right parameters. More details here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

