---
title: "bluetooth errors"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by Lukekelsall on 2006-05-11
Hey there,
](*,) O.k the problem is as follows:

I'm running ubuntu (brezzy badger) I have installed KDE (not kubuntu-desktop) as to make sure i have the KDEbluetooth framework. this has installed fine, i have a package I wish to install from source make and gcc are installed at latest version however when installing the package i get the following errors:

```
luke@Anubis:/etc/carwhisperer-0.2$ ls
carwhisperer.c  cw_scanner  in.raw   Makefile     out.raw  samples
cw_pin.pl       hcid.conf   LICENSE  message.raw  README   test.raw
luke@Anubis:/etc/carwhisperer-0.2$ sudo make
Password:
gcc  carwhisperer.c -o carwhisperer -lbluetooth
carwhisperer.c:46:33: error: bluetooth/bluetooth.h: No such file or directory
carwhisperer.c:47:27: error: bluetooth/hci.h: No such file or directory
carwhisperer.c:48:31: error: bluetooth/hci_lib.h: No such file or directory
carwhisperer.c:49:27: error: bluetooth/sco.h: No such file or directory
carwhisperer.c:50:30: error: bluetooth/rfcomm.h: No such file or directory
```

It is a blue tooth security program, i wish to test my security on my bluetooth headset. I tried updating the kdebluetooth frame work with:
sudo apt-get install kdebluetooth - but i'm running the latest version.

Any ideas on this one?

---

### Post by yogi183 on 2008-01-04
I have the exact same problem.

Any help would be appreciated. Thanks!

---

### Post by CheShA on 2008-01-18
it's just a case of 
```

apt-get install libbluetooth-dev
```

:)

---

### Post by mattycoze on 2008-04-25
I get an error on the "Make install" function... 

I think it's  due to a bad installation process as the cw_pin.sh does not exist. 


mattycoze@mattycoze-laptop:~/Desktop/carwhisperer-0.2$ ls
carwhisperer  carwhisperer.c  cw_pin.pl  cw_scanner  hcid.conf  in.raw  LICENSE  Makefile  message.raw  out.raw  README  samples  test.raw

mattycoze@mattycoze-laptop:~/Desktop/carwhisperer-0.2$ sudo make install
[sudo] password for mattycoze:
cp carwhisperer    /usr/bin/
cp /etc/bluetooth/hcid.conf /etc/bluetooth/hcid.conf.old
cp hcid.conf /etc/bluetooth/hcid.conf
cp cw_pin.sh /usr/bin/
cp: cannot stat `cw_pin.sh': No such file or directory
make: *** [install] Error 1


I've e-mailed Martin Herfurt and awaiting a reply as to what instructions we should follow.

Tell you how it goes!

MattyCoze

---

### Post by mattycoze on 2008-04-25
Sorry for the double post but I've found what might be wrong when running the "make install" command. Perhaps this might help;

The error message was due to a typo - simply edit the Makefile and change cw_pin.sh to cw_pin.pl (underneath install and uninstall).

I have also been told that in order for carwhisperer to work, you have to downgrade bluez-utils to a version < 3.

---

