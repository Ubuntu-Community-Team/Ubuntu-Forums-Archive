---
title: "Problems staying connected to internet"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by tulsh on 2006-08-21
My internet keeps on disconnecting.  After I reboot, it comes back up.  Then after a short time, it disconnects again.

tanya@mozart:~$ ping -c 5 google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from 64.233.187.99: icmp_seq=1 ttl=242 time=38.1 ms
64 bytes from 64.233.187.99: icmp_seq=2 ttl=242 time=38.9 ms
64 bytes from 64.233.187.99: icmp_seq=3 ttl=242 time=39.5 ms
64 bytes from 64.233.187.99: icmp_seq=4 ttl=242 time=38.4 ms
64 bytes from 64.233.187.99: icmp_seq=5 ttl=242 time=39.6 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4021ms
rtt min/avg/max/mdev = 38.162/38.961/39.652/0.629 ms
tanya@mozart:~$ sudo ifconfig
Password:
eth0      Link encap:Ethernet  HWaddr 00:40:CA:70:19:B5
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe70:19b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8486 errors:5 dropped:0 overruns:0 frame:6
          TX packets:7995 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5548988 (5.2 MiB)  TX bytes:4128868 (3.9 MiB)
          Interrupt:10 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3792 (3.7 KiB)  TX bytes:3792 (3.7 KiB)

tanya@mozart:~$ sudo dmesg|tail -n 30
[17179595.660000] SCSI device sdb: 58633344 512-byte hdwr sectors (30020 MB)
[17179595.660000] sdb: assuming drive cache: write through
[17179595.660000]  sdb: sdb1
[17179595.684000] sd 3:0:0:0: Attached scsi disk sdb
[17179595.700000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17179595.700000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[17179599.732000] ACPI: Power Button (FF) [PWRF]
[17179599.732000] ACPI: Power Button (CM) [PWRB]
[17179599.824000] ibm_acpi: ec object not found
[17179599.856000] pcc_acpi: loading...
[17179604.604000] ppdev: user-space parallel port driver
[17179604.960000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179604.960000] apm: overridden by ACPI.
[17179605.484000] eth0: no IPv6 routers present
[17179609.888000] Bluetooth: Core ver 2.8
[17179609.888000] NET: Registered protocol family 31
[17179609.888000] Bluetooth: HCI device and connection manager initialized
[17179609.888000] Bluetooth: HCI socket layer initialized
[17179609.924000] Bluetooth: L2CAP ver 2.8
[17179609.924000] Bluetooth: L2CAP socket layer initialized
[17179610.000000] Bluetooth: RFCOMM socket layer initialized
[17179610.000000] Bluetooth: RFCOMM TTY layer initialized
[17179610.000000] Bluetooth: RFCOMM ver 1.7
[17179625.376000] kjournald starting.  Commit interval 5 seconds
[17179625.376000] EXT3 FS on sdb1, internal journal
[17179625.376000] EXT3-fs: mounted filesystem with ordered data mode.
[17179892.012000] ppdev0: registered pardevice
[17179892.060000] ppdev0: unregistered pardevice
[17180199.344000] ppdev0: registered pardevice
[17180199.392000] ppdev0: unregistered pardevice
tanya@mozart:~$



Thanks for any help you can give me.

---

### Post by Major_Stitch on 2006-08-21
What kind of a connection do you use (dial-up modem, ethernet ADSL/Cable modem, USB -||- modem, bluetooth, etc.)?

Is it possible your modem is faulty? I had a similiar experience in Windows with my USB Adsl modem...

Cheers!

---

### Post by tulsh on 2006-08-21
I have high speed cable internet

---

