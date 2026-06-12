---
title: "Downloading and Installing the ATI Updates for Ubuntu"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by snwbord2456 on 2007-07-05
I installed Unbuntu and reached the erros about Gnome not working. After logging in and trying

> sude apt-get dist-upgrade

I it reads:

Reading Package lists...Done
Building dependency tree
Reading state information... Done
Calculatin upgrade... Done
0 uograded, 0 newly installed, 0 to remove and 0 not upgraded.

Then I tried the 

> sudo apt-get install xorg-driver-fglrx

and I get

Reading packages lists...Done
Building dependency tree
Reading state information...Done
E: COuldn't find package xorg-drive-fglrx


It seems like my internet isnt working, the wireless LED isnt lit, though my comp is connected by cable to the router.

---

### Post by stchman on 2007-07-05
> **snwbord2456 said:**
> I installed Unbuntu and reached the erros about Gnome not working. After logging in and trying



I it reads:

Reading Package lists...Done
Building dependency tree
Reading state information... Done
Calculatin upgrade... Done
0 uograded, 0 newly installed, 0 to remove and 0 not upgraded.

Then I tried the 



and I get

Reading packages lists...Done
Building dependency tree
Reading state information...Done
E: COuldn't find package xorg-drive-fglrx


It seems like my internet isnt working, the wireless LED isnt lit, though my comp is connected by cable to the router.

That means it cannot find that package in the repositories.  Make sure the proper repositories are enabled.

Also if you run Feisty it has the ATI restricted drivers installed.  You just need to enable them.

---

### Post by snwbord2456 on 2007-07-05
Looked up how to install the ATI stuff from the restricted drivers. When I tried

> sudo apt-get install linux-restricted-modules-generic restricted-manager

It said that there were 0 upgrades, 0 newly installed, 0 to remove and 0 not upgraded

yet when i restarted and I still got an error saying the X driver didnt want to work.

---

### Post by Raineer on 2007-07-05
That means they are already installed and just not enabled.  You might follow the "Envy" script (google it) or possibly run
```
sudo dpkg-reconfigure xserver-xorg
``` and select the proper ATi driver.

Also, you could post the last 10-20 lines of /var/log/Xorg.0.log, or just look at them with
```
tail -20 /var/log/Xorg.0.log
``` and see if that gives any help

---

### Post by scottDkoDer on 2007-07-06
ATI Downloader Installer Script.

Just copy and paste this into a file...

```

gksudo gedit ~/ATI_Installer
```

> #ATI Driver Installer Script for Feisty Fawn by Scott Moreau

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
rm -r /usr/local/src/ATI
mkdir /usr/local/src/ATI && cd /usr/local/src/ATI
wget [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.38.6-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.38.6-x86.x86_64.run)
aptitude update && aptitude install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-$(uname -r) linux-source
cd /usr/src && tar -xvjf linux-source-*
cd /usr/local/src/ATI
sh ./ati-driver-installer-8.38.6-x86.x86_64.run --buildpkg Ubuntu/feisty
dpkg -i xorg-driver-fglrx_8*.deb fglrx-kernel-source_8*.deb
m-a prepare && m-a update && m-a build fglrx && m-a install fglrx && depmod -ae

make executable...

```
sudo chmod +x ~/ATI_Installer
```

and run.

```
sudo sh ~/ATI_Installer
```

In the mean time, in another terminal...

```
gksudo gedit /etc/X11/xorg.conf
```

And search for Driver under the Device section and change it to fglrx.

Reboot. Install Xgl and Beryl.

---

### Post by Viewtifulj on 2007-07-06
The proper thing to type is

xorg-driver-fglrx

It just looks like you forgot the "r".

---

