---
title: "bootit ng"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by erniewinner on 2007-02-24
hi all,

i use bootit ng and won't change that. i stopped using ubuntu and stuck with xandros because of one specific issue with ubuntu. the issue is this:
i like to use booit because you can choose to have only the disks you want booted and hide any others. but if you forget to add a partition to the ubuntu boot choice when setting up ubuntu. it will think your whole disk is blank and will just re partition it. when you have hidden drives. this ain't a good idea... has this changed now? hope ya get me. thanks.:popcorn: :guitar:

---

### Post by klein de usa on 2007-02-24
hi
ubuntu edgy, both live and alternate cd see ntfs partions but when you use bootit ng and you chose a partion and tell it to boot a partion and then go to next boot device , bootit ng moves the boot flag to that partion so your program thinks it is on the first partion of that drive and if you have bootit ng set to hide all other partions then ubuntu thinks it is just blank space.
What i do for my self is to set up my native and swap file in bootit ng, then boot stright from cd without bootit ng and then ubuntu will see the ntfs partions and ask you whitch partions you would like to make native and swap (name your partions in boot it when you set them up) then after you set the root in ubuntu and swap it will ask you where to install grub, make sure you put it on the native partion and watch out for the numbering of partions grub starts with 0 (hd0,0) is the first hard drive first partion, (hd0) is the mbr so watch out it can get confusing, 

this is just what i have done and found out my self,

---

### Post by erniewinner on 2007-02-25
does ubuntu have a "back up" to cd and restore feature then or would bootit do a good job of backup... if i want to reinstall on a machine that  already has an os i am uneasy.
by the way i use fat 32. not sure if that makes a difference.

---

### Post by klein de usa on 2007-02-25
hi 
i have install ubuntu with a dos 6.22 partion and it saw dos, and there is a program called aptoncd it doesn't back up the hole ubuntu it backs up what ever packages you have updated or installed to a cd , when you reinstall you reinstall aptoncd program in ubuntu and reinstall all your packages from cd insted of from the net, for me i have installed aptoncd but i am going to back up ubuntu on cd with terabight back up utility it takes a snap shot but it might be very large maybe a couple dvd's, my back up from aptoncd is 400mb and that is just the packages i have down loaded and upgrades.
the main thing with bootit ng is is not use it when installing ubuntu, ubuntu needs to see all partions , then make sure you put the grub in the natave partion with ubuntu. 

i'm by no means an expert, iv had my bumps in the road but that is the way it worked for me

---

