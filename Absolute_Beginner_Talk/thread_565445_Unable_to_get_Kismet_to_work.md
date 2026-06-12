---
title: "Unable to get Kismet to work"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Kitsun on 2007-10-02
I have spent some time attempting to get Kismet to work under Ubuntu, but have always met error messages instead.

It runs fine under another Linux distro (Back Track 2), so its not a matter of incompatible hardware.

I am using a DWL-G650 (Atheros, PCMCIA, H/W ver = C3, F/W ver 4.30.

```
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
nwm@nwm-laptop:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (madwifi): Enabling monitor mode for madwifi_ag source interface ath0 channel 6...
WARNING: ath0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: 'get_mode' does not return integer parameters.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
nwm@nwm-laptop:~$ sudo kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (madwifi): Enabling monitor mode for madwifi_ag source interface ath0 channel 6...
WARNING: ath0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: 'get_mode' does not return integer parameters.
nwm@nwm-laptop:~$ 

```

Any attempts at helping me are appreciated.

---

### Post by j.bunce on 2007-10-02
try:
```
gksu gedit /etc/kismet/kismet.conf
```

and change the source to atheros,ath0,wifi

---

### Post by Kitsun on 2007-10-02
I changed
```
source=madwifi_ag,ath0,madwifi
```
To:
```
source=atheros,ath0,wifi
```

As suggested in the above post.

```
Server options:  none
Client options:  none
Starting server...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'atheros' in source 'atheros,ath0,wifi'
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
Waiting for server to start before starting UI...

```

Was the result.

---

### Post by j.bunce on 2007-10-02
Load backtract again, view the kismet.conf file

```
gedit /etc/kismet/kismet.conf
```

and copy down the sources from that.

---

### Post by Netoqrat on 2007-10-08
I got the exact same problem and messages. What do you think under "copying sources from there"? 
i would like to setup Kismet and do a litlle snooping around........

---

### Post by Netoqrat on 2007-10-08
this worked for me:
1. install madwifi-tools
sudo apt-get install madwifi-tools
2. edit kismet.conf
sudo kate /etc/kismet/kismet.conf
3. change source to:
source=madwifi_b,wifi0,laptop card


:guitar:

---

