---
title: "need help with a &quot;makefile&quot;"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by I26 on 2006-05-12
I downloaded my NIC drivers as a tar.gz file. I used the command tar -xzvf nic.tar.gz and it unpacked them. I then moved to that directory and i have a "makefile" I just don't know what to do with it from here. Anyone have any tidbits of info they could share? In the meantime i will keep searching for more tutorials and other posts. THANX!!!

---

### Post by Sutekh on 2006-05-12
Generally if you are compiling from source you should follow these steps using the a Terminal window (Applications -> Accessories Menu)
```
sudo apt-get install build-essential
``` To grab the neccessary compilers, make, and dkpg tools

Then change to the folder with the files and use these commands
```
cd /<path of files>
./configure
make
sudo make install
```

You should also read this link for installing software

[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)

---

### Post by skippy81 on 2006-05-12
To use a makefile you simply change into the directory where your files are and type "make"

> cd /location/of/unpacked/files/
make

There are a few points that I must 'make' though :p 

1) You need to install the build-essential package in order to use make, make is a program and must be installed.

2) You will probably also need the kernel headers for your version of the kernel, you can use "aptitude" to recover these from the installation CD. 

3) Often you need to edit the makefile, and adjust it to tell it where to find your kernel headers.

4) It is possible that the kernel allready comes with a compiled module for your NIC. There should be a file which ends with the extension .c in the package you unzipped.  Perform a file search on your entire file system using the name of that file, but without the .c at the end.  ie if the file is called driver.c then search your filesystem for "driver".  If you find a file called driver.ko then you allready have the driver and do not need to compile.  Just open a terminal and type > modprobe driver where driver is the name of the driver (dont add the .ko extension to the end. 

Hope this helps a bit

---

### Post by skippy81 on 2006-05-12
Hehe someone beat me to it.  To the OP, give us more details. What is the name of the driver?

Also do an > lspci from the terminal and paste it for us.  Oh and if you use modprobe as I suggested you will need to add "sudo" before the command.

---

