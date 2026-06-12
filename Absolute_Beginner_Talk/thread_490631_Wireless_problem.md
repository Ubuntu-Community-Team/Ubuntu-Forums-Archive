---
title: "Wireless problem"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by jemazoro on 2007-07-02
Hi, 
I am lost, ...
I have install Ubuntu 2.6.20-16-generic on my dell latitude D600 laptop.
My wireless chip is a BCM4306, so I have installed the driver (or at least I think I did)
 :~$ ndiswrapper -l 
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)


But I am still not able to connect to the wireless network.  As I understand there is still something work with my Wlan card:

laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


...................................
It says Power Management:off
What does it mean ?
Could it be an hardware problem now ?
Thanks for your help
Jeremy

---

### Post by TrevorRS on 2007-07-02
im having similar problems, but they only started today! on 2 of my pc's and its a pain in the backside1 think its a new update that messed it up!

Trevor

---

