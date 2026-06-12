---
title: "wireless woes -beginner"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by eipi1 on 2007-12-09
I'm posting here because I think my troubles are more due to my experience level than any advanced technical issue related to my wireless. I have looked at related posts - tried many - but have found no solutions yet.

I have installed Ubuntu 7.10, 2.6.22-14, 64 bit

I have a Linksys wireless G system with a Linksys WMP54G PCI wiress card (Ralink rt61pci) .

The wireless router itself is setup as follows:
mode: wiress b and g
ssid: snapper
wireless channel: auto
broadcast ssid: enable
security: wpa/wpa2 personnel
wpa: enabled
wpa2: disabled
encryption: TKIP
personnel key: BOPLENTY
group key renew: 3600
MAC Filter: off
Basic rate set #2
Trans rate: auto
CTS Disabled
beacon 100
DTIM 1
Frag thresh 2346
RTS thresh 2347
preamble long
network density low


'lsmod |grep rt61' gives:
rt61pci                28288  0 
rt2x00pci              13184  1 rt61pci
rt2x00lib              21760  2 rt61pci,rt2x00pci
mac80211              196104  4 rc80211_simple,rt61pci,rt2x00pci,rt2x00lib
eeprom_93cx6            3712  1 rt61pci

In my task tray there is a network connections icon (two tiny black computer monitors side by side). When I click it I see the "snapper" wireless network! When I select the snapper radio button the passphrase dialog box opens. I enter:
Wireless Security: WPA Personnel
Password: BOPLENTY
TYPE: TKIP (or auto)

and click Login...

It tries to connect for around 2 minutes then aborts.

Also: It's right next to router. Dual OS machine and card connects fine in windows xp.

Please help. I can use the terminal OK but I don't have a good Linux intuition yet.

---

### Post by CRCarl on 2007-12-09
My guess is that TKIP is not being used by your wireless card / Gnome network manager. Lets try and do this manually then we will play with the GUI. 

First, lets find out where your wireless device is - (all in the terminal)

```
iwconfig
```

Only one interface (probably wlan0) will have wireless extensions, note that interface name. 

Lets check for TKIP support - 

```
iwpriv <interface name>
```

This should return a bunch or methods for accessing the wireless cards feature set. You need to find a line regarding encryption modes (on mine it is "set_encr_mode"). Assuming your card is the same is mine do this - 

```
sudo iwpriv <interface name> set_encr_mode tkip
```

Then try and connect, let us know. 

Craig

---

### Post by eipi1 on 2007-12-09
OK!, Below is what I get. Looks like something's up with iwpriv. What's next?

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwpriv wlan1
wlan1     Available private ioctls :
          param            (8BE0) : set   2 int   & get   0      
          get_param        (8BE1) : set   1 int   & get   1 int

---

### Post by CRCarl on 2007-12-09
I did a little Google - It looks like that card is not supported with TKIP unless you install the drivers from here: [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com").

Install those per the instructions, give it a try. That project has even produced a GUI to help configure the cards. Check it out. 

Craig

---

### Post by eipi1 on 2007-12-10
Saw that, and tried it. Still no luck (at make it errors with Unrecognised symbol)

I then setup the router to use WEP and still no luck.

Some have said the NM applet doesn't work with this card. I guess I'll try shutting it down.

Does any have a recent wireless G card that was a simple "no brainer" install?

---

### Post by d^v3 on 2007-12-10
A really easy way to get around this is to just add your wireless mac add to the router and enable MAC filtering. then turning your ssid off.  especially if your card doesnt support whatever algorithms you have already tried. or just get an atheros card....they seem to work pretty well

---

### Post by max1e6 on 2007-12-10
Thank you d^v3

I see Atheros is a chipset mfg. and that they have several home/office wlan products. Do you know of a currently available Make/Model that implements an Atheros technology in a Ubuntu 64 compatable PCI card.

---

