---
title: "[SOLVED] connecting two computers"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-03-12
Ok I need to connect my notebook to my desktop to share internet and files. I am trying to get around buying a router as i am moving back over seas in a few months and wont be able to take it with me. here is my set up:

I have a desktop that has my internet connecting going into the on-board LAN port. I would like to buy a PCI LAN card and run a CAT5 for the PCI card to my notebook...is this possible?

oh and im using 7.10 right now but the notebook will have 7.10 and vista.

thanks :)

---

### Post by SpaceTeddy on 2008-03-12
sharing files is quite simple if you have a linux/linux environment, and a little (but not much) more difficult when one of them is windows. But it is certainly doable nontheless.
As for the internet sharing - yes, that is quite possible aswell, but it might require some understanding of how networks work in a basic manner.

Also, i must warn that i am very used to the commandline and will always default to it old habits die hard). So most help i can provide is CLI (command line interface) stuff only. If you do not wish to do this, ignore my post :)

ok, first off, [this]("http://ubuntuforums.org/showthread.php?t=708002") thread answered the question on how to share files between ubuntu and Mac OS X - don't worry, windows and linux can use those shares aswell. Sample configuration is included and should not be too hard to setup

Second, [this]("http://ubuntuforums.org/showthread.php?t=713874") thread explains how to make your ubuntu a router/firewall. I am afraid that this requires some basic understanding of how the network interfaces in ubuntu are handled. 

of course you can always ask if there is anything unclear in the instructions

---

### Post by ukripper on 2008-03-12
In this case, instead of buying CAT5 and PCMCIA LAN card, if I already have wireless card in my laptop I would rather get another PCI wirless card for my desktop and do adhoc wireless networking. 
Just an opinion!

[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

---

### Post by rockinlinux on 2008-03-12
yeah I thought about that but my wireless stopped working in my notebook a few weeks ago so thats a no go. i wish i could though. and actually i only have to but a pci card, my notebook already has a nic card...and i just need a second one for the desktop....i should have got that MOBO that had duel lans....oh well :)

space teddy: thanks, ill look at the links. :)

---

### Post by rockinlinux on 2008-03-12
so that file sharing is using samba...i was thinking more like a file server...but i have never tried samba either. I want to not only share a couple files but all of them.

---

### Post by SpaceTeddy on 2008-03-12
samba is a fileserver - or rather, a server that lets you create windows shares on a linux machine. The only other (simple) was i can think of is the sftp described there. For windows, you can then use winscp to connect to the linux machine..

alternatively, if your vista has a share, you can connect to it directly through the filebrowser, but typing "smb://IP-Address" where you replace the IP-Address by the acctualy phsycial address the windows has (should be a four number combination seperated by dots :) )

---

### Post by linux_believer on 2008-03-12
Well  you already know the simple solution is to buy a cheap 4 port router. Seems like you buying a NIC is a more feasable option for you. This will work assuming you get the second NIC working which shouldn't be an issue. Make sure you use a crossover Ethernet cable and not the standard straight thru

---

### Post by ukripper on 2008-03-12
> **rockinlinux said:**
> so that file sharing is using samba...i was thinking more like a file server...but i have never tried samba either. I want to not only share a couple files but all of them.

This may help to understand samba more - [http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend)

---

### Post by rockinlinux on 2008-03-12
if im setting ubuntu up as a router i would not need a cross over cable would I? i thought it would be just like a normal router....

thanks for al the help :)

---

### Post by SpaceTeddy on 2008-03-12
if there is no switch inbetween, and both lan cards have 100Mbit or less, you will need a crossover. If one  of your computer uses a Gbit Ethernet card, it the cable does not matter Gbit cards twist by themselves and figure out what is being used). If you use a switch inbetween, you need normal patch cables....

---

### Post by rockinlinux on 2008-03-12
well my on-board port is Gbit but i want to leave that for internet as i have a static IP and i dont want to call my ISP and have them change my MAC again. I guess i will look for a Gbit pci card...do i have to have tools to make a crossover cable? I only made one LAN cable and i used the crimp things...do i have to have them?

---

