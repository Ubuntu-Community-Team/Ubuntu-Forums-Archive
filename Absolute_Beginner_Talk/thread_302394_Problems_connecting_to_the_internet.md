---
title: "Problems connecting to the internet"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-11-18
I am having problems connecting to the internet (via wireless) after a new install on a Gateway machine. I can see that the wireless card is being correctly detected (using the "iwconfig" command). If I type the following in a terminal
```
iwconfig
```
then I get "no wireless connection" under eth0 but there is an output under eth1.

Then when I try to "activate" eth1 using System -> Networking I am not able to activate the connection. Am I making some mostake?

Additionally, I cannot see the available networks under the 'network essid' box. Why is this so?

Any suggestions are welcome.

---

### Post by ryu kun on 2006-11-18
What are the outputs of iwconfig and ifconfig?

---

### Post by aam-aadmi on 2006-11-18
Let me give the output from a bunch of commands so that someone can understand my problem better.

```
iwconfig

lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

```


```
ifconfig

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1456 (1.4 KiB)  TX bytes:1456 (1.4 KiB)

```


```
 ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:E0:B8:54:04:DF
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```


```
lspci | grep Eth

0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)


```


```
 route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


```

```
cat /etc/network/interfaces

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


```


```
cat /etc/resolv.conf

```
NO OUTPUT on the above command.

```
cat /etc/dhcp3/dhclient.conf

# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
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

```

Hope somebody can now figure out what is going on?

---

