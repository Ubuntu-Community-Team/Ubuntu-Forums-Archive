---
title: "[SOLVED] I'M IN DESPERATE NEED FOR HELP WITH MY WIRELESS!!! Please help me."
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-07-09
It wont connect. I restarted the computer 3 times and it wont work. Anyone have any problems like this? I need my wireless to work. Do I reset the wireless modem??? (Its a linksys WCG200). Its a modem wireless/Ethernet router G gateway. It was working all day until after I ran DoD:Source a couple of times.
Wireless card info :
Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


I already did this BTW.

tito@TITOS-LAPTOP:~$ sudo apt-get install bcm43xx-fwcutter
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
bcm43xx-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
libgnucrypto-java liblog4j1.2-java libswt3.2-gtk-java libseda-java
libcommons-cli-java libgtk-jni libcairo-java libbcprov-java libglib-java
libgtk-java libswt3.2-gtk-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
tito@TITOS-LAPTOP:~$

---

### Post by AlexenderReez on 2007-07-09
what is output of


> sudo iwconfig

try to use wifi-radar to connect...for me it is better than network-manager applet.....i remove network manager applet and install wifi-radar.......

---

### Post by ~~Tito~~ on 2007-07-09
O.O very shocking. . . .

tito@TITOS-LAPTOP:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

tito@TITOS-LAPTOP:~$

---

### Post by ~~Tito~~ on 2007-07-09
2nd poster please help me. I SERIOUSLY NEED TO GET MY WIFI BACK!!

---

### Post by eggdeng on 2007-07-09
Can you log on to the router to check what channel / frequency it's broadcasting on. You card is listening on channel 3 or 2422MHz  so you might need to change it to match the router's. For this use ```
sudo iwconfig eth1 channel <channel>
``` Might also help to set the ESSID using  ```
sudo iwconfig eth1 essid <essid>
``` Then you can scan for the AP ```
sudo iwlist eth1 scan
```

---

### Post by ~~Tito~~ on 2007-07-09
Crap is that why because i saw on the router settings that it was 6. . . ok ill try those codes.

---

### Post by ~~Tito~~ on 2007-07-09
Ok, the router settings let me change the channel. Ok ill try it out.

---

### Post by ~~Tito~~ on 2007-07-09
Nope, and it still won connect

tito@TITOS-LAPTOP:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Tito's Network"  Nickname:"Tito's Network"
          Mode:Managed  Frequency=2.422 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

tito@TITOS-LAPTOP:~$ sudo iwlist eth1 scan
eth1      No scan results
tito@TITOS-LAPTOP:~$

---

### Post by eggdeng on 2007-07-09
Have you got the same ESSID on the card and on the router?

---

### Post by lisati on 2007-07-09
> **~~Tito~~ said:**
> O.O very shocking. . . .

tito@TITOS-LAPTOP:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

tito@TITOS-LAPTOP:~$

This is one of Tito's early messages in the thread....there's no ESSID showing here....Has this been taken into account?

---

### Post by ~~Tito~~ on 2007-07-09
Listen it was working fine before i tryed to play DoD:source. . . . I want to uninstall the driver then reinstall it.

---

### Post by ~~Tito~~ on 2007-07-09
bump

---

### Post by ~~Tito~~ on 2007-07-09
Bump**

---

### Post by overdrank on 2007-07-09
> **~~Tito~~ said:**
> Bump**

HI and please stop bumping your thread. You have made several post on the same issue and I would suggest back tracking to the point of where is stopped working and go from there. You might also try posting in the wireless and networking.

---

### Post by ~~Tito~~ on 2007-07-09
Ok, sorry,but how do I uninstall the wireless driver then reinstall it?

---

### Post by AlexenderReez on 2007-07-09
do you install it in deb package...if it is...then just search in synaptic...just remove it the....but if you install tar.gz file that had been extract...using make.....just change directory to that folder then

> sudo make uninstall

---

### Post by ~~Tito~~ on 2007-07-09
I didn't install the driver, ubuntu recognized it but I had to enable something. I want to uninstall the driver completely then let ubuntu recognize it then I can enable it then I can be fine. Is that hard to do in ubuntu?

---

### Post by randytuggle on 2007-07-09
Go to Synaptic Package Manager - choose FILE>HISTORY and see if you can find the exact item you wish to remove. If you do, use the exact line item (file name) to remove it in Synaptic. You many have to click on the item in the search and select FORCE VERSION to roll it back to a previous one.

---

### Post by ~~Tito~~ on 2007-07-09
I looked and I cant find it. I want to know how to uninstall the **_driver_** not a program. Like I said before your post.

---

### Post by randytuggle on 2007-07-09
The Synaptic history file will show more than just programs - it will show drivers you updated, kernel changes,etc. I'm not a linux pro by any means but this is the best advice I can offer. I just thought I'd try to help you find the change made to the system so that you could find the file.

---

### Post by ~~Tito~~ on 2007-07-09
Please help me. I seriously need to fix this.

---

### Post by randytuggle on 2007-07-09
I have a Broadcom 4318 and I used this installer instead of anything with ndiswrapper.

 Go here: [http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

(edited from earlier)

---

### Post by ~~Tito~~ on 2007-07-09
Ok, does this uninstall then reinstall?

---

### Post by randytuggle on 2007-07-09
this is just an installer as far as i know. you may wish to offer questions on that page as well to get direct help from the wireless gurus.

---

### Post by ~~Tito~~ on 2007-07-09
Ok, thanks but, it still doesn't work. .  . . . . i don't know what happened to my wireless. . . . It shows that the driver installed correctly but I just don't know what happened after I played DoD:source.

---

### Post by ~~Tito~~ on 2007-07-09
I'm not going to sleep untill this gets fixed.
(I have been up sice 5:4ish pm, now its 7:05 am)

---

### Post by ~~Tito~~ on 2007-07-09
Had to reinstall, a lot of things got messed up also.

---

