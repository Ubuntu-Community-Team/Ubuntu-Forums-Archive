---
title: "Please help wireless stopped working"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by hawk1278 on 2008-04-20
I have an HP nc6000 with an Atheros 5213/5212 wireless adapter running Gutsy.  My nc6000 does not see my network but it sees my neighbor's network.  I have 3 other computers on the wireless network I have setup.  

I have tried using the network manager and manually inputing the ssid and wep key and I have tried just using roaming.  Sometimes it connects and says the signal strength is like 98% but I can't see any of the other systems on the network or get to the internet.

I have tried modifying the /etc/network/interfaces.  I have tried following the how-to located here: [http://ubuntuforums.org/showthread.php?t=571188&highlight=wireless+stopped+working]("http://ubuntuforums.org/showthread.php?t=571188&highlight=wireless+stopped+working"). 

Whenever I run sudo dhclient ath0 it says 
wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:20:94:be:0d
Sending on LPF/ath0/00:0f:20:94:be:0d
Sending on Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 internal 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 internal 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 internal 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 internal 7
No DHCPOFFERS received.
No working leases in persistant database - sleeping

Any suggestions would be much appreciated.

---

### Post by Mark20 on 2008-04-20
I would suggest trying another network manager such as Wicd.  You could also try connecting through the command line.  But the latter approach could take a very long time.

Either way, could you please post the output of
```
iwconfig
```

Mark

---

### Post by hawk1278 on 2008-04-20
output from iwconfig, sorry I had to hand jam it in:
lo            no wireless extensions

eth0       no wireless extensions

wifi0       no wireless extensions

ath0       IEEE 802.11g ESSSID:"thatsit" 
              Nickname:""
              Mode:Managed          
              Frequency:2.462 GHz       
              Access Point: Not-Associated
              Bit Rate: 0 kb/s          
             Tx-Power:15dBm                
              Sensitivity=1/1
              Retry: off                   
             RTS thr: off                         
              Fragment thr: off
              Power Management: off
              Link Quality= 0/70                 
              Signal level=-91 dBm       
              Noise level=-91 dBm
              Rx invalid nwid:273796        
              Rx invalid crypt: 0            
              Rx invalid frag: 0
             Tx excessive retries: 0          
             Invalid misc: 0                  
             Missed beacon: 0

irda0      no wireless extensions

---

### Post by hawk1278 on 2008-04-21
Any help, much appreciated...
bump

---

### Post by amir1979 on 2008-04-21
hi Hawk,  im a noob to linux/ubuntu i just installed it for the 1st time last night/few hours ago lol   i have a dell xpx 1330  my wireless doesnt work either... its a Broadcom 4328   iv read various options on how to install the drivers and tweaking it,  but they dont work for me for some reason either im not doin it right or.....  i just got tired of trying and bought a cheap card from newegg that has good rating for ubuntu....  try looking up ur atheros card on google with specific search for ubuntu.... heres a couple of links i found i dont know if it will work so dont blame me lol  im a noon to this stuff i dont know programing or anything like that im trying to understand the shell code process right now lol **** this **** is kinda hard to learn 


[http://hamzakc.wordpress.com/2006/12/11/atheros-wireless-setup-ubuntu/](http://hamzakc.wordpress.com/2006/12/11/atheros-wireless-setup-ubuntu/)

[http://ubuntuforums.org/archive/index.php/t-397742.html](http://ubuntuforums.org/archive/index.php/t-397742.html)

good luck

---

### Post by hawk1278 on 2008-04-21
Thank you for the liinks I will check them out after work and see if they help.

I did not think about this before but I am going to try the madwifi drivers as well.  I have read about people having luck with them.  

I am also going to check install and update logs to see if any recent updates might have borked up the wireless drivers.

Thank you for the help.

---

### Post by boomdiddly on 2008-04-21
Madwifi should sort your problems, a number of atheros chipsets are supported out the box with ubuntu luckly i was a lucky one!

---

