---
title: "*Please* help me with setting up CDEmu..."
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by StarscreamD on 2007-02-20
I run Ubuntu 6.10 Edgy but have since installed alot of the "K" apps such as Ktorrent.

When I try to install CDEmu, this is what I see...

/winfiles/install.sh: 146: function: not found

Couldn't find !
Type the full path here or press "Ctrl+C" to abort: 

Erm... What's goin' on here? :confused:

---

### Post by StarscreamD on 2007-02-20
I've gotten it now to get to the point that you "sudo make"

cd ~
wget [http://robert.private.outertech.com/virtualcd/cdemu-0.7.tar.bz2](http://robert.private.outertech.com/virtualcd/cdemu-0.7.tar.bz2)
tar xjf cdemu-0.7.tar.bz2
cd cdemu-0.7
sudo ls -la /lib/modules/`uname -r`/build 
sudo make
sudo make install
sudo modprobe cdemu
sudo gedit /etc/modules

at this point...

starscreamd@StarscreamD:~/cdemu-0.7$ sudo make
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/starscreamd/cdemu-0.7 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /home/starscreamd/cdemu-0.7/cdemu.o
/home/starscreamd/cdemu-0.7/cdemu.c:642: error: unknown field ‘dev_ioctl’ specified in initializer
/home/starscreamd/cdemu-0.7/cdemu.c:642: warning: initialization makes integer from pointer without a cast
/home/starscreamd/cdemu-0.7/cdemu.c:646: error: ‘CDC_IOCTLS’ undeclared here (not in a function)
make[2]: *** [/home/starscreamd/cdemu-0.7/cdemu.o] Error 1
make[1]: *** [_module_/home/starscreamd/cdemu-0.7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [all] Error 2
starscreamd@StarscreamD:~/cdemu-0.7$ 

ermmmm... this looks like another language to me. Can someone decode this mess?

---

### Post by StarscreamD on 2007-02-20
It seems noone can help me... Crap... Ah well I guess I will use bchunk... Thanks anyways!

---

### Post by commonplace on 2007-02-20
> **StarscreamD said:**
> It seems noone can help me... Crap... Ah well I guess I will use bchunk... Thanks anyways!

It's not very realistic, I don't think, to expect a response within eight minutes, no matter what forum you're on. Even paid support with most software companies won't get you a response that quickly, or anywhere near that quickly.

Someone will probably come along to help, but be patient! :)

/Kevin

---

### Post by commonplace on 2007-02-20
Alright, I would try deleting all that and starting over. When you do it again, don't do 'sudo make'; just run 'make' as yourself. (For 'make install', however, you DO need to use sudo, and also with the modprobe command).

What happens then?

/Kevin

---

### Post by StarscreamD on 2007-02-20
automake1.6 will not install either.. :\ I just skipped it... It comes up with this message...

starscreamd@StarscreamD:~/cdemu-0.7$ sudo apt-get install build-essential checkinstall automake1.6 libtool gcc-3.4 bchunk nrg2iso
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
checkinstall is already the newest version.
Package automake1.6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package automake1.6 has no installation candidate
starscreamd@StarscreamD:~/cdemu-0.7$ 

But this is what happens...

starscreamd@StarscreamD:~/cdemu-0.7$ make
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/starscreamd/cdemu-0.7 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /home/starscreamd/cdemu-0.7/cdemu.o
/home/starscreamd/cdemu-0.7/cdemu.c:642: error: unknown field ‘dev_ioctl’ specified in initializer
/home/starscreamd/cdemu-0.7/cdemu.c:642: warning: initialization makes integer from pointer without a cast
/home/starscreamd/cdemu-0.7/cdemu.c:646: error: ‘CDC_IOCTLS’ undeclared here (not in a function)
/home/starscreamd/cdemu-0.7/cdemu.c:1051: fatal error: opening dependency file /home/starscreamd/cdemu-0.7/.cdemu.o.d: Permission denied
compilation terminated.
make[2]: *** [/home/starscreamd/cdemu-0.7/cdemu.o] Error 1
make[1]: *** [_module_/home/starscreamd/cdemu-0.7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [all] Error 2

---

### Post by StarscreamD on 2007-02-20
:confused: 

*bump*

---

