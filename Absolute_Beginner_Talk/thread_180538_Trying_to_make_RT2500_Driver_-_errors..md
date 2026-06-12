---
title: "Trying to make RT2500 Driver - errors."
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-05-22
I downloaded the RT2500 driver for my internal wireless card from [here]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page") It definatley supports my kernel (Ubuntu Dapper 2.6). When I run "make" in the terminal (as it says in the README) I get the following error:

oliver@ubuntu:~/Desktop/rt2500-cvs-2006052208/Module$ make
make: *** /lib/modules/2.6.15-23-386/build: No such file or directory.  Stop.
rt2500.ko failed to build!
make: *** [module] Error 1

Any ideas greatley appreciated!!!

---

### Post by damianubuntu on 2006-05-22
I think you need to install your linux-headers.  Use Synaptic, search for linux-headers and select the one that suits your system, e.g. 2.6.15-23-386

BTW When I tried to get my wireless USB working on the same driver, I had problems with activating it.  The whole of Dapper froze.  What worked for me was to deactivate all other devices, and configure but not activate the wireless.  After a reboot the device either activated itself, or I had to do it manually (different on two different boxes) then I could reactivate other devices and everything was OK! 

You might also like to look at:

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)  if you haven't already!

Cheers

---

### Post by S{yndrom}e on 2006-05-22
be sure you also have build-essential
to do so type in terminal

sudo apt-get build-essential

---

### Post by tartarian on 2006-05-22
THANKS GUYS!!!

Yes I needed to install the kernel headers worked fine.... but..... when I tried  make install it spewed this error up. (nothing ever works :() 

oliver@ubuntu:~/Desktop/rt2500-cvs-2006052208/Module$ make install
echo "2.6 module install"
2.6 module install
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/oliver/Desktop/rt2500-cvs-2006052208/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  INSTALL /home/oliver/Desktop/rt2500-cvs-2006052208/Module/rt2500.ko
mkdir: cannot create directory `/lib/modules/2.6.15-23-386/extra': Permission denied
cp: cannot create regular file `/lib/modules/2.6.15-23-386/extra': Permission denied
make[2]: *** [/home/oliver/Desktop/rt2500-cvs-2006052208/Module/rt2500.ko] Error 1
make[1]: *** [modules_install] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
make: *** [modules_install] Error 2

>>>So I added sudo before the make install (on a whim ;))

oliver@ubuntu:~/Desktop/rt2500-cvs-2006052208/Module$ sudo make install
echo "2.6 module install"
2.6 module install
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/oliver/Desktop/rt2500-cvs-2006052208/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  INSTALL /home/oliver/Desktop/rt2500-cvs-2006052208/Module/rt2500.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
/sbin/depmod -a
grep: /etc/modprobe.conf: No such file or directory
append 'alias ra0 rt2500' to /etc/modprobe.conf

Thanks guys! 
P.S - S{yndrom}e - It said "Invalid operation" when i copied that into the terminal:-k

---

### Post by S{yndrom}e on 2006-05-22
OOPS i ment sudo apt-get install build-essential

Make sure you get if you combile things alot

and yea you have to do sudo make install not just make install :P

glad u got that worked out

---

### Post by tartarian on 2006-05-22
There is logic deep down in the unused part of my head.... It says hello once in a while tho :p

Any more wonderful ideas for me to try? :p  
my sudo apt-get install build-essential was all up to date...

---

### Post by damianubuntu on 2006-05-22
Have a look at the last section in this howto:

[http://doc.gwos.org/index.php/Rt2x00drivers](http://doc.gwos.org/index.php/Rt2x00drivers)

I think you'll have to do the moving about bit at the end!  (I like to sound technical when the opportunity arises!)

---

### Post by S{yndrom}e on 2006-05-22
also check for checkinstall

sudo apt-get install checkinstall

---

