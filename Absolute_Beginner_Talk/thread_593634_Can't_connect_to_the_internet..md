---
title: "Can't connect to the internet."
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by n0ur on 2007-10-27
hey 
i have ubuntu 7.04 and windows xp on partition on this pc. i can connect with the internet here on xp but can't on ubuntu
i have a wired connection ,adsl, router, ethernet ,.
 i tried this [https://wiki.ubuntu.com/ADSLPPPoE](https://wiki.ubuntu.com/ADSLPPPoE) and (after i typed in my user name and password) it says connection initiated, but i still cant view any webpage
-- pinging [www.google.com](www.google.com) would show unknown host
-- pinging the ip would show: destination host unreachable 
-- ifconfig would show the eth0 and the lo .. stuff

any stuff that i should try ? 
thanks in advance

---

### Post by qbox on 2007-10-27
You need to put your DNSfirst. Try to ping your provider. If you receive ping its ok if not make this:
sudo vi /etc/resolve.conf
put your DNS adreses in it.
Then make your IP adreses
ifconfig eth0 XXX.XXX.XXX.XXX netmask XXX.XXX.XXX.XXX
Then type this (I think that the problem is this line)
**sudo route add default gw _XXX.XXX.XXX.XXX ENTER YOUR GATEWAY_**

then
sudo pppoeconf
make configuration
open one console and ping [www.google.com](www.google.com)
open another console and tipe 
plog
you will see what is connection status
tell me if you made it

---

### Post by mikewhatever on 2007-10-27
Can you post the output of ifconfig here?

---

### Post by mdpalow on 2007-10-27
You should try Ubuntu 7.10. 

7.04 didn't work for me either, but with 7.10 everything worked at install.

---

### Post by n0ur on 2007-10-27
ok, hi again
qbox :
1- first i have to put in my dns as you said .. and i get it when i type in "ipconfig /all" in cmd //windows xp .. right? because when its different than the one i saw on ubuntu. 
so to add it, the command sudo vi/etc/resolve.conf didn't work, i used sudo nano /etc/resolve.conf 
and then added my dns server ip ..
2- second i have to make ip address, with this command :
ifconfig eth0 XXX.XXX.XXX.XXX netmask XXX.XXX.XXX.XXX
now what ip should i put after eth0 ? and after netmask ?
i tried after eth0 to put my dns, and after netmask to put the 255.255.255.0 or 225.225.225.0 or something that i saw when i typed in "ifconfig in terminal.
but i got access denied thing
3- and about the last command : sudo route add default gw XXX.XXX.XXX.XXX ENTER YOUR GATEWAY
(the gw is the same as my ip address right? ) i put it there and i got : unreachable network destination or something
and the plog:

Oct 27 18:09:31 nour-desktop pppd[4228]: Using interface ppp0
Oct 27 
18:09:31 nour-desktop pppd[4228]: Connect: ppp0 <--> eth0
Oct 27 
18:09:31 nour-desktop pppd[4228]: Remote message: permission denied
Oct 27 
18:09:31 nour-desktop pppd[4228]: PAP authentication failed
Oct 27 
18:09:31 nour-desktop pppd[4228]: Connection terminated.

--------------------------------------------------------------------------------------------------
and for mike .. or whatever :P thats the ipconfig :


eth0      Link encap:Ethernet  HWaddr 00:0E:2E:82:8F:44  
          
inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          
inet6 addr: fe80::20e:2eff:fe82:8f44/64 Scope:Link
          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          
RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          RX bytes:4437 (4.3 KiB)  TX bytes:7546 (7.3 KiB)
          Interrupt:19 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          
UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by qbox on 2007-10-27
gateway is not same like IP address. you must enter the comants in this order

for example my IP is 172.18.10.81
and my gateway is 172.18.10.1
my netmask is 255.255.255.0

enter 
sudo ifconfig eth0 172.18.10.81 netmask 255.255.255.0 up
sudo route add default gw 172.18.10.1

ajter this tri to ping your proviter 
if you DNS is ok you vill resive ping back from provider
ping yourprovider.com

if you dont receive ping let me know
 if you receive ping 
sudo pppoeconf

make your conection.

and dry to ping [www.google.com](www.google.com)

wait a little for connection arount 5 minutes (i have problems vith my connection too)

try plog command and past me ok

---

### Post by n0ur on 2007-10-27
well, it takes a few seconds and then it says unknown host (when i ping)

---

### Post by qbox on 2007-10-27
how you mean?

tel me what you do step by step.

and paste me everything ok

---

### Post by n0ur on 2007-10-27
i did everything u told me earlier :
i entered:
sudo ifconfig eth0 172.18.10.81 netmask 255.255.255.0 up

first it asks for password, i enter it and then it shows nothing, i go typing this line :
sudo route add default gw 172.18.10.1

and also nothing shows
i ping my isp, and i got: unknown host 

(replaced them with my own ip and gw and netmask )

---

### Post by qbox on 2007-10-27
you didnt understand me corectly

IP 172.18.10.81 is my own IP. you need to enter you IP and your gateway and your net mask

after that first check again your resolv.conf file, 
 then ping ISP
if you receive ping back from ISP your IP and gateway is correct if not they arent correct
if everything is ok with pppoeconfig make your connection and try to connect
ping google or open a webpage

---

### Post by n0ur on 2007-10-28
ok .. this isn't working
i will say again what did i do :
1- i added me dns in resolve.conf 
" sudo nano /etc/resolve.conf "

2- i added my ip
"sudo ifconfig eth0 (ip-goes-here) up "

3- "sudo route add default gw (gw-goes-here)

4- sudo pppoeconf 
and i go with the steps
and it finally says "connection initiated"

but then, i cant load any webpage !

 plog :

Oct 28 18:27:32 nour-desktop pppd[7333]: Plugin rp-pppoe.so loaded.
Oct 28 18:27:32 nour-desktop pppd[7335]: pppd 2.4.4 started by root, uid 0
Oct 28 18:27:32 nour-desktop pppd[7335]: PPP session is 1272
Oct 28 18:27:32 nour-desktop pppd[7335]: Using interface ppp0
Oct 28 18:27:32 nour-desktop pppd[7335]: Connect: ppp0 <--> eth0
Oct 28 18:27:34 nour-desktop pppd[7335]: Remote message: permission denied
Oct 28 18:27:34 nour-desktop pppd[7335]: PAP authentication failed
Oct 28 18:27:34 nour-desktop pppd[7335]: Connection terminated.

---

### Post by qbox on 2007-10-28
wait for a while. around 5-10 min

---

### Post by n0ur on 2007-10-29
i waited all yesterday! what could also go wrong ?

---

### Post by qbox on 2007-10-29
On my computer I do this
sudo ifconfig eth0 (my IP goes here) netmask (my netmask go here) up
sudo route add default gw (my gateway go here)

if you mess one of this address you will not be able to connect.
But you can ping your Internet provider that's right? If you can ping your provider, IP addresses are good. Maybe you enter wrong username and password.
In pppoeconf dialog put yes to all.

---

### Post by n0ur on 2007-10-29
ok, look here

 Connection-specific DNS Suffix  . :
 Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
 Physical Address. . . . . . . . . : 00-53-45-00-00-00
 Dhcp Enabled. . . . . . . . . . . : No
 IP Address. . . . . . . . . . . . : 86.108.55.67
 Subnet Mask . . . . . . . . . . . : 255.255.255.255
 Default Gateway . . . . . . . . . : 86.108.55.67
 DNS Servers . . . . . . . . . . . : 196.27.0.40
                                                  196.27.0.250
 NetBIOS over Tcpip. . . . . . . . : Disabled

// see, my gw is the same as my ip .. and, it keeps changing as you know

now, here what i type in terminal again:
1- i edited my dns so it will be "196.27.0.40"
2- sudo ifconfig eth0 86.108.55.67 netmask 255.255.255.255 up
3- sudo route add default gw 86.108.55.67
4- sudo pppoeconf
and i say yes to all

.... and waited 5/10 mins 
but still cant connect 

plog :
Oct 29 15:43:48 nour-desktop pppd[6614]: Plugin rp-pppoe.so loaded.
Oct 29 15:43:48 nour-desktop pppd[6616]: pppd 2.4.4 started by root, uid 0
Oct 29 15:43:48 nour-desktop pppd[6616]: PPP session is 5861
Oct 29 15:43:48 nour-desktop pppd[6616]: Using interface ppp0
Oct 29 15:43:48 nour-desktop pppd[6616]: Connect: ppp0 <--> eth0
Oct 29 15:43:54 nour-desktop pppd[6616]: Remote message: permission denied
Oct 29 15:43:54 nour-desktop pppd[6616]: PAP authentication failed
Oct 29 15:43:54 nour-desktop pppd[6616]: Connection terminated.
Oct 29 15:44:59 nour-desktop pppd[6616]: Timeout waiting for PADO packets
Oct 29 15:44:59 nour-desktop pppd[6616]: Unable to complete PPPoE Discovery


:(


Edit:
Yes, it works now! i just had to change the routers sittings so it can connects by itself, without all those commands :/
but I thank you for replying! i definitely learned new things :)

---

