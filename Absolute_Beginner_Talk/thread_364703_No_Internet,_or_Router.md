---
title: "No Internet, or Router"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by RyanOmailley on 2007-02-18
***Disclaimer: assume I am an idiot and don't know anything about anything.***

I have recently installed Ubuntu 6.10 on my new PC. I bought this PC open boxed, because it was a discount I just couldn't give up. It is an HP PC and having my trouble with Hewlett-Packard before, I wasn't surprised to find thousands of useless programs and **** on my desktop when I booted up for the first time. After trying to decide what I did and didn't need, I have decided I didn't need Windows at all! I would make the Linux switch.

Ah, so the install went perfectly fine, however I can't seem to connect to my internet, or router. I am concerned this may be a problem specifically related to the machine being from HP (satan), but am not going to leap to that conclusion just yet.

I have tried accessing my router (192.168.0.1) but nothing, nor can I access websites.

I'm really new to Linux, so if you need any information I'll try to provide you with what I can. Also, keep in mind anything you need me to do needs to be explained in somewhat detailed steps. Thanks!

---

### Post by jonathan.lees on 2007-02-18
First you need to check that your network card is detected, open a terminal, click on Applications > Accessories > Terminal and type:

```

lspci

```

And then copy and paste the results here.

---

### Post by RyanOmailley on 2007-02-18
If there is something you are looking for then I can get it, but I can't write all of that an a notepad and come up here and type it all out.. it would take an hour and my hand would probably cramp up in the process. If you need all of it, then thanks for your help, but I'll just revert to XP.

---

### Post by RyanOmailley on 2007-02-18
(double post, sorry)

The only thing I can find that might be related is this:

"02:03.0 Ethernet Controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)"

---

### Post by jonathan.lees on 2007-02-18
sorry, I should have realised, you need to look for a line that displays: Ethernet Controller. My one displays:

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)

You can also try clicking on System > Administration > Networking and look to see if there is a
wired connection. I am assuming you are using a wired connection and not wireless?

---

### Post by The Noble on 2007-02-18
Please tell us if you are trying to connect to the router through a wireless card or an ethernet port. It looks like you are trying to use an ethernet port to connect, so that may save some trouble. Would you mind typing

```

ifconfig

```

And pasting what it says here? (You copy stuff from the terminal by ctrl+shift+C)

---

### Post by jonathan.lees on 2007-02-18
ok, that's your ethernet card (wired), if follow the nobles instructions just right down the inet addr.

---

### Post by RyanOmailley on 2007-02-18
> **The Noble said:**
> Please tell us if you are trying to connect to the router through a wireless card or an ethernet port. It looks like you are trying to use an ethernet port to connect, so that may save some trouble. Would you mind typing

```

ifconfig

```

And pasting what it says here? (You copy stuff from the terminal by ctrl+shift+C)

My computer is downstairs, so I end up running down several flights of stairs and then scribbling things to a notepad and then running up several flights and then with my last gasping breath typing it out.

inet addr: 127.0.0.1 Mask: 255.0.0
inet6 addr: ::1/128 Scope: Host

I am using an ethernet port (wired)

---

### Post by jonathan.lees on 2007-02-18
ok, so it does'nt have an IP address. I guess it's configured for DHCP and there's no DHCP server available. If your router is 192.168.0.1 try configuring it as 192.168.0.2.

Click on System > Administration > Networking and highlight the Wired Connection. Click properties. In Configuration select Static, in the IP address field enter 192.168.0.2, in subnet mask enter 255.255.255.0 and in gateway 192.168.0.1 Click OK. Now click on the DNS tab and add 192.168.0.1 which is your router. Close the network settings window. Now open a terminal again and type:

```

ping 192.168.0.1

```
and hopefully you should get a reply. Try browsing the internet.

---

### Post by RyanOmailley on 2007-02-18
No connection with the ping, and (obviously?) I can't connect to any websites either.

---

### Post by jonathan.lees on 2007-02-18
type ifconfig again and see if there is a eth0 or eth1 and which one has an IP address of 192.168.0.2

---

### Post by jonathan.lees on 2007-02-18
Also check the cable at the back of the PC and check that the LED's are lit

---

### Post by RyanOmailley on 2007-02-18
no, there is no eth0 or eth1 and no ip is shown.

The cable is connected.

---

### Post by jonathan.lees on 2007-02-18
ok clutching at straws, open the terminal again and type:

```

cat /etc/network/interfaces

```

and check for a line that states auto

---

### Post by The Noble on 2007-02-18
Under System/Administration, click network(ing) and enable your wired connection. Usually this will be eth0. After its enabled with dhcp, make sure the little box to the left of it is checked and close the networking box. On your top panel of the desktop, right next to the shut down button, will be a computer icon. Double click that icon and the name of the connection should be "lo". Either select from the drop down box eth0/1 (whatever else is there), or type in eth0. This should enable your wired connection.  Basically, a wired connection should be no frills , ever, so just tool around with things and it should work.

