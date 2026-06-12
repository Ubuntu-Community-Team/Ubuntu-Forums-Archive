---
title: "No internet after kernel upgrade to Edgy"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by KernelKen on 2006-12-22
I upgraded from Dapper to Edgy and with it a new kernel  I read on a post to boot into the old kernel and you could access the internet.  I did and it worked.  I have been trying to find an answer but have not been succesful.

I think I have narrowed the problem down but don't know what to do to correct it. 

If I boot up using my old kernel and type the lshw command I get  

*-network:0
             description: Wireless interface
             product: Prism 2.5 Wavelan chipset
             vendor: Intersil Corporation
             physical id: 9
             bus info: pci@00:09.0
             logical name: eth1
             version: 01
             serial: 00:d0:59:f8:82:56
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list ethernet physical wireless
             configuration: broadcast=yes driver=orinoco_pci ip=192.168.0.4 multicast=yes wireless=IEEE 802.11b


But if I boot into the new kernel then I get

*-network:0 DISABLED
            description: Ethernet interface
            product: Prism 2.5 Wavelan chipset
            vendor: Intersil Corporation
            physical id: 9
            bus info: pci@00:09.0
            logical name: wlan0
            version: 01
            width: 32 bits
            clock: 33MHz
            capabilities: cap_list ethernet physical
            configuration: broadcast=yes driver=prism2_pci multicast=yes
            resources: iomemory:e000a000-e000afff irq:10

I don't know if this is the problem or not but I think it is.  If someone knows how to get wireless internet to work again and loose the wlan I would appreciate it.

---

### Post by trixxz on 2006-12-22
Try as root doing

dhclient eth0

---

### Post by KernelKen on 2006-12-23
This is what I got. 

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted

---

### Post by christhemonkey on 2006-12-23
Try prefixing that command with "sudo" so to get temporary root privelages:
```
sudo dhclient eth0 
```
Then enter your password.

---

### Post by KernelKen on 2006-12-24
I thought I tried that but I see I had a typo.  I tried again and this is what i got.

Internet Systems Consortium DHCP Client V3.0.4
 Copyright 2004-2006 Internet Systems Consortium.
 All rights reserved.
 For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
 
 Listening on LPF/eth0/00:c0:9f:10:57:84
 Sending on   LPF/eth0/00:c0:9f:10:57:84
 Sending on   Socket/fallback
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
 No DHCPOFFERS received.
> No working leases in persistent database - sleeping.

---

### Post by christhemonkey on 2006-12-24
The problem being that before you were using a static ip adress, and now you are trying to use dhcp (presumably when there is not a setup dhcp server).

To correct this, edit the file /etc/network/interfaces
```
gksudo gedit /etc/network/interfaces 
```

And look for the line:
> iface eth0 inet dhcp

and change it to
> iface eth0 inet static
    address 192.168.0.4 

And then try that command again.
```
sudo dhclient eth0 
```

---

### Post by KernelKen on 2006-12-24
Okay I made the changes and ran the command again.  Here are the results.

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:c0:9f:10:57:84
Sending on   LPF/eth0/00:c0:9f:10:57:84
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by christhemonkey on 2006-12-25
It seems to still be still trying to use dhcp...

Can you try changing it in the network settings dialog box from dhcp to static ip address?

(oh and happy christmas!)

---

### Post by KernelKen on 2006-12-25
I maybe should have included this in the original post. If I knew how to insert a picture I would insert a screen shot.  but for now under Network Settings, connections tab I have two wired connection choices one is (wlan0) the other (eth0) and no wireless connection like I did with the old kernel.  But I can rule out a problem with my card because I am using Ubuntu right now under the old kernel and it is recognizing my wireless card.

And I hope your Christmas is enjoyable as well.

---

### Post by Vorian on 2006-12-25
> **KernelKen said:**
> I maybe should have included this in the original post. If I knew how to insert a picture I would insert a screen shot.  but for now under Network Settings, connections tab I have two wired connection choices one is (wlan0) the other (eth0) and no wireless connection like I did with the old kernel.  But I can rule out a problem with my card because I am using Ubuntu right now under the old kernel and it is recognizing my wireless card.

And I hope your Christmas is enjoyable as well.

Try this in your terminal

iwconfig eth1 ap (what ever your ap mac address is)
iwconfig eth1 essid (name of your router)
iwconfig eth1 key s:passphrase
dhclient eth1

boom, your in....

i use iwlist eth1 scanning to get the ap address and router name..

---

### Post by Vorian on 2006-12-25
> **christhemonkey said:**
> It seems to still be still trying to use dhcp...

Can you try changing it in the network settings dialog box from dhcp to static ip address?

(oh and happy christmas!)

his wifi card is on eth1 (op).  dhclient on eth0 will not do much good for wifi ;)

---

### Post by KernelKen on 2006-12-26
Vorian I tried what you said but it didn't work.  I either typed it wrong or something.  I copied and pasted everything.

Let me know if you have any other ideas or can be more specific on what to do.  

Arp failed for 192.168.0.4 on eth1... (6)
Try to ping the address before setting it.
Error for wireless request "Set AP Address" (8B14) :
    invalid argument "192.168.0.4".

iwlist: unknown command `eth1'

---

### Post by Vorian on 2006-12-26
> **KernelKen said:**
> Vorian I tried what you said but it didn't work.  I either typed it wrong or something.  I copied and pasted everything.

Let me know if you have any other ideas or can be more specific on what to do.  

Arp failed for 192.168.0.4 on eth1... (6)
Try to ping the address before setting it.
Error for wireless request "Set AP Address" (8B14) :
    invalid argument "192.168.0.4".

iwlist: unknown command `eth1'

hmm..
On your network monitor, have you tried changing the connection to eth1?

---

### Post by KernelKen on 2006-12-27
Vorian,

I tried what you said but that didn't work either.

---

### Post by KernelKen on 2007-01-03
Well after trying several things I gave up on Edgy and reloaded Dapper.  I had several other problems with the upgrade that I decided productivity was better than the benefits of Edgy.  I also found out the benefit of having my home file on a seperate partition the hard way. I would agree if you are new to Linux or Ubuntu set your home file up on its on drive/partition.

---

### Post by stani on 2007-03-15
Help this bug out on Feisty, contribute by passing your details to launchpad:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

> Can everyone affected please attach (do not paste into comment) the output of "lspci -vv" and "lspci -vvn", make sure to name the file something like lspci-vv-<yourname>.txt

There is not much time left, please participate!

Stani

---

### Post by mi_were on 2007-03-15
> **KernelKen said:**
> I maybe should have included this in the original post. If I knew how to insert a picture I would insert a screen shot.  but for now under Network Settings, connections tab I have two wired connection choices one is (wlan0) the other (eth0) and no wireless connection like I did with the old kernel.  But I can rule out a problem with my card because I am using Ubuntu right now under the old kernel and it is recognizing my wireless card.

And I hope your Christmas is enjoyable as well.

I have a similiar set up and had the same problem. I uninstalled the wireless card then reinstalled it and everything was fine again.

Just a thought! I never did find out why the card stopped working but it works fine now.

Cheers

---

