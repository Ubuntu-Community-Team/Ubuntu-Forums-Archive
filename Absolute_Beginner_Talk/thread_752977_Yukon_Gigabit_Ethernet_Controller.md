---
title: "Yukon Gigabit Ethernet Controller"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Quality.mE on 2008-04-12
hello everyone,

im new to linux. i have the Gutsy Gibbon version installed.
i already had some problems installing it with the live cd. it wouldn't start because it would not recognize hardware parts. but anyway searching around i found some commands and got it installed. 

my problem now is installing my Yukon PCI-E Gigabit Ethernet Controller 88E8056.
i've got the driver from the marvell official site but when i try to install this is what happens 

#:~$ cd /home/***/Desktop/
#:~/Desktop$ sudo tar -xjf install_v10.50.1.3.tar.bz2 
#:~/Desktop$ cd DriverInstall/
#:~/Desktop/DriverInstall$ sudo sh install.sh 
install.sh: 45: Syntax error: "(" unexpected
#:~/Desktop/DriverInstall$ 

now i know i probably got wrong on some commands but im very new so i apologize for that. i would get it fixed by my own but without driver the connection speed is very low so i cant even surf the net searching for the solution

thx

---

### Post by chili555 on 2008-04-12
If you *gedit install.sh* and change the very first line to```
#!/bin/bash
```Then it will run. You do have build-essential installed, right?

---

### Post by Quality.mE on 2008-04-13
> **chili555 said:**
> If you *gedit install.sh* and change the very first line to```
#!/bin/bash
```Then it will run. You do have build-essential installed, right?

yes i have the build-essential installed.
anyway i did the gedit install.sh and now it starts.. but this is what happens 

Disconnect alternative devices:  (done)                                                                [  OK   ]
Unload alternative driver (done)                                                                          [  OK   ]
Create tmp dir (/tmp/Sk98IMXNCFIhMVPPerDbiJPCB)                                               [  OK   ]
Check user id (0)                                                                                               [  OK   ]
Check kernel version (2.6.22-14-generic)                                                             [  OK   ]
Check kernel symbol file (/proc/kallsyms)                                                             [  OK   ]
Check kernel type (SMP)                                                                                     [  OK   ]
Check number of CPUs (2)                                                                                  [  OK   ]
Check architecture./install.sh: line 390: arch: command not found (found)               [  OK   ]
Set architecture (i386)                                                                                        [  OK   ]
Check compiler (/usr/bin/gcc)                                                                              [  OK   ]
Check mcmodel flags (none)                                                                                [  OK   ]
Check module support (/sbin/insmod)                                                                   [  OK   ]
Check make (/usr/local/bin/make)                                                                         [  OK   ]
Check archive file (sk98lin)                                                                                   [  OK   ]
Check kernel gcc version (4.1.3) (Kernel:4.1.3 == gcc:4.1.3)                                    [  OK   ]
Check sk98lin driver availability (not loaded)                                                            [  OK   ]
Check kernel header files (not found)                                                                     [ failed ]
Kernel header not found. Please install the linux header files 
development package or create a symbolic link from the 
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

Installation of sk98lin driver module failed.

to fix it i did:
# mkdir /usr/src/linux
# ln -s /usr/src/rpm /usr/src/linux
# ln -s /usr/src/linux-headers-2.6.22-14 /usr/src/linux
# ln -s /usr/src/linux-headers-2.6.22-14-generic/ /usr/src/linux

but i still get the same error
ill keep trying by myself but ill be glad if u come up with a solution

---

### Post by chili555 on 2008-04-13
```
sudo apt-get install linux-headers-2.6.22-14-generic
```Or did you already install the headers? Also, this may be backwards:> ln -s /usr/src/linux-headers-2.6.22-14-generic/ /usr/src/linuxInstead, please try:```
ln -s /usr/src/linux/ /usr/src/linux-headers-2.6.22-14-generic/
```Please let us know.

---

### Post by Quality.mE on 2008-04-13
ok. the last command worked. i even got the confirm from the terminal but on the installation keeps giving me the same failure

Check kernel header files (not found)                                [ failed ]
Kernel header not found. Please install the linux header files 
development package or create a symbolic link from the 
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

Installation of sk98lin driver module failed.

---

### Post by chili555 on 2008-04-14
Let's throw everything but the kitchen sink at it!```
sudo apt-get install linux-headers-2.6.22-14-generic
sudo apt-get install linux-headers-2.6.22-14
sudo apt-get install linux-headers-generic
```And then try your install again.

---

### Post by stchman on 2008-04-14
> **Quality.mE said:**
> hello everyone,

im new to linux. i have the Gutsy Gibbon version installed.
i already had some problems installing it with the live cd. it wouldn't start because it would not recognize hardware parts. but anyway searching around i found some commands and got it installed. 

my problem now is installing my Yukon PCI-E Gigabit Ethernet Controller 88E8056.
i've got the driver from the marvell official site but when i try to install this is what happens 

#:~$ cd /home/***/Desktop/
#:~/Desktop$ sudo tar -xjf install_v10.50.1.3.tar.bz2 
#:~/Desktop$ cd DriverInstall/
#:~/Desktop/DriverInstall$ sudo sh install.sh 
install.sh: 45: Syntax error: "(" unexpected
#:~/Desktop/DriverInstall$ 

now i know i probably got wrong on some commands but im very new so i apologize for that. i would get it fixed by my own but without driver the connection speed is very low so i cant even surf the net searching for the solution

thx

That card works out of the box with Ubuntu according to the Ubuntu HCL.  No need for a driver as the 2.6.2x.xx kernel supports it.

[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsMarvell](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsMarvell)

I have (2) PCs with Marvell Yukon gigabit NICs and they work OOB.

---

### Post by Quality.mE on 2008-04-15
ok never mind. 
i got it working installing ubuntu with the alternate cd...
the alternate one is a lot better than the normal. i works even with my 8800 gt (no need to change it again)

THX anyways

---

