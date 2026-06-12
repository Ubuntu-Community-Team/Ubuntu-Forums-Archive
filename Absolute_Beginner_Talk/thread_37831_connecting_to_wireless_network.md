---
title: "connecting to wireless network"
date: 2005-05-28
forum: Absolute Beginner Talk
---

### Post by semi-awesome on 2005-05-28
today i downloaded and burned a LiveCD of Ubuntu, and it looks great, but i can't figure out how to connect to my wireless network. i am running it on a powerbook, and the network base station is an airport express. help would be greatly appreciated.

---

### Post by phen on 2005-05-29
Hello!

i am not using an apple pc, but i will give you some hints and ideas, where to start.

Is your WLAN adapter installed?

open a terminal and
type "iwconfig

```

lo        no wireless extensions.

eth0      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

``` 


this output means, that my wireless card is called eth0, and that it is not connected at the moment. Now, you can try to type 

iwconfig <name of YOUR adapter> ESSID <NameOfYourNetwork>

example: iwconfig eth0 ESSID homenet

you should have set the ifconfig (general network interface config) to DHCP for your  Wlan adapter. it might work by now!

there are also gnome-tools to edit all the network-specific stuff, just as it is in windows. 

try type man iwconfig
or man ifconfig

for the manuals of both tools.

if nothing works, give us the following information:

ifconfig output
iwconfig output
dmesg | grep Wireless   (this lists all hardware found by the kernel with the word Wireless in it, you can also type dmesg alone!)


cheers,
kai

---

### Post by Stealth on 2005-05-29
Unfortunately, I'm pretty sure those Mac wlan cards aren't supported in Linux yet :(

---

### Post by pravit on 2005-05-29
Configuring ubuntu to connect to my wireless net is easy using the GNOME interface(administration->networking->enter all fields) but I can't figure it out using Kubuntu. I went all over the place in that control center entering various stuff but it just wouldn't work. In particular what irritated me was entering my gateway(192.168.1.1), hitting "Apply", then coming back and the gateway field would be empty again. It also said some weird stuff about typing an alias first when I was trying to add DNS servers. I was finally able to connect to my wireless router, but not to the internet...

---

