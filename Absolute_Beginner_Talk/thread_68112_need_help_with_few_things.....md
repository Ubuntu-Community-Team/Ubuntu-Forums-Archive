---
title: "need help with few things...."
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by aran384 on 2005-09-22
tonight when i finished downloading 5.10 breezy :D .... am gonna install it and am wanting to do a few things to it... 

i want to when i install it, setup my second hdd that is in it as a 2nd drive like in windows xp

but not mounted onto / or /home

i then need to transfer my images over from a windows shared area and i want a background changer installed if there is one or a way to get it to change every few days or summat....

cause i have thousands of backgrounds :D.....

---

### Post by aran384 on 2005-09-22
cant any1 help :(  :neutral:

---

### Post by skoal on 2005-09-22
Howdy,

I think I understand what you want to do, but it might help first if you provide some sort of visual represntation of your hdd(s) layout.  For example,

hda:
/dev/hda1 - Windows XP
/dev/hda2 - /boot (100MB, ext3)
/dev/hda3 - / (20GB, ext3)
/dev/hda4 - /home (60GB, ext3)

hdb:
/dev/hdb1 - (120GB, fat32)

...or whatever.  That would probably help in my understanding here.

I just took a guess up above.  With my example, hdb (/dev/hdb1) would show up in XP as drive D: (probably), and in Ubuntu you could create a directory (path) somewhere in /media/windows (or /mnt/drive_d, or /home/drive_d, or whatever), and then just follow the Wiki [guide ](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29%7C%28mount%29) for mounting a fat32 drive in Ubuntu - you could use the script or do it manually....

\\//_

---

### Post by aran384 on 2005-09-22
right i got 2 computers .... 

1 xp and 1 ubuntu :D..... 

Soon im gonna update my ubuntu to breezy and when i do i need to access my windows shared folders and copy my background over 

during my install of breezy i want to setup 2 hdds but i dont wanna mount the second....

hda this beening /
and 
hdb this beening something else but not mounted , well need it to be sperate... (if u understand this )....

so maybe i guess mount it to a folder then that might make it easier.... but not something like / or /home..... 

gotta be /home/aran/Files or summat..... 

if u understand me....


and then  when all that is taken care of i want to get some kinda background changer cause i have thousands of backgrounds..... and i dotn wanna change them all time...

---

### Post by aran384 on 2005-09-22
change of plan really .... am not gonna install breezy yet but i still need 

2nd hdd sorting onto a folder ....

and 

background changer....

---

