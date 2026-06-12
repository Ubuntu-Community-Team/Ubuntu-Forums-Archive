---
title: "installing drivers from README files"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by havfunonline on 2007-12-31
I've attempted to download a driver for a new USB wireless network adapter.  I'm not sure it'll work if I do install it, and I'm not even sure it's the right one.

However, just in case it is, I've attempted to follow the instructions in the README file, it started working for a while, but I don't speak commandline, so I'm very lost and it keeps spouting error messages, and I'm very much expecting it to tell me that I've just broken everything.

Any pointers/hints? anyone feel like messaging me through it? Thanks for your help.

---

### Post by Cypher on 2007-12-31
A few details please..was the driver a loadable module? Where did you install it? What commands did you use to load/run it?

---

### Post by havfunonline on 2007-12-31
I downloaded it onto the desktop.  It doesn't appear to have any easy way to load or run it, it has a complex system of makefiles etc used to do anything with it, but I haven't got the first clue where to start.  I downloaded it from [http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html), its the fourth row down (RT2501USB(RT73:RT2571W/RT2573/RT2671)).  

Other than that I think I have less idea than you, sorry I'm so rubbish at all this, pretty new to the field of Linux

---

### Post by Cypher on 2007-12-31
OK..I downloaded the file and took a look at it, since this is a source Kernel driver, to compile it you will need to download the Kernel srouces first.
```

sudo apt-get install linux-source

```
Then you'll need to install the build tools
```

sudo apt-get install build-essential

```
Now from the command line follow the instructions in that readme..
```

cd ~/Desktop
tar -zxvf RT73_Linux_STA_Drv1.0.4.0.tar.gz
cd Module
cp Makefile.6 Makefile
make all
sudo mkdir -p /etc/Wireless/RT73STA
sudo cp rt73.bin /etc/Wireless/RT73STA
dos2unix rt73sta.dat
file rt73sta.dat <-- This should say binary
sudo /sbin/insmod rt73.ko
sudo /sbin/ifconfig rausb0 inet 192.168.100.50 up

```
For now, you can start with a STATIC ip and go from there..

---

