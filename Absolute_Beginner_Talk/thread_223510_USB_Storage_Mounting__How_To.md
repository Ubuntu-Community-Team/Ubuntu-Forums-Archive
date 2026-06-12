---
title: "USB Storage Mounting  How To"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by .::welemski::. on 2006-07-26
[COLOR=Black]Hi

 How do you mount a usb external HD in ubuntu?

 I tried this command:
 $sudo mount /proc/bus/usb -t usbfs /media/external

 It did mount to but it does now shows all the existing files instead it shows 5 folders and 1 text file.

 I tried this command:
 $tial -f /var/log/syslog

 All i saw was this:[/COLOR]     
[SIZE=1][COLOR=Blue]Jul 27 11:00:10 localhost kernel: [4295701.310000]   Type:   Direct-Access                 ANSI SCSI revision: 04
Jul 27 11:00:10 localhost kernel: [4295701.315000] SCSI device sda: 80043264 512 -byte hdwr sectors (40982 MB)
Jul 27 11:00:10 localhost kernel: [4295701.315000] sda: assuming drive cache: wr ite through
Jul 27 11:00:10 localhost kernel: [4295701.341000] SCSI device sda: 80043264 512 -byte hdwr sectors (40982 MB)
Jul 27 11:00:10 localhost kernel: [4295701.341000] sda: assuming drive cache: wr ite through
Jul 27 11:00:10 localhost kernel: [4295701.341000]  /dev/scsi/host2/bus0/target0 /lun0: p1
Jul 27 11:00:10 localhost kernel: [4295701.349000] Attached scsi disk sda at scs i2, channel 0, id 0, lun 0
Jul 27 11:00:10 localhost scsi.agent[9071]:      sd_mod: loaded sucessfully (for  disk)
Jul 27 11:00:11 localhost usbmount[9130]: cannnot execute /sbin/udev_volume_id
Jul 27 11:00:11 localhost usbmount[9168]: cannnot execute /sbin/udev_volume_id[/COLOR][/SIZE]

