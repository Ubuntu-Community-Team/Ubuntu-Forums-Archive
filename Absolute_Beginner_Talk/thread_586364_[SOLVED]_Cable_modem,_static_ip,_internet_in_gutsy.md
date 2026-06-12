---
title: "[SOLVED] Cable modem, static ip, internet in gutsy"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by dse.37 on 2007-10-22
I'm a complete nub when it comes to this OS and have recently installed Ubuntu 7.10 on my home PC (after a few problems). Now the only thing to do is get my internet connection working.

I use a cable modem and a static IP address. No router, no wireless. I'd have thought (and so I've read) that Ubuntu should configure the connection automatically, but the first time I tried to install the OS it was having problems configuring DHCP and caused the setup to hang at 85% later on in the process. The second time around I unplugged the cable from the ethernet card and skipped the 'net configuration to avoid the installation process hanging again.

Now when I try to configure my internet connection manually I get nothing. I lose all data when trying to ping addresses provided by the Ubuntu help and in all honesty I don't know which way to turn next.

I've searched, read a few posts and have seen that the people trying to help have asked for the oputput to ifconfig and lspci, so here they are just in case.

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0D:87:9D:EE:7A
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xc000 

eth0:avah Link encap:Ethernet  HWaddr 00:0D:87:9D:EE:7A  
          inet addr:169.254.9.13  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2112 (2.0 KB)  TX bytes:2112 (2.0 KB)
```

lspci:
```
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

Thanks in advance.

---

### Post by hyper_ch on 2007-10-22
What details on your static IPs were you given from your ISP?

Do you have the IP, netmask and gateway?

---

### Post by dse.37 on 2007-10-22
I do indeed. 

IP: 82.37.188.141
Subnet Mask : 255.255.248.0
Default Gateway: 82.37.184.1
DHCP Server: 62.31.176.115
DNS Servers: 62.31.176.39, 194.117.134.19, 195.188.53.175

I've tried using these but still I've had no joy.

---

### Post by hyper_ch on 2007-10-22
Have a look at my post in there:

