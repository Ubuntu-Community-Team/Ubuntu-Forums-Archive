---
title: "linux box off network!"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by wog on 2006-10-21
I have two xp machines and one linux machine on a network together. The windows machines aren't having trouble, but the linux box is.

The router is a Linksys Wireless-G, model WRT54GS. When I unplug the ethernet cable at the linux box end, the light goes off, so I'm assuming that means the cable is working properly.

The linux box is running Dapper, in Gnome, starting with Grub.

The linux box boots up okay, but there is no network connection and no internet when you try to access it. Attempting to ping the router brings up the message "connect: Network is unreachable".

I don't know what other information to give or in what order. I don't know how to troubleshoot this.

Help?

---

### Post by Liz on 2006-10-21
I also, am having this problem. 
have tested network cable on other machines, and its working. purchased a brand new network card incase it was that. still nothing. 

any help would be appreciated.

---

### Post by lloyd_b on 2006-10-21
> The linux box boots up okay, but there is no network connection and no internet when you try to access it. Attempting to ping the router brings up the message "connect: Network is unreachable".

I don't know what other information to give or in what order. I don't know how to troubleshoot this.


Please post the contents of the following files:

"/etc/network/interfaces"
"/etc/resolv.conf"

Please type the following commands, and post the results:

"ifconfig"
"route"

These will provide enough information to start with, though you'll probably be asked for more info later.

Lloyd B.

---

### Post by wog on 2006-10-21
Okay, here you are, in the order you requested them.

/etc/network/interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

/etc/resolv.conf:
search hsd1.wa.comcast.net.
nameserver 68.87.69.146
nameserver 68.87.85.98

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:50:2C:A4:FF:FB  
          inet6 addr: fe80::250:2cff:fea4:fffb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:31 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16028 (15.6 KiB)  TX bytes:16028 (15.6 KiB)

route:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

---

### Post by jordanmthomas on 2006-10-21
It seems you have been connected to the internet at least once.
You seem to be using ipv6, which causes all sorts of problems for me.  I have the same router at home and turning off ipv6 seemed to help a bunch.  To do this, I created a file called bad_list in /etc/modprobe.d and made sure that ipv6 was turned off.
```
sudo touch /etc/modprobe.d/bad_list
sudo nano /etc/modprobe.d/bad_list

```
put this in the file
```
alias net-pf-10 off
```
I also put a new line after this, but I am not sure if it is necessary.
```
Ctrl-O, Enter, Ctrl-X
```
to save and then exit.
```
sudo reboot
```
hopefully, when you reboot your internet will just work.

---

### Post by lloyd_b on 2006-10-21
If the preceeding message doesn't do the trick, could you post the contents of the following file:

"/etc/dhcp3/dhclient.conf"

It looks like your card is unable to obtain an IP address from the router, which means that the answer will most likely be in that file.

Lloyd B.

---

### Post by wog on 2006-10-22
I did the bad_list option and got an error message on reboot:

"Too many parameters were passed to the application."

---

### Post by wog on 2006-10-22
/etc/dhcp3/dhclient.conf:
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

---

### Post by jordanmthomas on 2006-10-22
Well, maybe you should remove that file then, just in case
```
sudo rm /etc/modprobe.d/bad_list
```
Another way of doing a similar thing (I think I might have forgot to do something earlier)

is to do this
```
sudo nano /etc/modprobe.d/blacklist
```
at the end add
```
blacklist ipv6
```

---

### Post by wog on 2006-10-22
Just to make sure I understand this...put the line
```
blacklist ipv6
```
within the blacklist file??

---

### Post by jordanmthomas on 2006-10-22
Yes, at the end.  Be sure to include a blank line after as well.

---

### Post by JayTee on 2006-10-22
Hi. I'm curious what your Windows XP configurations are. Can you run the command IPCONFIG /ALL from a command prompt in Windows and then paste it here? The IP address in your DHCP file on your linux box don't look like the default range of DHCP addresses leased by Linksys when it uses the defaults. If you go to the System|Administration menu and launch Network Tools (Assuming Gnome desktop on Ubuntu) and click the Ping tab and try to ping address 192.168.1.1 do you get any replies?

---

### Post by wog on 2006-10-22
I put the line into blacklist. I got this message again:

"Too many parameters were passed to the application".

On a hunch, I went back into the blacklist file and commented out the ipv6 line and rebooted. Same error message on startup. Whatever it refers to is not associated with what we're doing unless it has issues with the length of the blacklist file.

What next, O Cap-i-tan? :)
By the way, regardless of the outcome, I'm getting a great education, so I appreciate that. :)