[COLOR=Black]and so i kept on observing and i kept on seeing this stuff;[/COLOR]
[SIZE=1][COLOR=Blue]ul 27 11:01:12 localhost kernel: [4295763.476000] scsi2 (0:0): rejecting I/O to offline device
Jul 27 11:01:12 localhost kernel: [4295763.476000] scsi2 (0:0): rejecting I/O to offline device
Jul 27 11:01:12 localhost kernel: [4295763.478000] scsi2 (0:0): rejecting I/O to offline device
Jul 27 11:01:12 localhost kernel: [4295763.478000] Buffer I/O error on device sda, logical block 0
Jul 27 11:01:12 localhost kernel: [4295763.479000] usb-storage: device scan complete
Jul 27 11:01:13 localhost usbmount[9241]: cannnot execute /sbin/udev_volume_id
Jul 27 11:01:13 localhost usbmount[9257]: cannnot execute /sbin/udev_volume_id
Jul 27 11:01:29 localhost kernel: [4295780.066000] usb 3-1: new full speed USB device using uhci_hcd and address 8
Jul 27 11:01:29 localhost kernel: [4295780.140000] usb 3-1: device descriptor read/64, error -71
Jul 27 11:01:34 localhost kernel: [4295785.472000] usb 5-1: new high speed USB device using ehci_hcd and address 9
Jul 27 11:01:35 localhost kernel: [4295785.558000] scsi3 : SCSI emulation for USB Mass Storage devices
Jul 27 11:01:35 localhost kernel: [4295785.560000] usb-storage: device found at 9
Jul 27 11:01:35 localhost kernel: [4295785.560000] usb-storage: waiting for device to settle before scanning
Jul 27 11:01:35 localhost usb.agent[9298]:      usb-storage: already loaded
Jul 27 11:01:40 localhost kernel: [4295790.560000]   Vendor: Maxtor 3  Model: 4098H4            Rev: YAH8
Jul 27 11:01:40 localhost kernel: [4295790.560000]   Type:   Direct-Access                      ANSI SCSI revision:  04
Jul 27 11:01:40 localhost kernel: [4295790.564000] SCSI device sda: 80043264 512-byte hdwr sectors (40982 MB)
Jul 27 11:01:40 localhost kernel: [4295790.564000] sda: assuming drive cache: write through
Jul 27 11:01:40 localhost kernel: [4295790.590000] SCSI device sda: 80043264 512-byte hdwr sectors (40982 MB)
Jul 27 11:01:40 localhost kernel: [4295790.590000] sda: assuming drive cache: write through
Jul 27 11:01:40 localhost kernel: [4295790.590000]  /dev/scsi/host3/bus0/target0/lun0: p1
Jul 27 11:01:40 localhost kernel: [4295790.596000] Attached scsi disk sda at scsi3, channel 0, id 0, lun 0
Jul 27 11:01:40 localhost scsi.agent[9346]:      sd_mod: loaded sucessfully (for disk)
Jul 27 11:01:40 localhost usbmount[9405]: cannnot execute /sbin/udev_volume_id
Jul 27 11:01:40 localhost usbmount[9443]: cannnot execute /sbin/udev_volume_id
Jul 27 11:02:56 localhost kernel: [4295866.660000] usb 5-1: reset high speed USB device using ehci_hcd and address 9
Jul 27 11:02:59 localhost kernel: [4295869.722000] usb 5-1: device descriptor read/64, error -110
Jul 27 11:03:14 localhost kernel: [4295884.867000] scsi: Device offlined - not ready after error recovery: host 3 channel 0 id 0 lun 0
Jul 27 11:03:14 localhost kernel: [4295884.867000] scsi3 (0:0): rejecting I/O to offline device
Jul 27 11:03:14 localhost kernel: [4295884.867000] Buffer I/O error on device sda, logical block 0
Jul 27 11:03:14 localhost kernel: [4295884.867000] Buffer I/O error on device sda, logical block 1
Jul 27 11:03:14 localhost kernel: [4295884.867000] Buffer I/O error on device sda, logical block 2
Jul 27 11:03:14 localhost kernel: [4295884.867000] Buffer I/O error on device sda, logical block 3
Jul 27 11:03:14 localhost kernel: [4295884.867000] Buffer I/O error on device sda, logical block 4
Jul 27 11:03:14 localhost kernel: [4295884.867000] Buffer I/O error on device sda, logical block 5
Jul 27 11:03:14 localhost kernel: [4295884.867000] Buffer I/O error on device sda, logical block 6
Jul 27 11:03:14 localhost kernel: [4295884.867000] Buffer I/O error on device sda, logical block 7
Jul 27 11:03:14 localhost kernel: [4295884.867000] usb 5-1: USB disconnect, address 9
Jul 27 11:03:14 localhost kernel: [4295884.867000] scsi3 (0:0): rejecting I/O to offline device
Jul 27 11:03:14 localhost kernel: [4295884.867000] scsi3 (0:0): rejecting I/O to offline device
Jul 27 11:03:14 localhost kernel: [4295884.869000] scsi3 (0:0): rejecting I/O to offline device
Jul 27 11:03:14 localhost kernel: [4295884.869000] Buffer I/O error on device sda, logical block 0
Jul 27 11:03:14 localhost kernel: [4295884.870000] usb-storage: device scan complete
Jul 27 11:03:14 localhost usbmount[9528]: cannnot execute /sbin/udev_volume_id
Jul 27 11:03:14 localhost usbmount[9544]: cannnot execute /sbin/udev_volume_id
Jul 27 11:03:15 localhost kernel: [4295886.523000] hub 5-0:1.0: connect-debounce failed, port 1 disabled
Jul 27 11:03:18 localhost kernel: [4295888.566000] usb 3-1: new full speed USB device using uhci_hcd and address 9
Jul 27 11:03:18 localhost kernel: [4295888.642000] usb 3-1: device descriptor read/64, error -71
Jul 27 11:03:23 localhost kernel: [4295893.972000] usb 5-1: new high speed USB device using ehci_hcd and address 10
Jul 27 11:03:23 localhost kernel: [4295894.058000] scsi4 : SCSI emulation for USB Mass Storage devices
Jul 27 11:03:23 localhost kernel: [4295894.060000] usb-storage: device found at 10
Jul 27 11:03:23 localhost kernel: [4295894.060000] usb-storage: waiting for device to settle before scanning
Jul 27 11:03:23 localhost usb.agent[9587]:      usb-storage: already loaded
Jul 27 11:03:28 localhost kernel: [4295899.060000]   Vendor: Maxtor 3  Model: 4098H4            Rev: YAH8
Jul 27 11:03:28 localhost kernel: [4295899.060000]   Type:   Direct-Access                      ANSI SCSI revision: 04
Jul 27 11:03:28 localhost kernel: [4295899.065000] SCSI device sda: 80043264 512-byte hdwr sectors (40982 MB)
Jul 27 11:03:28 localhost kernel: [4295899.065000] sda: assuming drive cache: write through
Jul 27 11:03:28 localhost kernel: [4295899.091000] SCSI device sda: 80043264 512-byte hdwr sectors (40982 MB)
Jul 27 11:03:28 localhost kernel: [4295899.091000] sda: assuming drive cache: write through
Jul 27 11:03:28 localhost kernel: [4295899.091000]  /dev/scsi/host4/bus0/target0/lun0: p1
Jul 27 11:03:28 localhost kernel: [4295899.102000] Attached scsi disk sda at scsi4, channel 0, id 0, lun 0
Jul 27 11:03:28 localhost scsi.agent[9636]:      sd_mod: loaded sucessfully (for disk)
Jul 27 11:03:28 localhost usbmount[9695]: cannnot execute /sbin/udev_volume_id
Jul 27 11:03:28 localhost usbmount[9733]: cannnot execute /sbin/udev_volume_id
Jul 27 11:04:44 localhost kernel: [4295975.166000] usb 5-1: reset high speed USB device using ehci_hcd and address 10Jul 27 11:04:47 localhost kernel: [4295978.228000] usb 5-1: device descriptor read/64, error -110
Jul 27 11:05:02 localhost kernel: [4295993.391000] usb 5-1: device descriptor read/64, error -110
Jul 27 11:05:03 localhost kernel: [4295993.645000] scsi: Device offlined - not ready after error recovery: host 4 channel 0 id 0 lun 0
Jul 27 11:05:03 localhost kernel: [4295993.645000] scsi4 (0:0): rejecting I/O to offline device
Jul 27 11:05:03 localhost kernel: [4295993.645000] Buffer I/O error on device sda, logical block 0
Jul 27 11:05:03 localhost kernel: [4295993.645000] Buffer I/O error on device sda, logical block 1
Jul 27 11:05:03 localhost kernel: [4295993.645000] Buffer I/O error on device sda, logical block 2
Jul 27 11:05:03 localhost kernel: [4295993.645000] Buffer I/O error on device sda, logical block 3
Jul 27 11:05:03 localhost kernel: [4295993.645000] Buffer I/O error on device sda, logical block 4
Jul 27 11:05:03 localhost kernel: [4295993.645000] Buffer I/O error on device sda, logical block 5
Jul 27 11:05:03 localhost kernel: [4295993.645000] Buffer I/O error on device sda, logical block 6
Jul 27 11:05:03 localhost kernel: [4295993.645000] Buffer I/O error on device sda, logical block 7
Jul 27 11:05:03 localhost kernel: [4295993.645000] usb 5-1: USB disconnect, address 10
Jul 27 11:05:03 localhost kernel: [4295993.646000] scsi4 (0:0): rejecting I/O to offline device
Jul 27 11:05:03 localhost kernel: [4295993.646000] scsi4 (0:0): rejecting I/O to offline device
Jul 27 11:05:03 localhost kernel: [4295993.671000] usb-storage: device scan complete
Jul 27 11:05:03 localhost kernel: [4295993.745000] scsi4 (0:0): rejecting I/O to dead device
Jul 27 11:05:03 localhost kernel: [4295993.745000] Buffer I/O error on device sda, logical block 0
Jul 27 11:05:03 localhost usbmount[9815]: cannnot execute /sbin/udev_volume_id
Jul 27 11:05:03 localhost usbmount[9835]: cannnot execute /sbin/udev_volume_id
Jul 27 11:05:30 localhost kernel: [4296020.566000] usb 3-1: new full speed USB device using uhci_hcd and address 10
Jul 27 11:05:34 localhost kernel: [4296024.972000] usb 5-1: new high speed USB device using ehci_hcd and address 12
Jul 27 11:05:34 localhost kernel: [4296025.058000] scsi5 : SCSI emulation for USB Mass Storage devices
Jul 27 11:05:34 localhost kernel: [4296025.060000] usb-storage: device found at 12
Jul 27 11:05:34 localhost kernel: [4296025.060000] usb-storage: waiting for device to settle before scanning
Jul 27 11:05:34 localhost usb.agent[9879]:      usb-storage: already loaded
Jul 27 11:05:39 localhost kernel: [4296030.060000]   Vendor: Maxtor 3  Model: 4098H4            Rev: YAH8
Jul 27 11:05:39 localhost kernel: [4296030.060000]   Type:   Direct-Access                      ANSI SCSI revision: 04
Jul 27 11:05:39 localhost kernel: [4296030.065000] SCSI device sda: 80043264 512-byte hdwr sectors (40982 MB)
Jul 27 11:05:39 localhost kernel: [4296030.065000] sda: assuming drive cache: write through
Jul 27 11:05:39 localhost kernel: [4296030.090000] SCSI device sda: 80043264 512-byte hdwr sectors (40982 MB)
Jul 27 11:05:39 localhost kernel: [4296030.090000] sda: assuming drive cache: write through
Jul 27 11:05:39 localhost kernel: [4296030.090000]  /dev/scsi/host5/bus0/target0/lun0: p1
Jul 27 11:05:39 localhost kernel: [4296030.100000] Attached scsi disk sda at scsi5, channel 0, id 0, lun 0
Jul 27 11:05:39 localhost scsi.agent[9928]:      sd_mod: loaded sucessfully (for disk)
Jul 27 11:05:39 localhost usbmount[9987]: cannnot execute /sbin/udev_volume_id
Jul 27 11:05:39 localhost usbmount[10025]: cannnot execute /sbin/udev_volume_id
Jul 27 11:06:55 localhost kernel: [4296106.164000] usb 5-1: reset high speed USB device using ehci_hcd and address 12Jul 27 11:06:58 localhost kernel: [4296109.226000] usb 5-1: device descriptor read/64, error -110
Jul 27 11:07:02 localhost kernel: [4296113.481000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Jul 27 11:07:13 localhost kernel: [4296124.389000] usb 5-1: device descriptor read/64, error -110
Jul 27 11:07:14 localhost kernel: [4296124.643000] scsi: Device offlined - not ready after error recovery: host 5 channel 0 id 0 lun 0
Jul 27 11:07:14 localhost kernel: [4296124.643000] scsi5 (0:0): rejecting I/O to offline device

Jul 27 11:09:21 localhost gconfd (root-10195): starting (version 2.12.0), pid 10195 user 'root'
Jul 27 11:09:21 localhost gconfd (root-10195): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 27 11:09:21 localhost gconfd (root-10195): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Jul 27 11:09:21 localhost gconfd (root-10195): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Jul 27 11:09:21 localhost gconfd (root-10195): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Jul 27 11:09:21 localhost gconfd (root-10195): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Jul 27 11:09:21 localhost gconfd (root-10195): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Jul 27 11:09:21 localhost gconfd (root-10195): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Jul 27 11:09:21 localhost gconfd (root-10195): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Jul 27 11:09:31 localhost kernel: [4296261.924000] CSLIP: code copyright 1989 Regents of the University of CaliforniaJul 27 11:09:31 localhost kernel: [4296262.210000] PPP generic driver version 2.4.2
Jul 27 11:09:31 localhost pppd[10238]: pppd 2.4.3 started by root, uid 0
Jul 27 11:09:32 localhost chat[10242]: timeout set to 60 seconds
Jul 27 11:09:32 localhost chat[10242]: abort on (ERROR)
Jul 27 11:09:32 localhost chat[10242]: abort on (BUSY)
Jul 27 11:09:32 localhost chat[10242]: abort on (VOICE)
Jul 27 11:09:32 localhost chat[10242]: abort on (NO CARRIER)
Jul 27 11:09:32 localhost chat[10242]: abort on (NO DIALTONE)
Jul 27 11:09:32 localhost chat[10242]: abort on (NO DIAL TONE)
Jul 27 11:09:32 localhost chat[10242]: abort on (NO ANSWER)
Jul 27 11:09:32 localhost chat[10242]: send (ATZ^M)
Jul 27 11:09:32 localhost chat[10242]: send (AT&FH0L3^M)
Jul 27 11:09:32 localhost chat[10242]: expect (OK)
Jul 27 11:09:32 localhost chat[10242]: HxOK
Jul 27 11:09:32 localhost chat[10242]:  -- got it
Jul 27 11:09:32 localhost chat[10242]: send (ATDT101300^M)
Jul 27 11:09:33 localhost chat[10242]: timeout set to 75 seconds
Jul 27 11:09:33 localhost chat[10242]: expect (CONNECT)
Jul 27 11:09:33 localhost chat[10242]: ^M
Jul 27 11:09:33 localhost chat[10242]: ATZ^M^M
Jul 27 11:09:33 localhost chat[10242]: OK^M
Jul 27 11:10:03 localhost chat[10242]: ATDT101300^M^M
Jul 27 11:10:03 localhost chat[10242]: CONNECT
Jul 27 11:10:03 localhost chat[10242]:  -- got it
Jul 27 11:10:03 localhost pppd[10238]: Serial connection established.
Jul 27 11:10:03 localhost pppd[10238]: Using interface ppp0
Jul 27 11:10:03 localhost pppd[10238]: Connect: ppp0 <--> /dev/ttyS0
Jul 27 11:10:07 localhost pppd[10238]: PAP authentication succeeded
Jul 27 11:10:07 localhost kernel: [4296298.326000] PPP BSD Compression module registered
Jul 27 11:10:07 localhost kernel: [4296298.388000] PPP Deflate Compression module registered
Jul 27 11:10:08 localhost pppd[10238]: Cannot determine ethernet address for proxy ARP
Jul 27 11:10:08 localhost pppd[10238]: local  IP address 124.106.9.141
Jul 27 11:10:08 localhost pppd[10238]: remote IP address 210.213.255.6
Jul 27 11:10:08 localhost pppd[10238]: primary   DNS address 210.14.16.5
Jul 27 11:10:08 localhost pppd[10238]: secondary DNS address 210.14.16.2
Jul 27 11:17:02 localhost /USR/SBIN/CRON[10402]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jul 27 11:22:31 localhost kernel: [4297042.406000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Jul 27 11:22:31 localhost kernel: [4297042.406000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

[SIZE=2][COLOR=Black]Is there any known workarround on mounting any usb hard drive like Lacie?
[/COLOR][/SIZE][/COLOR][/SIZE]

---

### Post by jordilin on 2006-07-26
Ubuntu Dapper, mounts automatically any external usb hard drive when plug it, doesn't matter the type of format. 
And it seems your Os recognizes it:
> Jul 27 11:03:23 localhost kernel: [4295894.058000] scsi4 : SCSI emulation for USB Mass Storage devices
Jul 27 11:03:23 localhost kernel: [4295894.060000] usb-storage: device found at 10
Jul 27 11:03:23 localhost kernel: [4295894.060000] usb-storage: waiting for device to settle before scanning
Jul 27 11:03:23 localhost usb.agent[9587]: usb-storage: already loaded
Jul 27 11:03:28 localhost kernel: [4295899.060000] Vendor: Maxtor 3 Model: 4098H4 Rev: YAH8

---

### Post by .::welemski::. on 2006-07-28
Yes... the os seemed to recognized it but just for a while it then prints this message:
[COLOR=Red]
Jul 27 11:01:40 localhost usbmount[9405]: cannnot execute /sbin/udev_volume_id
Jul 27 11:01:40 localhost usbmount[9443]: cannnot execute /sbin/udev_volume_id[/COLOR]

---

### Post by .::welemski::. on 2006-07-29
The usb drive did not mount... :(

---

### Post by jordilin on 2006-07-29
Firstly, your hard drive what kind of format does it have? Secondly, type
```
uname -r
```
and tell what's the version of your kernel.

---

### Post by hw-tph on 2006-07-29
Check the log again. The assigned name is /dev/sda, so try mounting sda1 instead - the first partition on the device:
```
$sudo mount /dev/sda1 /media/external
```

Håkan

---

### Post by Rovenhot on 2006-07-30
I have a different, related problem, specifically that the HFS+ partition on my flash drive mounts as read-only; I can't modify its contents.  The FAT32 partition mouts normally.  This behavior started after the update to Dapper.

EDIT: I type my 'a's faster than my 'l's, apparently.

---

### Post by .::welemski::. on 2006-07-31
OK... tried mounting /dev/sda1 but I didn't see any of my files, instead it shows 5 files labeled 01-05 and a sixth file called device. Still when I checked the log... I get the same result.

My Hard Drive is a Lacie does it have any issues on mounting a lacie drive? If so maybe I gues I have to buy a new shell for my hard drive.

---

