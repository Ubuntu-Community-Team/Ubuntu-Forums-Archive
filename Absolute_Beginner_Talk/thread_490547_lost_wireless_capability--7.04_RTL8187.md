---
title: "lost wireless capability--7.04 RTL8187"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by scholzilla on 2007-07-02
Hi, 

Any experts out there on wireless cards? I had installed a network manager substitute program called wicd to try and troubleshoot another problem I was having, but needed to uninstall it and reinstall network manager (I won't get into details here, partially cause I can't reconstruct everything). Now I am unable to see any wireless network at all. If I pull down my network manager menu, I only get the options for wired networking and manual config, no wireless. Roaming mode is enabled and I've been through all the help on the ubuntu official docs. My chipset is supported (Realtek RTL8187) and I was connecting to wireless just fine before I decided to screw with things I don't know enough about. 

For what it's worth, here's my output for [COLOR="DarkSlateBlue"]iwconfig:[/COLOR]

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

For the sake of brevity, I've attached a copy of the output of [COLOR="DarkSlateBlue"]lsmod [/COLOR]as well.

Thanks in advance from a frustrated noob

---

### Post by ncappel1 on 2007-07-02
If you've been through the documentation, you may have tried this, but it looks as though there is no essid or accesspoint associated with wlan0. Have you tried the following?
```
sudo iwconfig wlan0 essid any
```
```
sudo iwconfig wlan0 ap auto
```

also, you should double check that the channel the signal is being sent through is the same channel the card is scanning. try:
```
iwlist scan
```
and see if the channel is the same listed in your iwconfig output for the same card.

---

### Post by scholzilla on 2007-07-03
Thanks, and by the way, sorry to all that I double posted this on the wireless board. I didn't discover there was a wireless forum until after I posted here.

As I noted there, I get the following output for iwlist:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Failed to read scan data : Operation not supported

wlan0     No scan results

Does this tell you anything? I entered the code you suggested, and with each line, I just returned to bash with no output.

Thanks for your help.

---

### Post by scholzilla on 2007-07-03
one more thing: I considered reinstalling the driver for my chipset (RTL8187), but there are two separate software packages offered by Realtek to support either RTL8187L or RTL8187B. If anyone has any idea which one does what, I would love some insight. The Realtek site doesn't offer much help.

---

### Post by panurge77 on 2007-07-05
I guess 8187B and 8187L and different hardware models. Mine is 8187L. The native linux drivers are not good, so I had to blacklist the driver, install windows98 driver with ndiswrapper, disable network manager and set /etc/network/interfaces with essid and passkey.

---

