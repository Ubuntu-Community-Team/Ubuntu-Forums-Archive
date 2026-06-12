---
title: "OK - so I messed up!"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by birdseye on 2006-12-09
first time install of ubuntu onto a pc with XP and lots of other programs on the HDD that I want to retain. got to the partitioning bit and when it asked for the size of the new partition I reduced it to a 30 GB min. Turns out that the new partition is the old one containing windows and the 30 GB is not enough space for what I want.

Anyway I aborted the Ubuntu installation for a different reason and am about to re-start it. How do I resize the windows partition whilst installing Ubuntu? And will the resized partition be correctly formatted NTFS or whatever or do I have to reformat it somehow?

---

### Post by taurus on 2006-12-09
You can use gparted from the LiveCD to resize your harddrive first, leaving one big empty space at the end.  Then tell the installer to use that empty space to install Ubuntu on it.  It will know how to handle it, creating / and swap...

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by birdseye on 2006-12-09
Understand what you say about Ubuntu, but can I use the partitioning tool to re- exapand my windows partition that I accidentally shrank further than I want. And if I can do that, how do I format that increased partition in the windows format without losing data. Or do I instead create an extra windows partition (the HDD is big enough) and then either transfer the existing system or simply use it for documents? Either way I will have enough space for Ubuntu

---

### Post by quarkhirad on 2006-12-09
> **birdseye said:**
> Understand what you say about Ubuntu, but can I use the partitioning tool to re- exapand my windows partition that I accidentally shrank further than I want. And if I can do that, how do I format that increased partition in the windows format without losing data. Or do I instead create an extra windows partition (the HDD is big enough) and then either transfer the existing system or simply use it for documents? Either way I will have enough space for Ubuntu

Hey just click on ur windows partition and then right click on it and say resize. Make the change in size and then just click apply. Note resizing partiotions may take time depending on their size so be patient.

---

