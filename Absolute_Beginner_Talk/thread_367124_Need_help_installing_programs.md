---
title: "Need help installing programs"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by jasoncs20 on 2007-02-21
Hello
This is my first post
I am trying to install XMMS but i get the following when i try

jason@ubuntuDESK:~/xmms-1.2.8$ sudo ./configure
loading cache ./config.cache
checking host system type... i686-pc-linux-gnuoldld
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... no
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for prefix by checking for xmms... no
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH
jason@ubuntuDESK:~/xmms-1.2.8$

---

### Post by linux_kid on 2007-02-21
How about ```
sudo apt-get install xmms
``` This will be much easier.

---

### Post by Luk0r on 2007-02-21
Yes, you should always use apt-get if the software is available on it, unless there's a specific reason you don't want to.

---

### Post by r4ik on 2007-02-21
Is it not in Synaptic ?

---

### Post by Luk0r on 2007-02-21
Well yeah, either apt-get or Synaptic.

---

### Post by jasoncs20 on 2007-02-21
i can do it that way
but i was really trying to install an antivirus thats not listed
and got the same problem 
so i figurred i would try to install this program
first the manual way

i would really like to do it the manual way

---

### Post by Luk0r on 2007-02-21
```
cd <directory of source>
./configure
make
sudo make install
```
is the basic way of installing software like that.

As for the CC error, try doing:
```
sudo apt-get install build-essential
export CC="gcc"
```

---

### Post by Maestro23 on 2007-02-21
> **jasoncs20 said:**
> i can do it that way
but i was really trying to install an antivirus thats not listed
and got the same problem 
so i figurred i would try to install this program
first the manual way

i would really like to do it the manual way

What anti-virus program?  Where are you getting it from?

---

### Post by r4ik on 2007-02-21
One manual :)

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28XMMS.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28XMMS.29)

---

### Post by jasoncs20 on 2007-02-21
its ClamAV from TuCows

---

### Post by igknighted on 2007-02-21
clamAV should be in the repo's...

---

### Post by r4ik on 2007-02-21
Try,

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_a_GUI_desktop_On-Access_Anti-Virus_Scanner_for_KDE_.28KlamAV.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_a_GUI_desktop_On-Access_Anti-Virus_Scanner_for_KDE_.28KlamAV.29)

Good luck !

---

