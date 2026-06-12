---
title: "Wireless connection problem"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by uwo2000 on 2007-12-27
Hi all,
I loaded Ubuntu 7.10 on my old Thinkpad A22m (256 MB RAM) and tried to connect to my wireless network - no luck so far. I am using a DLink Airplus G Wireless USB 2.0 adapter with WPA-PSK password. The adapter picks up nearby networks (including mine) but I cannot seem to connect it. I have entered my password and tried to configure it manually but no luck.
Any guidance would be appreciated.
Thanks!

---

### Post by jas0 on 2007-12-27
Since you can see your network and other networks, it's pretty safe to assume that your wireless card is installed properly. Here is one thing which I found sometimes helps connect to a network: in addition to typing in your key and selecting WPA-PSK/WPA2-PSK, also select either TKIP or AES. If that doesn't work, try resetting your preshared key to something else just to eliminate the possibility that you may be entering the incorrect key.

I'm sure other folks will come up with a few other suggestions.

Good luck!

---

### Post by walkerk on 2007-12-27
Give [WICD]("http://wicd.sourceforge.net") a try. It will automatically determine the correct encryption and connect.

Visit the linked site above or the thread listed in my signature.

---

### Post by uwo2000 on 2007-12-27
Thanks for the quick reply jas0. The 'wireless security' pull down menu in the 'Connect to other wireless network' window does not have a WPA-PSK option, so I tried the WPA Personal and WPA2 Personal options - no luck.
And yes, to ensure my password is correctly entered, I have on an opensource writer document from where I copy and paste it into the password box.

---

### Post by jas0 on 2007-12-27
WPA-PSK = WPA Personal. I should have written this, sorry.

When filling in the options in your wireless network, under 'type' select either TKIP or AES. Here at work, it simply does not work without selecting the encryption type.

Also, which access point do you have? This may help us see whether there are any known issues with your setup.

---

### Post by uwo2000 on 2007-12-27
I'm sorry - I am truly a newbie. If by access point you mean my router, I am using a DLink DI-524 802.11g router.

---

### Post by spiderbatdad on 2007-12-27
is it possible there is some aspect of the adapter's driver that is failing. I was looking for a link on drivers for usb adapters but i cant' find the one i'm looking for

---

### Post by jas0 on 2007-12-27
Again, sorry, I should have said router instead of access point.

Interestingly enough I have the same router and do not have any issues with my wireless connection on a few laptops running Ubuntu.

Here is what I would do if I were you, login to your router and make note of all the settings make sure that WPA-PSK (i.e. WPA Personal on Ubuntu) is selected and not WPA2-PSK. Also make note of the encryption being used (i.e. TKIP vs AES vs Both as the same time).

Once you have all this information handy, select the same settings when connecting to the wireless network. If this doesn't work, we'll have to get some information from your logs to see just where the connection process is failing. 

Also, if you have a Windows laptop handy or you dual boot your current one, make sure that you are indeed able to connect from there. This will give us some confirmation that the issue is definitely on the Ubuntu end.

---

### Post by uwo2000 on 2007-12-27
Ok - done the following:
- checked my router settings and made sure that the same setiings are used when I try to connect from Ubuntu - no luck
- the USB adapter is working fine as I used it earlier in the day to connect another machine to my router
- the router is also ok, as I am connected wirelessly to with this Dell laptop.

---

### Post by jas0 on 2007-12-27
Alright, try to authenticate again, wait 30 seconds and paste the last 30-50 lines of

```
cat /var/log/messages

and

dmesg
```

PS: If anyone knows of a better location to get log into, please feel free to help. ;-)

---

### Post by uwo2000 on 2007-12-27
Here is the outut:

Dec 27 17:11:09 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason

Dec 27 17:11:11 ubuntu kernel: [   50.796000] NET: Registered protocol family 17

Dec 27 17:11:12 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name

Dec 27 17:11:12 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain

Dec 27 17:11:12 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers

Dec 27 17:11:14 ubuntu kernel: [   53.012000] NET: Registered protocol family 10

Dec 27 17:11:14 ubuntu kernel: [   53.016000] lo: Disabled Privacy Extensions

Dec 27 17:11:42 ubuntu kernel: [   81.732000] ondemand governor failed to load due to too long transition latency

Dec 27 17:18:43 ubuntu kernel: [  502.464000] e100: eth0: e100_watchdog: link down

Dec 27 17:18:48 ubuntu kernel: [  506.892000] usb 1-1: new full speed USB device using uhci_hcd and address 2

Dec 27 17:18:48 ubuntu kernel: [  507.208000] usb 1-1: configuration #1 chosen from 1 choice