### Post by SpaceTeddy on 2008-03-12
buy a gbit card or a crossover cable together with a 100mbit card... you can make it yourself... but there i cannot help you :(

---

### Post by rockinlinux on 2008-03-13
ok i got my crossover cable and a second LAN card for my desktop. I followed spaceteddy's how to at [http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874) .

It still does not work.

here is what i have:

my desktop in connected to the internet through eth0
i have my laptop plugged into eth1 on the desktop.

eth1 has the following:

address 10.8.16.1
        netmask 255.255.255.0
        broadcast 10.8.16.0
        network 10.8.16.0
eth0 is my ineternet, this is a static ip connection and my isp gave me the following:

ip: 192.xxx.xxx.xx
subnet: 255.255.255.192
gateway: 91.192.159.65
DNS 1: 193.111.156.4
DNS 2: 91.192.159.1

The laptop is setup with a static ip address and has the following:
ip: 10.8.16.2
netmask:  255.255.255.0
gateway: 10.8.16.1
DNS: 193.111.156.4 (found in /etc/resolv.conf and is the same as my ISP gave me)

From the laptop i can ping the gdesktop at the 10.8.16.1 i recive pakets back. I cannot ping the noteboot at 10.8.16.2 from the desktop. I also can not ping any websites from the notebook.

I have checked all the files 6 times to make sure they are all correct and im sure they are. The only thing im not sure about is the /etc/rc.local file, mine looks like this after i edited it:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE

exit 0  
```
The thing in question to me is the "exit 0" should i leave that there or not?

any help would be awesome, thanks again for everyones time :)

---

### Post by rockinlinux on 2008-03-13
i just tried to change the net mask on eth1 and the notebook the the one that my isp gave me but it still didnt work so i changed it all bakc to how i have it posted above.

---

### Post by rockinlinux on 2008-03-13
anyone?

---

### Post by SpaceTeddy on 2008-03-13
> From the laptop i can ping the gdesktop at the 10.8.16.1 i recive pakets back. I cannot ping the noteboot at 10.8.16.2 from the desktop. I also can not ping any websites from the notebook.

this does not make a lot of sense - you can ping the desktop from the notebook (i.e. from 10.8.16.2 you get answers from 10.8.16.1) - but you cannot ping the other way around - i.e. you are able to ping the laptop from the desktop. or is there a third computer in it i do not know about ? please clarify this...

also, did you edit the /ect/sysctl.conf to enable ip forwarding - otherwise your ubuntu desktop will not let anything pass thought it. this can be check via
```
cat /proc/sys/net/ipv4/ip_forward
```

the reply should be 1 if it is enabled

as for the rc.local - the exit 0 stays in there. 
The first line to allow the paket filter to pass any pakets
the second is that anything going out to the internet should be hidden your desktop pc

---

### Post by lespaul_rentals on 2008-03-13
Install **bridge-utils** from the repositories.  Add the following to your */etc/network/interfaces*:

```
auto br0
iface br0 inet static
bridge_ports eth0 eth1
```

Where *eth0* and *eth1* are the names of your LAN cards.

Then, run:

```
sudo ifup br0
```

and it should work from there.

---

### Post by SpaceTeddy on 2008-03-13
i thought bridging nics means they get put on the same subsegment of the network., i.e. you enable the network cards to forward layer 2 instead of layer 3 and upwards... 
this would mean you need a second ip address from the internet to assign to the laptop... 

but, maybe i am mistaken. just never used bridgeutils that way...

---

### Post by lespaul_rentals on 2008-03-13
> **SpaceTeddy said:**
> i thought bridging nics means they get put on the same subsegment of the network., i.e. you enable the network cards to forward layer 2 instead of layer 3 and upwards... 
this would mean you need a second ip address from the internet to assign to the laptop... 

but, maybe i am mistaken. just never used bridgeutils that way...

Yes, but brige-utils will be much more easy to get working.  I'm assuming he's behind a NAT?

---

### Post by rockinlinux on 2008-03-13
ok i did do that spaceteddy but it returns a 0 so it is not enabled...here is my file.

```

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.
kernel.maps_protect = 1

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1

```

---

### Post by rockinlinux on 2008-03-13
i think im going to try to get space teddy wasy to work but will try this next if i cant. There is not a thride computer....i can do in a terminal on the laptop "ping 10.8.16.1" and i get packets back. If i got to the desktop and do "ping 10.8.16.2" i get nothing.

---

### Post by SpaceTeddy on 2008-03-13
i've seen this behavoir before, that the sysctl.conf gets ignored - add this line to your rc.local
> /bin/echo 1 > /proc/sys/net/ipv4/ip_forward
which will overwrite the ip_forwarding directly at the kernel. to enable it directly (withoutht reboot, run these commands
> sudo su
/bin/echo 1 > /proc/sys/net/ipv4/ip_forward
the first one makes you root, the second will enable ip_forwarding directly.

as for the reverse ping - windows blocks icmp requests with the build in firewall - so that  is not a real suprise that they do not come back. try disableing the firewall on the laptop and then retry the ping


@lespaul_rentals:
well, he is not exactly behind a nat - the router IS the nat :) also, i've been thinking about bridgeing the interfaces - i think that would mean that any paket in the local network would get forwarded into the internet (and vice versa) - i.e. even dhcp-requests and windows share broadcasts... i am not sure if that is really the case, but at the moment i am pretty convinced it is... 
and that would be a behaviour i would not want - but i have been wrong before on my assumptions, and i am not entirely sure about this one...

---

### Post by rockinlinux on 2008-03-13
the laptop is running mandriva by the way...

---

### Post by rockinlinux on 2008-03-13
works great! thanks for everyhting!!

just so i can understand more...why did it ignore that file?

---

### Post by SpaceTeddy on 2008-03-13
i don't know why it ignores it, or why it gets reset to the default value - that is something i still need to figure out. But i have seen that problem before - once on a server running debian lenny.

also congratulations that the configuration works now - have fun surfing the net with both machines. :)

---

### Post by rockinlinux on 2008-03-14
thanks, could not have done it with out you. It really taught me a lot, i have always hated the NM so now i think i can avoid it. on the Mandriva laptop I didnt use the NM...i did basically the same thing as setting up the desktop :)

Now for the Samba server....i read that post of yours, and a few others...seem very hard but im sure I can do it. Ill start a new post if I have problems (sure i will) ;)

anyways, spaceteddy...you are like a network god it seems like and tahnks for blessing me with some of your smarts :)

---

