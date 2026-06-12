---
title: "how to install martian lucent modem driver files via Terminal window"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by RoBo5050 on 2008-02-13
Hello forum members
  I have a internal Trendnet 56k analog modem that needs drivers compatible with Ubuntu 7.10; I just downloaded a driver package by the name 'Martian,extract4d the files,but do not know how to install the Martian driver files via Ubuntu Terminal!!:confused:

I subsequently downloaded a ubuntu library package that is supposed to be installed in part with the Martian driver files;I would like to know if anyone one has the same chipset modem,and what steps were taken to get Ubuntu to install the modem drivers???

Thanks in advance for a reply !!

---

### Post by HappyFeet on 2008-02-13
add the following line to your /etc/apt/source,list
deb [http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/](http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/) ./
do in terminal
```
gksudo gedit /etc/apt/sources,list
```
then at the end of the file, on its own line, add: deb [http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/](http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/) ./

then save file, and then in terminal,
```
sudo apt-get update
```
exit terminal and restart.
see if  driver shows up in restricted drivers manager. if not, open synaptic package manager and search for martian lucent modem.

---

