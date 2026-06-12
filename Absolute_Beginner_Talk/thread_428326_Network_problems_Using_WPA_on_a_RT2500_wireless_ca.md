---
title: "Network problems: Using WPA on a RT2500 wireless card"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by penkie on 2007-04-30
I am totally new to Linux and installed Feisty yesterday for the very first time.

I am stuck with my wireless network. I have a Ralink RT2500 wireless card and need to connect to my Router using WPA. 

I followed the guides as found [here]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#head-af86b211b480d43b791cd9b4e698f96638d6d25f").
I also tried the alternatives as well as other alternatives that I found in forums elsewhere. Furthermore, I disabled the network manager. But in the end, nothing seems to work.

This are my current settings for the Interfaces file (tried dhcp as well):
```

auto lo
iface lo inet loopback

#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto ra0
iface ra0 inet static
	address 192.168.2.45
	netmask 255.255.255.0
	gateway 192.168.2.1
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 mode managed
pre-up iwconfig ra0 channel 11
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid "MYSSID"
pre-up iwpriv ra0 set WPAPSK="MY HEX WPA Key"
pre-up iwpriv ra0 set TxRate=0
pre-up iwconfig ra0 essid "MYSSID"
pre-up ifconfig ra0 up

```

It seems to work a little bit. This is what I get from iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"MYSSID"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: <<routers mac>>   
          Bit Rate=24 Mb/s   Tx-Power:2 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level=-48 dBm  Noise level:-193 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Moreover, "Network Tools" says that ra0 has an IP has transmitted quite some bytes and also receives quite some bytes (with 7 collisions). However, I am not able to ping my router (which works with a wireless laptop running winxp) and firefox doesn't work.

Can anyone help me? :confused:

---

### Post by penkie on 2007-04-30
Ok, so I tried to solve it in a different way. 

I moved my computer to my router, so that I had a direct internet connection. Then I decided to give ndiswrapper a try by following [this guide]("http://moonintheroom.blogspot.com/"). I followed the guide precisely, but it didn't seem to work (after everything was finished, it said it couldn't find the device). Until I commented out the rt2500 in the /etc/modprobe.d/blacklist file. I restarted, and suddenly my wireless internet connection worked!! Just to be sure I restarted again and it still worked.

