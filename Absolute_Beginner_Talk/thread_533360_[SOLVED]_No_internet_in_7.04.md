---
title: "[SOLVED] No internet in 7.04"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by preacher2B on 2007-08-23
I have recently installed Ubuntu 7.04 for an AMD64. Windows XP is still installed on one hard drive and Ubuntu on the other.  Everything was working great until I did an update for security issues. Now my internet connection does not work in Ubuntu. It works normal in XP.

I have tried *sudo pppoeconf*. After running tests it I received the message "Access Concentrator did not respond..."

I am connected via Ethernet on a college LAN. 

I tried to find out info about "Sambo" but am still unclear what to do or if that will help.

I am very new, this is my first experience with Unix, etc.

---

### Post by K.Mandla on 2007-08-23
Can you give us the information that shows up for these commands?

```
cat /etc/iftab
sudo ifconfig
```
And not to be patronizing, but you've connected all your cables properly and you know that the network is functioning, right? (Sorry, have to ask. :| )

---

### Post by preacher2B on 2007-08-24
Result from *cat /etc/iftab*:
"# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.


eth0mac (MAC address) arp 1"

Result from *sudo ifconfig*:
"eth0      Link encap:Ethernet HWaddr (MAC address)
           inet6 addr: fe80::213:d4ff:dfeb6:4eb4/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
           Interrupt:21

eth0:avah Link encap:Ethernet HWaddr (MAC address)
           inet address:*.*.*.* Bcast:*.*.*.* Mask:*.*.*.*
           UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
           Interrupt:21

lo            Link encap:Local Loopback
           inet addr:127.0.0.1 Mask:255.0.0.0
           inet6 addr::I/128 Scope:Host
           UP LOOPBACK RUNNING MTU:16436 Metric:1
            RX packets:162 errors:0 dropped:0 overruns:0 frame:0
           TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:14924 (14.5 KiB) TX bytes:14924 (14.5 KiB)"

As far as the cables, etc. I am currently on the same computer running Windows XP. Two hard drives are installed: one for XP, one for Ubuntu. The internet works fine on XP.

I appreciate any help.
Thanks

---

### Post by K.Mandla on 2007-08-25
See if restarting your network gives you an IP address (I'm assuming there's some kind of DHCP system working there).

```
sudo /etc/init.d/networking restart
```
Then check ifconfig again and see if your eth0 entry has an IP yet. You might also try 

```
sudo dhclient3 eth0
```
but I haven't used that command in a long time, so it might have changed. :oops:

P.S.: I forgot to ask about /etc/network/interfaces. Can you show us how your network is configured to start?

```
cat /etc/network/interfaces
```

---

### Post by preacher2B on 2007-08-25
I am starting to be a little discouraged with trying to run Ubuntu. If I cannot solve the internet problem I will have to reformat my drive and start over. :(

I tried *sudo /etc/init.d/networking restart*

* Reconfiguring network interfaces...
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid 5330
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


Hold on a second...
I just check the web site above and downloaded a updated version V3.0.6
I'm going to burn it and try to install it in Ubuntu from CD
Be back with the results soon

---

### Post by preacher2B on 2007-08-25
No luck -- I don't understand how to install the update or even if it's for me?!?

Back to *sudo /etc/init.d/networking restart*

Listening on LPF/eth0/(MAC address)
Sending on LPF/eth0/(MAC address)
Sending on Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium
All rights reserved
For info... (See Above Post)

Listening on LPF/eth0/(MAC address)
Sending on LPF/eth0/(MAC address)
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
NO DHCPOFFERS received.
No working leases in persistent database - sleeping.

It then checks for other devices and Internet connections of which I don't have. I only have one Realtek NIC.

Moving on.

*cat /etc/network/interfaces*

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1, eth2, ath0, wlan0. (I do not have these)



Update:

*sudo ifconfig*

eth0:avah Link encap:Ethernet HWaddr (MAC address)
          inet addr:169.254.8.154 Bcast:169.254.255.255 Mask:255.255.0.0

insert IP addresses where * is in previous post.

Again, I am on a college campus network.  Maybe a firewall or router in the LAN is blocking internet on a UNIX platform?  Windows is working fine.

Should I continue to search out this dilema or should I try a different OS like openSUSE or something else?  An OS without internet capabilities on my computer is not efficient and productive.

If I would change to another UNIX based OS do you have a suggestion?

Thanks again

---

### Post by freebeer on 2007-08-25
It's not a question of distros - Ubuntu has very good network/internet support - usually it's all automatic.  We just have to figure out why it's not working for you and then fix the problem.  :D

It seems that your last attempt got you an IP address.  Can you not browse the internet now?

Another thing you can try is to boot off the LiveCD.  See if you get an internet connection then.  Then reboot your installed version and see if you get a connection.  Report back here with the results.

---

### Post by preacher2B on 2007-08-25
I have tried to reboot using the LiveCD and have tried to reinstall. Both to no avail.  Still no internet

---

### Post by preacher2B on 2007-08-25
The first time I ran the LiveCD I had internet. After the initial installation I had internet. After the "security updates" which were downloaded, No internet.  I cannot use the internet with the LiveCD or installed OS.

---

### Post by freebeer on 2007-08-25
That's kind of weird... the security updates can't affect the OS that's on the LiveCD....

---

### Post by preacher2B on 2007-08-26
The initial installation I was referring to was the first installation to my hard drive and reboot. When I rebooted with no LiveCD, I had internet. Then I did the updates and then there was no internet for Ubuntu.

After erasing the slave drive (where Ubuntu was installed) I reinstalled Ubuntu. I notice now that the kernel installed is .15 rather than .16 which was running the first go-round. I accidentally erased my first .iso that I burned to disk, and burned it again using the same .iso saved on my master hard drive (with XP on it). I checked the disk for errors and none were detected.

If I don't have this figured out by tomorrow, I'll have to abandon it. School starts this week and I won't have time to solve internet woes.

I appreciate all the help and input and I will keep trying for a little longer.

---

### Post by preacher2B on 2007-08-28
Realtek 8139/810x Fast Family Ethernet driver released June/July 2007 does not work in Ubuntu.

Rolled back driver in Windows to March 2007.  This is being sent via Ubuntu!

---

