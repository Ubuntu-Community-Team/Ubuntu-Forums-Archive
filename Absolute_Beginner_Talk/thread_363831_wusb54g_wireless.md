---
title: "wusb54g wireless"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by nafphsis on 2007-02-17
hello, I am fairly new to linux, and I just recently installed xubuntu 6.06 on an older computer and I am having trouble getting my wireless adapter to work. I installed ndiswrapper and ndisgtk and successfully installed the drivers off my wireless cd. but if i go to set it up under network settings under the rausb0 and activate it my computer freezes up and i have to reboot. I read somewhere that i need to disable the rausb0 wireless by blacklisting the rt2570 driver. but when i try to do this by typing:

$sudo gedit /etc/modprobe.d/blacklist rt2750

it tells me that that driver isnt on the system, so therefore it cannot blacklist it. 

I feel like I am close to getting the internet to work but whatever I try doesnt really seem to work. I believe i need to change the rausb0 to wlan0 in order to get my wusb54gv4 adapter to work but i am not sure how to do this.

hears some additional information if it helps any:

when I type in ifconfig I get:

lo link encap: Local Loopback
inet addr: 127.0.0.1 mask:255.0.0.0
up loopback running mtu: 16436 metric:
rx packets:3 errors:0 dropped:0 overruns:0 carrier: 0
rx bytes: 172 (172.0 b) tx bytes: 172 (172.0 b)

When I type iwconfig I get:

lo no wireless extension
eth0 no wireless extension
rausb0 rt2500usb wlan essid
mode: managed frequency= 2.412ghz
rts thr: off fragment thr: off
link quality 0/70 signal level:-120 dbm
noise level -256 dbm
...etc

I have know idea if that info helps 

any suggestions?

---

