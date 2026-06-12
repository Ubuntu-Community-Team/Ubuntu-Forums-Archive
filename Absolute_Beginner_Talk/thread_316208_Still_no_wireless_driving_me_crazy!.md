---
title: "Still no wireless: driving me crazy!"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-12-10
Hi,

I'm running Ubuntu 6.10 and after numerous trials my wireless is still not working. I have an Intel 2200 BG wireless card and this card is supposed to work "out of the box" with Edgy.

I have installed GNOME network manager and can connect to my wireless network but I can't browse the internet and I cannot ping adresses (either IP or names). I can access my wireless router configuration (through wireless connection) and I removed the WEP encryption. But again I can connect to the network but cannot browse or ping anything. My wired connection works fine with DHCP but my wireless is still not working. I tried to put a static IP address but I'm still not able to browse or ping anything! I also compiled and installed the latest kernel 2.6.19 and the latest intel firmware version 3 but still have the exact same issues. Disabling the wired connection and leaving only the wireless connection enabled in System/administration/Networking doesn't bring anything as well:(


I really don't understand what's happening. My card is nothing fancy and I know people get it working in Ubuntu 6.10 but what am I doing wrong here??

Any help greatly appreciated!

Output of some commands:

**iwconfig**
lo        no wireless extensions.

eth1      unassociated  ESSID:"kilou"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:256  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

**lspci**
01:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

**ping -c 4 [www.google.com](www.google.com)**
ping: unknown host [www.google.com](www.google.com)

**ping -c 4 216.239.39.99**
PING 216.239.39.99 (216.239.39.99) 56(84) bytes of data.

--- 216.239.39.99 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms

**sudo gedit /etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid kilou
wireless-key **********

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



Of course the first and last output are slightly different when no encryption key is set but WEP active or not I still can't browse or ping. Is the problem related to the fact that iwconfig returns that my network is "unassociated"??? What does it mean?

---

### Post by spd106 on 2006-12-10
Unassociated usually means that it can't find an access point for the essid. What result do you get from **sudo iwlist eth1 scan**?

---

### Post by kilou on 2006-12-10
Thanks for your help! The sudo iwlist eth1 scan gives the following:

eth1      Scan completed :
          Cell 01 - Address: 00:13:46:A7:AE:50
                    ESSID:"Kilou"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=92/100  Signal level=-53 dBm  
                    Extra: Last beacon: 104ms ago


Also I made a mistake before because I ran the iwconfig command when connected to the wired network, so wireless appeared as unassociated. If I connect to the wireless network and then run iwconfig again I have the following:

lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Kilou"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:A7:AE:50   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=93/100  Signal level=-35 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:256  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

So now the association works correctly...but still no browsing or pinging possible :(

---

### Post by igknighted on 2006-12-10
Download the program wifi-radar.  As long as your wifi card is working, wifi-radar can do all the connection settings for you and find the networks.  Its a really nifty little program.

---

### Post by kilou on 2006-12-10
Tried wifi-radar but the same occurs: it says I'm connected but it won't let me browse or ping anything....and I prefer Gnome network manager anyway. I'm totally lost here, my hardware is very common but I connect get a wireless connection working.

---

### Post by igknighted on 2006-12-10
Hmm, I am curious, when it says you connect does it give you an IP address?  That's how I know when my wireless is screwy, I get a message that says I am connected, but no IP address.  Also, are you using WPA encryption?  If so this might be the issue.  Ubuntu struggle with it.

---

### Post by kilou on 2006-12-10
I have an IP and I use WEP encryption (not WAP). However I also tried desactivating WEP but still get the same results: I'm connected but cannot ping anything.

---

### Post by spd106 on 2006-12-10
Could you post the output of **ip route**? To see if you have a default route set to the wifi router/gateway.

Also check if there are any firewalls running that might be stopping ping requests.

---

### Post by kilou on 2006-12-10
Output of ip route when connected to wireless:

192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.100 
default via 192.168.0.1 dev eth1 

I have disabled the firewall too. I also tried to disable IPV6 (not only in FF) following this guide [http://ubuntuforums.org/archive/index.php/t-6841.html](http://ubuntuforums.org/archive/index.php/t-6841.html) but then again browsing and pinging still doesn't work. I don't have any MAC address filtering in my router settings too. This is incredible ](*,)


PS: my router is a D-Link DI-624 Xtreme G

---

### Post by spd106 on 2006-12-10
Are there any firmware updates available for the router? Maybe you could try another AP or borrow a friends NIC.

Sorry, I'm starting to clutch at straws now.

Maybe it's worth trying to capture packets with Ethereal (Wireshark) or tcpdump.

---

### Post by igknighted on 2006-12-10
I have that exact same router and have never had an issue, so I doubt the router is to blame.  How did you set up the wireless card?  What drivers did you use?  If you are having issues, you can always try Ndiswrapper, which is not difficult to use.

---

### Post by kilou on 2006-12-11
I didn't try Ndiswrapper yet because wireless in Edgy with a intel 2200bg card is supposed to work out of the box. At first I did not setup anything for the wireless card, I only installed Gnome network manager to be able to see available network...and this works. I could successfully connect to my network so the card and router seem to work correctly. But I just cannot ping anything. That's why I believe it's something related to a setting somewhere rather than a problem with the card, router or drivers. The strange thing is that it works for most people but not here. I've also booted from the LiveCD and the wireless doesn't work there as well: again I can connect no problem but cannot ping. However my wired connection works without a hitch.

I really don't understand what's going on :-k

PS: my laptop is MSI S260 with onboard wireless card Intel 2200BG. I have the latest Linux kernel (2.6.19) and latest IPW2200 firmware (ver. 3) but the wireless has never worked with these as well as with the "stock" Ubuntu Edgy kernel and IPW2200 firmware.

---

### Post by igknighted on 2006-12-11
I'm out of my league now... I'd have to recommend posting this in the networking forum, maybe someone there knows

---

### Post by kilou on 2006-12-11
Is it allowed to restart the same topic on another section?? Or can a moderator transfer this topic to the networking section please :)

The best would be to make a symlink of this thread in the networking section but I'm not sure this is possible :D

---

