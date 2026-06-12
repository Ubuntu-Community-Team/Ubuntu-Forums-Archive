---
title: "ubuntu 7.10 enable wireless device compaq v6000"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by analoog on 2008-03-10
hi,

I have a problem with my wireless network in my compaq presario v6000.
I use ubuntu 7.10 with kernel  2.6.24-11-generic (newest stable kernel)

System -> Administration -> restricted driver managers says ipw3945 driver enabled but status not in use, I think i somehow have to enable this, but how??


iwconfig output
```

mind@broom:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0_rename  IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lspci output about wireless device
```
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

---

### Post by Het Irv on 2008-03-11
It looks to me that the drivers are correctly installed, what kind of security do you have on the Access Point. 
**NOTE: I am not an expert, or even close.  I could be 100% wrong.**

---

### Post by analoog on 2008-03-11
I am not able to see any wireless ap's with several programs like wifiradar and there should be several in range,

---

### Post by stchman on 2008-03-11
> **analoog said:**
> hi,

I have a problem with my wireless network in my compaq presario v6000.
I use ubuntu 7.10 with kernel  2.6.24-11-generic (newest stable kernel)

System -> Administration -> restricted driver managers says ipw3945 driver enabled but status not in use, I think i somehow have to enable this, but how??


iwconfig output
```

mind@broom:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0_rename  IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lspci output about wireless device
```
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

Now that the Restricted driver is enabled just click on the Network Manager icon in the upper right corner and connect to your wireless router.  I recommend that you don't hide your SSID (actually worse for security) and it should pop up.  If you are running encryption NM will ask for the passphrase and you will be off and running.

---

### Post by analoog on 2008-03-20
doesn't work :(
```

mind@broom:/etc/network$ lsmod|grep 3945
iwl3945                89844  0 
iwlwifi_mac80211      219108  1 iwl3945

```
I have the newest kernel and on the [http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi) iwlwifi site I read that the kernel already support my wireless card and that i don't have to install the drivers..

should i remove them? and how?

---

