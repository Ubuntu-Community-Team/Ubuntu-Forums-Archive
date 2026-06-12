---
title: "Minor\Large problem with the os"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Firesnow on 2007-05-11
Hey guys, I just installed ubuntu a day ago and so far its far surpassed my expectations! however i'm having some troubles with it. The OS will randomly shut down with out warning, its becoming a problem and more of a hassle to be reading up on how to use this OS and having it randomly turn off. Any help will be much appreciated as i'm looking forward to using this os!

Thanks in Advance!

PS is there any uuber begginers tutorial that you would suggest for an extreme newbie?

---

### Post by oilchangeguy on 2007-05-11
define the os shuts down. do you mean ubuntu shuts down or the entire computer shuts down?

---

### Post by Firesnow on 2007-05-11
My bad, the computer randomly shuts down, first the OS goes through what looks like its normal shut down processes then the computer turns off.

---

### Post by Acksys on 2007-05-11
Maybe something to do with Power Management? Check Power Management settings under the System -> Preferences menu.

Is it a laptop or desktop?

---

### Post by Firesnow on 2007-05-11
Its a Dell inspiron 6000 laptop, all the options in the power settings are set to never. 

Is it possibly a problem that i'm dual booting between ubuntu and windows xp?

---

### Post by compmodder26 on 2007-05-11
It sounds to me like an overheating issue.  Can you hear your fans running?

---

### Post by oilchangeguy on 2007-05-11
the computer doesn't care if you dual boot. that's not the problem. sounds like a hardware problem. does it do this while using xp?

---

### Post by Firesnow on 2007-05-11
Never had a problem with WinXp when it came to randomly shutting down.
There is a cool pad under the computer and its running at a regular temprature, the os goes through what appears to be its shutdown sequence, then the computer turns off...

---

### Post by Snowcat on 2007-05-11
It would help if you found the log of the crash, somewhere in /var/log/syslog (entries are sorted by time), and pasted it here.

---

### Post by Firesnow on 2007-05-11
Its all greek to me at the moment, the next time it happens i'll post the log.

---

### Post by oilchangeguy on 2007-05-11
go to system, admin, system log. and see what's there.

---

### Post by livingtarget on 2007-05-11
> **Firesnow said:**
> PS is there any uber beginners tutorial that you would suggest for an extreme newbie?

Here's two websites I'd recommend to a linux fledgling:
1. [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) excellent site which goes beyond just dishing you the obsure commands.
2. [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) a site which will give you plenty of terminal commands to just copy & paste for a multitude of common problems. I'm not sure how good it still is, but it helped me out a lot in the beginning.

---

