---
title: "intel pro/wireless 3945ABG not working on Edgy"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by simonsimon on 2007-01-06
OK.

I've seen many other posts like this and tried to use them for help but my wireless still isn't working.  Any help would be greatly appreciated.  Here's what I get from iwconfig:

simon@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"linksys_SES_2243"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2263   Missed beacon:0

sit0      no wireless extensions.

simon@laptop:~$ 


My wireless card is recognized.  Wifi radar says I'm connected but I can't ping anything or get access to the internet.  Any ideas? 

Thanks

---

### Post by Vorian on 2007-01-06
```
sudo dhclient eth1
```
should do the trick

---

### Post by simonsimon on 2007-01-06
k

I did that and this is the result:

simon@laptop:~$ sudo dhclient eth1
Password:
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:41:1a:f5
Sending on   LPF/eth1/00:13:02:41:1a:f5
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any ideas what this all means?

Thanks again

---

### Post by Bachstelze on 2007-01-06
It means your wireless card couldn't connect to the DHCP server -  your router. Is your router running DHCP ? Have you configured your WEP key properly ? You might also want to use GUI tools instead of the command line.

---

### Post by simonsimon on 2007-01-06
To be honest I'm not sure if I did it correctly.  

I know the password is correct but I don't know if it is hexadecimal or plain.  How do I find this out?

---

### Post by Bachstelze on 2007-01-06
if you have only numbers from 0 to 9 and letters from A to F, it's most likely hexadecimal. Just type your key without any spacers, letters uppercase, like this :

```
sudo iwconfig eth1 key 1234567890ABCDEF1234567890
```

---

### Post by simonsimon on 2007-01-06
Thanks guys.

I'm up and running!

:)

---

### Post by simonsimon on 2007-01-06
Hmmm.  Do I have to run those commands every time I reboot?

I rebooted and in order to get my wireless working again I had to open wifi-radar, then do the iwconfig and dhclient stuff 

Thanks again.

---

### Post by Vorian on 2007-01-06
You will have to run dhclient every now and then....

You shouldn't have to re-enter your key, unless you reset your key...

:D

---

### Post by r4ik on 2007-01-06
Prob. a stupid question so forgive me.
I cant seem to go from "open to "shared any ware.
Can somebody give me a pointer please...
Thanks !

---

### Post by Vorian on 2007-01-06
> **r4ik said:**
> Prob. a stupid question so forgive me.
I cant seem to go from "open to "shared any ware.
Can somebody give me a pointer please...
Thanks !
What do you mean, can you give some details of your problem:mrgreen:

---

### Post by r4ik on 2007-01-06
If i go to network  settings the option is not there if i click properties.

---

### Post by r4ik on 2007-01-07
Oke installed Wifi Radar and now it looks like this


It says i am connected but there is no signal.
Please guys i am a complete noob on this.

---

