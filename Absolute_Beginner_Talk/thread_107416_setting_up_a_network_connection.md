---
title: "setting up a network connection"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by anoncompboy on 2005-12-23
I have gone into network settings and my wireless card is enabled and activated, and have entered the correct SSID and WEP key. Still, Firefox does is not able to load any content. I have DHCP enabled instead of a static IP, is this right? Also, do I need to add a DNS server to the list?

---

### Post by macheadPDX on 2005-12-23
[QUOTE=anoncompboy]I have gone into network settings and my wireless card is enabled and activated, and have entered the correct SSID and WEP key. Still, Firefox does is not able to load any content. I have DHCP enabled instead of a static IP, is this right? Also, do I need to add a DNS server to the list?[/QUOTE]

Have you tried deactivating and then activating the wireless connection in the Network Settings window?  

 I installed network-manager using Synaptic Package Manager (Systems>Administration> Synaptic Package Manager). Just an easier way to manage your network connections.

Good Luck!



I

---

### Post by akniss on 2005-12-23
[QUOTE=anoncompboy]I have gone into network settings and my wireless card is enabled and activated, and have entered the correct SSID and WEP key. Still, Firefox does is not able to load any content. I have DHCP enabled instead of a static IP, is this right? Also, do I need to add a DNS server to the list?[/QUOTE]

More information would be helpful.  Have you tried following the directions here
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29](https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29)
Post anything you don't understand or where things aren't making sense.  At the very least post the results of the commands:
iwconfig
ifconfig

---

### Post by anoncompboy on 2005-12-23
Thanks, went to that site and found that the only driver compatible with my wireless card is [madwifi]("http://madwifi.org/wiki"). I downloaded and extracted, and its just a filedump. Has anyone messed around with madwifi? What do I do?

---

### Post by Lambert on 2005-12-23
madwifi comes with breezy so there's probably a configuration tweak that needs to make your wireless work.

after trying to activate the interface post the output of iwconfig and ifconfig here.

Also what kind of wep settings do you have? Open or shared key? hexadecimal or ascii key?

Post the output of your /etc/network/intefaces file here. You can xxx out any personal information

Also what card make and model # are you using?

try this command

sudo iwlist ath0 scan. Do you get output where it can see your router?

---

### Post by akniss on 2005-12-23
[QUOTE=anoncompboy]Thanks, went to that site and found that the only driver compatible with my wireless card is [madwifi]("http://madwifi.org/wiki"). I downloaded and extracted, and its just a filedump. Has anyone messed around with madwifi? What do I do?[/QUOTE]

The wireless card I had in my desktop machine uses the madwifi driver, and it worked 'out-of-the-box' with Breezy.  Give it a go!

---

### Post by anoncompboy on 2005-12-25
Thanks for the help everyone, wouldnt know what to do without it!

Lambert, you sound like you really know what you are talking about so I will share all my tasty data with you...

1)iwconfig```
matt@thewoodmachine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"ApexPolice"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:11:50:3B:99:F9
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```
2)ifconfig```
matt@thewoodmachine:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:95:92:C2:39
          inet6 addr: fe80::211:95ff:fe92:c239/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:3441 dropped:0 overruns:0 frame:3441
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:140 (140.0 b)
          Interrupt:19 Memory:e0ae0000-e0af0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:90629 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6725822 (6.4 MiB)  TX bytes:6725822 (6.4 MiB)
```
3) /etc/network/interfaces file:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface ath0 inet dhcp
wireless-essid ApexPolice
wireless-key s:xxxxxxxxx
auto ath0
```
4)sudo iwlist ath0 results: I got a list of all the wireless networks my card usually detects in windows when it is working. It is far too long to post so I will just include where it detected my wireless network.
```
          Cell 05 - Address: 00:11:50:3B:99:F9
                    ESSID:"ApexPolice"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=15/94  Signal level=-80 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:wpa_ie=xxxxxxxxxxxxxxxxxxxx
```
5) I also went into device manager and located the wireless card, here are a few bits of info that I retrieved, may help:
```
(Device Manager>Computer>Unknown (0x001a)>Networking interface)

linux.sysfs_path type=string /sys/class/net/ath0
net interface type=string ath0
net.interface_up type=bool false
net.physical_device type=string /org/freedesktop/Hal/devices/pci_168c_1a
```

6) the card is a **[D-link DWL-G510]("http://www.dlink.com/products/?sec=0&pid=308")**. Have had no problems with it in windows.

---

### Post by Lambert on 2005-12-25
Long day and tired, about to call it a night but here are some last minute thoughts. I'll come back to this later.

1. The one answer I didn't see is if you're using open or shared key. So I'm going to recommend this on an assumption.

run this command

```
sudo iwpriv ath0 authmode 2
```

then

```
sudo dhclient ath0
```

then try to surf. If that doesn't work then try authmode 3

2. your command iwlist ath0 scan gave this last line

extra:wpa_ie 

I believe you put the x's there in place of the normal output but could be bad assumption.

My understanding is this line tells that  the router is using wpa and not wep. In that case you need to install an app wpasupplicant and configure with wpa and not wep.

If so go to this link to set up wpa.

[https://wiki.ubuntu.com/WPAHowto?highlight=%28wpa%29](https://wiki.ubuntu.com/WPAHowto?highlight=%28wpa%29)


Your current problem. Your device is not being assigned an ip address. When you run ifconfig you should see a line like this.

 inet addr:192.168.1.12  Bcast:192.168.255.255  Mask:255.255.0.0

the inet addr being the ip assigned to the device. Right now the router is not authenticating your dhcp request and sending you a dhcpoffer. 

verify you are using wep and not wpa and try these things. Post back anything you think relevant.

---