---

### Post by jordanmthomas on 2006-10-22
I dunno.  If it doesn't work with ipv6 disabled, then I don't know a solution (I *am* in the beginner's forum, right?)

Maybe JayTee can help since he's here?

---

### Post by wog on 2006-10-22
> **JayTee said:**
> Hi. I'm curious what your Windows XP configurations are. Can you run the command IPCONFIG /ALL from a command prompt in Windows and then paste it here? The IP address in your DHCP file on your linux box don't look like the default range of DHCP addresses leased by Linksys when it uses the defaults. If you go to the System|Administration menu and launch Network Tools (Assuming Gnome desktop on Ubuntu) and click the Ping tab and try to ping address 192.168.1.1 do you get any replies?

Okay, JayTee... In answer to your second question, when I ping the router from the command line, I get the message
"connect: Network is unreachable". When I use the ping within System > Adminstration > Network Tools it doesn't seem to do anything. 

This is why it's confusing to me. The hardware all works, yet the linux box can't see the router and vice-versa. 

This is the ipconfig /all for the laptop I'm working on in order to post all this. Mind you, the connection is wireless for the laptop:
Windows IP Configuration

        Host Name . . . . . . . . . . . . : MOBILEJAMES
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : hsd1.wa.comcast.net.

Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Controller
        Physical Address. . . . . . . . . : 00-11-43-73-23-4D

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . : hsd1.wa.comcast.net.
        Description . . . . . . . . . . . : Intel(R) PRO/Wireless 2200BG Network Connection
        Physical Address. . . . . . . . . : 00-12-F0-42-E5-F2
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.101
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 68.87.69.146
                                            68.87.85.98
        Lease Obtained. . . . . . . . . . : Saturday, October 21, 2006 6:05:03 PM
        Lease Expires . . . . . . . . . . : Sunday, October 22, 2006 6:05:03 PM

---

### Post by JayTee on 2006-10-22
ok, here goes. Go to System|Applications and launch Network Tools.
First step is to try and ping 127.0.0.1. This is the internal loopback address. If you get replies we know the hardware and drivers are working ok internally. Now to try and talk to the rest of the net.
On the Devices tab use the up/down arrow in the Network Device text box to show Ethernet Interface (eth0) and click the configure button. 
Make sure the Enable this connection box is checked!!!!
Copy the current information in the text boxes down and paste them in a response to this post. Then try this to see if it works. I still want to see what values are in there _before you make the changes._ Note: If DHCP is set the address, subnet mask and gateway boxes will be grayed out. This is normal.
On the Interface properties dialog that pops up you need to set the following  options.
 
Configuration: Static IP Address (set by clicking on the up/down arrows in the text box.)
IP Address: 192.168.1.90
Subnet Mask: 255.255.255.0
Gateway Address: 192.168.1.1

This will allow a static address within the range reserved for the Linksys router that it does not use for DHCP. I'm assuming you don't have hundreds of computers on this network :-)
Reboot and try pinging your laptop address at 192.168.1.101 and also try pinging the router (Linksys) at 192.168.1.1

I'll check back tomorrow to see how things went. Gonna get some sleep.

---

### Post by wog on 2006-10-22
The ping of 127.0.0.1 goes smoothly. 0 packet loss.

When I bring up the Ethernet option in Network Tools, the Configure button is grayed out. I can't select it.

Below, the IP Information and Interface Information areas all say "not available". On the other side, the Interface Statistics are all 0 except for Transmission Errors, which reads 57.

Your description of setting Static IP sounds familiar. I find I can get to something like that through System > Administration > Networking, where there's an option for Ethernet Connection where the Properties button isn't grayed out. Is it the same interface, or is it a different one?

Within it I find a way to set Static IP, Subnet Mask and Gateway, but if it's not the same one I'm uncertain whether I should mess with it.

---

### Post by JayTee on 2006-10-22
Whne you choose Network instead of Network Tools the interface is different until you select the Ethernet connection and click on properties. Then you are looking at the same dialog as in Network Tools. When you open the Network Tools applet and click the device tab the Configure button next to the Network Device box is grayed out because it shows the loopback which can't be changed. _You just need to click on the up/down arrow of the Network Device listbox to show the Eth0 interface instead of loopback._ So you can use Network, select Properties or Network Tools | Devices and click the Network Device up/down arrow to show Eth0, it doesn't matter because it brings you to the same dialog box to change your settings. I was advising you to use Network Tools so you wouldn't have to open Network and a Terminal window to ping, etc. I prefer using the Net Tools app because you can make changes and test all in one applet. Do you have more than one network card in this computer at the moment?

