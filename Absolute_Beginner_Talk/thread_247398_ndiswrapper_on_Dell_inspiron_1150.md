---
title: "ndiswrapper on Dell inspiron 1150"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by beyle on 2006-08-30
Hello,

My appologies to bring up this subject again as this is mentioned a lot of times. I have just started using ubuntu which works great except for the wifi. I have setup ndiswrapper and ndiswrapper-utils threw the package manager and now I have installed the  windows driver with the ndiswrapper windows driver installation tool. All is working great, the windows driver bcmwl5 is installed and I have the message: Hardware present: Yes
Can things get any better :-)
Now unfortunatelly the wlan0 does not work, even ifconfig gives the connections eth0 and lo but no wlan.
I have used the drivers from my CD, the drivers from the dell website and even tried the driver which I found for dell on the ubuntu website 
[http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)
I have spent several days on the www forums and tried all possible drivers I could download. All gave an identical result (some did not find the hardware which is even worse than my case).
None had any succes. As I'm new to Linux, I have no idea where I can find some log file or other feature to find out what is now the problem.
Any help?

---

### Post by TFX360 on 2006-08-30
> **beyle said:**
> Hello,

My appologies to bring up this subject again as this is mentioned a lot of times. I have just started using ubuntu which works great except for the wifi. I have setup ndiswrapper and ndiswrapper-utils threw the package manager and now I have installed the  windows driver with the ndiswrapper windows driver installation tool. All is working great, the windows driver bcmwl5 is installed and I have the message: Hardware present: Yes
Can things get any better :-)
Now unfortunatelly the wlan0 does not work, even ifconfig gives the connections eth0 and lo but no wlan.
I have used the drivers from my CD, the drivers from the dell website and even tried the driver which I found for dell on the ubuntu website 
[http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)
I have spent several days on the www forums and tried all possible drivers I could download. All gave an identical result (some did not find the hardware which is even worse than my case).
None had any succes. As I'm new to Linux, I have no idea where I can find some log file or other feature to find out what is now the problem.
Any help?


I've got Ubuntu too and Wireless (WPC54G v1.2 driver version 2). My wlan is not wlan0. My wlan is eth0

lo        no wireless extensions.

sit0      no wireless extensions.

eth0      IEEE 802.11g  ESSID:"Essid"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:XX:XX:XX:XX:XX
          Bit Rate:54 Mb/s   Tx-Power:14 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XXXX          Power Management:off
          Link Quality:100/100  Signal level:-55 dBm  Noise level:-256 dB
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Ubuntu wierdness, ethernet is ethernet not wlan. But it works.


Give me your


```
sudo iwconfig
```


PS: You are free to ask anything even if it has been before.

---

### Post by beyle on 2006-08-30
Hey,

Manny thanks for your quick answer.
I have done a ifconfig with this result:
eth0      Link encap:Ethernet  HWaddr 00:11:43:6B:93:26
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe6b:9326/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:147901 errors:0 dropped:0 overruns:0 frame:0
          TX packets:345847 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:203698863 (194.2 MiB)  TX bytes:23863171 (22.7 MiB)
          Interrupt:7

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1753 (1.7 KiB)  TX bytes:1753 (1.7 KiB)

Again thanks, greetings from Belgium...

---

### Post by beyle on 2006-08-30
Oh my appologies again, I now used your command iwconfig, sorry, I overlooked this:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"USR_carmennico"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xx   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by TFX360 on 2006-08-30
> **beyle said:**
> Oh my appologies again, I now used your command iwconfig, sorry, I overlooked this:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"USR_carmennico"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xx   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



I can see two errors here. The essid seems untrue. Is this really your ssid?


If you use the bcm43xx drivers in combination with ndiswrapper you must do:

```
sudo echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

This is to blacklist the bcm43xx and use the ndiswrapper driver.


Groeten uit een regenachtig Nederland vrind!

---

### Post by TFX360 on 2006-08-30
Here is a little script I wrote to get an overall view, nobody used it though. It does work!

____________________________________________________


I added this script for easy creating of the output.

It generates what I need to help you to output.txt.

You can paste this output in this thread.

Copy the file to you home directory or where ever you want.

The file -> [broadcom]("http://home.casema.nl/d.sluijter/broadcom")

and do:

```
sudo chmod +x broadcom; ./broadcom
```


Copy and paste the contents of output.txt here in the forum. Gedit starts automatically showing you the output.txt. Copy & Paste!


Kind regards,


TFX.

---

### Post by beyle on 2006-08-30
Hey, I did run your script, looks nice, here is the output whatever it all means:

0000:02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
eth1      IEEE 802.11b/g  ESSID:"USR_carmennico"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      Link encap:Ethernet  HWaddr 00:11:43:6B:93:26  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe6b:9326/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:155164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:359436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:209670021 (199.9 MiB)  TX bytes:25108831 (23.9 MiB)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4934 (4.8 KiB)  TX bytes:4934 (4.8 KiB)

Installed ndis drivers:
bcmwl5		driver present, hardware present 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid USR_carmennico
wireless-key s:xxxxxxxxxx

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by beyle on 2006-08-30
> **TFX360 said:**
> I can see two errors here. The essid seems untrue. Is this really your ssid?


If you use the bcm43xx drivers in combination with ndiswrapper you must do:

```
sudo echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

This is to blacklist the bcm43xx and use the ndiswrapper driver.


Groeten uit een regenachtig Nederland vrind!



Hey, me again,
I did the two lines you asked, the second one sudo tee -a /etc/modprobe.d/blacklist is hanging I think, terminal is blinking without a prompt.

---

### Post by TFX360 on 2006-08-30
> **beyle said:**
> Hey, me again,
I did the two lines you asked, the second one sudo tee -a /etc/modprobe.d/blacklist is hanging I think, terminal is blinking without a prompt.

Look good exept this then. Try manually editing:

Open a terminal:

```
sudo nano /etc/modprobe.d/blacklist
```

add to the bottom

```
blacklist bcm43xx
```

ctrl-x
enter
enter

reboot to be sure.

After that, what encryption are you using?

Ik ga om ongeveer 00:00 naar dromenland toe!

---

### Post by beyle on 2006-08-30
hi,

Ok, I edited the file, now the line is there, I rebooted, still no succes
I'm going to sleep not, I 'll try more tomorow.
Thankyou very much for all your help...

---

### Post by beyle on 2006-08-30
Euh ecryption, WEP, I think using a hex key
in my windows, the network name is USR_carmennico
Now if I open the wireless properties in ubuntu, I can not find any networks, although on my other laptop (windows) it works.

---

### Post by TFX360 on 2006-08-30
> **beyle said:**
> Euh ecryption, WEP, I think using a hex key
in my windows, the network name is USR_carmennico
Now if I open the wireless properties in ubuntu, I can not find any networks, although on my other laptop (windows) it works.

Did you try:

```
iwlist eth1 scan
```

If this works it's only your encryption that does work, yet.


Sleep well!

---

### Post by beyle on 2006-08-31
hi again.

After rebooting this night, my eth1 disapeared, also in the graphical ubuntu tool for connection properties, there was no wireless device any more.
I have started over from scratch where I followed the code from 
[http://www.ubuntuforums.org/showthread.php?t=247427&highlight=ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=247427&highlight=ndiswrapper)
all works :-)
So I'm now totally online wireless...
For others who also try this on a dell, I used the windows driver from 
driver R74092.exe
[http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)

special thanks to TFX360 for all your help.

---

### Post by TFX360 on 2006-08-31
Your welcome. Isn't linuxant a paid driver?

---

### Post by beyle on 2006-09-04
Hi,

My appologies for this late answer but now that all worked perfectly, I was trying out the whole system.

No the driver was free of charge. Now possibly the others would also work but now that mine works, I'm not going to test any further. :)

Keep up the good work...
=D>

---

