---
title: "now.. its the modem!!"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by nightwolf2k5 on 2006-07-19
hey fellow ubuntu mates!
sorry i had to create this new thread.. i guess... since i kinda got through the first phase of mounting the ntfs partitions without any problem.. i guess its all cool now..
now.. its the modem!
ok.. i got this billion adsl modem.. its got linux drivers.. when i like click on them.. i had to like extract them and then its like i got this readme file which made asolutely no sense to me! is there like a general procedre out there or should i post the contents of the readme file.. so that someone can explain it to me..
i shall be forever greatful.. with this.. and i'll be one step closer to eliminating the use of windows!:cool:

---

### Post by richbarna on 2006-07-19
> **nightwolf2k5 said:**
> should i post the contents of the readme file.. so that someone can explain it to me..
i shall be forever greatful.. with this.. and i'll be one step closer to eliminating the use of windows!:cool:

Yeah, let us have a look at it.

---

### Post by nightwolf2k5 on 2006-07-19
> 
This document describes the steps of the installing the E2 or Hasbani (BIPAC - 7000) on the LINUX. Driver version 062802_REL1.7

First, uncompress the package: USBNT_E2_LINUX_062802_REL1.7.tar.gz
# tar zxvpf USBNET_E2_LINUX_062802_REL1.7.tar.gz

A directory names E2 will be created under current directory.
Secong, changing directory to the "E2" directory
# cd e2

Third, compiling the source code
#make

At last, copy the firmware file "CnxE2FW.bin" to directory "/etc"
#cp CnxE2Fw.bin /etc/CnxE2Fw.fin

Now, you can install the driverby the command below under current directory:
# insmod e2.0

If you would like to install driver elsewhere, please copy the e2.0 to the directory: /lib/modules/2.4xx-xxx/kernal/drivers/usb first.

If the network does not up automatically, run the folowing commands
#ifconfig hsb 0 up
# dhcpcd -n hsbo

this was from the drivers i got from the internet..
the drivers i got form the internet company for the modem also has drivers for linux.. but.. its in some rpm file.. and i cant extract it or open it..
actually.. if the rpm files are installed.. it might be better.. but.. i guess anythin will do..

---

### Post by 3rdalbum on 2006-07-19
You can install the RPM. First, you need the alien program:

```
sudo apt-get install alien
```

Put the RPM file directly into your home directory. Open a terminal and type:
```
alien nameOfFile.rpm
```

(where nameOfFile.rpm is the filename of the RPM)

This will create a .deb package for you. Double-click the .deb to install it, if you are running Dapper.

I suggest viewing some online tutorials about the command line, so you can understand Linux installation/compilation instructions like the one you posted above.

---

### Post by nightwolf2k5 on 2006-07-19
whats an alien program? and where is my home directory? the only place where i can copy files is on to my desktop!! i dont have write permissions on the other drives!

edit
i tried it anyways.. it said package could not be found:(

---

### Post by Sonic Alpha on 2006-07-19
If you have no net access at all through Ubuntu, you'll need to download the Alien package, **and all it's dependencies** via [the package site]("http://packages.ubuntu.com/") with another computer/boot, and transfer them to your linux computer/boot via CD or USB stick.

Alien is [here]("http://packages.ubuntu.com/dapper/admin/alien").

---

### Post by nightwolf2k5 on 2006-07-19
ok.. i downloaded the alien thingy.. i'll like copy it into the desktop  (of ubuntu) and try it..i'll post what happens..


EDIT:

hey man.. this is what happened.. i got this message..
error: dependency is not satisfiable : debhelper

](*,) ](*,)

---

### Post by nightwolf2k5 on 2006-07-19
sorry abt double posting.. anyways.. i kinda figured out the way out of that error.. did somethin.. not sure what!
anyways.. i see that it needs some more parts or somethin.. how do i install them but more importantly.. how do i get them?!

---

### Post by Sonic Alpha on 2006-07-19
> **nightwolf2k5 said:**
> hey man.. this is what happened.. i got this message..
error: dependency is not satisfiable : debhelper

> **Sonic Alpha said:**
> you'll need to download the Alien package, **and all it's dependencies**

Don't forget all the dependencies, and their dependencies (and so on).

---

### Post by nightwolf2k5 on 2006-07-21
ok.. so i finally got alien installed.. and got all the dependencies done too!! now.. when i tried to run the command to install the rpm file.. i get.. the file "billion" cannot be found! :(
the file is right there on the desktop.. but.. somehow it cant find it!
also.. i tried double clickin on it.. what i ended up with was with archive manager.. so.. i unzipped it and got two folders with a bunch of files! and i'm like.. now what!! so.. help.. anyone!

---

### Post by nightwolf2k5 on 2006-07-24
erm.. bump!!

---

