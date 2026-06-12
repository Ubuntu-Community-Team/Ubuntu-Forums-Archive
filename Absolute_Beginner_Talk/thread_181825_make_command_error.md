---
title: "make command error"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by Mad_Gouki on 2006-05-24
i am very new to linux, i am having a problem compiling a rt2570 driver for nintnedo nifi use.  when i try to do make on the folder it gives the error 

```
alex@ubuntu:~$ cd /home/alex/Desktop/rt2570-cvs-2006052417/Module
alex@ubuntu:~/Desktop/rt2570-cvs-2006052417/Module$ make
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1
alex@ubuntu:~/Desktop/rt2570-cvs-2006052417/Module$ sudo make
Password:
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!

```

so no matter what i try to compile i get the same error. i think it has to do with 
```
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!
```

does anyone know what that means? i looked in that folder and there is no folder within named build.

---

### Post by Harold P on 2006-05-24
You did do ./configure... right?

---

### Post by Sef on 2006-05-24
To compile, build-essential is needed.

Did you download it?

sudo apt-get update

sudo apt-get install build-essential

(If you have Kubuntu, use kdesu instead of sudo.)

---

### Post by user1397 on 2006-05-24
try downloading build-essential and IMO also checkinstall:
```
sudo apt-get update
```
```
sudo apt-get install build-essential
```
```
sudo apt-get install checkinstall
```
i prefer using checkinstall to install stuff:
```
./configure
```
```
make
```
```
sudo checkinstall
```

---

### Post by Mad_Gouki on 2006-05-24
it has no configuration settings, its a driver if that makes any difference(?)
i obtained the driver from this site
[http://simon.teunvandeberg.nl/nifi/](http://simon.teunvandeberg.nl/nifi/)
it comes with shell files that run these commands, notice there is no ./config for them.

```
       Shell1 - Before the usbwifi-stick is inserted
            mkdir /home/knoppix/Desktop/nin_rt2570
            cp /mnt/hda1/nin_rt2570/* /home/knoppix/Desktop/nin_rt2570
            cd /home/knoppix/Desktop/nin_rt2570
            make
            cp /home/knoppix/Desktop/nin_rt2570/* /lib/modules/2.6.12/kernel/drivers/misc
            rm /lib/modules/2.6.12/misc/rt2570.ko
            depmod -a

      Shell3 - After the usbwifi-stick is inserted, using the "older" WMB app (remember that I changed the normal file so that you can still simply type wmb, and not wmbhost)
            iwpriv ninusb0 rfmontx 1
            iwconfig ninusb0 mode monitor channel 13 rate 2M
            mkdir /home/knoppix/Desktop/NinWifi_20060309
            cp -a /mnt/hda1/NinWifi_20060309 /home/knoppix/Desktop/NinWifi_20060309
            cd /home/knoppix/Desktop/NinWifi_20060309/NinWifi_20060309
            make
            cp /home/knoppix/Desktop/NinWifi_20060309/NinWifi_20060309/wmbhost/wmbhost /usr/bin/wmb
```

that shell is made for installing it from hda1, but any directory should work.  but when i do make it just gives that error.  ill get the install program, do i need to restart after i install these programs?

the tutorial was written for use with knoppix but i dont see how a distro would make a difference considering i heard something about it working with ubuntu

---

### Post by Mad_Gouki on 2006-05-24
ok well i need to run this command but it gives an error related to the breezy servers
```
sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4
```
...
so yeah, i guess now i know what the problem is, only to find another one

---

