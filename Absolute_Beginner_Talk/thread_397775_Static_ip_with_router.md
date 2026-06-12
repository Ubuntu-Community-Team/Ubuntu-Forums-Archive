---
title: "Static ip with router"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by vicked on 2007-03-31
Hip,

I tried to make static ip, but i cant access the router with that way. Only when i use "dhclient ath0"

I write down the following lines to the /etc/network/interfaces file:

iface ath0 inet static
pre-up iwconfig ath0 key s:1111111111111
pre-up iwpriw ath0 authmode 2
pre-up iwconfig essid "mz/x"
address 192.168.2.136
netmask 255.255.255.0
gateway 192.168.2.1

its only works when i use the dhclient, and i cant get static ip. 
Somebody pls tell me, what sould i do?

I use SMC wifi card, with madwifi driver and USR router.

---

### Post by PurplePenguin on 2007-03-31
I set mine up with a static IP by going (in Edgy) to System -> Administration -> Networking, clicking on my wired connection (you'd select your wifi connection), clicking Properties, switching from DHCP to Static IP, and entering the appropriate information.

That worked for me, and the best thing - no fooling around with configuration files! :)

---

### Post by vicked on 2007-03-31
i tried that way and its not worked. i switch to static ip, wrote down the infos to the fields, and do not work. 

i filled the essid, the key (i use 13 chars ascii wep key) and the ip what i want to get: 192.168.2.136, the subnet-mas: 255.255.255.0 and the gateway: 192.168.2.1, and when i reboot its not work.

---

### Post by Austin_KW on 2007-03-31
You sure it is not working, Remember you also need to set a dns nameserver

---

### Post by bogolisk on 2007-03-31
Unfortunately, my recipe is not really for *absolute beginners*

[LIST=1]
[*]enable static DHCP in the router (with some routers, this would require 3rd-party firmware)
[*]optionally enable DNSMasq in the router (with some routers, this would require 3rd-party fimrware)
[*]enter the MAC/IP combo of your PC to the router list of static dhcp
[*]repeat the previous step with other PC, labtops, etc.
[*]ensure that Ubuntu's dhcp client would send the hostname (e.g. /etc/dhcp3/dhclient.conf) if you want DNSMasq in the router to act as a local DNS server.
[/LIST]

I've done the above and now all comps would always receive the same IP even if it's DHCP. Also, name resolution also works so I can use hostname instead of IP.

---

### Post by Austin_KW on 2007-03-31
For most consumer routers 'static DHCP' is done by just setting the DHCP lease to never/long expire.

Also you should not be using an address that you got from DHCP as a static address. Static addresses should be assigned from outside the DHCP pool.

---

### Post by vicked on 2007-03-31
under xp, i could set the static ip, with a guide. i find this guide in the utorrent site. so i think the router is good configured. maybe you can make me an example what i need to set in linux :)

---

### Post by chili555 on 2007-03-31
Does your interfaces file include:```
auto ath0
```After you amend, if necessary, reboot and let us know.

---

### Post by vicked on 2007-03-31
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp



iface ath0 inet static
	address 192.168.2.101
	netmask 255.255.255.0
	network 192.168.2.1
	broadcast 192.168.2.255
	gateway 192.168.2.1
	wireless-essid mz/x
	wireless-key s:1212121212121


```

its my interface file

---

### Post by vicked on 2007-03-31
i add the auto ath0 line to the /etc/network/interface file, noting changed. :)

---

### Post by chili555 on 2007-03-31
Nothing changed after you rebooted, or what? What is the result when you do:```
sudo ifdown ath0
sudo ifup ath0
ping -c3 192.168.2.1
```And:```
sudo iwlist ath0 scan
```

---

### Post by Austin_KW on 2007-03-31
What exactly is not working?
post the output of the following commands
ifconfig ath0
iwconfig ath0
iwlist ath0 scan 
ping 192.168.2.1
ping google.com
dig google.com
cat /etc/resolv.conf

---

### Post by vicked on 2007-03-31
```

