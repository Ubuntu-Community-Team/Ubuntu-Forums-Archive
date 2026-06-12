---
title: "iwconfig :&quot;Access point invalid&quot;! HELP!"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by sorryjustme on 2007-02-07
I am unable to connect to my home wireless network, since I changed a few things whilst on holiday to access WPA. The output of iwconfig gives me this:

IEEE 802.11b/g  ESSID:"myESSID"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  **Access Point: Invalid**
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
I spent ages with a very helpful guy on this forum last night trying to work out what to do... We have drawn a blank, and not sure what to do...

Any ideas?

Sorryjustme, aka The Judderman

---

### Post by JamieC on 2007-02-07
You need to set the SSID of your router. You can do this using the following command (where <device> is the name of your network interfaces (wlan0, eth0, etc) and <ssid> is your router's SSID.):
```

sudo iwconfig <device> essid <ssid>

```

---

### Post by sorryjustme on 2007-02-07
> **JamieC said:**
> You need to set the SSID of your router. You can do this using the following command (where <device> is the name of your network interfaces (wlan0, eth0, etc) and <ssid> is your router's SSID.):
```

sudo iwconfig <device> essid <ssid>

```

I have already done that... I changed the essid in the post for anonymity (a bit pointless I realise, but hey!!!) and it still has the same output from iwconfig:access point invalid...

I realise this is something to do with the MAC allocation, and we tried messing round with that last night with iwconfig, but it still wouldn't work out...

---

### Post by sorryjustme on 2007-02-07
My latest thoughts are that I probably mucked up some important config file, while trying to connect to wpa, and that my best bet might be to just reinstall Ubuntu?
In which case, I was wondering wether it makes more sense to stick to Dapper, or to upgrade to edgy..... but that is another post and not appropriate here...

---

### Post by Mba7eth on 2007-02-07
did you try any network manager application ? 
if not go for wifi-radar . 
if your wlan is encrypted try network-manager .
those packages in the repository . 
Try and tell us :D

---

### Post by sorryjustme on 2007-02-07
> **Mba7eth said:**
> did you try any network manager application ? 
if not go for wifi-radar . 
if your wlan is encrypted try network-manager .
those packages in the repository . 
Try and tell us :D

yes, I have got network manager installed, and when I try to connect to my wireless it just times out... 
In the past, I also tried wifi-radar, and couldn't get it configured. I gather that there are sometimes conflicts between the two, so I have now removed wifi-radar...
For the time being, I have taken off encryption while I sort out the problem anyway...

---

### Post by Mba7eth on 2007-02-07
```
$ifconfig -a
$iwconfig
$iwlist scan 
```
please !!!

---

### Post by JamieC on 2007-02-07
> **Mba7eth said:**
> ```
$ifconfig -a
$iwconfig
$iwlist scan 
```
please !!!

He has an invalid access point, this will not help.

I suggest you ensure that the SSID is correct, you should specify it as a string, not seperated by colons. The SSID will then relate to the MAC address of your router, therefore you will have a valid access point.

If your access point has a custom name you may want to consider using the default string of 12 characters.

---

### Post by sorryjustme on 2007-02-07
ifconfig -a :
eth0      Link encap:Ethernet  HWaddr 00:14:38:08:A9:6A
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:38ff:fe08:a96a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5269 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4690384 (4.4 MiB)  TX bytes:1170173 (1.1 MiB)
          Interrupt:185

eth1      Link encap:Ethernet  HWaddr 00:90:4B:A6:3F:E7
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:43017 (42.0 KiB)
          Interrupt:11 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1272 (1.2 KiB)  TX bytes:1272 (1.2 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

**peter@laptop:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Judderman"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

**peter@laptop:~$ iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

Any help?! These haven't changed one bit in all the work we did last night!!! How depressing!!!!

---

### Post by Mba7eth on 2007-02-07
try
$sudo ifdown eth1
$sudo ifup eth1
$iwlist eth1 scanning

PLEASE !

---

### Post by sorryjustme on 2007-02-07
peter@laptop:~$ sudo ifdown eth1
Password:
Sorry, try again.
Password:
Ignoring unknown interface eth1=eth1.
peter@laptop:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.
peter@laptop:~$ iwlist eth1 scanning
eth1      No scan results

What does it mean by ignoring unknown interface eth1=eth1?

Hope this helps you?!!!!

---

### Post by sorryjustme on 2007-02-07
any ideas, anyone?

---

### Post by sorryjustme on 2007-02-07
Any new ideas from anyone?

---

### Post by HuckleSmothered on 2008-04-08
**Solution:**
Hit the *Fn-F2* keys
Run *sudo /etc/init.d/networking restart*
Check *iwconfig*

**Background:**
Earlier, I was attempting to hit Alt-F2 to run a program, was in an hurry and hit every other key but Alt, including the Fn key. And on my Dell Latitude D800 the Fn-F2 key has a small picture of a radio antenna on it. Not too obvious.

**Source:**
[https://answers.launchpad.net/ubuntu/+question/14689](https://answers.launchpad.net/ubuntu/+question/14689)

---

### Post by DoctorLes on 2008-05-18
Hi, 

I recently updated Kubuntu Gutsy Gibbon to Hearty Heron, or whatever it's called. Since then, I've lost my internet connection.  I was using a thumb drive USB wireless adapter.  So I had a long go at trying to get the integrated wireless chip in my laptop to function--it never did in Gutsy Gibbon either. 

So now I'm having a hair-pulling day on this same kind of problem. 

First, please just tell me where to find my Access Point; I think I know what it is, but where do I find the magic numbers that iwconfig demands?  I can get into my setup screen on my DLink wireless server but there is no mention of any "access point" numbers per se'.  I suspect they use a synonym, but what is it?  My ssid is simply "default", and I don't use a nickname.  

All this is because I'm trying to get an HP laptop that has a Broadcom b4306 wireless chip in it.  I've tried updating the firmware on the chip, using ndiswrapper for the driver, etc., etc.  This is really using up one hell of a lot of time. 

I'm also wondering that if the laptop's wireless chip isn't really tweaked or installed just right then all the iwconfig efforts will continue to throw back misleading information?  

Thanks for anything

Les

---

