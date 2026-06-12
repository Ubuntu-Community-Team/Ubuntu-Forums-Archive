---
title: "Need help connecting wifi driver"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by jordanae on 2008-03-31
I need help conecting my wifi driver. I went to System> Administration> Hardware Drivers and clicked the box next to my driver (Broadcom B43 wirless driver) and it begins to download the package.
The problem is that An error occured. It said:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb)
   Could not resolve 'archive.ubuntu.com'

What do I do?

---

### Post by Michael.Godawski on 2008-03-31
Can you download the deb file manually just by clicking on the link provided by you?
And then install the deb package by double clicking on it, and then try to activate the driver one more time.

---

### Post by jordanae on 2008-03-31
It's not a link. And also I have no internet connection. But I do try to install it and it begins but stops. Could I download it on my Windows computer and put it on a disk and download it on my Linux computer?

---

### Post by Joe325 on 2008-03-31
That might be an easier way; or if you have a USB Drive.
Cant you connect wired to the internet?

---

### Post by NR1224 on 2008-03-31
the lack of internet is the reason you cant download it, you can get it from any other computer any copy it, any source is fine, just get it and tell u how it goes

---

### Post by Michael.Godawski on 2008-03-31
Well when I click on [http://archive.ubuntu.com/ubuntu/poo...011-1_i386.deb](http://archive.ubuntu.com/ubuntu/poo...011-1_i386.deb) a download screen pops up and I can save the deb package to my PC.

You can download a deb file in windows and transfer it via a usb stick or compact disc to linux. You might get problems if there are unresolved dependencies, but I guess you won't run into such issues with this fwcutter package.

---

### Post by jordanae on 2008-03-31
I tried the copying it to a CD and installing it but it said that the installation failed. But I tried installing the wifi driver again through Hardware Drivers anyway. 
It comes up with a box that says:

While the driver itself is free software, it relies on proprietary firmware which cannot be legally shipped with the operating system. Your hardware will not work without the firmware. 

Also, I cannot connect to the internet with an ethernet cable. I don't know why but it just doesn't work.

---

### Post by jordanae on 2008-03-31
It's gonna be a pain typing this but when it finishes installing it says:
Installation finished
Failed to install package 'b43-fwcutter_011-1_i386.deb'
And in the terminal it says:
(Reading database ... 121312 files and directories currently installed.)
Preparing to replace b43-fwcutter ...
Setting up b43-fwcutter ...
--16:23:54--   [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
       => `wl_apsta-3.130.20.0.o
Resolving downloads.openwrt.org... failed: Name or service not known.
dpkg: error processing b43-fwcutter (--install):
  subprocess post-installation script returned error exit status 1

---

### Post by Michael.Godawski on 2008-03-31
Can you please post the output of these terminal commands. They will shed some light on your current network status:

```
iwconfig
sudo lshw -C network
cat /etc/network/interfaces
```

---

### Post by NR1224 on 2008-03-31
for the record. you can cut and paste

---

### Post by jordanae on 2008-03-31
Nope. No internet. I'm using two computers

---

### Post by jordanae on 2008-03-31
Here

> jordan@HP-Pavilion:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0_rename  IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jordan@HP-Pavilion:~$ sudo 1shw -C network
[sudo] password for jordan: 
sudo: 1shw: command not found
jordan@HP-Pavilion:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by jordanae on 2008-03-31
Maybe if I can connect through ethernet. But it doesn't detect the ethernet cable. Any ideas what's wrong?

---

