---
title: "Ubuntu and wireless Belkin F5D8230-4"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by huntis619 on 2008-01-09
Hello all. I have a hp zv5410us laptop and I am having trouble connecting to the internet by wireless. I can connect by ethernet. :popcorn:

---

### Post by huntis619 on 2008-01-09
Also if anyone has info on the touchpad on my laptop. I don't use a mouse. Every now and then when I move the cursor it will open up pages without me clicking the buttons.....aghh HELP

---

### Post by eolson on 2008-01-09
If your using Gutsy
   System > Preferences > Mouse
     You'll find the touchpad stuff there.

On your wifi,  what chipset do you have?

---

### Post by huntis619 on 2008-01-09
I m still new to this. chipset for wifi?

---

### Post by huntis619 on 2008-01-09
I went to preferences for the touchpad and tap to click and vertical scrolling is checked. horizontal scrolling is unchecked. I am still having same problem. Its becoming rather annoying

---

### Post by huntis619 on 2008-01-09
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Steven"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by burpsmirk on 2008-01-09
I'm having the same issue.

WPA wireless works fine with my Asus router & my Buffalo router at home, but it will not work with my Mums Belkin F5D7633.

Unfortunately I don't really know anything like enough to start experimenting with config files.

lshw shows a "PRO/Wireless 3945ABG Network Connection", "Intel Corperation", driver is "ipw3945". Also _sometimes_ "Wireless=unassociated".

ifconfig reports (manually assigned) IP address

iwconfig shows correct ESSID as well as all the other relavant info (AP mac address for example). _Occassionally_ the first word is "unassociated"

iwlist scan reports the correct access point & signal quality approx 82/100.

Finally, host [www.google.com](www.google.com) returns ",, connection timed out; no servers could be reached"

Hope this might of use to someone.

---

### Post by burpsmirk on 2008-01-09
Actually, I've just cracked my problem. Thought I'd post the solution incase anyone else encounters it.

Network Manager was not correctly generating the PSK from my network password. Either that or it was not saving the updated /etc/network/interfaces with the new one (I have 2 locations saved).

In a terminal, run

```
wpa_supplicant <Network ESSID> <passphrase>
```

then copy the psk into the "wpa-psk" field in your /etc/network/interfaces file. You may find you need to re-do for your "other" wireless network when you move back (if you have another wireless network).

Hope it helps.

---

### Post by huntis619 on 2008-01-09
Nope didn't work for me

---

### Post by burpsmirk on 2008-01-10
Thats about as much help as I'm able to offer I'm afraid. Your wireless card appears to be connected ok to the router.

I would check the following:

1. Do you have a DNS configured?
  - Does your router accept pings & can you ping it's IP address?
  - If yes, can you ping [www.google.com?](www.google.com?)
  - If no, you likely need a DNS entry (usually your routers IP address)

2. Is your router configured with any kind of wireless security? MAC/IP filtering, for example?
  - If yes, ensure that you add your wireless cards IP/Mac address

3. Are you using a DHCP server?
  - If so, has your wireless card correctly configured itself with the right IP addresses?
  - If not, is your manually assigned IP address in the correct subnet for your network?

After all that, I would double check that your /etc/network/interfaces file looks how it should. Try this post for more info: [http://ubuntuforums.org/showthread.php?t=202834&highlight=wireless+WPA+WEP+HOWTO]("http://http://ubuntuforums.org/showthread.php?t=202834&highlight=wireless+WPA+WEP+HOWTO")

---

### Post by burpsmirk on 2008-01-10
Also, double check your SSID. Apparently this can cause "Access Point: Invalid".

[http://ubuntuforums.org/showthread.php?t=355400&highlight=Access+Point+Invalid]("http://ubuntuforums.org/showthread.php?t=355400&highlight=Access+Point+Invalid")
[http://ubuntuforums.org/showthread.php?t=662363&highlight=Access+Point+Invalid]("http://ubuntuforums.org/showthread.php?t=662363&highlight=Access+Point+Invalid")

Other than that, I can't find much info on "Access Point: Invalid" I'm afraid.

---

