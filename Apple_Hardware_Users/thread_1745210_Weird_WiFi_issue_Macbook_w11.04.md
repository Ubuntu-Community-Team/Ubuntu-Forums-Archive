---
title: "Weird WiFi issue Macbook w/11.04"
date: 2011-04-30
forum: Apple Hardware Users
---

### Post by mikeydangerous on 2011-04-30
I just made the full switch to have Ubuntu as my primary OS, but I've run into a weird and annoying issue. 

My Macbook connects to WiFi without any problems, and never disconnects from my WAP, but the Internet connection will regularly cut out, so browsers will get stuck on "looking for http...." If I disconnect and reconnect to my WiFi, things work fine for a while, then the Internet will cut out again. 

I have a 2006 black plastic Macbook (1GHz Core 2 Duo, 2GB RAM). Just did a clean install of Ubuntu 11.04. Also have partitions for Mac OSX and Windows 7. And, everything is fully updated including the Mactel repo.

Thanks in advance for any help!

---

### Post by x2z on 2011-05-11
I have the same problem with the same Macbook. It happens especially when I'm running Transmission. Is this a problem with 802.11n? Any help would be much appreciated. I really want to make ubuntu my new primary OS. Oh and im running 64 bit 11.04.

---

### Post by ways on 2011-07-27
I have the same experience. I use 32-bit. When copying files (rsync) the wifi drops out. No indication from network-manager. Have to disconnect and reconnect.

Found any solutions?

Edit:
Is the invalid misc the problem?

$ iwconfig 
wlan0     IEEE 802.11abgn  ESSID:"linksys N"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:39:29:87:EA   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:196   Missed beacon:0

Attempted iwconfig wlan0 power off (from another post). No help.

---

