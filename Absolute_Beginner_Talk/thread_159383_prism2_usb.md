---
title: "prism2_usb"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by polishemokid on 2006-04-12
I am trying to connect with a netgear ma111 usb stick.  And i havent found many places that have explained really what i can do.  I have what i believe is "breezy badger" version?  
People have said I can use prism2_usb to install it, where can i download prism2_usb?

---

### Post by az on 2006-04-12
You already have it.  Just install linux-wlan-ng (it's a package that is on your cd and probably cached on your hard drive by the installer)

It is not straigtforward to use, but it is relable.  The graphical tool to configure your network connection does not speak the same language as a prism2_usb device.

Once you have that installed, edit your /etc/network/interfaces file and add a stanza like this:
sudo gedit /etc/network/interfaces


auto wlan0

iface wlan0 inet dhcp
 wireless_mode managed
 wireless_essid MYHOUSE
 wireless_enc on
 wlan_ng_key0 aa:aa:aa:aa:aa


Where HYHOUSE and aaaaaaaaaa are your ssid and wep.

The connection should be brought up on boot.  To bring it up by hand immediately, run

sudo ifup wlan0

---

### Post by babelfishi on 2006-04-23
Hmm. I have the same USB device and I got these errors:
```

sudo ifup wlan0
/etc/network/interfaces:19: interface wlan0 declared allow-auto twice
ifup: couldn't read interfaces file "/etc/network/interfaces"

```

My /etc/network/interfaces file:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface eth0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
wireless_mode managed
#4.23.06 modify
auto wlan0

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid NETGEAR
wireless_enc on
wlan_ng_key0 85:3A:53:4B:C9

```


Anyone know why and how I can fix it?

---

### Post by az on 2006-04-23
[QUOTE=babelfishi]Hmm. I have the same USB device and I got these errors:
```

sudo ifup wlan0
/etc/network/interfaces:19: interface wlan0 declared allow-auto twice
ifup: couldn't read interfaces file "/etc/network/interfaces"

```

My /etc/network/interfaces file:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface eth0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
wireless_mode managed
#4.23.06 modify
auto wlan0

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid NETGEAR
wireless_enc on
wlan_ng_key0 85:3A:53:4B:C9

```


Anyone know why and how I can fix it?[/QUOTE]

auto eth0
iface eth0 inet dhcp
#auto wlan0
#iface wlan0 inet dhcp
#wireless_mode managed
#4.23.06 modify
auto wlan0

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid NETGEAR
wireless_enc on
wlan_ng_key0 85:3A:53:4B:C9

---

### Post by babelfishi on 2006-04-25
Now it becomes this:
```

@ubuntu:/etc/network$ sudo ifup wlan0
wlanctl-ng: No such device
Failed to enable the device, exitcode= 1 .
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code  1
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set Encode" (8B2B) :
    GET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up wlan0.

```

/etc/network/interfaces file:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

auto eth0
iface eth0 inet dhcp
#auto wlan0
#iface wlan0 inet dhcp
#wireless_mode managed
#4.23.06 modify
auto wlan0

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid NETGEAR
wireless_enc on
wlan_ng_key0 85:3A:53:4B:C9


```

..help?

---

### Post by az on 2006-04-26
"sudo ifup wlan0
wlanctl-ng: No such device"

Maybe you have a different device?

Reboot without it plugged in, open a terminal and type

tail -f /var/log/messages
and then plug it in.  Wait a few seconds and then post the output of what's in the terminal.

---

### Post by babelfishi on 2006-04-26
The output:
```

@ubuntu:~$ tail -f /var/log/messages
Apr 26 14:38:49 localhost gconfd (chris-8887): starting (version 2.12.0), pid 8887 user 'chris'
Apr 26 14:38:49 localhost gconfd (chris-8887): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr 26 14:38:49 localhost gconfd (chris-8887): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Apr 26 14:38:49 localhost gconfd (chris-8887): Resolved address "xml:readwrite:/home/chris/.gconf" to a writable configuration source at position 2
Apr 26 14:38:49 localhost gconfd (chris-8887): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Apr 26 14:38:49 localhost gconfd (chris-8887): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4Apr 26 14:38:49 localhost gconfd (chris-8887): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Apr 26 14:38:49 localhost gconfd (chris-8887): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Apr 26 14:38:49 localhost gconfd (chris-8887): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Apr 26 14:39:01 localhost gconfd (chris-8887): Resolved address "xml:readwrite:/home/chris/.gconf" to a writable configuration source at position 0
Apr 26 14:39:33 localhost kernel: [4294779.305000] usb 1-1: new full speed USB device using uhci_hcd and address 4

```

When I plugged USB in it was Apr 26 14:39:33
(and yes, I'm using a Netgear MA111 Wireless USB)

---

### Post by az on 2006-04-26
Are you running breezy?  Because your card is not recognised by the kernel - no driver is being loaded for it.  Warty and Hoary did not include the at76c503 driver which is probably what your device is.  Is this the case?

If it were a prism2_usb device, the prism2_usb driver woudl be loaded and you would see that in the log.

---

### Post by babelfishi on 2006-04-26
Yes I am running Breezy. (5.10)
and I have the package:
**linux-wlan-ng**
on my computer.
Is there anything else I could do about it? Would this post help? ([http://www.ubuntuforums.org/showthread.php?t=111913&highlight=netgear+MA111](http://www.ubuntuforums.org/showthread.php?t=111913&highlight=netgear+MA111))

---

### Post by babelfishi on 2006-04-26
I tried loading the prism2_usb moudle:
```
sudo modprobe prism2_usb
```
and I tried running it again:
```

@ubuntu:~$ sudo modprobe prism2_usb
Password:
@ubuntu:~$ sudo ifup wlan0
wlanctl-ng: No such device
Failed to enable the device, exitcode= 1 .
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set Encode" (8B2B) :
    GET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up wlan0.


```

...=/

---

### Post by jobezone on 2006-04-26
And you also modprobed at76c503, and it still wasn't detected by the system, right (we chatted on #ubuntu)?

Could you execute **lsusb**, with the adapter plugged in and paste the output here?
Also, install the package **lshw**, run it, and paste the output here.

The link you gave is very interesting, as he has the same hardware as yours, so it may be helpfull to compare both of your results to these commands, and configurations.

---

### Post by az on 2006-04-26
You don't have a prism2_usb device.

Perhaps try Dapper (live cd) to see if the chipset has a linux driver, or use ndiswrapper.

---

### Post by jobezone on 2006-04-27
Found a tutorial on setting up ndiswrapper: [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

---

### Post by babelfishi on 2006-04-27
Hmm.
Here are some outputs:
```

chris@ubuntu:~$ lsusb
Bus 002 Device 002: ID 0ea0:2168 Ours Technology, Inc. Transcend JetFlash 2.0 / Astone USB Drive
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 413c:2001 Dell Computer Corp.
Bus 001 Device 003: ID 413c:1001 Dell Computer Corp.
Bus 001 Device 002: ID 0846:4230 NetGear, Inc. MA111 WiFi
Bus 001 Device 001: ID 0000:0000
chris@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 255MB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.1.2
          size: 1800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: 82845 845 (Brookdale) Chipset Host Bridge
          vendor: Intel Corporation
          physical id: e8000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e8000000-efffffff
        *-pci:0
             description: PCI bridge
             product: 82845 845 (Brookdale) Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 MX/MX 400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: b2
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:fc000000-fcffffff iomemory:f0000000-f7ffffff irq:3
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: 7
                bus info: pci@02:07.0
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=EMU10K1_Audigy
                resources: ioport:ece0-ecff irq:16
           *-input
                description: Input device controller
                product: SB Live! MIDI/Game Port
                vendor: Creative Labs
                physical id: 7.1
                bus info: pci@02:07.1
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Emu10k1_gameport
                resources: ioport:ecd8-ecdf
           *-communication UNCLAIMED
                description: Communication controller
                product: HCF 56k Data/Fax Modem
                vendor: Conexant
                physical id: 8
                bus info: pci@02:08.0
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:fe1f0000-fe1fffff ioport:ecd0-ecd7 irq:10
           *-network
                description: Ethernet interface
                product: 21x4x DEC-Tulip compatible 10/100 Ethernet
                vendor: Davicom Semiconductor, Inc.
                physical id: 9
                bus info: pci@02:09.0
                logical name: eth0
                version: 31
                serial: 00:80:ad:87:a7:6f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=dmfe ip=192.168.1.3 multicast=yes
                resources: ioport:e800-e8ff iomemory:fe1efc00-fe1efcff irq:18
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801BA IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:ffa0-ffaf
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   product: WDC WD800JB-00FMA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 74GB
              *-disk:1
                   product: IC35L040AVER07-0
                   vendor: Hitachi
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   capacity: 37GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   product: Memorex DVD+/-RW True-8X
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
              *-cdrom:1
                   product: LG CD-RW CED-8080B
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:ff80-ff9f irq:19
           *-usbhost
                product: Intel Corporation 82801BA/BAM USB (Hub #1)
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0 UNCLAIMED
                   description: Generic USB device
                   product: MA111 WiFi
                   vendor: NetGear, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: maxpower=256mA speed=12.0MB/s
              *-usb:1
                   description: USB hub
                   product: Dell USB Keyboard Hub
                   vendor: NMB
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.01
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=50mA slots=3 speed=12.0MB/s
                 *-usb
                      description: Keyboard
                      product: Dell USB 7HK Keyboard
                      vendor: NMB
                      physical id: 1
                      bus info: usb@1:2.1
                      version: 0.01
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=50mA speed=12.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 12
             width: 32 bits
             clock: 33MHz
             resources: ioport:dcd0-dcdf irq:10
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@00:1f.4
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:ff60-ff7f irq:23
           *-usbhost
                product: Intel Corporation 82801BA/BAM USB (Hub #2)
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: Flash Disk
                   vendor: USB
                   physical id: 2
                   bus info: usb@2:2
                   version: 2.00
                   serial: 611041BE954F0096
                   capabilities: usb-2.00 scsi
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
  *-scsi
       physical id: 1
       bus info: scsi@0
       logical name: scsi0
       capabilities: scsi-host
       configuration: driver=usb-storage

```

I read the ndiswrapper howto, but it still does not work. I downloaded the right files (mine was 0846:4230), installed with ndiswrapper, and it reconizes my drivers ok, but it does not show up in system-admin-network
```

chris@ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
ma111v2 driver present, hardware present
chris@ubuntu:~$ sudo depmod -a
Password:
chris@ubuntu:~$ sudo modprobe ndiswrapper
chris@ubuntu:~$ tail /var/log/messages
Apr 27 20:35:48 localhost gconfd (chris-11379): starting (version 2.12.0), pid 11379 user 'chris'
Apr 27 20:35:48 localhost gconfd (chris-11379): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0Apr 27 20:35:48 localhost gconfd (chris-11379): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Apr 27 20:35:48 localhost gconfd (chris-11379): Resolved address "xml:readwrite:/home/chris/.gconf" to a writable configuration source at position 2
Apr 27 20:35:48 localhost gconfd (chris-11379): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Apr 27 20:35:48 localhost gconfd (chris-11379): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Apr 27 20:35:48 localhost gconfd (chris-11379): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Apr 27 20:35:48 localhost gconfd (chris-11379): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Apr 27 20:35:48 localhost gconfd (chris-11379): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Apr 27 20:35:59 localhost gconfd (chris-11379): Resolved address "xml:readwrite:/home/chris/.gconf" to a writable configuration source at position 0
chris@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:AD:87:A7:6F
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::280:adff:fe87:a76f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:27075669 (25.8 MiB)  TX bytes:1518086 (1.4 MiB)
          Interrupt:18 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:122899 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122899 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11702904 (11.1 MiB)  TX bytes:11702904 (11.1 MiB)

chris@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

hmm. how about the /etc/network/interfaces file? should i use my original file or the new one in the first page?
I have tried both with the ndiswrapper done, but it still does not work. =/

---

### Post by tbg58 on 2006-06-27
Just a quick note to say thanks for all the help you've given to others working on the Prism2 wireless hardware issues -- thanks for your patience and aplomb working with the same sorts of questions over and over again -- without ever once berating someone for being a n00b.  Hat tip to you, sir.

---

### Post by tbg58 on 2006-06-27
Previous post was to Azz.

---

### Post by acorrigan on 2006-07-15
> **azz said:**
> 
sudo gedit /etc/network/interfaces


auto wlan0

iface wlan0 inet dhcp
 wireless_mode managed
 wireless_essid MYHOUSE
 wireless_enc on
 wlan_ng_key0 aa:aa:aa:aa:aa


Where HYHOUSE and aaaaaaaaaa are your ssid and wep.

The connection should be brought up on boot.  To bring it up by hand immediately, run

sudo ifup wlan0

running sudo ifup wlan0 alone doesn't start my wireless I need to run (as sudo):

```

rmmod prism2_usb
modprobe prism2_usb prism2_doreset=1
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
ifdown wlan0
ifup wlan0

```

Furthermore, when I reboot according to the networking manager wlan0 is disconnected and I can't use the internet.  I need to run the above commands again to get it working again.  My question is: How do I make it so that when I reboot my wireless works, without running those commands?

Also, my wireless dies, after a few minutes it will just not work even though the network monitor shows that it's fine.  Does anyone know what the problem could be? For example, by the time I finished typing this message I had to restart my connection using the above set of commands since 'submit reply' didn't work.

Thanks for any help!


btw, my /etc/network/interfaces is:
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless_mode managed
wireless-essid hop_to_it
wireless_enc on
wlan_ng_key0 11:34:BE:01:50:C1:04:8E:C6:19:B1:35:6D

```

---

