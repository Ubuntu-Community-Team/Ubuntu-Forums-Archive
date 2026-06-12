---
title: "gparted crashed live cd help"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by fanny on 2007-03-04
after to much time im trying to install my ubuntu. i was told ( after gparted crashed ) to download gparted livecd and to make the new partition from there . 
first i dont know which type of format i need to make to my new partition . ntfs ext2 ext3 etc... please tell me what i need to choose.
i tried to format it to ext3.. but when im back to ubuntu installation i still have those 3 options:
1) resize IDE2 master . partition #1 (hdc1) and use freed space. ( remember i dont wont to install in c )
2) erase entire disk........... (no)
3)manually edit ..............(doesnt work for me i tried until the crashed )

its exactly like it was/ i forget to say i have  c 40g and d 40g also my xp is in c: i wont it in my computer. 
thanks!

---

### Post by xyz on 2007-03-04
[TRY THIS - GOOD LUCK]("http://www.psychocats.net/ubuntu/partitioning")

---

### Post by fanny on 2007-03-04
sorry but it didnt help me..

---

### Post by fanny on 2007-03-04
anyone?

---

### Post by fanny on 2007-03-04
i tried again but no success . please answer and remember im totally new to linux and 100% dumb , maybe then i will install ubuntu ...

---

### Post by rpm13 on 2007-03-04
Yeah Ive also seen gparted crash
In that case two things help

1. swapoff
2. use parted

though parted is a command-line tool which can be intimidating fro a newbie

---

### Post by annda on 2007-03-04
am i right that you have created an ext3 partition using gparted livecd? or did you try it and failed?

remember, you need a so-called root partition (/ with ext3 filesystem) and a swap partition (/swap, filesystem: swap size: 1GB is a good idea).

when you tried again, did your computer crash again when you chose manual partitioning using ubuntu cd? or did gparted crash again?

the more info you give us, the more likely we are to come up with a solution.

can you boot from livecd, launch the terminal (applications > accessories) and post the output of 
```
sudo fdisk -l
```

this will show how exactly your drive is partitioned at the moment. oh, and are C and D two disks or two partitions on the same disk?

---

### Post by fanny on 2007-03-04
o.k. i will explain . i have xp in my computer i have c and d in the same HD. now i have ubuntu live cd i tried to install manually until gparted crashed and i cant see d: anymore. after that i downlaod gparted live cd and tried to make d: ( there is a option to format so i did it and format it to ext3) i was back to ubuntu installation but still i couldnt install manually and the installation dont give me the option to "install in the biggest free space " only the 3 options that i wrotw above. 
*gparted crashed when i used ubuntu cd , not when i used gparted live cd.

---

### Post by annda on 2007-03-04
ok, i think i get the picture. here's my suggestion.

since gparted live cd works, boot from it again and delete the new partition you have created.

then you can try ubuntu live cd again. it should see that you have free unpartitioned space on your disk and give you the option of installing on that.

alternatively, you can use gparted live again and prepare TWO partitions for ubuntu (ext3 and swap). during install, choose manual partitioning and choose and mount (no need to partition again here) those two new linux partitions as / and /swap.

i hope it works this time.

---

### Post by fanny on 2007-03-04
thnks man i installed successfully

---

