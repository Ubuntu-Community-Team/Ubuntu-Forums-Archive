---
title: "how to see the strength of the wi-fi signal"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-07-20
Hello,
I have 3 questions all related to wireless networking. 
1. I am using a wireless home network to get connected to internet. I am wondering whether I can see the strength of the signal. I know I am connected but currently I can not see how strong the signal is.
Any help will be appreciated.

2. I am new in wireless network management. if anyone can suggest handy softwares to manage the whole network and configure the router, that would be helpful.

3. There is an icon at the right top that shows there is no connection through Ethernet card.  It is kinda annoying. May I have it disappeared? Thanks...

Thanks in advance....

---

### Post by NilsE on 2007-07-20
NETWORK MANAGER

The following steps worked for me which I culled from a few other posts. 

I would first to to add the "notification applet" (outlined at the bottom of this) to the panel to see if it shows up. The nm-applet will show you connection strength

```
In Synaptic package manager:

1) Make sure network-manager-gnome  is installed
2) Install libpam-keyring
```

```
In terminal:
sudo echo "@include common-pamkeyring" | sudo tee -a /etc/pam.d/gdm

NOTE: This will allow you to remember connection passwords/keys in the keyring

and not get prompted by the keyring manager every time. This is not mandatory.
```

```
In System/Preferences/Session:

Add gksudo nm-applet (if the network manager is not already  there) as the command 
line to a new start programs. You can name it whatever you want. It may
work without the gksudo.
```

```
You may also have to clean out the /etc/network/interfaces file if you have

 configured any devices manually. Just leave these 2 lines. (back it up first)

auto lo

iface lo inet loopback
```
SHUTDOWN AND RESTART

NOTE: The applet may not show up in the upper panel so you can right click
on the top panel, select add to panel then add the notification applet.

NOTE: After the first time you try to connect to a new available network in the pulldown it will ask for the SSID and key etc. but should remember it after that.

NOTE: Make sure that in the manual settings for the configuration that all devices are set to roaming.

---

### Post by Kralizec on 2007-07-20
A way to view your signal strength via terminal would be to type 'iwconfig' then look for the line that reads 'Link Quality' which should give you a value out of 100, referring to a percentage.
This is my result:
```

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11g  ESSID:"9313Brookwood"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:13:46:A9:8F:D2   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          **Link Quality:39/100 ** Signal level:-71 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by S15_88 on 2007-07-20
when you're parousing wifi signals for strength's you can do an:  iwlist scan  and it will also show the Link Quality: #/100.

Thanks, Alain

---

### Post by moore.bryan on 2007-07-21
*through quite a bit of blood, sweat, and tears, i almost got network-manager working exactly how i wanted... the only problem was it was still only "almost."  then i found [wicd]("http://wicd.sourceforge.net/") and my prayers were answered!  it will save, encrypted, my wpa passphrase and i can get it to load before my x-session so it's already running when the desktop shows up!  i find it INFINITELY better than network-manager!*

---

