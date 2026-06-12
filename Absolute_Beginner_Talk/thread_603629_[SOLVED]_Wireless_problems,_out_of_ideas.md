---
title: "[SOLVED] Wireless problems, out of ideas"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Bobrm2 on 2007-11-05
I have moved from Xp pro to Linux (Gutsy) and am having spent several days on two problems, that I have been unable to solve. Setting up a wireless network, and getting the HP PSC 2400 to be seen by the Ubuntu 7.10 program.  I am starting to believe that the two problems are connected??

 I bridged the Speed Stream 4200 modem (new a month ago) and have new D-link WBR-1310 router along with, also new, WDA-1320 adapter installed withing the Ubuntu box. This works with the windows operating system.
  In order to connect with the internet, I am using wired connection(s) to the back of the router. Security is set with WPA hex, and password was entered, (now this morning, I am unable to reenter the password.)
   
  Continue to search for information. Any help appreciated. I have additional information, but don´t know what is needed/wanted in order to solve this problem.

	Bob.

---

### Post by KentS on 2007-11-05
Exactly what is the network problem? Do you see your wireless device when you type
```
iwconfig
```
in a terminal?

---

### Post by Bobrm2 on 2007-12-08
Sorry for the long delay.  Disorganization is my best suit.  Received the following:

bob@Bob:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"-------------"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:F0:55:54:7F   
          Bit Rate:48 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/70  Signal level=-61 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bob@Bob:~$ 


Not for sure what it means, nor if it sees the printer?  Where can I learn about what information is being provided with ´ifconfig´?

---

### Post by spiderbatdad on 2007-12-08
have you seen this post?

[http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless](http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless)

---

