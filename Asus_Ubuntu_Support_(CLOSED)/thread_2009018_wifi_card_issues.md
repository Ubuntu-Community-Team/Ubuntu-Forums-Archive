---
title: "wifi card issues"
date: 2012-06-23
forum: Asus Ubuntu Support (CLOSED)
---

### Post by stephen45ss on 2012-06-23
I have a Asus U52F-BBG6 running dual boot Backtrack 5 R1 and BlackBuntu 0.3 . My Issue is with my wireless card on BlackBuntu which is based off Ubuntu 10.10 which isn't supported anymore but my wireless card is a Intel Centrino Advanced-N + WIMAX 6250 but says disconnected on BlackBuntu 0.3 . When I type in ifconfig in terminal it shows eth0 and wmx0 but no wlan0 and installing Wicd to manage the wifi connection doesn't show up anything for wifi networks. The default connection manager doesn't scan for wifi networks you have to manually connect to a wifi network by setting one up by knowing BSSID or SSID of the wireless network. I have tried sudo rfkill unblock all and it does nothing. So if anyone has a solution to this problem and wants to help it would be appriciated. The funny thing is BackTrack 5 R1 is based off Ubuntu 10.04 yet I can connect to wireless networks with Wicd without any problems and that how Im connect now but since I have devoted 440 GB of 640 GB to Blackbuntu and really don't want to reinstall a new OS over Blackbuntu 0.3 since I spent so much time getting the sound to work and skyrim over half way downloaded on that side. I don't really want to redownload 5.7 GB on slow connection and waste all the time spent on fixing the sound on bb03 so if anyone can help respond to this as soon as you can. BlackBuntu forums have no solution to this problem and  the mods have given me no response to my posts so Im here.

---

### Post by lesstatt on 2012-11-21
1. Go here 

[http://www.kernel.org/pub/linux/kernel/projects/backports/2012/10/08/compat-drivers-2012-10-08.tar.gz](http://www.kernel.org/pub/linux/kernel/projects/backports/2012/10/08/compat-drivers-2012-10-08.tar.gz)

2.  Download the file at the link above

3.  Extract the file

4.  Open the terminal

5.  Type:

sudo su

6.  enter your password

7.  move to the directory with extracted files

8.  type:

make

9:  type

make install

10.  type:

reboot

when your system reboots you should be up and running

if you have more problems go to joeldellinger.info

---

