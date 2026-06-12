---
title: "I Need Help From A Ubuntu Pro!"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by kornoholio on 2006-11-03
**** heres my problem ... at first i thought its my firefox or somethin, then i installed epiphany web browser n still i have the same problem...WHEN EVER I TRY TO SIGN IN TO SOMETHIN THAT NEEDS AUTHENTICATION LIKE HOTMAIL.COM OR YAHOO.COM I RECEIVE THIS 

(IN FIREFOX):
Unable to connect

      

      
      
      

      
        
        

          

Firefox can't establish a connection to the server at login.yahoo.com.

        


        
        


    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

(IN EPIPHANY):

“login.yahoo.com” refused the connection.

The server may be busy or you may have a network connection problem. Try again later.

There may be an old version of the page you wanted:


    * in the Google Cache

    * in the Internet Archive


(if theres any pro's outhere plz help coz till now noone gave me any solution)

---

### Post by NetworkGuy on 2006-11-03
Not much to work on.  I'll take a shot.  Have you installed any firewall frontend software like firestarter?

If from terminal you run ```
sudo iptables -L
``` what do you get as a reply?

BTW - I am not one of these "pros" you are looking for..

---

### Post by kornoholio on 2006-11-03
root@unknown:/# sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@unknown:/#


im new with linux , comparing to me u r a pro man [-(  so what do u get from this output? n No i got no firewalls installed .... i guess

---

### Post by NetworkGuy on 2006-11-03
Well Linux has a firewall built into the kernel call iptables, however you are not blocking anything.  

I'm assuming that http traffic works since you are here :)

Can you access the wiki when you click on the tab on the top right of the forums?   I think you are just having a problem accessing secure http (https) sites.

---

### Post by kornoholio on 2006-11-03
NetworkGuy i think ur right ... i couldnt access Wiki .... same message ... what should i do?

---

### Post by dbott67 on 2006-11-03
EDIT: Oops... I missed the part about accessing secure sites.  So, you can access regular sites (port 80 / http) but not secure sites (port 443 / https), correct?

Can you post the output of the following commands:
```
ifconfig -a
```
```
cat /etc/network/interfaces
```
```
route -n
```
```
cat /etc/resolv.conf
```
```
ping www.google.com -c 4
```
```
ping 72.14.205.99 -c 4
```

Other pertinent info:
1. How are you connecting to the internet (cable, DSL, dial-up, etc.)?
2. Do you have a router (D-Link, Linksys, Netgear, etc.)
3. Wired ethernet / wireless?
4. Can you access any online services (Synaptic, chat, e-mail, etc.)?

-Dave

---

### Post by NetworkGuy on 2006-11-03
I've searched but haven't found any hits.

Two things come to mind..

 - From firefox type about:config into the url line,  type ssl into the find box and make sure that most if not all of the security ssl lines say true for their value.

 - Are you using a internet router between you and the internet?  If so, do you have anoter machine you can try to see if https: pages work on it.  Maybe the router is stopping https traffic from reaching you for some reason.

These are shots in the dark, if neither of these do the trick, I may be out of ammunition.

---

### Post by livinginx on 2006-11-03
I'm not a Linux pro, but in general it seems like somehow your computer/connection are not allowing you access to _secure_ pages.

---

### Post by dbott67 on 2006-11-03
Do you use a proxy server?

Check your proxy settings: SYSTEM > PREFERENCE > NETWORK PROXY.

Click DIRECT INTERNET CONNECTION if your do not use a proxy.

-Dave

---

### Post by kvonb on 2006-11-03
Sounds like an MTU problem!

I'm guessing your ISP uses PPPoE right?

Call your ISP and ask them what MTU they are using, you might need to speak to a tech or someone who knows more than the basics.

What network configuration are you using. ie do you have a server which connects to the net with internet sharing, does your Ubuntu computer connect directly, or does your router/DSL modem connect to the net and you just hook into that?

I can't go any further until I know that.

Regards,  Kev :)

---

### Post by kornoholio on 2006-11-03
well network guy here r the info u asked for :

root@unknown:/# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:18:2E:E8:4C
          inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fe2e:e84c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:165896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2657 txqueuelen:1000
          RX bytes:105129887 (100.2 MiB)  TX bytes:7902278 (7.5 MiB)
          Interrupt:169 Base address:0x6c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3299 (3.2 KiB)  TX bytes:3299 (3.2 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.118.1  Bcast:172.16.118.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.103.1  Bcast:192.168.103.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

--------------------------------------------------------------------------------------------------------
root@unknown:/# cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.14
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
-----------------------------------------------------------------------------------------------------------------
root@unknown:/# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.103.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8172.16.118.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
root@unknown:/#
-------------------------------------------------------------------------------------------------------------
root@unknown:/# cat /etc/resolv.conf
nameserver 192.168.0.1
-----------------------------------------------------------------------------------------------------------------
root@unknown:/# ping [www.google.com](www.google.com) -c 4
connect: Network is unreachable
root@unknown:/#
-------------------------------------------------------------------------------------------------------------------

im on a LAN ... i dont have a router ... wired ethernet .... and im using Synaptic normally

---

### Post by NetworkGuy on 2006-11-03
I see VMware networks in your config.  Has this problem occured since you installed VMware player/server?

Since you are on a LAN, as it was stated above, is your company/uni using a proxy server?  If you are using one, that may be the problem.  Are other people on the same LAN having the same issue?  

If it is a proxy server, this may be something that your company/uni needs to address.

EDIT:  If you are using a proxy server, make sure your settings in your browser use the proxy for SSL sites.
For FireFox it's under Edit / Preferences / Connection Settings

---

### Post by kornoholio on 2006-11-03
i think the problem started after installin vmware ... i havent had such problems b4 ... n by the way im @ home .. i think the vmware caused all this ... if i killed the processes u think it'll work?

---

### Post by dbott67 on 2006-11-03
It looks as though you are missing the default gateway off of your LAN (according to your routing table).

```
root@unknown:/# route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.103.0 0.0.0.0 255.255.255.0 U 0 0 0 vmnet8
172.16.118.0 0.0.0.0 255.255.255.0 U 0 0 0 vmnet1
192.168.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
root@unknown:/#
```

Basically, your routing table only knows where to send packets on the 192.168.103 subnet, the 172.16.118.0 subnet and the 192.168.0 subnet.  If any packet is destined for anywhere else (ie 0.0.0.0) it needs to be sent to your gateway (192.168.0.1).

Type the following command from the terminal:
```
sudo route add -net default gw 192.168.0.1 dev eth0
```

Here's mine for comparison:
```
dbott@thedrake:~/Desktop/cube$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
[COLOR="Red"]0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0[/COLOR]

```
Note that my subnet is 192.168.**[COLOR="Red"]1[/COLOR]**.0

-Dave

---

### Post by NetworkGuy on 2006-11-03
You can try to remove VMware and see if that fixes your issue.   

Do you have any other PC's on your home LAN that you can check your https: connections?

If removing VMware doesn't fix your problem, then please try to explain how your LAN is setup.  Something has to be routing you out to the Internet.

---

### Post by kornoholio on 2006-11-03
same problem ... i removed vmware player n components from synaptic n had the same message:-?  is vmware now completely removed from my os or is there anythin else i should do?

---

### Post by NetworkGuy on 2006-11-03
Describe how your LAN is setup.

I'm confused that without a default route, you can surf to http sites but not https: sites.   I'm betting you have some sort of router or better yet proxy server on your LAN.

---

### Post by kornoholio on 2006-11-03
I Cant Thank U Enough Network Guy ! Ur A Genius! Really Thank U! It Worked!

---

### Post by NetworkGuy on 2006-11-03
LOL..

What worked??  What did you do to fix it?

---

### Post by dbott67 on 2006-11-03
I think he meant to thank me for the 
```
sudo route add -net default gw 192.168.0.1 dev eth0
```
command.

-Dave

---

### Post by kornoholio on 2006-11-03
LOL! WELL YEA UR RIGHT .... I MEANT U dbott!! n network guy 2 , u both were a gr8 help ... thnx again guys!

---

### Post by kornoholio on 2006-11-03
i hope i didnt bother u guys .... when it comes to linux im a pain in d *** coz im new

---

### Post by NetworkGuy on 2006-11-03
That's what the community is for.  Have fun catching up on your yahoo mail :)

---

### Post by kornoholio on 2006-11-03
nahhh... forget yahoo :P linux is so damn interresting .... if u guys have time i need more help :P n TONS of questions :P

---

