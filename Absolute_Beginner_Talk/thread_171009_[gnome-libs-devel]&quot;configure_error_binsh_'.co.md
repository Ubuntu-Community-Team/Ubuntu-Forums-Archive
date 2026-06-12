---
title: "[gnome-libs-devel]&quot;configure: error: /bin/sh './configure' failed for vflow&quot; error"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-05-05
"configure: error: /bin/sh './configure' failed for vflow" error 
  
I tried to install then the : 
gnome-libs-devel 
it's not in repos.
  
I then tried the: 
Download gnome-libs-1.4.1.7-i386-1.tgz from
[http://ftp.iasi.roedu.net/mirrors/ft...s/gnome-1.4.1/](http://ftp.iasi.roedu.net/mirrors/ft...s/gnome-1.4.1/)
and unpack the file. I hope this time you will find gnomeConf.sh
  
Not working either ... 
  
Woudl someone have any idea ??
  
Thank you , 

Patrick
  
> checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking command to parse /usr/bin/nm -B output... ok
checking how to hardcode library paths into programs... immediate
checking for /usr/bin/ld option to reload object files... -r
checking dynamic linker characteristics... Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for objdir... .libs
creating libtool
loading cache /dev/null
checking what warning flags to pass to the C compiler... -Wall -Wunused
checking what language compliance flags to pass to the C compiler...
checking for pthread_create in -lpthread... yes
checking for fftw... configure: error: FFTW not found. Please check your installation!
configure: error: /bin/sh './configure' failed for vflow


---

### Post by patrick295767 on 2006-05-05
I installed : 

```
apt-get -f -y install fftw2 fftw-dev
```
 
It's working !! :-)

Solved

---

### Post by alexohara1 on 2006-06-11
im getting a similar problem cant find gnomeConf.sh file 
im trying to set up internet connection with buntu 5.04
and have no idea what im doing im new to linux and buntu(old windows user)
i found a package called gnome-dialup-0.4.5.tar.gz im trying to install it
using the terminal i cant use  synaptic cause i downloaded this file from another pc onto a memory stick, then placed it on the desktop on the laptop, extract it and thats it now im stuck....
i have tried these two things below but get all sorts of error perhaps im in the wrong directory???these things below where done in the folder of the unzipped package above
sudo apt-get -f -y install fftw-dev
this reads the package list and builds a dependency tree then says cant find package fftw
sudo apt-get build-essential
this says invalid operation build essential
so whats happening???
or can someone tell me how to connect or set an internet connection
any help would be appreciated
regards alex:???:

---

