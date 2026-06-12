---
title: "Problem getting Wireless to work"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by shmoe010 on 2008-04-16
I had my wireless working for a little while, but now it has stopped working again and I can't seem to get it going. I have a Linksys WUSB54G external USB wireless adapter which has a Ralink chipset.

The drivers that ship with 7.10 didn't work, so I removed them and installed a stable Serialmonkey driver instead, which worked for a couple of days.

Now when I log in, it sees my wireless adapter (called rausb0) but when I click on the network GUI it says "wireless disabled" and it's greyed out. In the config program, my only choice is to disable roaming mode, and when I do that and put in all the info for my wireless network it still won't connect.

Wired connection works fine, but I really need to get the wireless working. Here's the output from terminal:

***@garlinux:~$ sudo ifdown rasub0
ifdown: interface rasub0 not configured
***@garlinux:~$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

rausb0    RT2500USB WLAN  
          Link Quality:0  Signal level:136  Noise level:113
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

I don't know what "lo" is either, but it seems to have showed up about the time my connection stopped working. If there are some other command-line things I could do that would be helpful, as I'm new to linux. I'm probably going to look like a nublet when someone tells me what I did wrong, but that's what the beginner forums are for right?

Cheers!

---

### Post by phidia on 2008-04-16
Hi, wireless can be a pain sometimes. I don't know if this will work but often trying the simple stuff 1st is the best way to go.
"lo" btw is loopback device see if that is selected in (from the top menu) System>Administration>Network tools. If it is change it to the wireless interface.
I have found that sometimes gets wireless working again. Why the loopback device gets selected in the 1st place I don't know. Hope that helps.

---

### Post by dstew on 2008-04-16
> I don't know what "lo" is eitherThat is your local loopback interface, it is a standard feature, don't worry about it.

Is that really the full output of iwconfig? Your wireless driver is not giving much information.

Do you have a configured and working wired interface? Post the output of ifconfig.

---

### Post by shmoe010 on 2008-04-16
***@garlinux:~$ sudo ifconfig

eth0      Link encap:Ethernet  HWaddr 00:01:29:D4:63:25  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fed4:6325/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53698021 (51.2 MB)  TX bytes:3204414 (3.0 MB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:01:29:D4:63:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by Austin_KW on 2008-04-16
You ra interface is not up.

These drivers do not work well with network  manager and are better configured manually or thru /etc/network/interfaces

what is the output of the following commands
sudo ifconfig rausb0 up
sudo iwlist scan

---

### Post by shmoe010 on 2008-04-16
Running ifconfig rausb0 up just left white space and then looked like I held down the 'enter' button (repeated prompts.)

iwlist scan gave me this:

rausb0    Scan completed :
          Cell 01 - Address: 00:1C:10:0B:AF:FE
                    Mode:Managed
                    ESSID:"Lolipop"
                    Encryption key:on
                    Channel:6
          Cell 02 - Address: 00:1C:10:0B:B0:88
                    Mode:Managed
                    ESSID:"you're my"
                    Encryption key:on
                    Channel:6
          Cell 03 - Address: 00:13:10:FD:B2:61
                    Mode:Managed
                    ESSID:"linksys_SES_16313"
                    Encryption key:on
                    Channel:6
          Cell 04 - Address: 00:1A:70:67:BA:5D
                    Mode:Managed
                    ESSID:"D2R"
                    Encryption key:on
                    Channel:6
          Cell 05 - Address: 00:14:BF:40:23:DE
                    Mode:Managed
                    ESSID:"lemurs"
                    Encryption key:on
                    Channel:6
          Cell 06 - Address: 00:1C:10:1E:04:02
                    Mode:Managed
                    ESSID:"loonies"
                    Encryption key:on
                    Channel:6
          Cell 07 - Address: 00:18:39:4D:63:CD
                    Mode:Managed
                    ESSID:"linksys"
                    Encryption key:off
                    Channel:8

---

### Post by Triggerhapp on 2008-04-16
You need to connect to an interface by setting a MAC and/or key etc.

try these
```

sudo iwconfig rausb0 addr ADDRESSOFYOURNETWORK
sudo iwconfig rausb0 key s:YOURKEY
sudo iwconfig rausb0 essid YOURESSID
sudo ifconfig rausb0 up
#NOTE: ifconfig this one
sudo dhclient rausb0

```

---

### Post by Austin_KW on 2008-04-16
the ifconfig command just brought up the interface, the iwlist command verifies that the adapter is working and can see your network.

Follow Triggerhapp instructions above; 
Not sure about the first command the one I know is 
```
sudo iwconfig rausb0 ap MAC_ADDR_OF_AP
``` but this should not be necessary as it should find it from the eSSID/networkname

Also if you use a wep hex key eave off the "s:"
```
 sudo iwconfig rausb0 key YOUR_HEX_KEY
```

If you use WPA-PSK post back and we can give you a slightly different command sequence.

And if it works post back and we can tell you how to add the commands to /etc/network/interfaces to automate the commands

---

### Post by Triggerhapp on 2008-04-16
> Follow Triggerhapp instructions above; 
Not sure about the first command the one I know is 
```
sudo iwconfig rausb0 ap MAC_ADDR_OF_AP
```


Yes very correct, my mistake!
I was writing that from memory :P

I've actually written up a perl script to get all the info depending on which ESSID and set my custom keys for each network i use. Its enough for me.

---

