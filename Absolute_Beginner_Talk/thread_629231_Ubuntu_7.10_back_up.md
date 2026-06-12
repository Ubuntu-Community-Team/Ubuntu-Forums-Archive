---
title: "Ubuntu 7.10 back up"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by dnice on 2007-12-02
Hello all very new to ubuntu and in need of some guidance. Could anyone tell me how to back up my current config. Can i make another CD with all that i have installed on it. If anyone could help please explain it step by step. I am not only new to Ubuntu but computers in general.


Dnice

---

### Post by Daveth on 2007-12-02
well, you have a range of options:

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite?highlight=%28backup%29](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite?highlight=%28backup%29)

or some of this 

[https://help.ubuntu.com/community/BackupYourSystem?highlight=%28backup%29](https://help.ubuntu.com/community/BackupYourSystem?highlight=%28backup%29)

I use sbackup myself, writing to an external usb hard drive. Sbackup does not tell you when it has finished (or at least the version I use doesn't) but i find the system monitor a good proxy for when it has stopped (my cpus drop down in activity) - crude but it works!

---

### Post by sourcemorph on 2007-12-02
if i get it right u want a backup of all the softwares that u have installed on ubuntu...

i have wanted to do the same thing for a while and the best option that i know right now is.. aptoncd..

install this software, aptoncd, it will guide u to prepare an iso file containing all the debian packages installed on your system (they r present in /var/cache/apt/archives) and then later gives on the option of restoring them. at the time of restoring however it copies the .deb files (with the associated dependencies) to the /var/cache/apt/archives folder and you'll have to manually install them.

u can save some time by typing this command in the terminal

"sudo dpkg -i *.deb" without the quotes.

---

### Post by dnice on 2007-12-02
YOU GUYS ARE GREAT!!!! I feel the luv in the room, thanks a bunch

Dnice

---

### Post by mdpalow on 2007-12-02
Another option and more luv... :)

See links in my signature below...

---

### Post by dadawan on 2007-12-02
I backed up my entire Ubuntu partition using the CloneZilla/GParted Live CD.  It made a compressed image of the whole Ubuntu partition, which I then burned onto a DVD.    It wasn't exactly a very noob-friendly sequence though.   I thought I might make a tutorial for it.

-Kevin

---

### Post by dnice on 2007-12-02
Thanks to all, you are making the transition to ubuntu 7.10 smooth.

---

