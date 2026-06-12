---
title: "Wireless Help"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by kilroy423 on 2007-02-19
anyone have some good tutorials on using command line to configure wireless internet...I can use the ubuntu gui's to configure the internet but i would like a total lesson on how to use the command line...havent really found anything on the first couple of pages google to fulfill my quest for knowledge..heh...thx

---

### Post by mikewhatever on 2007-02-19
check the wireless trouble shooting section
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless)

---

### Post by MrFSL on 2007-02-19
Here is my quick and dirty howto.

1) To determine if your wireless adapter is detected and get your adapter name:
```
iwconfig
```

2) Bring down your network:
```
sudo /etc/init.d/networking stop
```

3) Edit config file with all pertinent networking information:
```
sudo nano /etc/nework/interfaces
```

*You can use any command line text editor you like. In this example I used nano but you can use vi or vim or what-have-you.

4) Here is an example /etc/network/interfaces file to give you an idea how to write yours.
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
wireless-essid MY_ESSID
wireless-key 12345678901234567890abcdef
address 192.168.10.2
netmask 255.255.255.0
gateway 192.168.10.1

```

* Granted this is just an example. You would have to change "MY_ESSID" for your network SSID, change your wireless key, etc. In this example the wired network on interface eth0 uses dhcp. The wireless network on interface eth1 uses static assigned addresses.

5) Bring networking back up:
```
sudo /etc/init.d/networking start
```

Simple enough?

---

### Post by kilroy423 on 2007-02-20
indeed simple enough....i have to save whatever variables to that text file?...i can't just do 

```
sudo iwconfig eth1 essid linksys
```
```
sudo iwconfig eth1 ap 90-234-242-234243-2
```
```
sudo iwconfig eth1 key xxxxxxx
```
```
sudo iwconfig eth1 channel 6
```

won't just entering this into the terminal allow for a quick on the fly change over to a network and then when i do a ifdown eth1 and then a ifup eth1 immediately switch back to whatever the default is in the file?  one more question is there anyway to allocate the wifi card to use wlan0 or is that more of a pain then it is worth?

thx,
dan

{edit}
after changing the text file to accommodate my settings i am still having problems...not even being able to connect to the Internet....btw im using a linksys router with WEP encryption

---

