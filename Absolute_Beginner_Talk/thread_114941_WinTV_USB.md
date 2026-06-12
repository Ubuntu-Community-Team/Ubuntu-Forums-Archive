---
title: "WinTV USB"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by sgarrand on 2006-01-09
I am new to Ubuntu and Linux in general and I'd like to get my old Hauppauge WinTV USB working with Ubuntu Breezy. I searched and all the instructions for it (usbvision?) are way over my head. I know it sounds dumb, but I don't know how to compile a thing. If anyone could help me with the commands needed to get it working I'd appreciate it greatly. Thanks in advance.

Scott

---

### Post by alpianon on 2006-03-17
Ubuntu 5.10 - driver usbvision 0.9.8.2 for Hauppage WinTV USB

1- Go to [http://usbvision.sourceforge.net/](http://usbvision.sourceforge.net/) and dowload the sources 
(version 0.9.8.3 can't be compiled under Ubuntu 5.10, you have to download v0.9.8.2)

**Here's the direct link for lazy people** ;) 
[http://prdownloads.sourceforge.net/usbvision/usbvision-0.9.8.2.tar.gz?download](http://prdownloads.sourceforge.net/usbvision/usbvision-0.9.8.2.tar.gz?download)


2- **Save it in your home directory**


3- In Synaptic, **enable the Universe repository**


4- You need to install make, gcc-3.4, linux-headers; you need also "zapping" to watch tv.
You have to complile and install the module, then you may add a script to load it during startup

**Open a console window, then type**:   
(please note that the character ` is not ' and it can be obtained with AltGr+' - anyway, you may just copy and paste the following lines)

sudo apt-get install make gcc-3.4 linux-headers-`uname -r` zapping
tar -xf usbvision-0.9.8.2.tar.gz
cd usbvision-0.9.8.2/src
sudo make
sudo make install
sudo modprobe usbvision
echo -e "modprobe usbvision\n" >usbvision
sudo cp usbvision /etc/init.d
cd /etc/init.d
sudo chmod 755 usbvision
sudo update-rc.d usbvision start 51 S .

( . at the end of the line is needed!)

4- Connect the WinTV USB card, and run zapping (it should be in the Audio&Video menu)

Cheers!
Alberto Pianon (Italy)

---

### Post by beninburgh on 2006-06-19
I followed this advice, and got my card to work with 5.10, but in 6.06 xawtv is giving a b&w picture, zapping crashes when trying to alter preferences, and tvtime freezes the entire system... Does anyone have any advice? Is there a better tv app?

---

### Post by beninburgh on 2006-06-21
Ok, after installing all tv apps I could find, kdetv seemed to work the best. The black & white picture (on s-video input) was resolved by setting the module param SwitchSVideoInput to 1 (I did this in usbvision.c, as could work out how to pass it as a parameter). Now my only problem is getting a decent picture quality. (I have a VIA mini-ITX box. model M:

0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03)

Does anyone have a driver?

Ben

---

### Post by sicone on 2007-10-15
Sorry for dragging up an old thread, but I'm trying to get a WinTV Usb to work in 6.06 and when following the above instructions, at the Sudo make bit I get ```
make -C /lib/modules/2.6.15-29-386/build SUBDIRS=/home/sicone/usbvision-0.9.8.1/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-29-386'
  CC [M]  /home/sicone/usbvision-0.9.8.1/src/i2c-algo-usb.o
/home/sicone/usbvision-0.9.8.1/src/i2c-algo-usb.c:208: error: unknown field ‘name’ specified in initialiser
/home/sicone/usbvision-0.9.8.1/src/i2c-algo-usb.c:208: warning: initialisation from incompatible pointer type
/home/sicone/usbvision-0.9.8.1/src/i2c-algo-usb.c:209: error: unknown field ‘id’ specified in initialiser
/home/sicone/usbvision-0.9.8.1/src/i2c-algo-usb.c:209: error: ‘I2C_ALGO_BIT’ undeclared here (not in a function)
/home/sicone/usbvision-0.9.8.1/src/i2c-algo-usb.c: In function ‘i2c_usb_add_bus’:
/home/sicone/usbvision-0.9.8.1/src/i2c-algo-usb.c:226: error: ‘struct i2c_algorithm’ has no member named ‘id’
make[2]: *** [/home/sicone/usbvision-0.9.8.1/src/i2c-algo-usb.o] Error 1
make[1]: *** [_module_/home/sicone/usbvision-0.9.8.1/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-29-386'
make: *** [default] Error 2

```

I get the same error with 0.9.8.2 and 0.9.8.3 as well (I was trying different versions to see if any worked)

---

