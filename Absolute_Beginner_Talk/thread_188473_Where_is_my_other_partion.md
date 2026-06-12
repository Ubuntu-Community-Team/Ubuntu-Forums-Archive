---
title: "Where is my other partion?"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by slimdog360 on 2006-06-04
Today I just bought a new 60Gb hdd for my laptop. When I was choosing how to partion my hdd in gparted, via the ubuntu install, I chose to create a 14GB space for ubuntu, another 14GB space for winxp, aabout 800MB as a linux swap file and the reat as a fat32 partion so I could share file between windows and ubuntu. 
I havent installed windows yet but using ubuntu I cant see the fat32 partion.
Can anyone help me out here
thanks

---

### Post by kayrune on 2006-06-04
you have mounted the fat32 partition ?

open a terminal and make a folder
```
 mkdir share
sudo mount /dev/hda4 /home/<your username>/share

```

I assume hda4 is the name of your partition based on how you described your partitioning. (you will find the correct name in gparted)

you need to edit /etc/fsab to do this automatically at every boot
```

sudo gedit /etc/fstab

```

---

