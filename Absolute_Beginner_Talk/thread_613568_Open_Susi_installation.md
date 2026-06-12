---
title: "Open Susi installation"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by jmfa59 on 2007-11-15
I tried to install Open Susi 10.3 on top of Vista and Gutsy of course in a third partition the problem after patitioning ( I tried to do manually, let the system do it ) and installing the files when the system reboot for the first time and before configuring the network and the password it gives an option boot from hard disk where I will see Vista & Gutsy (no sign of Susi) or installation where I will do it all over again I tried to do it Vist alone same problem is an order problem or the file is corrupt or it is simply not possible.

---

### Post by natehatewindows on 2007-11-15
if i understood you right grub does not show SUSE.


do you know where the location of SUSE is? just run gparted and it should tell you (sda1,2,3,4,5 ect).

i think (i have never done this but i have with wondows and i think it should be the same) you can just edit your /boot/grub/menu.lst to include suse. 

```
sudo gedit /boot/grub/menu.lst
```

and add a option at the bottom where you see something like this for windows. just add it under ubuntu,

title		Windows Vista(loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

i would read a little more but this is what i would try first, and dont forget that if you want it to be default put it right under the ## ## end default options##

---

### Post by jmfa59 on 2007-11-15
I am not familiar with GRUB. I think it didn't reach that point the installtion is not finish I installed Susi 10.3 beta and had no problem but this one no way to do it.
THANKS

---

