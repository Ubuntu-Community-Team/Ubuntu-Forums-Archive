---
title: "LTSP on Ubuntu"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by akay56 on 2005-10-14
HI 

I have been trying to get LTSP working on my Ubuntu box (5.04). I have mostly followed the instructions from various sources on the web, including wiki and ltsp.org

when i try to boot from the diskless client, the client is recognized by the DHCP server and the fixed ip address is allocated and the boot process via the tftp kicks in as well, but then everything comes to a halt at the following  point:


PCI: Found IRQ 11 for device 01:08.0
e100: eth0: Intel(R) PRO/100 Network Connection
Hardware receive checksums enabled

Running dhcpcd on port 67
Mounting root filesystem: /opt/ltsp4/i386 from: 192.168.217.42
mount: 192.168.217.42:/opt/ltsp4/i386 failed, reason given by server: Permission denied
mount: nfsmount failed: Bad file descriptor
NFS: mount program didn't pass remote address!
mount: mounting 192.168.217.42:/opt/ltsp/i386 on /mnt failed: Invalid argument

ERROR! Failed to mount the root directory via NFS!
Possible reasons include:
1) NFS services may not be running on the server
2) Workstation IP does not map to a hostname, either in /etc/hosts, or in
DNS
3) Wrong address for NFS server in the DHCP config file
4) Wrong pathname for root directory in the DHCP config file

Kernel panic: Attempted to kill init!
<3>e100: eth0 NIC Link is Up 10 Mbps Half duplex


Other  relevant information for my setup is:

ubuntu 5.04
/opt/ltsp4 has 777 rights
192.168.217.42 is running the LTSP server
192.168.217.50 is the fixed ip for 1 client pc
the dhcpd.conf file is attached
the following line appears in the inetd.conf:
tftp dgram udp wait root /usr/sbin/tcpd /usr/sbin/in.tftpd /tftpboot

i am running tftpd-hpa

I would be extremely thankful to the members to show some light on this.

Regards
Ash

---

### Post by adwait on 2005-10-14
I don't really know much about LTSP, but breezy (the new version of Ubuntu) supports LTSP........

---

