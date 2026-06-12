---
title: "Recovering data after a system failiure"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by kgls13349 on 2006-11-21
Hello people,
a few days ago the server i had built up running ubuntu crashed, it was a hardware failiure, ive now replaced the parts and reinstalled ubuntu exactly the same as before but now i cannot access the hdd i used as storage, if i have it connected at runtime the system hangs during the grub loading screen
ive even tried, becouse is a sata drive, connecting it onces the system has booted up and unsuprisingly it didnt work, ive tried to get at the information on the drive using other machines,

obvoisuly the hdd cannot be seen in windows (my main pc is a windows machine unfortunatly) so i wasnt able to get at my university work, ive tried loading up the second boot on my main machine which is ubuntu and although that could see the drive it said it could not mount it something like "sdb is not removable, unable to load pmount" or something along those lines

This is VERY important to me, there is huge amounts of university for that i cannot redo on this drive!

Does ANYONE have any suggestions as to how i can access the drive! even if its just for a few miniutes so i can transfer files to another drive!

THANK YOU IN ADVANCE!

---

### Post by John E on 2006-11-21
The only thing I can suggest is taking out your hard drive and putting onto a Windows system running Partition Magic. PM allows you to copy entire partitions to another drive (not file-by-file, but partition-by-partition).

There's probably a similar utlity for Linux but I'm a newbie myself so I don't know what it would be.

---

### Post by kgls13349 on 2006-11-21
thanks for the reply,
i would actually have to setup partition magic int he first place to try that :)
neither of my windows machines have it on them, its confusing becouse im pretty sure theres nothing wrong with the drive its only like a month or so old

but thats the best solution ive had so far, thanks

---

### Post by smoker on 2006-11-21
why dont you download and burn the gparted iso, it can also copy partitions, i've used it for this several times. available from sourceforge.net

sorry edit: i should've added the gparted disc will boot before eg, windows starts, if you attach your harddrive as a secondary on your windows machine you will still be able to use gparted!

---

### Post by kgls13349 on 2006-11-21
ok thanks, i have nothing to loose by trying gparted so ill give it a go, (the only problem being i dont have any blank CDs, only DVDS grrr just my luck :( )

the only thing im worried about is, yeah ok i copy the partition thats fine but WHAT if theres a file corrupted on the partition thats stopping it working?
copying the partition form one drive to another would fix the problem is it is a hardware problem but (unless im being stupid) it wont fix a software based problem

i would willingly reformat the drive as long as i could just pull off like 2mb of files from it

---

### Post by smoker on 2006-11-21
the thing is, if you copy the partition, you can try other methods to retrieve your data and still have the original to fall back on if the worst comes to the worst. if the file table is corrupted, there may be linux apps that could correct this, but i'm quite new to this myself so maybe someone with a greater experience of ubuntu/linux could suggest some apps to try.

best of luck

---

### Post by kgls13349 on 2006-11-21
Thanks for the reply,
i think im getting a bit too stressed out over this at the moment, i proberly should just leave it for now before i completely mess it up :-? 

i knew i should have kept backups at uni ](*,)

---

### Post by kiyometane on 2006-11-21
simply connect the hdd to a windows pc as slave. then access your data.

---

### Post by kgls13349 on 2006-11-21
wont work, tried it, its formatted as ext3 under linux, windows just wont look twice at it, although i wish i could do that :(

---

