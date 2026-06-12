---
title: "Cannot connect to Internet with wireless"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by ahlandberg on 2006-05-15
I finally got my Netgear wireless card (WG311 v3) installed yesterday. Needed to use ndiswrapper and the driver files from the card's driver CD to fix the problem.

It seems that the card is correctly configured. I am using a wireless router which  runs DHCP. Therefore, I selected DHCP as connection type when configuring my ath0 connection. It even detected all wireless networks in my area and offered me to choose one to connect to. So all the settings seem to be ok.

When I now try to ping any other machine on the network (even my own one), it says: network unreachable. Also, when starting Firefox I cannot connect to the internet.

Who has got an idea what's wrong here?

Thanks in advance!

Cheers, Anders

---

### Post by whitey on 2006-05-15
Hello,

i just got my wireless working reliable, here are some things to do.  If your card is read using:

#sudo iwconfig

Then the card is configured correctly, at that point, your next big hurdle is finding a good wireless control package.  I prefer wifi-radar which allows me use WEP and WPA and automatically detects wifi hotspots on the fly.  You can download and install this with:

#sudo apt-get install wifi-radar

Hope that helps you.

---

### Post by jimrz on 2006-05-15
Check and make sure that you have DNS server address in Networking. For some reason on the Beta2 live cd on my machine those were omitted. Manually entering appropriate addresses cured the problem.

---

### Post by ahlandberg on 2006-05-16
Can't install wifi-radar because i have no internet connection and it's not available!

---

### Post by Koech on 2006-05-16
If you can't connect to internet you may have to connect via a LAn proxy first. Or if you can run windows then switch over to Linux ie after downloading it on windows.

---

### Post by DJ Scribblinni on 2006-05-16
> Here is the output from the commands 'ifconfig' and 'iwconfig':

'ifconfig'
-------------------------------------------------------------
ahlandberg@ubuntu:~$ ifconfig
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:6574 errors:0 dropped:0 overruns:0 frame:0
TX packets:6574 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:508716 (496.7 KiB) TX bytes:508716 (496.7 KiB)

wlan0 Link encap:Ethernet HWaddr 00:0F:B5:8B:AA:25
inet6 addr: fe80::20f:b5ff:fe8b:aa25/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Memory:ca010000-ca01ffff

ahlandberg@ubuntu:~$



'iwconfig'
-------------------------------------------------------------
ahlandberg@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.

wlan0 IEEE 802.11FH ESSIDff/any
Mode:Managed Channel:0 Access Point: 00:00:00:00:00:00
Bit Rate:1 Mb/s Sensitivity=-200 dBm
RTS thr:2346 B Fragment thr:2346 B
Power Managementff
Link Quality:100/100 Signal level:-71 dBm Noise level:-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:11 Invalid misc:7 Missed beacon:0



I notice you posted this twice so I just put everything in this reply where people have been chatting.  

From your output your computer is obviously not connected to the router, hence Access Points reads all zeros, and you do not have an IP address for wlan0. 

 My next thought would be to check the Properties you have for the wlan0, check the ESSID.  (Unless you get connected to that router, you won't get any IP address; even assigning a static IP won't even help you)

Other than that I seriously have no clue...

---

### Post by rubrboots on 2006-05-16
After weeks of playing with my Netgear MA111, I finally got it working. The main problem was that ubuntu has a native driver that appears to work. Meaning the NIC drivers are loaded and everythng appears a the wireless guides indicate they should. I could see my network at full strength in wifi radar but could not ping anything or get an ip address.

So I installed ndiswrapper using this guide [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

At first I didnt think that it worked at all, but I discovered that the old native driver was still bound to the NIC. So I stopped the service, restarted nidiswrapper and the NIC, then installed the driver again using ndiswrapper. Now when I went to Networking (not wifi radar), I noticed that there was a new network interface wlan1, I configured it for DHCP and activated. VOILA! it worked immediately.

I am sure its obvious that I dont know alot about this stuff, this was pretty much a trial and error thing, I dont even know why I no longer have wlan0. 
Also note that other guides had me editing interface files and such, which never worked. This success was after a clean install of dapper, and I did not manually edit any files. So if your interface files are all messed up this might not work.
Ndis will probably work but you will have to stop the native driver from taking over so the ndis driver can work. And when it is working it should connect easily through the built in ubuntu networking utility, my wifi radar was not showing any strength when I was actually connected and downloading updates.



Good Luck

---

### Post by joshrobinson on 2006-05-16
yeah ndiswrapper is a pain in the balls the first time you install it, but after you do it a few times, from reinstalling ubuntu, or installing ubuntu on someone elses computer with the same chipset, it because very easy

i also added a script into my init.d that exectues the commands to bring up my wireless interface, and connect to my wpa access point and grab an ip from my dhcp.. so everything is done by the time i get into gnome and im ready to go

```

lspci -v |grep -i bcm
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper


ifconfig eth0 up
iwconfig eth0 essid "home"
wpa_supplicant -B -D wext -i eth0 -c /etc/wpa_supplicant.conf
sleep 2
dhclient eth0
```

thats generally what my script looks like, obviously you would have to change it to fit your needs

---