---

### Post by wog on 2006-10-23
I meant I selected eth0 in Network Tools and the Properties button was still grayed out. But if the window you get is the same as the one I got through System > Administration > Networking, it makes no difference which method I use to get to the proper dialog box. :)

I have only one ethernet slot...the one built into the motherboard.

I followed your previous instructions to the letter. Once I'd rebooted, the previously grayed-out Configure button for eth0 was selectable. The only thing in the Devices tab which reads "not available" at this point is Link Speed. 

Pinging either 192.168.1.101 or 192.168.1.1 gets 100% packet loss.

---

### Post by JayTee on 2006-10-23
you said earlier you had two Windows computers. The laptop is wireless. Is the other Windows computer also wireless? If not, try the cable and port on the Linksys that one is plugged into but do a power on/off on the Linksys when you do and try pinging the laptop. Also if you can post the IPCONFIG /ALL of the wired Windows machine that might give me a better clue. Sounds like your ethernet interface is working properly but there's a break in the connection between that and the Linksys which could either be a bad port on the Linksys or a bad CAT5 cable. It could also be that you've gotten ahold of a crossover cable which would kill the connection. crossover cables swap send and recieve pairs and are only used to connect two computers directly without a switch or access point/router.

---

### Post by wog on 2006-10-24
Okay, maybe I didn't explain something. This entire setup was working properly until a day before I posted this problem. Same wires, same everything. Unless a crossover cable could work for a period of time on a router before finally deciding to not work again, it's probably not a crossover cable.

That said, owing to the ideosyncracies of networking, I tried the cable anyway, restarting the router in the process.

The router doesn't seem to see the linux box after restarting, and from the linux box packet loss is 100% regardless of which of the two IP addresses I ping. Just to be certain, I tried pinging the wired windows machine, which got the same result.

Because I'm weird, when plugging the wired windows machine back in, I used the previous linux cable, just for the test it implies. I can access the laptop from the wired windows box, but I can't find the linux box from the wired windows box.

Here's the ipconfig /all from the wired windows box:
Windows IP Configuration

        Host Name . . . . . . . . . . . . : that
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : hsd1.wa.comcast.net.

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : hsd1.wa.comcast.net.
        Description . . . . . . . . . . . : VIA Compatable Fast Ethernet Adapter
        Physical Address. . . . . . . . . : 00-E0-4C-AC-8D-2C
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 68.87.69.146
                                            68.87.85.98
        Lease Obtained. . . . . . . . . . : Tuesday, October 24, 2006 3:24:09 AM
        Lease Expires . . . . . . . . . . : Wednesday, October 25, 2006 3:24:09 AM

---

### Post by wog on 2006-10-27
So am I going to have to reformat my hard drive to sort this out?

---

### Post by JayTee on 2006-10-27
Is your NIC an embedded NIC or is it in a PCI slot? I'd try another NIC just to make sure. Preferably an INTEL one. Normally if you can ping the loopback address the hardware should be good but if you tested the cable then something inside your box is definitely amiss. You've changed your ethernet configuration and the one you have now should let you ping the other computers on your home network assuming your firewall isn't blocking ICMP traffic. Were you ever able to connect at all? One of the previous posters seemed to think so. When it comes to networking, I understand TCP/IP, routers, firewalls etc and have no problems troubleshooting in the Windows world but when it comes to configuring them on the linux side of things I'm still something of a noob. Are you running the standard x86 kernel in Ubuntu or are you running the 686 or AMD version? Can you do an IFCONFIG again and post it here so I can see the changes? There are alot of posts on here about people having troubles with the Via adapters that come embedded on the motherboards but I haven't found one with any obvious solution for you. Sorry I can't be more help.

---

### Post by wog on 2006-10-28
The ethernet connection I've been using up to now is embedded in the motherboard. In the past I've been able to get an internet connection. 

I've had a certain amount of trouble getting the windows boxen to access the linux box with the same freedom they apparently access each other, but I'd always assumed it was due to my inexperience with samba.

I'll have to hunt around for a NIC. I may even have to order one, it's been so long since I've needed one that hasn't come onboard.

I'm running the AMD kernal with the nVidia driver.

I'll have to get you the ifconfig in the morning.

---

### Post by Liz on 2006-11-05
well i figured out my problem. 
i purchased a new network card, and the socket i plugged it in to, didnt work right. so i moved it onto anotehr pci slot, and it works. 

odd when that happens.

---