So then, I powered the pc down and moved my computer back and started up again. Then, again internet connection was dead. :( 

By fiddling with the blacklist enty and restarting time again I got my connection working again. Kind of. It is extremely slow and sometimes not working. Browsing alternates in being slow and not-responding and being just normal.  If I look in Network Tools I see a "ra0", but also sometimes after reboot I see two entries for "ra0" and a "ra0:something". Also, in network tools I see a lot of "Collisions" (roughly about half the number of "Received packets")

I have the feeling this is the result of a driver clash, or something, between the native rt2500 drivers and the ndiswrapper driver. The problem might be that they have the same name. ndiswrapper calls the windows drivers also rt2500. So if I put "rt2500" in the blacklist, I guess they are both ruled out. But if I let them both load they conflict.

Does anyone has an idea of how to get out of this mess? Should I maybe delete the native driver, and if so, how?? Thanks!!

---

### Post by fiatguy85 on 2007-07-01
The ndiswrapper driver is called rt2500, but the module is named ndiswrapper.  Therefore, blacklisting rt2500 should not affect ndiswrapper.

---

### Post by mjgumbley on 2007-07-06
I've had untold woe getting an rt2500 card (a Belkin F5D7010), in an IBM Thinkpad T21 working with a D-Link DSL-G604T in WPA mode, that doesn't broadcast its SSID.
 
I blogged about it some time ago at
[http://ccgi.gumbley.plus.com/blog/?page_id=25](http://ccgi.gumbley.plus.com/blog/?page_id=25)
although the instructions there now don't work with Feisty.

Here's an update now I've finally got something working!

I'm using kernel 2.6.20-16-386, wpasupplicant  0.5.7-0ubuntu2, and I have network-manager and network-manager-gnome 0.6.4-6ubuntu7.

I was using ndiswrapper, and have 1.38-1ubuntu1  of this and ndiswrapper-utils-1.9 installed, with the Windows drivers described in the above post - which I believe are now no longer available. Anyway, I don't need these any more. I do still have ndiswrapper listed in /etc/modules, and this is still loaded as is rt2500 (checked with lsmod)


Magically, last night, after much luck, I managed to get a connection.

So, in /etc/network/interfaces, I have:
```

auto lo
iface lo inet loopback

iface eth1 inet static
address 192.168.0.42
netmask 255.255.255.0
gateway 192.168.0.69

iface ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "MYSSID"
        pre-up iwconfig ra0 mode Managed
        pre-up iwconfig ra0 channel 6 rate 11M 
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK=ababababababababababa-hexstring-magic-ababa
        pre-up ifconfig ra0 up
auto ra0

```

Generate the hex string WPAPSK with wpa_passphrase, like this:
```

root@rodin:/sbin # wpa_passphrase MYSSID
# reading passphrase from stdin
foobarquux
network={
        ssid="MYSSID"
        #psk="foobarquux"
        psk=40224c3e1c2b7d048385732f1cbb45227a4377d55246e1555fe80288129bf9a3
}

```

Note, I do NOT blacklist rt2500 in /etc/modprobe.d/blacklist. I have the PCMCIA card inserted on boot, not inserted after boot.

I have wpasupplicant running on startup from /etc/init.d/wpa_supplicant.conf:
```

ap_scan=2

network={
        ssid="MYSSID"
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        scan_ssid=0
        #psk=ababa-same-hex-string-as-above-abaa
        # Or, you can put your actual password in...
        psk="foobarquux"
        priority=2
}

```

My /etc/default/wpasupplicant file reads:
```

# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>          Wireless Driver
#  -i <ifname>          Interface (required, unless specified in config)
#  -c <config file>     Configuration file
#  -d                   Debugging (-dd for more)
#  -w                   Wait for interface to come up

OPTIONS="-w -i wlan0 -D wext -dd -c /etc/wpasupplicant.conf"

```

Now I don't know if I need this - it was the last thing I tried last night and things just worked on a reboot - but it's referring to interface wlan0, and the wext wireless extensions driver, not ra0 and rt2500 ... your mileage may vary.

ifconfig reports:
```

ra0       Link encap:Ethernet  HWaddr <<The Belkin's MAC>>  
          inet addr:192.168.0.200  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe8e:8281/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2390 errors:3 dropped:3 overruns:0 carrier:0
          collisions:68 txqueuelen:1000 
          RX bytes:1931929 (1.8 MiB)  TX bytes:330894 (323.1 KiB)
          Interrupt:11 Base address:0xc000 

```

And iwconfig reports:
```

ra0       RT2500 Wireless  ESSID:"MYSSID"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: <<MYSSID's MAC>>   
          Bit Rate:11 Mb/s   Tx-Power:2 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=60/100  Signal level=-67 dBm  Noise level:-193 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Now network-manager's nm-applet is running, but when I logged in, it didn't prompt for a password to unlock the keychain; I have previously gone through the usual configuration to get my WPA password etc. set with network-manager. However, the lights on the PCMCIA card come on before login, at the gdm greeter screen - so I'm not sure network-manager's doing anything special here. It certainly isn't doing its usual invocation of wpasupplicant, as you might see in /var/log/daemon.log.

One thing I do have to do is sudo ifdown eth1 (even though there's no Ethernet cable attached), or uncheck it in System >> Administration >> Network, otherwise both ra0 and eth1 have an entry in the route table. When all's working, I get:
```

root@rodin:/etc/default # route -n
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 ra0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.0.69    0.0.0.0         UG    0      0        0 ra0

```

The /var/log/kern.log reports, for the rt2500 driver:
```

Jul  6 20:28:40 localhost kernel: [   54.624000] rt2500 1.1.0 BETA4 2006/06/18 http://rt2x00.serialmonkey.com
Jul  6 20:28:40 localhost kernel: [   54.624000] PCI: Setting latency timer of device 0000:06:00.0 to 64
Jul  6 20:28:40 localhost kernel: [   54.796000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
Jul  6 20:28:40 localhost kernel: [   54.796000] rt2500 EEPROM:  5  5  5  5  5  5  5  5  5  5  5  5  5  5  dBm Maximum
Jul  6 20:28:40 localhost kernel: [   54.836000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul  6 20:28:40 localhost kernel: [   54.852000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
Jul  6 20:28:40 localhost kernel: [   54.852000] rt2500 EEPROM:  5  5  5  5  5  5  5  5  5  5  5  5  5  5  dBm Maximum
Jul  6 20:28:40 localhost kernel: [   54.992000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
Jul  6 20:28:40 localhost kernel: [   54.992000] rt2500 EEPROM:  5  5  5  5  5  5  5  5  5  5  5  5  5  5  dBm Maximum

```

Anyway, I hope this is of use to someone out there, or at least, if I never get a wireless connection again, I'll know that there is some hope.

---

### Post by mkoyle on 2007-07-11
> **mjgumbley said:**
> 
```

auto lo
iface lo inet loopback

iface eth1 inet static
address 192.168.0.42
netmask 255.255.255.0
gateway 192.168.0.69

iface ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "MYSSID"
        pre-up iwconfig ra0 mode Managed
        pre-up iwconfig ra0 channel 6 rate 11M 
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK=ababababababababababa-hexstring-magic-ababa
        pre-up ifconfig ra0 up
auto ra0

```


I am guesing that the

        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down

stuff merely delays the actual startup that matters.  I would suggest trying

 pre-up sleep 20

instead (sleep is a program that stops does nothing for the number of seconds you tell it so sleep 20 will delay 20 seconds from when it executes and when your actual ifup command runs).  On my laptop with a broadcom device, I have to put 'pre-up modprobe ndiswrapper' in, too but if I don't put the sleep comand in first there appear to be some prerequisites not yet running and my network doesn't come up until I manually modprobe ndiswrapper and ifdown/ifup.

As far as wpasupplicant, in theory, the how to at [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) (which runs wpasupplicant with commands inside /etc/network/interfaces) should do the same thing as you configured in a separate file.  It seems like a better approach, but this is mostly opinion.

Good luck!

--Matthew

---

