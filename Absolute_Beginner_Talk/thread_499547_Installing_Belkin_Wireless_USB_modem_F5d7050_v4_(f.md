---
title: "Installing Belkin Wireless USB modem F5d7050 v4 (feisty)"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by fuwkej on 2007-07-12
I have tried quiet a few of ways to install this F5D7050V4 Belkin wireless USB modem with no success. The most recent one looks like it might have worked for a few people but I get to the install step and cannot seem to install it. The guide I was using is at: 

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

I get to step 5:

[B][I]Step 5 - Create and install the driver using make both

Make both versions of the driver with with the "sudo make both" command:

user@ubuntu:~/zd1211-driver-r83$ sudo make both

This will take several minutes. There will be warnings, but there can be no errors or the build will not complete. Even if you only want one version zd1211 or zd1211b it is a lot easier to make both and it will install them for you.

Verify that the driver was installed correctly using the list short command:

user@ubuntu:~/zd1211-driver-r83$ ls /lib/modules/`uname -r`/net 

You should see the files zd1211b.ko and zd1211.ko[/I][/B]


But when I type make both (in any directory, I tried all that seem logical), it just says

make: *** No rule to make target `both'.  Stop.


Any help on this is welcome.

---

### Post by C.S.Cameron on 2007-07-13
I got my Belkin F5D7050 USB working the other day, not as complex as Nvidia Drivers.
I tried a bunch how to's so I'm not sure if I ended up with the rt73 drivers off the Belkin disk or the rt73-cvs-daily.tar.gz ones.
I am sure that nothing worked until I got rid of Network manager and installed wicd.
It's working great now.
Cork

---

### Post by Austin_KW on 2007-07-13
> **C.S.Cameron said:**
> I got my Belkin F5D7050 USB working the other day, not as complex as Nvidia Drivers.
I tried a bunch how to's so I'm not sure if I ended up with the rt73 drivers off the Belkin disk or the rt73-cvs-daily.tar.gz ones.
I am sure that nothing worked until I got rid of Network manager and installed wicd.
It's working great now.
Cork

The rt73 is the V3 F5D7050  not the V4.
"lsmod | grep usbcore" should tell you which driver you have loaded.

---

### Post by imdano on 2007-07-13
open a terminal and type ```
sudo apt-get install build-essential
``` then try installing again.

---

### Post by fuwkej on 2007-07-14
Yes the build essential tools are all installed, I found out the make wasn't working because the site did not give me the same file as the helpfile was using. The helpfile gave me a link to [http://zd1211.ath.cx/](http://zd1211.ath.cx/) for zd1211-driver-r83 but there is no such file there. Several help files have this same link, but there is no such file there that I can find. All I could find was the zd1211-firmware1.3.tar.bz2 which just has these files: README, zd1211_ub, zd1211_uph, zd1211_uphm, zd1211_uphr, zd1211_ur, zd1211b_ub, zd1211b_uph, zd1211b_uphm, zd1211b_uphr, zd1211b_ur. No makefile. If anyone knows how to get the file zd1211-driver-r83.tgz, I could complete the rest, but I had no luck in finding it.

Also tried the alternate route with ndiswrapper but was unable to find the driver I need, several links led me to .exe files, but those are useless without windows. The file needed for that is ZD1211BU.INF.

Also tried going to best buy and circuit city to buy a new wireless card, but none of those are supported by Linux, haha. This is getting to be a pain. ](*,) Any words of wisdom in this matter are welcome.

Source::[http://ubuntuforums.org/showthread.php?t=283250&highlight=zd1211-driver-r83.tgz](http://ubuntuforums.org/showthread.php?t=283250&highlight=zd1211-driver-r83.tgz)

---

### Post by fuwkej on 2007-07-20
Ok, I was able to get on a windows machine to get ahold of the ZD1211BU.INF file I needed for ndiswrapper and installed that. I now get this:

[HTML]$ lsusb
Bus 001 Device 003: ID 050d:705c Belkin Components 
Bus 001 Device 001: ID 0000:0000  

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Tx-Power:-2147483648 dBm   Sensitivity=0/3  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/HTML]


It looks like it's all working. I attempted to configure the modem in Network, but I still could not get an internet connection. I had success on windows with this modem so I know the problem is with the configuration.

---

### Post by scrapnon on 2007-07-22
After a metric buttload of research, i found out that the F5D7050v4 uses the zd1211 driver. The driver has been included since Linux kernel  2.6.18, but, the device will only work (without doing some technical crap) in kernel 2.6.20 or later because the device ID wasn't included in the older kernels

---

### Post by imdano on 2007-07-22
[http://ubuntuforums.org/showthread.php?t=488622](http://ubuntuforums.org/showthread.php?t=488622)

Read this thread.  Someone with the same chipset as you was able to get wireless working using updated vendor-supplied drivers.

---