### Post by Firesnow on 2007-05-11
May 11 16:41:46 andrew-laptop udevd-event[4370]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host2/target2:0:0/2:0:0:0/ioerr_cnt' failed
May 11 16:41:46 andrew-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
May 11 16:41:48 andrew-laptop kernel: [   36.196000] eth1: no IPv6 routers present
May 11 16:41:48 andrew-laptop kernel: [   36.516000] eth0: no IPv6 routers present
May 11 16:41:50 andrew-laptop dhcdbd: Started up.
May 11 16:41:50 andrew-laptop NetworkManager: <information>^Istarting... 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^Ieth1: Device is fully-supported using driver 'ipw2200'. 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Successfully dropped root privileges.
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: avahi-daemon 0.6.17 starting up.
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Successfully called chroot().
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Successfully dropped remaining capabilities.
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: No service found in /etc/avahi/services.
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Joining mDNS multicast group on interface eth0.IPv4 with address 130.245.207.130.
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: New relevant interface eth0.IPv4 for mDNS.
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Network interface enumeration completed.
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Registering new address record for fe80::213:ceff:fe32:f17c on eth1.*.
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Registering new address record for fe80::212:3fff:fee7:dd96 on eth0.*.
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Registering new address record for 130.245.207.130 on eth0.IPv4.
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Server startup complete. Host name is andrew-laptop.local. Local service cookie is 4124940672.
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Registering HINFO record with values 'I686'/'LINUX'.
May 11 16:41:50 andrew-laptop NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^INow managing wireless (802.11) device 'eth1'. 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IDeactivating device eth1. 
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Withdrawing address record for fe80::213:ceff:fe32:f17c on eth1.
May 11 16:41:50 andrew-laptop NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'b44'. 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IDeactivating device eth0. 
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Withdrawing address record for 130.245.207.130 on eth0.
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Leaving mDNS multicast group on interface eth0.IPv4 with address 130.245.207.130.
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Interface eth0.IPv4 no longer relevant for mDNS.
May 11 16:41:50 andrew-laptop avahi-daemon[4887]: Withdrawing address record for fe80::212:3fff:fee7:dd96 on eth0.
May 11 16:41:50 andrew-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
May 11 16:41:50 andrew-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IWill activate connection 'eth0'. 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IDevice eth0 activation scheduled... 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IActivation (eth0) started... 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IOld device 'eth0' activating, won't change. 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
May 11 16:41:50 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May 11 16:41:51 andrew-laptop NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
May 11 16:41:51 andrew-laptop kernel: [   39.648000] [drm] Initialized drm 1.1.0 20060810
May 11 16:41:51 andrew-laptop kernel: [   39.656000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 18
May 11 16:41:51 andrew-laptop kernel: [   39.660000] [drm] Initialized i915 1.6.0 20060119 on minor 0
May 11 16:41:52 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May 11 16:41:52 andrew-laptop NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
May 11 16:41:52 andrew-laptop kernel: [   40.524000] ppdev: user-space parallel port driver
May 11 16:41:53 andrew-laptop NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
May 11 16:41:53 andrew-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
May 11 16:41:53 andrew-laptop dhclient: DHCPACK from 130.245.207.1
May 11 16:41:53 andrew-laptop avahi-daemon[4887]: Joining mDNS multicast group on interface eth0.IPv4 with address 130.245.207.130.
May 11 16:41:53 andrew-laptop avahi-daemon[4887]: New relevant interface eth0.IPv4 for mDNS.
May 11 16:41:53 andrew-laptop avahi-daemon[4887]: Registering new address record for 130.245.207.130 on eth0.IPv4.
May 11 16:41:53 andrew-laptop avahi-daemon[4887]: Withdrawing address record for 130.245.207.130 on eth0.
May 11 16:41:53 andrew-laptop avahi-daemon[4887]: Leaving mDNS multicast group on interface eth0.IPv4 with address 130.245.207.130.
May 11 16:41:53 andrew-laptop avahi-daemon[4887]: Interface eth0.IPv4 no longer relevant for mDNS.
May 11 16:41:53 andrew-laptop avahi-daemon[4887]: Joining mDNS multicast group on interface eth0.IPv4 with address 130.245.207.130.
May 11 16:41:53 andrew-laptop avahi-daemon[4887]: New relevant interface eth0.IPv4 for mDNS.
May 11 16:41:53 andrew-laptop avahi-daemon[4887]: Registering new address record for 130.245.207.130 on eth0.IPv4.
May 11 16:41:53 andrew-laptop NetworkManager: <information>^IDHCP daemon state is now 4 (reboot) for interface eth0 
May 11 16:41:53 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
May 11 16:41:53 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
May 11 16:41:53 andrew-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
May 11 16:41:53 andrew-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
May 11 16:41:53 andrew-laptop NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
May 11 16:41:53 andrew-laptop NetworkManager: <information>^I  address 130.245.207.130 
May 11 16:41:53 andrew-laptop NetworkManager: <information>^I  netmask 255.255.255.0 
May 11 16:41:53 andrew-laptop NetworkManager: <information>^I  broadcast 130.245.207.255 
May 11 16:41:53 andrew-laptop NetworkManager: <information>^I  gateway 130.245.207.1 
May 11 16:41:53 andrew-laptop NetworkManager: <information>^I  nameserver 130.245.255.3 
May 11 16:41:53 andrew-laptop NetworkManager: <information>^I  nameserver 130.245.255.4 
May 11 16:41:53 andrew-laptop NetworkManager: <information>^I  hostname 'aally' 
May 11 16:41:53 andrew-laptop NetworkManager: <information>^I  domain name 'hendrix-resnet.stonybrook.edu' 
May 11 16:41:53 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 11 16:41:53 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
May 11 16:41:53 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May 11 16:41:53 andrew-laptop avahi-daemon[4887]: Withdrawing address record for 130.245.207.130 on eth0.
May 11 16:41:53 andrew-laptop avahi-daemon[4887]: Leaving mDNS multicast group on interface eth0.IPv4 with address 130.245.207.130.
May 11 16:41:53 andrew-laptop avahi-daemon[4887]: Interface eth0.IPv4 no longer relevant for mDNS.
May 11 16:41:53 andrew-laptop avahi-daemon[4887]: Joining mDNS multicast group on interface eth0.IPv4 with address 130.245.207.130.
May 11 16:41:53 andrew-laptop avahi-daemon[4887]: New relevant interface eth0.IPv4 for mDNS.
May 11 16:41:53 andrew-laptop avahi-daemon[4887]: Registering new address record for 130.245.207.130 on eth0.IPv4.
May 11 16:41:53 andrew-laptop dhclient: bound to 130.245.207.130 -- renewal in 3174 seconds.
May 11 16:41:53 andrew-laptop hpiod: 1.7.3 accepting connections at 2208... 
May 11 16:41:54 andrew-laptop kernel: [   41.796000] apm: BIOS not found.
May 11 16:41:54 andrew-laptop hcid[5225]: Bluetooth HCI daemon
May 11 16:41:54 andrew-laptop kernel: [   42.080000] Bluetooth: Core ver 2.11
May 11 16:41:54 andrew-laptop kernel: [   42.080000] NET: Registered protocol family 31
May 11 16:41:54 andrew-laptop kernel: [   42.080000] Bluetooth: HCI device and connection manager initialized
May 11 16:41:54 andrew-laptop kernel: [   42.080000] Bluetooth: HCI socket layer initialized
May 11 16:41:54 andrew-laptop hcid[5225]: Starting SDP server
May 11 16:41:54 andrew-laptop NetworkManager: <information>^IClearing nscd hosts cache. 
May 11 16:41:54 andrew-laptop NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
May 11 16:41:54 andrew-laptop kernel: [   42.152000] Bluetooth: L2CAP ver 2.8
May 11 16:41:54 andrew-laptop kernel: [   42.152000] Bluetooth: L2CAP socket layer initialized
May 11 16:41:54 andrew-laptop NetworkManager: <information>^IActivation (eth0) successful, device activated. 
May 11 16:41:54 andrew-laptop NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
May 11 16:41:54 andrew-laptop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May 11 16:41:54 andrew-laptop kernel: [   42.380000] Bluetooth: RFCOMM socket layer initialized
May 11 16:41:54 andrew-laptop kernel: [   42.380000] Bluetooth: RFCOMM TTY layer initialized
May 11 16:41:54 andrew-laptop kernel: [   42.380000] Bluetooth: RFCOMM ver 1.8
May 11 16:41:54 andrew-laptop anacron[5283]: Anacron 2.3 started on 2007-05-11
May 11 16:41:54 andrew-laptop /usr/sbin/cron[5310]: (CRON) INFO (pidfile fd = 3)
May 11 16:41:54 andrew-laptop /usr/sbin/cron[5311]: (CRON) STARTUP (fork ok)
May 11 16:41:54 andrew-laptop anacron[5283]: Normal exit (0 jobs run)
May 11 16:41:55 andrew-laptop /usr/sbin/cron[5311]: (CRON) INFO (Running @reboot jobs)
May 11 16:41:54 andrew-laptop ntpdate[5341]: step time server 82.211.81.145 offset -0.785361 sec
May 11 16:41:55 andrew-laptop avahi-daemon[4887]: Registering new address record for fe80::212:3fff:fee7:dd96 on eth0.*.
May 11 16:42:00 andrew-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
May 11 16:42:00 andrew-laptop NetworkManager: <debug info>^I[1178916120.352604] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
May 11 16:42:04 andrew-laptop kernel: [   52.956000] eth0: no IPv6 routers present
May 11 16:42:06 andrew-laptop gdm[4958]: Couldn't authenticate user
May 11 16:42:11 andrew-laptop kernel: [   60.508000] usb 5-5: reset high speed USB device using ehci_hcd and address 2
May 11 16:42:12 andrew-laptop dhclient: No DHCPOFFERS received.
May 11 16:42:12 andrew-laptop dhclient: No working leases in persistent database - sleeping.
May 11 16:42:12 andrew-laptop avahi-autoipd(eth1)[5433]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
May 11 16:42:12 andrew-laptop avahi-autoipd(eth1)[5433]: Successfully called chroot().
May 11 16:42:12 andrew-laptop avahi-autoipd(eth1)[5433]: Successfully dropped root privileges.
May 11 16:42:12 andrew-laptop avahi-autoipd(eth1)[5433]: fopen() failed: Permission denied
May 11 16:42:12 andrew-laptop avahi-autoipd(eth1)[5433]: Starting with address 169.254.8.118
May 11 16:42:13 andrew-laptop NetworkManager: <debug info>^I[1178916133.063061] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_503__SW070303513_if0_scsi_device_lun0_scsi_generic'). 
May 11 16:42:13 andrew-laptop kernel: [   61.492000]  sdb1
May 11 16:42:13 andrew-laptop kernel: [   61.492000] sd 2:0:0:0: Attached scsi disk sdb
May 11 16:42:13 andrew-laptop kernel: [   61.492000] sd 2:0:0:0: Attached scsi generic sg2 type 0
May 11 16:42:13 andrew-laptop gconfd (andrew-5498): starting (version 2.18.0.1), pid 5498 user 'andrew'
May 11 16:42:13 andrew-laptop gconfd (andrew-5498): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 11 16:42:13 andrew-laptop gconfd (andrew-5498): Resolved address "xml:readwrite:/home/andrew/.gconf" to a writable configuration source at position 1
May 11 16:42:13 andrew-laptop gconfd (andrew-5498): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 11 16:42:13 andrew-laptop gconfd (andrew-5498): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 11 16:42:13 andrew-laptop gconfd (andrew-5498): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 11 16:42:18 andrew-laptop avahi-autoipd(eth1)[5433]: Callout BIND, address 169.254.8.118 on interface eth1
May 11 16:42:18 andrew-laptop avahi-daemon[4887]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.8.118.
May 11 16:42:18 andrew-laptop avahi-daemon[4887]: New relevant interface eth1.IPv4 for mDNS.
May 11 16:42:18 andrew-laptop avahi-daemon[4887]: Registering new address record for 169.254.8.118 on eth1.IPv4.
May 11 16:42:22 andrew-laptop NetworkManager: <information>^IUpdating allowed wireless network lists. 
May 11 16:42:22 andrew-laptop avahi-autoipd(eth1)[5433]: Successfully claimed IP address 169.254.8.118
May 11 16:42:22 andrew-laptop avahi-autoipd(eth1)[5433]: fopen() failed: Permission denied
May 11 16:42:22 andrew-laptop NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
May 11 16:42:22 andrew-laptop ntpdate[5586]: adjust time server 82.211.81.145 offset -0.000125 sec
May 11 16:42:24 andrew-laptop gconfd (andrew-5498): Resolved address "xml:readwrite:/home/andrew/.gconf" to a writable configuration source at position 0

---

