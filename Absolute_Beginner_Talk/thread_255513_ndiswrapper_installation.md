---
title: "ndiswrapper installation"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Chris Val Kef on 2006-09-11
i'm trying to install ndiswrapper from source file (in order to install my modem later).

i got the tar.gz file and extract the files with 'tar zxvf ...' command.
then as the install said i change to the created directory. i've done it with 'cd ...' (hope i'm right') and then says to 
"run 

make uninstall
make"

how to do this? i type make, press enter and get the message 
"bash: make: command not found"
i have no idea!
i'm very new to all these. 
please if you want to help tell me all the details...

i'm doing all these under a temp folder (/home/username/temp). is that ok? do i have to  do all the process to a specific folder?

---

### Post by sailor2001 on 2006-09-11
ndiswrapper is already in synaptics........easy way to do it

---

### Post by ruedu on 2006-09-11
As sailor said, just install ndiswrapper via apt.  If you MUST build from source then you need to install all of the devel packages.  You would also do this using apt with an apt-get install build-essential.  I personally would just install ndiswrapper with apt-get install ndiswrapper-utils

---

### Post by Chris Val Kef on 2006-09-11
apt-get don't work cause i don't have internet cause ubuntu can't find the modem... so i have to do it on my own...

---

### Post by ruedu on 2006-09-11
So are you trying to get wireless networking to work or a modem?

---

### Post by rccharles on 2006-09-11
The ndiswrapper source file indicates that ndiswrapper is included in Ubuntu.  See paragraph two below:


Some wireless LAN vendors refuse to release hardware specifications or drivers for their products for operating systems other than Microsoft Windows. NdisWrapper makes it possible to use such hardware with Linux by means of a loadable kernel module that "wraps around" NDIS (Windows network driver API) drivers.

This package provides the source code for the NdisWrapper kernel module. The default Ubuntu kernel already provides the required modules. You might only need this package if you use a custom kernel.

[http://packages.ubuntu.com/dapper/misc/ndiswrapper-source](http://packages.ubuntu.com/dapper/misc/ndiswrapper-source)

Robert

---

### Post by rccharles on 2006-09-11
> **Chris Val Kef said:**
> i'm trying to install ndiswrapper from source file (in order to install my modem later).


Perhaps, you should explain what problem you are trying to solve. You should be able to plug in an external modem and configure.  

Some internal modems of the winmodem variety are more of a problem.

Robert

---

### Post by Arevos on 2006-09-12
The Ubuntu Wiki has a page that describes how to install ndiswrapper on a machine without internet access:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

