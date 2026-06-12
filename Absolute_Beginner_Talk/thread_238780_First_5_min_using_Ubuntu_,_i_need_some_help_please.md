---
title: "First 5 min using Ubuntu , i need some help please :)"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by thaer on 2006-08-18
hi guys 

this is my first 5 min using Ubuntu , and my first " working " OS. I just moved from win XP and yeah i really like this linux system ( i installed it not live CD ) 

i have some questions, when i try to accsess my HDD , i get this annoying message !! how can i avoide it ? this message comes when i try to go to any partittion other than the one i installed ubuntu on , excluding my USB drive.

[IMG]http://i7.tinypic.com/24x48c0.jpg[/IMG]

and the messenger which is already installed , when i sing in , it shows my buddy list then the program just disappears !! i mean the Gaim Internet Messenger !! 

hope some1 could help me with these stuff :-D :-D  

thx

---

### Post by meng on 2006-08-18
What message are you getting?
How are you trying to access the drive?
What type of partitions are giving you trouble? NTFS perhaps?
Just need a few more details here.

---

### Post by anaconda on 2006-08-18
pmount is used to mount removable drives, like USB-stiks. CD:s etc.  It doesn't work with fixed drives. (like HDD:s)

if you want to mount a HDD-partition you can add the mounting commant to your /etc/fstab -file.. after that each time you boot the HDD-partitions are mounted and accessible automatically.

---

### Post by givré on 2006-08-18
I guess it's a windows partition which isn't mount at bootup.
There is two way to fix that problem:
- You can use it just like an usbdsik, it means that it will only be mount when you click on it. For that, you will need to edit your pmount.allow
```
gksu gedit /etc/pmount.allow
```
and add /dev/hda5 at the end of the file. 
(pmount is the program that mount removable device)
- You can also mount it at bootup by editing your /etc/fstab file that contain information about partition mount at startup. For that, i recommand you to look at [http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

### Post by anaconda on 2006-08-18
Or you can (first) learn how they are mounted manually. Open terminal and try:

sudo su   (to get root rights)
mkdir /mnt/disk  (make the directory you mount your hdd to)
mount -t auto /dev/hda1 /mnt/disk    (mount the hdd)

the "hda1" is the argument you have to "know" hda1 is the first IDE drive, hdb1 is the second etc.. if you have SATA HDD then the first is sda1, second sdb1 etc.. and the 1 in the end is the number of the partition you want to mount. so if you want to mount 2nd partition from your 2nd SATA-hdd then the command would be:
mount -t auto /dev/sdb2 /mnt/disk

---

### Post by seshomaru samma on 2006-08-18
About Gaim
open a terminal (Applications > Accessories > Terminal)
and write 
```
gaim
```
if there is any output in the terminal , copy it and post it on this thread

---

### Post by thaer on 2006-08-18
thank you all , especially givré , your first way worked perfectly :o :o 

thank you

---

### Post by thaer on 2006-08-18
thank you all for your help :D :D  really appreciate it . 1 more problem , hopefully last, the audio player , when i try to play any audio file ( i tried mp3 and wma) the audio player says that i need a decoder , i downloaded also Noatun , but it doesn't play at all 

if u wanna have a look at the message : 

[IMG]http://i7.tinypic.com/24y91ts.jpg[/IMG]

as i said , hopefully last problem :D  

thx

---

### Post by givré on 2006-08-18
Have a look there :
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Or simply get everything automaticly :
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by thaer on 2006-08-19
thank you , u made my dream of a complete OS come true !! really thank you 

now , if u can tell me , after installing Ubuntu partition magic won't run to modify my old partitions , [IMG]http://i8.tinypic.com/24zamom.jpg[/IMG]

i even tried formating my whole hard drive , but same problem . looks like ubuntu is blocking me from editing my partitions .

---

### Post by givré on 2006-08-19
Last time i used partition magic, it totaly change my partition table, and i had to change it manually.
Try to not use it, prefer gparted
```
sudo apt-get gparted
```
or to do things more safely, it's better to run gparted from the live CD (if you have it) or to try gparted liveVD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
It's always better to modify partitions when they are not in use.

---

### Post by thaer on 2006-08-19
wow man , you're like Ubuntu's Bill Gates , you have a solution for everything !! that's mad :) don't worry just give 2 months using Ubuntu and i'll be the same as you :) . I'm gonna try gparted live CD and tell you what happens . Thank you :)

---

### Post by NorseDude on 2006-08-19
I had the same problem with not being able to mount anything, so what to do? Simple, really. I had given root the entire hard drive during setup and nothing to the user. I don't really see the connection, but I reinstalled, gave root and swap just the space they needed and user the rest. This worked great! I have never had problems mounting anything ever again. I also tried to use an USB mp3 player as a storage device. Worked every time.

As for mp3 and wma files, they are not supported by Linux "out of the box". You need a codec to play them. This can be found everywhere if you search. I think Xmms supports at least mp3's right away, and MPlayer and Totem are two great allrounders that plays more or less anything. Or so they say, though I haven't had the chance to try them yet. (got Linux a few days ago and don't even have an online connection on it yet). ;)

Just a few tips. ;)

---

