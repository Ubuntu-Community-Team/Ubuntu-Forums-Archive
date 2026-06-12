---
title: "Please help me with these error messages."
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by ananchai on 2006-02-14
I am very new to Ubuntu Linux, and I need help installing ndiswrapper-1.10. I did not install ndiswrapper from the Ubuntu Linux 5.10 at all. The followings are the messages.


[B]ananchai@ubuntu:~/Desktop/ndiswrapper-1.10$ make
make -C driver
make[1]: Entering directory `/home/ananchai/Desktop/ndiswrapper-1.10/driver'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/ananchai/Desktop/ndiswrapper-1.10/driver \
        DRIVER_VERSION=1.10
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/ananchai/Desktop/ndiswrapper-1.10/driver/hal.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/ananchai/Desktop/ndiswrapper-1.10/driver/hal.o] Error 127
make[2]: *** [_module_/home/ananchai/Desktop/ndiswrapper-1.10/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/ananchai/Desktop/ndiswrapper-1.10/driver'
make: *** [all] Error 2[/B]

Thanks.

---

### Post by patrick295767 on 2006-02-14
To start with, did you install ?
```
apt-get -f -y install gcc
apt-get -f -y install gcc-3.4
```

Greetz'

---

### Post by TrendyDark on 2006-02-14
. . . . *sudo apt-get install ndiswrapper*  if you can use a wired connection, if not, [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

---

### Post by ananchai on 2006-02-14
Thanks for all the replied. The same error messages still appear though. 

[B]sudo apt-get -f -y install gcc
Password:
Reading package lists... Done
Building dependency tree... Done
gcc is already the newest version.

sudo apt-get -f -y install gcc-3.4
Reading package lists... Done
Building dependency tree... Done

ananchai@ubuntu:~$ cd Desktop
ananchai@ubuntu:~/Desktop$ cd ndiswrapper-1.10
ananchai@ubuntu:~/Desktop/ndiswrapper-1.10$ make
make -C driver
make[1]: Entering directory `/home/ananchai/Desktop/ndiswrapper-1.10/driver'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/ananchai/Desktop/ndiswrapper-1.10/driver \
        DRIVER_VERSION=1.10
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/ananchai/Desktop/ndiswrapper-1.10/driver/hal.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/ananchai/Desktop/ndiswrapper-1.10/driver/hal.o] Error 127
make[2]: *** [_module_/home/ananchai/Desktop/ndiswrapper-1.10/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/ananchai/Desktop/ndiswrapper-1.10/driver'
make: *** [all] Error 2
ananchai@ubuntu:~/Desktop/ndiswrapper-1.10$[/B]

From how I understand, ndiswrapper-1.10 is stable, isn't it? I need to try the newest version of ndiswrapper-1.10, because I can't get Linksys WUSB11v4 to work.

Thanks.

---

### Post by KCMiller3 on 2006-02-24
here a cheat that may work for you:

cd /usr/bin
sudo ln -s gcc-4.0 gcc-3.4


hope that helps

~Kevin

EDIT: I got this code from another site...I have tested this and it does work.

---

