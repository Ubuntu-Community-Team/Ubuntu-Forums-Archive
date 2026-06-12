---
title: "Ubuntu 9.10 on Macbook1,1"
date: 2009-12-07
forum: Apple Hardware Users
---

### Post by ts230 on 2009-12-07
Hi there!
I got Ubuntu 9.10 on my MAcbook 1,1 but the WiFi is dead now. I need this fixed, and I want to keep ubuntu. I tried both of my external USB wifi sticks, none worked. Is there any way to fix this??
Thanks!

---

### Post by linuxopjemac on 2009-12-08
just hook it up to a cable, update your repository list and install the updates. You should then be able to select a hardware driver in the control panel.

---

### Post by ts230 on 2009-12-08
OK. I will try that when I get home. So I connect the LAN cable and then open up update manager? I've forgotten most of my Ubuntu, so can anyone tell me how to do this in steps?

---

### Post by linuxopjemac on 2009-12-08
Click Update Manager (System -> Administration -> Update Manager). Then check, and then Install updates. Then you go to System -> Administration -> Hardware Drivers. Select the appropriate driver for your network card.

---

### Post by ts230 on 2009-12-08
OK. I will try that now.

---

### Post by ts230 on 2009-12-08
I tried that, but in hardware drivers, nothing appears.
What should I do now?

---

### Post by Jdutch101 on 2009-12-09
Strange that you have this problem. Unfortunately, I can't help because my wifi worked "out of the box". Have you had any issues with anything else? My sound driver required some tweaking to get sound out of the headphone jack. I downloaded an ALSA GUI mixer application. I'd be happy to send you the name of it.

---

### Post by linuxopjemac on 2009-12-09
Can you give me the output of
```
sudo lspci | grep Atheros
```

If you have a Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01), you should be able to have wireless with the ath5k module.

Can you also give a :
```
sudo lsmod | grep ath
```

and also:
```
sudo ifconfig
```

PS If you don't see any ath module, you should modprobe it:
```
sudo modprobe ath5k
```

If you have ath5k loaded, you should have wireless:
```
sudo iwconfig
```


If all is well, you should be able to find a network with the network manager, or with wicd.

---

### Post by rvndrk3233 on 2009-12-09
I do NOT advise this setup. Advise to downgrade to IBEX. Pulsseaudio forced integration is the LEAST of your troubles.

(nevermind the effed up X11 config, which nobody seem to fix for 32 bit users....... :_P)

Nothing but hassles, but the USB modem support is dead-on with the proper scripts.

No offense, I know my ibook 2001 is over 10 years old, but I've seen OSx perform much better.(Mind you Linux is more current.) And where is that window buffer compression?? Its there on OSX, and it DOES make a difference.

Im using XFCE and am ok with it.GNOME interface is just too ungodly slow.I would use IceWM but it is a big hassle to config menus and get a desktop image up.Yes, I've done it before with Debbie.Ubuntu is just more stable both at install and post install ATM. I have a standard AIRCARD in mine, no issues except for anything higher than WEP doesn't connect.

---

### Post by ts230 on 2009-12-09
I do not have any issues. Actually, most of the things improoved. The Graphics Driver is the correct one now. I will send you the output of those 2 commands in a few minutes.

---

### Post by ts230 on 2009-12-09
Here is the output:
```

tristan@tristan-laptop:~$ sudo lspci | grep Atheros
[sudo] password for tristan: 
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
tristan@tristan-laptop:~$ sudo lsmod | grep ath
tristan@tristan-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:cb:cb:86:a5  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cbff:fecb:86a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1893 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:925008 (925.0 KB)  TX bytes:275015 (275.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8172 (8.1 KB)  TX bytes:8172 (8.1 KB)

tristan@tristan-laptop:~$ sudo modprobe ath5k
tristan@tristan-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=30 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tristan@tristan-laptop:~$ 

```
The Wlan works now for some reason, all that doesn't work is the two-finger scrolling with the mousepad. Can anyone help me with that?

---

### Post by ts230 on 2009-12-09
I just think this is weird. I re-booted, and it did not work. Then I repeated the steps    	linuxopjemac suggested, and then it worked. Is there any way that I can execute these steps even before I log in and run them as root? I think the call to modprobe might have fixed it.

---

### Post by linuxopjemac on 2009-12-10
Can you show me the following:
```
sudo cat /etc/modprobe.d/blacklist
```

or 
```
sudo cat /etc/modprobe.d/blacklist.conf
```

I don't know which to use, I think the first one. I am on a Windows PC right now, so I can't check. Maybe ath5k is blacklisted but should load at boot time.

---

### Post by linuxopjemac on 2009-12-10
For the two finger scrolling, you have to install gsynaptics. Then from administration -> gsynaptics, you can enable two finger scrolling. It works on my MacBook 2,1 too like that.
```
sudo apt-get install gsynaptics
```

---

### Post by ts230 on 2009-12-10
Ok. I will try that now.

---

### Post by ts230 on 2009-12-10
the driver is not blacklisted. I think what I need is some kind of init script that executes the modprobe. How do I write a init script? The gsynaptics did not solve the 2-finger scrolling.

---

### Post by linuxopjemac on 2009-12-12
maybe you can add ath5k to the /etc/modules config file. Hopefully that works for you.

---

### Post by foreverubun2 on 2009-12-12
[This]("https://help.ubuntu.com/community/MacBook1-1/Jaunty") might be helpful to anyone with problems.

Edit: This is for Jaunty, but many of the things probably still apply.

---