---

### Post by jonathan.lees on 2007-02-18
I just realized in System > Administration > Networking and highlight the Wired Connection. Click properties. In the top corner there is a tick box, enable this connection, is it ticked?

---

### Post by RyanOmailley on 2007-02-18
Yes, there are four.

auto eth1
auto eth2
auto wlan0
auto ath0

Yes, the connection is enabled.

---

### Post by RyanOmailley on 2007-02-18
****, I lied. I got it to work.

I, in fact, didn't have the box checked! haha! Silly me. :(

Thanks, a lot, though.

I have to get my onboard video working now, because as is I only can get up to 800x600 resolution. Should I make a new topic for this?

---

### Post by jonathan.lees on 2007-02-18
when did it start working?

---

### Post by jonathan.lees on 2007-02-18
I would start a new topic on that, it's more command line work editing files, you're sure gonna get fit running up and down them stairs!!

---

### Post by RyanOmailley on 2007-02-18
> **jonathan.lees said:**
> I would start a new topic on that, it's more command line work editing files, you're sure gonna get fit running up and down them stairs!!

I'll do so, thanks.

Yeah, I didn't know Ubuntu came with an exercise program.

---

### Post by igorc on 2007-03-27
Hi,

I have the same problem with the same Realtek 8139 network card. It was working fine for 6 months on Ubuntu 6.06 kernel 2.6.15-23 and suddenly decided to stop. This card should work with 8139too driver or 8139cp which are already compiled in the 2.6.x kernels.

I did some goggling and it seams that a lot of users have the same problem with this card. It might be a problem related to:

- IRQ settings, ACPI or APIC according to this link:
[https://help.ubuntu.com/community/DebuggingIRQProblems?highlight=%28problems%29%7C%28IRQ%29](https://help.ubuntu.com/community/DebuggingIRQProblems?highlight=%28problems%29%7C%28IRQ%29)

- or duplicate driver problem: try booting with 8139cp driver (generic one) blacklisted in /etc/hotplug/blacklist file

- or parameter settings in the 8139too module.

You can try booting with the kernel parameters disabled like in the recommendations from the link above. Also can you please send the output of these commands:

# ifconfig
# ping <router_ip_address>
# dmesg | grep eth
# lspci -vv
# lsmod | grep 8139
# sudo lshw -class network
# sudo dhclient eth0
# modinfo 8139too

Cheers,

Igor

---

### Post by Darkened_Sol on 2008-03-21
I have the same problem too. I can not connect to the internet via  a router. Heres a list of some information that might be helpful.

**_lspci;_**
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

**_ifconfig;_**
tat@AMD-64-X2-5000:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19328 (18.8 KB)  TX bytes:19328 (18.8 KB)

**_pinging my router;_**
tat@AMD-64-X2-5000:~$ ping 192.168.2.1
connect: Network is unreachable

**_sudo dhclient eth0;_**
tat@AMD-64-X2-5000:~$ sudo dhclient eth0
[sudo] password for tat:
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: Device or resource busy
SIOCSIFFLAGS: Device or resource busy
Listening on LPF/eth0/00:e0:4d:71:51:cd
Sending on   LPF/eth0/00:e0:4d:71:51:cd
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any help would be much appreciated! :)

---

### Post by bumanie on 2008-03-21
Don't know whether this will help, but it has fixed some problems with internet access on gutsy (I assume you're using gutsy).
open firefox. In the address bar type about:config --> enter. In the filter type ipv6 --> enter. Right click on the line that appears and left click on toggle and change the value to true. If it doesn't work revert your system by returning to firefox and toggle the value back to false.

---

### Post by Darkened_Sol on 2008-03-21
Well, I tried that but it doesnt connect :|. I'll try running the live CD of Ubuntu 6.06, I recall it connecting to the internet with no problem at all. Then maybe upgrade to gutsy? :| That would take a while! I'll report back soon!

---

### Post by Darkened_Sol on 2008-03-21
No luck. when i boot up it says something like: MP-BIOS bug:8254 timer not connected to IO-APIC. This the case, I booted up again, pressed F6 and added 'noapic' to the end of the boot command. But still no luck! Whats going on? :S It worked on my Intel system but not my current AMD system!

---

### Post by Darkened_Sol on 2008-03-25
Solved my problem by installing Kubuntu, then installing GNOME desktop environment and using  GNOME as default. Is it safe to uninstall KDE Desktop Environment this way? :S

---

### Post by maljaros on 2008-03-25
Deleted

---