vicked@gwaeron:~$ sudo ifdown ath0
Password:
vicked@gwaeron:~$ sudo ifup ath0
vicked@gwaeron:~$ ping -c3 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.101 icmp_seq=1 Destination Host Unreachable
From 192.168.2.101 icmp_seq=2 Destination Host Unreachable
From 192.168.2.101 icmp_seq=3 Destination Host Unreachable

--- 192.168.2.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2007ms
, pipe 3
vicked@gwaeron:~$ sudo iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:14:C1:1D:73:F2
                    ESSID:"mz/x"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/94  Signal level=-52 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101800003a4000027a4000042435e0062322f00

vicked@gwaeron:~$ ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:13:F7:0F:23:EC  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:f7ff:fe0f:23ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vicked@gwaeron:~$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"mz/x"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/94  Signal level=-64 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vicked@gwaeron:~$ iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:14:C1:1D:73:F2
                    ESSID:"mz/x"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/94  Signal level=-52 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101800003a4000027a4000042435e0062322f00

vicked@gwaeron:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.101 icmp_seq=2 Destination Host Unreachable
From 192.168.2.101 icmp_seq=3 Destination Host Unreachable
From 192.168.2.101 icmp_seq=4 Destination Host Unreachable
From 192.168.2.101 icmp_seq=6 Destination Host Unreachable
From 192.168.2.101 icmp_seq=7 Destination Host Unreachable
From 192.168.2.101 icmp_seq=8 Destination Host Unreachable

--- 192.168.2.1 ping statistics ---
9 packets transmitted, 0 received, +6 errors, 100% packet loss, time 7999ms
, pipe 3
vicked@gwaeron:~$ ping google.com
ping: unknown host google.com
vicked@gwaeron:~$ dig google.com

; <<>> DiG 9.3.2 <<>> google.com
;; global options:  printcmd
;; connection timed out; no servers could be reached
vicked@gwaeron:~$ cat /etc/resolv.conf
nameserver 192.168.2.1

```

and my interface file atm:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto ath0
iface ath0 inet static
	address 192.168.2.101
	netmask 255.255.255.0
	network 192.168.2.1
	broadcast 192.168.2.255
	gateway 192.168.2.1
	wireless-essid mz/x
	wireless-key s:1212121212121

```

problem still up :)

---

### Post by Austin_KW on 2007-03-31
You are not associated to the network mz/x. So either the key is wrong or try putting the network in quotes "mz/x" the '/' might be interpreted as a special character.

---

### Post by chili555 on 2007-03-31
These are the hardest to solve, because everything looks perfect, because you seem knowlegable and conscientious and because no one here knows any reason you shouldn't connect practically before you press the power button. Are you familiar with the term "grasping at straws?" That's what I'm doing, I admit it.

I would troubleshoot your wireless key. Look in the router and be sure it's ASCII. Write it down and check it twice. 40- or 64-bit ASCII has 5 characters; 128-bit ASCII has 13 characters. In your router, have you selected 40- 64- or 128-bit ASCII and do you have the correct number of characters?

Now go to your computer, look in /etc/network/interfaces. Is the key correct in every respect? Check it twice.

I think your interfaces file is "busy." There are things in there that look correct, but are redundant. I suggest paring it down to:```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto ath0
iface ath0 inet static
	address 192.168.2.101
	netmask 255.255.255.0
	gateway 192.168.2.1
	wireless-essid "mz/x"
	wireless-key s:1212121212121 open
```I have never seen a slash mark / in an ESSID, but that doesn't mean it won't work. Let's put quotes around it to tell iwconfig, "Yes, we confirm it's got a slash!" Also, sometimes cards respond better to the term 'open' after the key; sometimes, 'restricted.' Try each one and restart networking:```
sudo /etc/init.d/netwoorking restart
ping -c3 192.168.2.1
```
Sometimes, wireless cards respond, almost magically, to a command to attach to a specific access point. So, lets try:```
sudo iwconfig ath0 ap 00:14:C1:1D:73:F2
sudo ifup ath0
ping -c3 192.168.2.1
```If it works, I'm praying, we can add wireless-ap to interfaces.

I'm running short on ideas.

---