Dec 27 17:18:50 ubuntu kernel: [  509.196000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister

Dec 27 17:18:50 ubuntu kernel: [  509.196000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put

Dec 27 17:18:50 ubuntu kernel: [  509.196000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get

Dec 27 17:18:50 ubuntu kernel: [  509.196000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register

Dec 27 17:18:50 ubuntu kernel: [  509.472000] usbcore: registered new interface driver rt2500usb

Dec 27 17:18:51 ubuntu kernel: [  510.016000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Dec 27 17:19:21 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason

Dec 27 17:20:20 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason

Dec 27 17:21:24 ubuntu kernel: [  663.588000] ADDRCONF(NETDEV_UP): wlan0: link is not ready



[   44.984000] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)

[   45.096000] thinkpad_acpi: another device driver is already handling bay events

[   45.096000] thinkpad_acpi: disabling subdriver bay

[   45.588000] Non-volatile memory driver v1.2

[   45.616000] input: /usr/sbin/thinkpad-keys as /class/input/input7

[   45.812000] ondemand governor failed to load due to too long transition latency

[   46.052000] Failure registering capabilities with primary security module.

[   46.340000] Bluetooth: Core ver 2.11

[   46.340000] NET: Registered protocol family 31

[   46.340000] Bluetooth: HCI device and connection manager initialized

[   46.340000] Bluetooth: HCI socket layer initialized

[   46.376000] Bluetooth: L2CAP ver 2.8

[   46.376000] Bluetooth: L2CAP socket layer initialized

[   46.448000] Bluetooth: RFCOMM socket layer initialized

[   46.448000] Bluetooth: RFCOMM TTY layer initialized

[   46.448000] Bluetooth: RFCOMM ver 1.8

[   50.796000] NET: Registered protocol family 17

[   53.012000] NET: Registered protocol family 10

[   53.016000] lo: Disabled Privacy Extensions

[   63.696000] eth0: no IPv6 routers present

[   81.732000] ondemand governor failed to load due to too long transition latency

[  502.464000] e100: eth0: e100_watchdog: link down

[  506.892000] usb 1-1: new full speed USB device using uhci_hcd and address 2

[  507.208000] usb 1-1: configuration #1 chosen from 1 choice

[  509.176000] ieee80211_init: failed to initialize WME (err=-17)

[  509.196000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister

[  509.196000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put

[  509.196000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get

[  509.196000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register

[  509.200000] wmaster0: Selected rate control algorithm 'simple'

[  509.472000] usbcore: registered new interface driver rt2500usb

[  510.016000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[  663.588000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by jas0 on 2007-12-27
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/144239]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/144239")

Hm... doesn't look good.

---

### Post by anewguy on 2007-12-27
Do you have WPA supplicant running?  I don't know if it's "on" by default in any of the releases, but it used to be you had to turn it "on".

Also, I had similar problems with my 2WIRE wireless router (I'm using DSL) whenever I tried to use WPA - I could never get it to work, no matter what I tried for key and personal vs AES.  Nobody was ever able to supply an answer for me either.

I wonder if by chance your wireless card actually needs a WPA driver loaded besides just the hardware driver.  I've seen some adapters that use "extra stuff" to get WPA working.  Do you have the Windows driver disk for the card?  Look in there for a readme or some such thing and see if it says anything about using WPA.  

I suspect if you turn off WPA at your router you will be able to connect.  You may want to consider just using MAC address filtering.:)

---

### Post by anewguy on 2007-12-27
One other thing - I assume you are using the Windows drivers via ndiswrapper?:)

---

### Post by uwo2000 on 2007-12-27
1) Not sure how to check if the WPA supplicant is on or not - how do I do it?
2) I installed ndiswrapper from the CD-ROM but again, am unsure how to use this program.
3) I have been using this USB wireless adapter with an XP machine, and it works just fine with the WPA-PSK stuff, so I presume the Windows drivers must be installed and working......??? I did think about downgrading my security to WEP, but there are plenty of freeloaders in my neighbourhood, so am reluctant to do that, even with SSID off and MAC filtering.
4) I finally lugged an ethernet cable and connected the machine to my router with this, and I was up and running on the net in a second. So (from my extremely limited) knowledge, it does seem an issue with the Dlink USB wireless adapter. I have seen some discussion of this problem on the Web and saw some proposed solutions, but those were way way beyond my newbie level.
5) So, what are my options? Should I attempt to work around this driver/adapter problem or should I spend some $ on getting a new USB wireless adapter that works with Ubuntu?????

---

### Post by anewguy on 2008-01-02
I'm sorry I didn't get back to you sooner - the holidays and all kinda got in the way.  At any rate, if you still need help with your wireless let me know.:)

---

### Post by uwo2000 on 2008-01-06
Oh yes! Any help would be greatly appreciated. I am still struggling to get the Dlink to work. I tried an earlier suggestion of using WICD instead of Network Manager, but that was a step backward, as WICD didn't even recognize my USB wireless adapter. So I re-installed Network Manager and tried again, but no luck.
At this stage, I am even willing to consider spending some $$ at Best Buy to get a USB wireless adapter that works with Ubuntu......
Any suggestions are most welcome.
Thanks again,

---

### Post by walkerk on 2008-01-06
> **uwo2000 said:**
> Oh yes! Any help would be greatly appreciated. I am still struggling to get the Dlink to work. I tried an earlier suggestion of using WICD instead of Network Manager, but that was a step backward, as WICD didn't even recognize my USB wireless adapter. So I re-installed Network Manager and tried again, but no luck.
At this stage, I am even willing to consider spending some $$ at Best Buy to get a USB wireless adapter that works with Ubuntu......
Any suggestions are most welcome.
Thanks again,

Network Manager and WICD are only programs used to interface you to your wireless lan... they do not recognize your wireless hardware as that is the job of the kernel module (driver in windows talk)

2 Links both by wieman01.

1. [Ralink WLAN]("http://ubuntuforums.org/showthread.php?t=563547") (Get your hardware working properly)
2. [Wireless without Network Manager, WICD, etc...]("http://www.ubuntuforums.org/showthread.php?t=202834") (Set up your own network interface)

---

### Post by revpaul on 2008-01-06
This may help but make sure MAC address filterings is not enabled untill you connect then put pc into mac filter and re-enable it.

---

### Post by walkerk on 2008-01-06
> **revpaul said:**
> This may help but make sure MAC address filterings is not enabled untill you connect then put pc into mac filter and re-enable it.

If you're having issues connecting at all you should ensure that ALL security (Encryption/MAC Security) is turned off... Troubleshoot.

---