[http://ubuntuforums.org/showthread.php?t=586340](http://ubuntuforums.org/showthread.php?t=586340)

---

### Post by dse.37 on 2007-10-22
You couldn't have made this anymore simple, really. But I still have no connection.

When I open the web browser now I get a message in the status bar saying "Looking up www.domain.com" instead of the "Server not found" page. I don't know if that puts me any closer to where I want to be, but I thought I'd share what little info I have.

---

### Post by hyper_ch on 2007-10-22
Can you output the contents of:

/etc/network/interfaces

/etc/hosts

/etc/resolv.conf

?

(Hint: use the "cat" command:   cat /etc/hosts)

---

### Post by dse.37 on 2007-10-22
/etc/network/interfaces:

```
# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet static
        address 82.37.188.141
        netmask 255.255.248.0
        gateway 82.37.184.1

auto eth0
```

/etc/hosts:

```
127.0.0.1 localhost
62.31.176.115  dse-ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

/etc/resolv.conf:

```
nameserver 62.31.176.39
nameserver 194.117.134.19
nameserver 195.188.53.175
```

---

### Post by hyper_ch on 2007-10-23
etc/network/interfaces:

```
# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet static
        address 82.37.188.141
        netmask 255.255.248.0
        gateway 82.37.184.1

```
Well, first you configure a static device and then you overthrow it with DHCP --> auto eth0

---

### Post by dse.37 on 2007-10-23
Still nothing. But now I've removed that the browser window goes straight to "Server not found."

---

### Post by hyper_ch on 2007-10-23
did you also restart the network interface?

---

### Post by dse.37 on 2007-10-23
Yes. And the PC itself. I don't know if that makes much of a difference with this OS, but I thought I'd try anyway.

I'm getting desperately close to giving the PC flying lessons. :(

---

### Post by hyper_ch on 2007-10-23
Well, how is your network setup? How do you try to reach that machine?

From where can't you connect to it?

---

### Post by dse.37 on 2007-10-23
I don't have a network. It's just a cable modem plugged into the machine. Dual booting :$

I've just been on the phone with my ISP and all the only advice they can give is "Restart your modem."

It's beginning to sound like more trouble than it's worth.

---

### Post by hyper_ch on 2007-10-23
boot into windozw and the open a command terminal and type:

```

ipconfig /all

```

And post that ;)

---

### Post by dse.37 on 2007-10-23
```
Windows IP Configuration

        Host Name . . . . . . . . . . . . : r2-dtard
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet NIC
        Physical Address. . . . . . . . . : 00-0D-87-9D-EE-7A
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 82.37.188.141
        Subnet Mask . . . . . . . . . . . : 255.255.248.0
        Default Gateway . . . . . . . . . : 82.37.184.1
        DHCP Server . . . . . . . . . . . : 62.31.176.115
        DNS Servers . . . . . . . . . . . : 62.31.176.39
                                            194.117.134.19
                                            195.188.53.175
        Lease Obtained. . . . . . . . . . : 23 October 2007 10:17:54
        Lease Expires . . . . . . . . . . : 27 October 2007 04:50:15
```

---

### Post by hyper_ch on 2007-10-23
Can you also pastebin your hosts file?

It will be in c:\windows\system32\drivers\etc

---

### Post by dse.37 on 2007-10-23
I have no 'hosts' file. There is 'hosts1.bak' and 'hosts2.bak' along with lmhosts (example file), networks, protocol and services. And both of those are the same apart from one line.

hosts1.bak:
```
[...] # For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host

127.0.0.1       localhost
```

hosts2.bak:
```
[...] # For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host

127.0.0.1       localhost

#block wga
```

---

### Post by hyper_ch on 2007-10-23
well, I have no clue why it won't work :(

---

### Post by dse.37 on 2007-10-23
It's okay. I'm sure I'll get it working one way or another. Thank you for your time. It's greatly appreciated :]

---

### Post by redhotchili on 2007-10-23
I have the same problem...I am at my 1st time on ubuntu,I installed it and all going fine till at this "internet connection" step where I m in the same situacion as **dse.37** is really a headache...I was watching carefully this thread and followed every step on it coz I have exactly the same problem and can't get it work:(...anyways **dse.37** if you find out how to fix this shoot a PM please...thanks much **hyper_ch** for your effort

BTW ..ubuntu is the single OS installed on my laptop now and can't get it connect to internet:(

---

### Post by mrog on 2007-10-23
I'm a little confused here. Are you sure you should have a static IP address? Judging by the Windows ipconfig output, it's setup to use DHCP. (Dhcp Enabled. . . . . . . . . . . : Yes)

What happens when you replace (/etc/network/interfaces):

iface eth0 inet static
        address 82.37.188.141
        netmask 255.255.248.0
        gateway 82.37.184.1

auto eth0

with:

auto eth0
iface eth0 inet dhcp

---

### Post by dse.37 on 2007-10-23
The same thing. Nothing. I've just been on Ubuntu sniffing around the help files and came across that. I've followed it word for word and still I don't know what could be wrong.

I've even gone as far as removing the cable, using sudo ifdown eth0, rebooting, plugging in the cable and using sudo ifup eth0.

It tries to acquire the information it needs but returns a load of information I don't quite understand with a message tagging along at the end that says something like 'No working leases in persistent database - sleeping.'

Thanks for taking a look at this.

And for as long as I can remember my IP address has been the same. I'm talking 2 years+.

---

### Post by mrog on 2007-10-23
Just for the fun of it, try disconnecting everything from the cable modem including the power for a few minutes.

---

### Post by dse.37 on 2007-10-23
I've tried that too. Just now, even. The modem was off for a good 10 minutes or so and I even went as far as releasing my IP before restarting into linux. I still get the "No working leases in persistent database - sleeping." message.

I'm beginning to lose hope.

I did notice that when I plugged the cable back into the ethernet card that the light that's usually there wasn't anymore. I can't see it being a hardware problem seeing as everything checks out with 'lspci' though.

Anymore thoughts or ideas?

---

### Post by dse.37 on 2007-10-23
At last!

I fixed it by going to Control Panel>System>Hardware(tab)>Device Manager.

Expanded 'Network Adapters' and opened up the properties for my network card. Under the 'Advanced' tab I enabled the Wakeup-On-Lan After Shutdown option and rebooted.

I hope this spares some other poor soul the headache I've had over the last few days.

---

### Post by NotTheMessiah on 2007-10-23
Haha..it is always something very simple and not visible :)

---

### Post by hyper_ch on 2007-10-24
glad you solved that problem :)

---

### Post by ARhere on 2007-11-25
> **dse.37 said:**
> At last!

I fixed it by going to Control Panel>System>Hardware(tab)>Device Manager.

Expanded 'Network Adapters' and opened up the properties for my network card. Under the 'Advanced' tab I enabled the Wakeup-On-Lan After Shutdown option and rebooted.

I hope this spares some other poor soul the headache I've had over the last few days.

HUH????  I have the exact same problem right now, and I have no clue where > Control Panel>System>Hardware(tab)>Device Manager ...is.  Is that a Windoz system you are talking about? ...or Kubuntu?

-ARhere

---

### Post by soulgt on 2008-01-21
> **dse.37 said:**
> At last!

I fixed it by going to Control Panel>System>Hardware(tab)>Device Manager.

Expanded 'Network Adapters' and opened up the properties for my network card. Under the 'Advanced' tab I enabled the Wakeup-On-Lan After Shutdown option and rebooted.

I hope this spares some other poor soul the headache I've had over the last few days.

I think I may have this exact problem. Unfortunately, I'm not dual-booting - I replaced my WinXP installation with Ubuntu on my laptop. Is there a way to edit those settings in Ubuntu?

---

