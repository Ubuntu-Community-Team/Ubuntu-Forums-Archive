---
title: "Gutsy Dell True Mobile 1300 Wireless worked in Feisty"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by dndrich on 2007-10-21
OK, I have a Dell M600 laptop with a Dell Truemobile wireless card.  It was working fine in Feisty, but in order to get it to work, I had to use the windows driver with a wrapper.  I can't even remember how I did it, but it was complicated, and it worked.  Now I have updated to Gutsy through the update manager, and wireless no longer works.  Interestingly, it appears that the wrapper is still there, because I can detect my network.  Now, I have enabled the restricted drivers, which appears to have firmware for Broadcom cards.  I think the Dell is a broadcom card.  Under system, there is an entry for Windows wireless drivers, just like under Feisty, so I think somehow whatever I installed before survived the upgrade, but doesn't work.  Do I need to uninstall the windows wireless setup for this to work?  Or, is there a configuration file I have to edit to get the native drivers to work?  I vaguely remember having to edit some configuration file to get the wrapper to work.  Perhaps that has to be undone in some manner?  Any ideas?

---

### Post by GSF1200S on 2007-10-21
> **dndrich said:**
> OK, I have a Dell M600 laptop with a Dell Truemobile wireless card.  It was working fine in Feisty, but in order to get it to work, I had to use the windows driver with a wrapper.  I can't even remember how I did it, but it was complicated, and it worked.  Now I have updated to Gutsy through the update manager, and wireless no longer works.  Interestingly, it appears that the wrapper is still there, because I can detect my network.  Now, I have enabled the restricted drivers, which appears to have firmware for Broadcom cards.  I think the Dell is a broadcom card.  Under system, there is an entry for Windows wireless drivers, just like under Feisty, so I think somehow whatever I installed before survived the upgrade, but doesn't work.  Do I need to uninstall the windows wireless setup for this to work?  Or, is there a configuration file I have to edit to get the native drivers to work?  I vaguely remember having to edit some configuration file to get the wrapper to work.  Perhaps that has to be undone in some manner?  Any ideas?

I would say you should completely remove ndiswrapper and restart the computer. Make sure the checkbox is enabled for you wireless card in the Restricted Drivers Manager. It may be trying to use ndiswrapper. Report back so we can help you and so that others know...

---

### Post by dndrich on 2007-10-21
OK, I did that, removed it completely.  I have the Broadcom restricted driver enabled, and I was able to download it from the internet when hooked up with ethernet.  Still no go.  Interestingly, when I click on manual configuration of network, and select wireless, it still has my old settings, and can detect my signal strength.  But for some reason, it does not connect.  I have the windows drivers all removed, so it must be detecting the card.  Can't figure out why it won't connect.

---

### Post by Espreon on 2007-10-21
I have a Dell wireless card with ndiswrapper too, I had to disable roaming mode and manually enter the network stats to get it to connect.

---

### Post by dndrich on 2007-10-21
No, I've done that.  It is set up for my network with the correct WEP key etc.  I am convinced that some old setting that persists after the upgrade is causing the problem.  I looked in the blacklist file that I had to modify when I used the ndiswrapper, and the blacklist entry is gone, so it was correctly modified by Gutsy.  Just can't figure this out.

---

### Post by GSF1200S on 2007-10-21
Try this:

sudo iwconfig ath0 essid "networkname"
sudo iwconfig ath0 key wepkey
sudo dhclient ath0

where ath0 is the name of your wireless device (ath0, wifi0, etc are common)

Tell me what the terminal reports...

---

### Post by dndrich on 2007-10-21
Hmm.  I cannot get those commands to work, since I don't know what the device is called.  ath0 does not work.  Any ideas how to figure that out?

---

### Post by GSF1200S on 2007-10-21
> **dndrich said:**
> Hmm.  I cannot get those commands to work, since I don't know what the device is called.  ath0 does not work.  Any ideas how to figure that out?

Type:

```
iwconfig
```

in the terminal and post the results... :)

---

### Post by dndrich on 2007-10-21
OK, here is the results of iwconfig:

daniel@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

daniel@ubuntu:~$

---

### Post by Espreon on 2007-10-21
> **dndrich said:**
> OK, here is the results of iwconfig:

daniel@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

daniel@ubuntu:~$
You should edit your post and put the results between code tags example:

[code']
result
[/code']

but when doing it remove the ' s

---

### Post by dndrich on 2007-10-21
I'm not quite sure what that last post means, but I am trying to get the wireless working!

---

### Post by GSF1200S on 2007-10-21
> **dndrich said:**
> OK, here is the results of iwconfig:

daniel@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

daniel@ubuntu:~$

Ok, we were just using the wrong device..

Type:

sudo iwconfig eth1 essid networkname
sudo iwconfig eth1 key wepkey
sudo dhclient eth1


Note that you need to change networkname to whatever your wireless router names the network (so if you called it Ferrari, than thats what you would type in place of networkname) Same thing applies to the wepkey for the second command; put the wep key in its place.

Not trying to dumb you down.. ive always found details like this to mess me up :)

---

### Post by dndrich on 2007-10-21
OK, here is what I got trying the above:

daniel@ubuntu:~$ sudo iwconfig eth1 essid ben1alex
[sudo] password for daniel:
daniel@ubuntu:~$ sudo iwconfig eth1 key wepkey
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "wepkey".
daniel@ubuntu:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:90:4b:b1:e0:5a
Sending on   LPF/eth1/00:90:4b:b1:e0:5a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
daniel@ubuntu:~$

---

### Post by dndrich on 2007-10-21
Oops.  Did the wepkey thing wrong.  Here is the result of that:

iwconfig: unknown command "5191b22294"
daniel@ubuntu:~$ sudo iwconfig eth1 key 5191b22294
daniel@ubuntu:~$

---

### Post by GSF1200S on 2007-10-21
> **dndrich said:**
> Oops.  Did the wepkey thing wrong.  Here is the result of that:

iwconfig: unknown command "5191b22294"
daniel@ubuntu:~$ sudo iwconfig eth1 key 5191b22294
daniel@ubuntu:~$

Thats fine.. im mainly concerned with what 

sudo dhclient eth1

spits out in the terminal...

---

### Post by dndrich on 2007-10-21
I have to hit the sack now.  Thanks for your help, but I will just have to resume this tomorrow.

---

### Post by GSF1200S on 2007-10-21
> **dndrich said:**
> I have to hit the sack now.  Thanks for your help, but I will just have to resume this tomorrow.

OK, but those 3 commands should at least put you online.. give it a shot tommorrow :)

---

