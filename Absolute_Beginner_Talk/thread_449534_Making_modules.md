---
title: "Making modules ??"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by joramdam on 2007-05-20
Why do i get this messages ?

I cant install the modules ??

joramdam@dreamer:/usr/src/rt73-cvs-2007051917/Module$ sudo make install
Password:
*** Install module in /lib/modules/2.6.20-15-386/extra ...
make -C /lib/modules/2.6.20-15-386/build SUBDIRS=/usr/src/rt73-cvs-2007051917/Module modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-386'
INSTALL /usr/src/rt73-cvs-2007051917/Module/rt73.ko
DEPMOD 2.6.20-15-386
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-386'
/sbin/depmod -a
*** Update /etc/modprobe.conf alias for wlan*
*** Install firmware in /lib/firmware ...
*** Check config ...


And this


joramdam@dreamer:/usr/src/rt73-cvs-2007051917/Module$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-386'
Building modules, stage 2.
MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-386'
!!! WARNING: Module file much too big (>1MB)
!!! Check your GCC settings or ask for support
*** Module rt73.ko built successfully
joramdam@dreamer:/usr/src/rt73-cvs-2007051917/Module$
Edit/Delete Message

---

### Post by joramdam on 2007-05-20
I really need tu bump this one :-)

---

### Post by abhishek456 on 2007-05-20
ok Joramdan try to install some missing ones

try this in terminal

> sudo apt-get install build-essential


may be this will give you sucess

---

### Post by joramdam on 2007-05-20
I have done that and it did not help :-(

---

### Post by Bachstelze on 2007-05-20
The module _is_ installed. Now you need to load it :

```
sudo modprobe rt73
```

---

### Post by joramdam on 2007-05-20
Yes, thanks. I have to look in the wifi section to get the rausb0 to work. I cant switch betwen the desired networks. Neither can i use the network rausb0.... But thanks..:-)

---

### Post by Bachstelze on 2007-05-20
```
sudo ifup rausb0
sudo iwconfig rausb0 essid YOUR_ESSID key YOUR_WEP_KEY
sudo dhclient rausb0
```

You're there :)

---

### Post by joramdam on 2007-05-20
joramdam@dreamer:~$ sudo ifup rausb0
Ignoring unknown interface rausb0=rausb0.
joramdam@dreamer:~$

---

### Post by Bachstelze on 2007-05-20
Sorry, my mistake, it should be

```
sudo ifconfig rausb0 up
```

---

### Post by joramdam on 2007-05-20
joramdam@dreamer:~$ sudo ifconfig rausb0 up
rausb0: ERROR while getting interface flags: No such device
joramdam@dreamer:~$

---

### Post by Bachstelze on 2007-05-20
Is your card detected properly ?

```
sudo iwconfig
```

---

### Post by joramdam on 2007-05-20
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:"Jensen"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:02:72:51:60:A3   
          Bit Rate=36 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=67/100  Signal level:-72 dBm  Noise level:-107 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

joramdam@dreamer:~$

---

### Post by Bachstelze on 2007-05-20
Replace rausb0 with wlan0 then.

---

### Post by joramdam on 2007-05-20
I am wery sorry for this unessesary post...My USB contakt was not properly connected :frown:

---

### Post by joramdam on 2007-05-20
And thanks wery mutch HymnToLife for the help.......

---

