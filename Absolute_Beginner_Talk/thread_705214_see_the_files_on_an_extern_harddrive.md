---
title: "see the files on an extern harddrive"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by EMiRo on 2008-02-23
hi. I started with Ubuntu two days ago, and now i'm in a dilemma :P
i have an external usb harddrive with ntfs formatting, containing all my backupfiles that i want to copy to ubuntu. but when Ubuntu finally let's me see the harddrive as "disk" the two only files i see are a map named "windows" and a .txt file named "$$rename.txt"

anyone know what the problem is?

---

### Post by EMiRo on 2008-02-23
please help, i need all the files on that HDD. and i have no clue what to do .

---

### Post by sayakb on 2008-02-23
How much free space is the HDD showing? Does it really have the data in it? Also, please make sure that fuse-utils is installed:
sudo apt-get install fuse-utils

---

### Post by EMiRo on 2008-02-23
when i go to preferences i can see that there are 3345 files on it in 150 folders. 150 gb is used and 330 is free (and windows shows the same results, when i connect to another computer. )

EDIT: and i just installed fuse-utils, but it didn't change the outcome of the hdd.

---

### Post by quinnten83 on 2008-02-23
try reinstalling ntfs-3g
helps me everytime
First remove the hard disk/memory card, whatever
sudo apt-get install ntfs-3g
then in system tools>ntfs configuration tool check mark write support for internal device and write support for extrernal device.

if it doesn't work right away, try restarting the X-server
Alt-Ctrl-bkspc

if that doesn help, try a full restart
if that doesn't help, than I can't help you further.....
you'll need a guru!:lolflag:

---

### Post by EMiRo on 2008-02-23
thank you for all response, but as the noob i am, i just realized the harddrive have to be formatted or something. because i was installing windows on this machine first, but when it failed i installed ubuntu instead. during the windows install i must have fomatted and chosen the ext. hard drive to install it on.. lol. so now i'm recovering my data from the hard drive. 

anyways. thanks for all help.

---

### Post by david_kt on 2008-02-23
> **EMiRo said:**
> hi. I started with Ubuntu two days ago, and now i'm in a dilemma :P
i have an external usb harddrive with ntfs formatting, containing all my backupfiles that i want to copy to ubuntu. but when Ubuntu finally let's me see the harddrive as "disk" the two only files i see are a map named "windows" and a .txt file named "$$rename.txt"

anyone know what the problem is?

How did you make the backup files? Did you use special program ? How do you recover the backup files in windows?

DK

---

