---
title: "Help with Linksys wireless-G Broadband Router model WRT54G w/ WLAN"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by _Silhouette_ on 2008-04-16
Okay, I have looked all over google and in some threads here and I don't really understand any of them, or even know if they are having the same problem.

Anyhow, I am trying to figure out how to connect my Ubuntu laptop to my wireless lan (run by my linksys WRT54G wireless router).
I ran the Linksys EasyLink Advisor CD on my XP desktop, and that seems to run OK, but all the information it gives me is the SSID, encryption type (WEP-128bit) and encryption key (a big stream of continuous letters and numbers).
I tried going into network-admin and disabling roaming wireless, entering in the SSID in the first box, WEP-hexadecimal in the password type, and putting in the encryption key in the password spot, and set the configuration to automatic. However, nothing happened, and I didn't get connected to anything. I'm obviously not understanding something.
Please help!

---

### Post by Crafty Kisses on 2008-04-16
Post the following output:
```
iwconfig
```

---

### Post by _Silhouette_ on 2008-04-16
I can get online, I just don't know how to connect to my wireless lan...

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Academy2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:42:12:0F   
          Bit Rate=24 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=61/100  Signal level=-62 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by elmer_42 on 2008-04-16
Wait, you want to access the configuration page? To do that, open up Firefox and put this in the location bar: 192.168.1.1. It will probably ask for a password. The default user is admin and the default password is admin.
Do you want to connect to other users on your wireless LAN, like access a SAMBA share? I don't quite understand what you mean. You say you can connect to the internet but can't connect to your LAN. My only two guesses have already been stated.

---

### Post by _Silhouette_ on 2008-04-16
> **elmer_42 said:**
> Wait, you want to access the configuration page? To do that, open up Firefox and put this in the location bar: 192.168.1.1. It will probably ask for a password. The default user is admin and the default password is admin.
Do you want to connect to other users on your wireless LAN, like access a SAMBA share? I don't quite understand what you mean. You say you can connect to the internet but can't connect to your LAN. My only two guesses have already been stated.

I mean I can connect to the internet via wireless (what the lan is also connected to) but I want to access my lan via wireless. 
I entered the ip address in a new tab in Firefox...it doesn't seem to be doing anything but loading the page for a very long time...?

---

### Post by _Silhouette_ on 2008-04-16
Anyone?

---

### Post by _Silhouette_ on 2008-04-17
Okay...I switched to my Vista partition, and I successfully connected there, and now the network shows up in the Ubuntu network-admin program, but when I enter the network information, it says "waiting for network key," then after a bit just asks for the password again. Afterward, I can't connect to anything, and IM programs mention a "switchboard error." What's the deal?

---

### Post by _Silhouette_ on 2008-04-17
Solved. Was using wrong encryption type!

---

### Post by alexander.forster on 2008-05-23
so what encryption type did you use?!

---

