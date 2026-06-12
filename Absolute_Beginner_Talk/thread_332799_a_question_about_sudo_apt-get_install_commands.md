---
title: "a question about sudo apt-get install commands"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by fontenot_1031 on 2007-01-06
Hey I have a question.  I can't get internet on my ubuntu computer.  For commands like this...
```
sudo apt-get install libqt3-mt
wget http://ftp.wayne.edu/shared-qt_en_i386.deb
sudo dpkg -i opera_9.02-20060919.6-shared-qt_en_i386.deb

```

can you replace the "http://" with the address of a .deb file on a flash drive?

---

### Post by Solver on 2007-01-06
wget is specifically for Net downloads. But for dpkg you surely can replace and do, say,

```

sudo dpkg -i /media/usb/program.deb

```

---

### Post by fontenot_1031 on 2007-01-06
do you still need the sudo apt-get install command?


thank you very much btw

---

### Post by Atomic Dog on 2007-01-06
Nope just use the command he gave you.  You could also open the flash drive folder in nautilus and double click on the .deb file.

---

### Post by benuski on 2007-01-06
not when you're using "dpkg".  apt-get is a frontend that downloads a program, makes sure all the dependencies are satisfied, and then it runs "dpkg" on the .deb files.

---

### Post by 23meg on 2007-01-06
No, you'll still need that first command to install libqt3-mt, which is required by Opera. If you want to install without an internet connection, download the package libqt3-mt from [http://packages.ubuntu.com](http://packages.ubuntu.com) and install it with "sudo dpkg -i".

---

### Post by pistcivet on 2007-01-06
If you're installing Opera 9.02, you should know Opera is now at 9.10

Also, (to meet Opera's dependencies) you will probably have to add:```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```to /etc/apt/sources.list. (for Dapper, not sure for Edgy)

---

### Post by fontenot_1031 on 2007-01-15
Thank you for all the help everybody!!!

:KS

---

### Post by msak007 on 2007-01-15
Also if I'm not mistaken, you don't even need the terminal if you have a local .deb package already downloaded. Just double-click on it, and Ubuntu will use gdebi to install the .deb without you having to type anything in (aside from your password).

---

