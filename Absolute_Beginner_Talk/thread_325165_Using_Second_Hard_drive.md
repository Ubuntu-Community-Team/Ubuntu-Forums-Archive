---
title: "Using Second Hard drive"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by azziman on 2006-12-25
hi all recently put ubuntu into vmware - want to test it fully before i move across :-D 

first up i want to use  a second hdd

so i opened terminal and put this in:

sudo apt-get install gparted

that gave me gParted (System -> Administration -> GNOME Partition Editor (GParted))

i used to that to CRTL+N /dev/sdc then it says it will create a msdos patition - just pressed CREATE

in terminal and type in: sudo mkdir /media/hdd3

sudo chmod 777 /media/hdd3

sudo gedit /etc/fstab

in this file type in at the bottom: /dev/sdc1 /media/hdd3 ext3 defaults 0 0

file and save.

thats how far i get and then i get stuck ](*,) 

any help to get it done will be most helpful 8)

---

### Post by pseudonym on 2006-12-25
> **azziman said:**
> in this file type in at the bottom: /dev/sdc1 /media/hdd3 ext3 defaults 0 0

file and save.

thats how far i get and then i get stuck ](*,) 
What errors do you get when you try and mount the drive? I found out recently that Ubuntu is using the UUID naming scheme for drives in /etc/fstab now. [This thread]("http://www.ubuntuforums.org/showthread.php?t=286758") may shed some light on it for you.

---

### Post by azziman on 2006-12-25
oki think i managed to get it done, is this even the correct way ? as i followed a tutorial but some of the steps didnt really work so i asjusted it slightly:

-------------------------------------------------------------------------------

sudo gedit /etc/fstab

in this file type in at the bottom: /dev/sdc1 /media/hdd3 ext3 defaults 0 0

file and save.

open gParted again and then go into /dev/sdc, right click the unallocated space and press NEW, leave defaults and press ADD

press the Apply (green tick) in the gParted interface, wait for it to finish and then close the gParted interface 

back in terminal type in: sudo mount /dev/sdc /media/hdd3


if that doesnt work go back into gParted and right click on the /dev/sdc1 and press mount to button from menu

restart ubuntu, drive should appear in the PLACES area and on the desktop

--------------------------------------------------------------------------------------------

the lost+found folder in the new hdd seems to be restricted? i cant get access to it ...... the deleted items go into the trash folder though. is that the way it should be ??

but i noticed when i created the partition that i could make  fat32, fat16, etc as well .... so which is better ext3 or fat32 ? would leaving it in fat32 allow for me to use the hdd in both windows and linux environments ?

and the UUID how would i be able to get that for the hard drive ....... 



sorry for the questions ... but i just getting to grips with ubuntu

---

### Post by pseudonym on 2006-12-25
> **azziman said:**
> oki think i managed to get it done, is this even the correct way ? as i followed a tutorial but some of the steps didnt really work so i asjusted it slightly:

-------------------------------------------------------------------------------

sudo gedit /etc/fstab

in this file type in at the bottom: /dev/sdc1 /media/hdd3 ext3 defaults 0 0

file and save.

open gParted again and then go into /dev/sdc, right click the unallocated space and press NEW, leave defaults and press ADD

press the Apply (green tick) in the gParted interface, wait for it to finish and then close the gParted interface 

back in terminal type in: sudo mount /dev/sdc /media/hdd3


if that doesnt work go back into gParted and right click on the /dev/sdc1 and press mount to button from menu

restart ubuntu, drive should appear in the PLACES area and on the desktop
that looks OK to me. if it mounts successfully, reboot so you can access it as user.


> **azziman said:**
>  the lost+found folder in the new hdd seems to be restricted? i cant get access to it ...... the deleted items go into the trash folder though. is that the way it should be ??
Yes. You don't want to access the lost+found folder. It's to do with the ext3 filesystem's journal and has nothing to do with your trash folder. Read up on that [here]("http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html") if you want

> **azziman said:**
> but i noticed when i created the partition that i could make  fat32, fat16, etc as well .... so which is better ext3 or fat32 ? would leaving it in fat32 allow for me to use the hdd in both windows and linux environments ?
fat32 will allow access from windows and linux. It's safer to use windows formatting tools to format it, though (Control Panel>Admin. Tools>Disk Management) . You won't be able to run linux programs from a fat32 drive, however, because it doesn't use the permissions system linux needs to run programs. For that you'll need ext3 or any other linux file system (eg. reiserfs, xfs) fat32 is fine for data storage, though, provided your files are smaller than 2 or 4gb, I can't remember which.

> **azziman said:**
> and the UUID how would i be able to get that for the hard drive .......
See the link I made in my first post above. 



> **azziman said:**
> sorry for the questions ... but i just getting to grips with ubuntu
no problem. you ask whatever questions you feel you need answers to :)

---

### Post by azziman on 2006-12-25
great yep i found the UUID:

sudo vol_id -u <partition>

---

