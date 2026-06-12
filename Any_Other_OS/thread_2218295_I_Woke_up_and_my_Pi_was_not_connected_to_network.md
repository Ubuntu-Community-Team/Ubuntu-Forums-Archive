---
title: "I Woke up and my Pi was not connected to network"
date: 2014-04-20
forum: Any Other OS
---

### Post by pqwoerituytrueiwoq on 2014-04-20
What I need to know is was this a error on my Pi server or my router
I have my Pi setup as a headless server
i unplugged the cable and plugged it back in and it came back online
this was in the dmesg output
```
[   20.370680] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[211963.452286] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[211963.452369] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[211963.452405] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[211963.452438] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[211963.452468] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[211963.452497] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[211963.452526] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[211963.452556] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[211963.452585] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[211963.452613] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[216468.455037] smsc95xx 1-1.1:1.0 eth0: link down
[216470.035423] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[216474.392324] net_ratelimit: 1840 callbacks suppressed
[216474.392369] smsc95xx 1-1.1:1.0 eth0: kevent 4 may have been dropped
[216474.397943] smsc95xx 1-1.1:1.0 eth0: link down
[216475.975229] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[262088.287234] usb 1-1.1: USB disconnect, device number 3
[262088.287684] smsc95xx 1-1.1:1.0 eth0: unregister 'smsc95xx' usb-bcm2708_usb-1.1, smsc95xx USB 2.0 Ethernet
[262088.287747] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[262088.320192] Indeed it is in host mode hprt0 = 00001101
[262088.549435] usb 1-1: reset high-speed USB device number 2 using dwc_otg
[262088.549636] Indeed it is in host mode hprt0 = 00001101
[262089.217044] usb 1-1.1: new high-speed USB device number 4 using dwc_otg
[262089.497356] usb 1-1.1: New USB device found, idVendor=0424, idProduct=ec00
[262089.497393] usb 1-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[262089.500694] smsc95xx v1.0.4
[262089.603839] smsc95xx 1-1.1:1.0 eth0: register 'smsc95xx' at usb-bcm2708_usb-1.1, smsc95xx USB 2.0 Ethernet, b8:27:eb:a2:68:54
[262089.873916] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[262091.731771] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[284635.970765] smsc95xx 1-1.1:1.0 eth0: link down
[284646.504119] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[284646.620721] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[284658.452063] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
```
anyone know a way to find out what time it disconnected?

---

### Post by tomearp on 2014-04-20
```
dmesg -T
```
will display human-readable timestamps

---

### Post by tgalati4 on 2014-04-20
RaspberryPi's are sensitive to power level and if you had a mini power outage or voltage drop, that would be enough to disrupt it.  Dmesg time is time from boot in seconds so drag out the calculator and divide 216468.455037 by 3600 to get minutes from boot.  In your case 60 hours from boot.  Any other devices in the house that show evidence of power outage?

Some Pi blogs recommend putting some large capacitors (called bypass capacitors) to buffer the 5VDC power level and use a 2 amp source not the 1 amp source recommended--which is 4X what a USB port typically provides for power.

---

### Post by pqwoerituytrueiwoq on 2014-04-20
thanks for that -T option, no idea when i booted it
```
[Thu Apr 17 03:54:25 2014] smsc95xx v1.0.4
[Thu Apr 17 03:54:25 2014] smsc95xx 1-1.1:1.0 eth0: register 'smsc95xx' at usb-bcm2708_usb-1.1, smsc95xx USB 2.0 Ethernet, b8:27:eb:a2:68:54
[Thu Apr 17 03:54:25 2014] udevd[156]: starting version 175
[Thu Apr 17 03:54:28 2014] bcm2708-i2s bcm2708-i2s.0: Failed to create debugfs directory
[Thu Apr 17 03:54:31 2014] EXT4-fs (mmcblk0p2): re-mounted. Opts: (null)
[Thu Apr 17 03:54:32 2014] EXT4-fs (mmcblk0p2): re-mounted. Opts: (null)
[Thu Apr 17 03:54:38 2014] FAT-fs (mmcblk0p1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[Thu Apr 17 03:54:38 2014] EXT4-fs (mmcblk0p3): mounting ext2 file system using the ext4 subsystem
[Thu Apr 17 03:54:38 2014] EXT4-fs (mmcblk0p3): mounted filesystem without journal. Opts: (null)
[Thu Apr 17 03:54:40 2014] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[Thu Apr 17 03:54:42 2014] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[Sat Apr 19 14:47:05 2014] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[Sat Apr 19 14:47:05 2014] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[Sat Apr 19 14:47:05 2014] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[Sat Apr 19 14:47:05 2014] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[Sat Apr 19 14:47:05 2014] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[Sat Apr 19 14:47:05 2014] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[Sat Apr 19 14:47:05 2014] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[Sat Apr 19 14:47:05 2014] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[Sat Apr 19 14:47:05 2014] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[Sat Apr 19 14:47:05 2014] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
[Sat Apr 19 16:02:10 2014] smsc95xx 1-1.1:1.0 eth0: link down
[Sat Apr 19 16:02:12 2014] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[Sat Apr 19 16:02:16 2014] net_ratelimit: 1840 callbacks suppressed
[Sat Apr 19 16:02:16 2014] smsc95xx 1-1.1:1.0 eth0: kevent 4 may have been dropped
[Sat Apr 19 16:02:16 2014] smsc95xx 1-1.1:1.0 eth0: link down
[Sat Apr 19 16:02:17 2014] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[Sun Apr 20 04:42:30 2014] usb 1-1.1: USB disconnect, device number 3
[Sun Apr 20 04:42:30 2014] smsc95xx 1-1.1:1.0 eth0: unregister 'smsc95xx' usb-bcm2708_usb-1.1, smsc95xx USB 2.0 Ethernet
[Sun Apr 20 04:42:30 2014] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[Sun Apr 20 04:42:30 2014] Indeed it is in host mode hprt0 = 00001101
[Sun Apr 20 04:42:30 2014] usb 1-1: reset high-speed USB device number 2 using dwc_otg
[Sun Apr 20 04:42:30 2014] Indeed it is in host mode hprt0 = 00001101
[Sun Apr 20 04:42:31 2014] usb 1-1.1: new high-speed USB device number 4 using dwc_otg
[Sun Apr 20 04:42:31 2014] usb 1-1.1: New USB device found, idVendor=0424, idProduct=ec00
[Sun Apr 20 04:42:31 2014] usb 1-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[Sun Apr 20 04:42:31 2014] smsc95xx v1.0.4
[Sun Apr 20 04:42:31 2014] smsc95xx 1-1.1:1.0 eth0: register 'smsc95xx' at usb-bcm2708_usb-1.1, smsc95xx USB 2.0 Ethernet, b8:27:eb:a2:68:54
[Sun Apr 20 04:42:31 2014] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[Sun Apr 20 04:42:33 2014] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[Sun Apr 20 10:58:17 2014] smsc95xx 1-1.1:1.0 eth0: link down
[Sun Apr 20 10:58:28 2014] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[Sun Apr 20 10:58:28 2014] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[Sun Apr 20 10:58:40 2014] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
```
looks like it went down at Sun Apr 20 04:42:33 2014, which would be about midnight, seems i need to set the time zone
[edit]the time was +4hrs, i have fixed the time issue[/edit]

low voltage is possible, i am using a single USB port on my desktop (modular seasonic 520W -> M4A79XTD Evo -> Pi)
i am using a USB HDD cable for power, as my 1.8amp PSU never arrived...

[edit]
```
pi@raspberrypi:~$ cat /var/log/syslog.1
Apr 19 06:25:06 raspberrypi rsyslogd: [origin software="rsyslogd" swVersion="5.8.11" x-pid="1892" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Apr 19 06:39:01 raspberrypi /USR/SBIN/CRON[5045]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 07:09:01 raspberrypi /USR/SBIN/CRON[5052]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 07:17:01 raspberrypi /USR/SBIN/CRON[5060]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 07:39:01 raspberrypi /USR/SBIN/CRON[5068]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 08:09:01 raspberrypi /USR/SBIN/CRON[5075]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 08:17:01 raspberrypi /USR/SBIN/CRON[5082]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 08:39:01 raspberrypi /USR/SBIN/CRON[5089]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 09:09:01 raspberrypi /USR/SBIN/CRON[5096]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 09:17:01 raspberrypi /USR/SBIN/CRON[5103]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 09:39:01 raspberrypi /USR/SBIN/CRON[5110]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 10:09:01 raspberrypi /USR/SBIN/CRON[5117]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 10:17:01 raspberrypi /USR/SBIN/CRON[5124]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 10:39:01 raspberrypi /USR/SBIN/CRON[5131]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 11:09:01 raspberrypi /USR/SBIN/CRON[5138]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 11:17:01 raspberrypi /USR/SBIN/CRON[5145]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 11:39:01 raspberrypi /USR/SBIN/CRON[5152]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 12:09:01 raspberrypi /USR/SBIN/CRON[5159]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 12:17:01 raspberrypi /USR/SBIN/CRON[5166]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 12:39:01 raspberrypi /USR/SBIN/CRON[5173]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 13:09:01 raspberrypi /USR/SBIN/CRON[5180]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 13:17:01 raspberrypi /USR/SBIN/CRON[5187]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 13:39:01 raspberrypi /USR/SBIN/CRON[5354]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 14:09:01 raspberrypi /USR/SBIN/CRON[5689]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 14:17:01 raspberrypi /USR/SBIN/CRON[5706]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 14:39:01 raspberrypi /USR/SBIN/CRON[5798]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 14:46:58 raspberrypi kernel: [211963.452286] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
Apr 19 14:46:58 raspberrypi kernel: [211963.452369] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
Apr 19 14:46:58 raspberrypi kernel: [211963.452405] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
Apr 19 14:46:58 raspberrypi kernel: [211963.452438] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
Apr 19 14:46:58 raspberrypi kernel: [211963.452468] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
Apr 19 14:46:58 raspberrypi kernel: [211963.452497] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
Apr 19 14:46:58 raspberrypi kernel: [211963.452526] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
Apr 19 14:46:58 raspberrypi kernel: [211963.452556] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
Apr 19 14:46:58 raspberrypi kernel: [211963.452585] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
Apr 19 14:46:58 raspberrypi kernel: [211963.452613] smsc95xx 1-1.1:1.0 eth0: kevent 2 may have been dropped
Apr 19 15:09:01 raspberrypi /USR/SBIN/CRON[5941]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 15:17:01 raspberrypi /USR/SBIN/CRON[5948]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 15:39:01 raspberrypi /USR/SBIN/CRON[5956]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 16:02:03 raspberrypi kernel: [216468.455037] smsc95xx 1-1.1:1.0 eth0: link down
Apr 19 16:02:03 raspberrypi ifplugd(eth0)[1555]: Link beat lost.
Apr 19 16:02:05 raspberrypi kernel: [216470.035423] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
Apr 19 16:02:05 raspberrypi ifplugd(eth0)[1555]: Link beat detected.
Apr 19 16:02:09 raspberrypi kernel: [216474.392324] net_ratelimit: 1840 callbacks suppressed
Apr 19 16:02:09 raspberrypi kernel: [216474.392369] smsc95xx 1-1.1:1.0 eth0: kevent 4 may have been dropped
Apr 19 16:02:09 raspberrypi kernel: [216474.397943] smsc95xx 1-1.1:1.0 eth0: link down
Apr 19 16:02:10 raspberrypi ifplugd(eth0)[1555]: Link beat lost.
Apr 19 16:02:11 raspberrypi kernel: [216475.975229] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
Apr 19 16:02:11 raspberrypi ifplugd(eth0)[1555]: Link beat detected.
Apr 19 16:09:01 raspberrypi /USR/SBIN/CRON[5965]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 16:17:01 raspberrypi /USR/SBIN/CRON[5978]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 16:39:01 raspberrypi /USR/SBIN/CRON[6112]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 17:09:01 raspberrypi /USR/SBIN/CRON[6439]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 17:17:01 raspberrypi /USR/SBIN/CRON[6450]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 17:39:01 raspberrypi /USR/SBIN/CRON[6469]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 18:09:01 raspberrypi /USR/SBIN/CRON[6477]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 18:17:01 raspberrypi /USR/SBIN/CRON[6484]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 18:39:01 raspberrypi /USR/SBIN/CRON[6492]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 19:09:01 raspberrypi /USR/SBIN/CRON[6522]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 19:17:01 raspberrypi /USR/SBIN/CRON[6618]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 19:39:01 raspberrypi /USR/SBIN/CRON[6626]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 20:09:01 raspberrypi /USR/SBIN/CRON[6633]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 20:17:01 raspberrypi /USR/SBIN/CRON[6640]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 20:39:01 raspberrypi /USR/SBIN/CRON[6647]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 21:09:01 raspberrypi /USR/SBIN/CRON[6654]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 21:17:01 raspberrypi /USR/SBIN/CRON[6662]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 21:39:01 raspberrypi /USR/SBIN/CRON[6669]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 22:09:01 raspberrypi /USR/SBIN/CRON[6676]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 22:17:01 raspberrypi /USR/SBIN/CRON[6684]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 22:39:01 raspberrypi /USR/SBIN/CRON[6691]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 23:09:01 raspberrypi /USR/SBIN/CRON[6698]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 19 23:17:01 raspberrypi /USR/SBIN/CRON[6705]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 23:39:01 raspberrypi /USR/SBIN/CRON[6712]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 20 00:09:01 raspberrypi /USR/SBIN/CRON[6779]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 20 00:17:01 raspberrypi /USR/SBIN/CRON[6786]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 20 00:39:01 raspberrypi /USR/SBIN/CRON[6818]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 20 01:09:01 raspberrypi /USR/SBIN/CRON[6826]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 20 01:17:01 raspberrypi /USR/SBIN/CRON[6833]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 20 01:39:01 raspberrypi /USR/SBIN/CRON[6840]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 20 02:09:01 raspberrypi /USR/SBIN/CRON[6847]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 20 02:17:01 raspberrypi /USR/SBIN/CRON[6854]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 20 02:39:01 raspberrypi /USR/SBIN/CRON[6862]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 20 03:09:01 raspberrypi /USR/SBIN/CRON[6873]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 20 03:17:01 raspberrypi /USR/SBIN/CRON[6900]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 20 03:39:02 raspberrypi /USR/SBIN/CRON[6919]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 20 04:09:01 raspberrypi /USR/SBIN/CRON[6983]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 20 04:17:01 raspberrypi /USR/SBIN/CRON[6990]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 20 04:39:01 raspberrypi /USR/SBIN/CRON[6997]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 20 04:42:21 raspberrypi kernel: [262088.287234] usb 1-1.1: USB disconnect, device number 3
Apr 20 04:42:21 raspberrypi kernel: [262088.287684] smsc95xx 1-1.1:1.0 eth0: unregister 'smsc95xx' usb-bcm2708_usb-1.1, smsc95xx USB 2.0 Ethernet
Apr 20 04:42:21 raspberrypi kernel: [262088.287747] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
Apr 20 04:42:21 raspberrypi kernel: [262088.320192] Indeed it is in host mode hprt0 = 00001101
Apr 20 04:42:22 raspberrypi kernel: [262088.549435] usb 1-1: reset high-speed USB device number 2 using dwc_otg
Apr 20 04:42:22 raspberrypi kernel: [262088.549636] Indeed it is in host mode hprt0 = 00001101
Apr 20 04:42:22 raspberrypi ifplugd(eth0)[1555]: Link beat lost.
Apr 20 04:42:22 raspberrypi ifplugd(eth0)[1555]: Exiting.
Apr 20 04:42:22 raspberrypi kernel: [262089.217044] usb 1-1.1: new high-speed USB device number 4 using dwc_otg
Apr 20 04:42:22 raspberrypi kernel: [262089.497356] usb 1-1.1: New USB device found, idVendor=0424, idProduct=ec00
Apr 20 04:42:22 raspberrypi kernel: [262089.497393] usb 1-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Apr 20 04:42:22 raspberrypi kernel: [262089.500694] smsc95xx v1.0.4
Apr 20 04:42:23 raspberrypi ntpd[2072]: Deleting interface #2 eth0, 10.0.0.25#123, interface stats: received=1292, sent=1300, dropped=0, active_time=262050 secs
Apr 20 04:42:23 raspberrypi ntpd[2072]: 108.61.73.243 interface 10.0.0.25 -> (none)
Apr 20 04:42:23 raspberrypi ntpd[2072]: 24.4.62.1 interface 10.0.0.25 -> (none)
Apr 20 04:42:23 raspberrypi ntpd[2072]: 23.253.213.220 interface 10.0.0.25 -> (none)
Apr 20 04:42:23 raspberrypi ntpd[2072]: 23.92.26.57 interface 10.0.0.25 -> (none)
Apr 20 04:42:23 raspberrypi ntpd[2072]: peers refreshed
Apr 20 04:42:23 raspberrypi kernel: [262089.603839] smsc95xx 1-1.1:1.0 eth0: register 'smsc95xx' at usb-bcm2708_usb-1.1, smsc95xx USB 2.0 Ethernet, b8:27:eb:a2:68:54
Apr 20 04:42:23 raspberrypi ifplugd(eth0)[7066]: ifplugd 0.28 initializing.
Apr 20 04:42:23 raspberrypi ifplugd(eth0)[7066]: Using interface eth0/B8:27:EB:A2:68:54 with driver <smsc95xx> (version: 22-Aug-2005)
Apr 20 04:42:23 raspberrypi ifplugd(eth0)[7066]: Using detection mode: SIOCETHTOOL
Apr 20 04:42:23 raspberrypi ifplugd(eth0)[7066]: Initialization complete, link beat not detected.
Apr 20 04:42:23 raspberrypi kernel: [262089.873916] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
Apr 20 04:42:25 raspberrypi kernel: [262091.731771] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
Apr 20 04:42:25 raspberrypi ifplugd(eth0)[7066]: Link beat detected.
Apr 20 04:42:25 raspberrypi ifplugd(eth0)[7066]: Executing '/etc/ifplugd/ifplugd.action eth0 up'.
Apr 20 04:42:25 raspberrypi ifplugd(eth0)[7066]: client: /sbin/ifup: interface eth0 already configured
Apr 20 04:42:25 raspberrypi ifplugd(eth0)[7066]: Program executed successfully.
Apr 20 05:09:01 raspberrypi /USR/SBIN/CRON[7077]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 20 05:17:01 raspberrypi /USR/SBIN/CRON[7084]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 20 05:39:01 raspberrypi /USR/SBIN/CRON[7091]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 20 06:09:01 raspberrypi /USR/SBIN/CRON[7098]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Apr 20 06:17:01 raspberrypi /USR/SBIN/CRON[7105]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 20 06:25:01 raspberrypi /USR/SBIN/CRON[7112]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
```[/edit]

---

### Post by tomearp on 2014-04-20
I would definitely recommend running the Pi off its own supply rather than from a USB port. I have a few Pis and have experienced issues trying to run them off USB ports.

Plugging USB peripherals into a Pi has also caused me problems in the past. I have a particularly power hungry Dell USB keyboard that will either make a Pi hang or cause weird behaviours (repeated keystrokes etc) unless connected through a separately powered USB hub.

I don't bother trying to run them off other things anymore, dedicated supplies all the way.

---

### Post by pqwoerituytrueiwoq on 2014-04-20
I am not using any usb equipment with my pi, just the etherent, unless you count the power input

---

### Post by tomearp on 2014-04-20
From the [RasPi site]("http://www.raspberrypi.org/help/faqs/#powerReqs"):
Model B uses 0.7 - 1.0 Amps @ 5V, Model A with no peripherals can be as low as 0.5 A @ 5V.

From the [USB page on Wikipedia]("http://en.m.wikipedia.org/wiki/USB") the following current limits are given for USB ports:
USB 1.0 - 0.15 Amps
USB 2.0 - 0.5 amps
Other (USB 3 etc...) - varies

So USB 1.0 ports cannot deliver the required power, USB 2.0 ports might power a Model A with no peripherals, 'other' ports might deliver enough.

TL;DR - use an external power supply and enjoy trouble-free operation.

---

### Post by pqwoerituytrueiwoq on 2014-04-20
i probably should get a molex power brick so i can power addition hardware controlled by relays
i think it may have been the GPIO switch that put it over the limit as it has ran without issue before i added that and had it on

i have no monitor so i am not using the GPU, that is probably how i was able to power it this long

---

### Post by pqwoerituytrueiwoq on 2014-04-28
well it is not a power issue, i got it more power and it has happened twice, but reconnecting the network cable does nothing
it how has a full amp of regulated power at its disposal, voltage test at the pi shows 5.07 to 5.1v (5.09-5.10 is the usual)
highest observed core temp is 48C

This seems to have some connection to mpd (music player daemon) until i had that running (by which i mean playing) it never acted up once
mpd is still working (playing) and accepting commands after the nic is down (controlled via toggle switch)
going to try using the analog video output next time i can make it happen to try to get more info

---

### Post by tomearp on 2014-04-30
I haven't used the desktop much in recent versions of raspbian, I tend to use SSH for doing things. 

In early versions there was a CPU graph in the bottom right corner. I would be interested to see if something is maxing out the CPU or causing persistent high usage.

---

### Post by pqwoerituytrueiwoq on 2014-04-30
my pi runs heedlessly
i cant ssh in to fix the eth0 being down as eth0 need to be working to use ssh
```
[Wed Apr 30 11:03:57 2014] usb 1-1.1: USB disconnect, device number 3
[Wed Apr 30 11:03:57 2014] smsc95xx 1-1.1:1.0 eth0: unregister 'smsc95xx' usb-bcm2708_usb-1.1, smsc95xx USB 2.0 Ethernet
[Wed Apr 30 11:03:57 2014] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[Wed Apr 30 11:03:57 2014] Indeed it is in host mode hprt0 = 00001101
[Wed Apr 30 11:03:57 2014] usb 1-1: reset high-speed USB device number 2 using dwc_otg
[Wed Apr 30 11:03:57 2014] Indeed it is in host mode hprt0 = 00001101
[Wed Apr 30 11:03:58 2014] usb 1-1.1: new high-speed USB device number 4 using dwc_otg
[Wed Apr 30 11:03:58 2014] usb 1-1.1: New USB device found, idVendor=0424, idProduct=ec00
[Wed Apr 30 11:03:58 2014] usb 1-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[Wed Apr 30 11:03:58 2014] smsc95xx v1.0.4
[Wed Apr 30 11:03:59 2014] smsc95xx 1-1.1:1.0 eth0: register 'smsc95xx' at usb-bcm2708_usb-1.1, smsc95xx USB 2.0 Ethernet, b8:27:eb:a2:68:54
[Wed Apr 30 11:03:59 2014] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[Wed Apr 30 11:04:00 2014] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[Wed Apr 30 11:04:00 2014] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
```
I managed to hook up a old school av cable/keyboard to trouble shoot it this time
i got it working again with [FONT=courier new]ifup eth0[/FONT]
i then made this script a root cron job that runs every minute
```
#!/bin/sh
checkNIC(){
    echo $(/sbin/ifconfig "$nic" | grep 10.0.0.25 | wc -l)
}
fixNIC(){
    echo "Attempting to fix NIC"
    /usr/sbin/service networking restart
    sleep 2
    echo "Attempting to configure $nic"
    /sbin/ifup "$nic"
    echo "Attempt Complete"
    sleep 13
}
nic="eth0"
if [ $(checkNIC) -ne 1 ];then
    log="/var/log/fixnic"
    if [ -f "$log.stop" ];then
        exit
    fi
    echo "BEGIN------$(date)------" >> "$log"
    dmesg -T | tail -15 >> "$log"
    echo "---------------------------------------------" >> "$log"
    mpc >> "$log"
    echo "END------------------------------------------" >> "$log"
    echo "$(fixNIC)" >> "$log"
    if [ $(checkNIC) -ne 1 ];then
        echo "---TRY_2---" >> "$log"
        /usr/sbin/service networking start >> "$log"
        echo "$(fixNIC)" >> "$log"
        if [ $(checkNIC) -ne 1 ];then
            touch "$log.stop"
        fi
    fi
fi
```

---

### Post by pqwoerituytrueiwoq on 2014-04-30
duplicate post, browser cache tricked me

---

### Post by pqwoerituytrueiwoq on 2014-05-01
my script manged to grab this
```
BEGIN------Thu May  1 07:02:01 EDT 2014------
[Wed Apr 30 12:03:11 2014] usb 1-1.3: USB disconnect, device number 5
[Wed Apr 30 12:03:11 2014] usb 1-1.3.4: USB disconnect, device number 6
[Thu May  1 07:01:35 2014] usb 1-1.1: USB disconnect, device number 4
[Thu May  1 07:01:35 2014] smsc95xx 1-1.1:1.0 eth0: unregister 'smsc95xx' usb-bcm2708_usb-1.1, smsc95xx USB 2.0 Ethernet
[Thu May  1 07:01:35 2014] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[Thu May  1 07:01:35 2014] Indeed it is in host mode hprt0 = 00001101
[Thu May  1 07:01:35 2014] usb 1-1: reset high-speed USB device number 2 using dwc_otg
[Thu May  1 07:01:35 2014] Indeed it is in host mode hprt0 = 00001101
[Thu May  1 07:01:36 2014] usb 1-1.1: new high-speed USB device number 7 using dwc_otg
[Thu May  1 07:01:36 2014] usb 1-1.1: New USB device found, idVendor=0424, idProduct=ec00
[Thu May  1 07:01:36 2014] usb 1-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[Thu May  1 07:01:36 2014] smsc95xx v1.0.4
[Thu May  1 07:01:37 2014] smsc95xx 1-1.1:1.0 eth0: register 'smsc95xx' at usb-bcm2708_usb-1.1, smsc95xx USB 2.0 Ethernet, b8:27:eb:a2:68:54
[Thu May  1 07:01:37 2014] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[Thu May  1 07:01:39 2014] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
END------------------------------------------
```

---

### Post by widi2 on 2014-05-01
Slightly off topic, but the distro in question is not Debian. It's Raspbian, unless you flashed an image of Debian itself, obtained from debian.org.

---

### Post by pqwoerituytrueiwoq on 2014-05-01
> **widi2 said:**
> Slightly off topic, but the distro in question is not Debian. It's Raspbian, unless you flashed an image of Debian itself, obtained from debian.org.
true, it is Raspbian
debian was a prefix option and Raspbian is not, figured debian would be close enough, lol

---

### Post by tgalati4 on 2014-05-01
It seems like an ethernet chip problem.  As I recall, the ethernet chip on the PI is shared with the USB controller and is not very robust.  Put your finger on the chip and feel how warm it is.  It could be failing.  Some PI's are made better than others.  What country manufactured yours?

I've seen demos of Pi's running 3D, 1080i movies using XBMC, so I know that the graphics can handle it, but I don't know if the movies were streamed or simply stored on the SD card.  With a 100 MB/sec NIC, I doubt there is enough bandwidth.  For music, 100 MB/sec is generally enough, but if your network traffic is heavy, then there could be dropouts and it's possible that the NIC driver needs tuning to handle it.  Or the chip is failing.

---

### Post by pqwoerituytrueiwoq on 2014-05-01
The CPU is under 50C, have never seen over 48C
mpd is playing files stored on the sd card
My PI was made in the UK

i have tried to see bring the NIC down from high use and gave up after 6 hours of continuously running iperf in a loop
Surface temps:
The chip near the NIC measures at about 43C
the large cip in the middle measures at 37C
the voltage regulator measures at 40C

until i had it run mpd it never crashed (about 5 days of uptime)
when i had it run over night a couple times it when down the second time

If it is a temperature problem i will find out tomorrow, i have a 80mm fan cooling it, core temps is down 10C as a result

i really doubt it is a high network load causing it to go down, usage should have been idle at that time
mpd may be using the loopback address, i am not sure how it works i just know it continues running when the network goes down
it is running owncloud (only me using it and all computers except the PI were off)
it is running SSH and apt-cache-ng and apt-cache-ng was not receiving any request
the only thing i can see as a cause is mpd playing over the analog audio output
when i thought the issue was a lack of power i stopped playing mpd (it was in the paused state) and the crashes stopped, i got more power and used mpd playback and it crashed the 1st night
idk why mpd would cause eth0 to fail or cause anything to fail while not interrupting itself

---

### Post by tgalati4 on 2014-05-02
Do some research on the analog sound.  It's possible that the sound chip is also on the same die as the USB and NIC.  That means playing audio with mpd will cause that chip to get doubly hot.  If you are just playing files locally from the SD and not streaming then use *mocp*.  I would only run mpd if you are streaming your tracks to other computers as a server, not as a media player.

moc - ncurses based console audio player
moc-ffmpeg-plugin - ncurses based console audio player - ffmpeg plugin

What are the CPU loads when idle?

---

### Post by pqwoerituytrueiwoq on 2014-05-02
on idle if i don't count top 1.5%
mpd uses 8.9% when playing
only other thing that really uses cpu is apache2

i had my 80mm fan keeping it super cool last night and it ran until the power went out for about 3 seconds at about 10:30 am, nothing crashed
how ever i upgraded my surge protector and got the speaker system on a surge protector last night also

i deiced to have it also be a media player since it was syncing my music via owncloud so it already had the audio files on the disk

the chip near the usb ports is the usb controller right? perhaps i should just slap a beefy heat sync on it (edit: yes it is and it is specked to handle 70C, unless it is defective it should not a thermal issue)

i should probably point out the times it did go down mpd would have been the only thing using and resources
by only i mean only, no video, no usb, no net activity

does moc have shuffle, repeat, replay gain and have a service user name?
i added www-data to the mpd group so it could read the music files in my owncloud folder

---

### Post by tgalati4 on 2014-05-02
moc handles shuffle and repeat, but I don't know about replay gain.  I'm not sure what server user name is.  Moc has been around a long time and if useful for low resource machines.  It's possible that your owncloud instance is causing network issues.  Try turning it off and run mpd for several days and see if the network connection remains stable.

---

### Post by pqwoerituytrueiwoq on 2014-05-02
i have gone several days (at least 5) without mpd running and everything else i use running without issue (and that was on a measly 500mA of juice)
unless mpd is the straw that broke the camels back i dont see that making a difference
but moc does have it's own user like mpd does? it runs as a service right not just a user application (for example apache2 runs as a service while gmusicbrowser is a user app)

---

### Post by pqwoerituytrueiwoq on 2014-05-03
cooling is not the issue, had it 5C below normal idle and it crashed
```
BEGIN------Sat May  3 07:48:01 EDT 2014------
[Fri May  2 17:18:28 2014] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[Fri May  2 17:18:29 2014] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[Sat May  3 07:47:08 2014] usb 1-1.1: USB disconnect, device number 3
[Sat May  3 07:47:08 2014] smsc95xx 1-1.1:1.0 eth0: unregister 'smsc95xx' usb-bcm2708_usb-1.1, smsc95xx USB 2.0 Ethernet
[Sat May  3 07:47:08 2014] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[Sat May  3 07:47:08 2014] Indeed it is in host mode hprt0 = 00001101
[Sat May  3 07:47:08 2014] usb 1-1: reset high-speed USB device number 2 using dwc_otg
[Sat May  3 07:47:08 2014] Indeed it is in host mode hprt0 = 00001101
[Sat May  3 07:47:09 2014] usb 1-1.1: new high-speed USB device number 4 using dwc_otg
[Sat May  3 07:47:09 2014] usb 1-1.1: New USB device found, idVendor=0424, idProduct=ec00
[Sat May  3 07:47:09 2014] usb 1-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[Sat May  3 07:47:09 2014] smsc95xx v1.0.4
[Sat May  3 07:47:09 2014] smsc95xx 1-1.1:1.0 eth0: register 'smsc95xx' at usb-bcm2708_usb-1.1, smsc95xx USB 2.0 Ethernet, b8:27:eb:a2:68:54
[Sat May  3 07:47:09 2014] smsc95xx 1-1.1:1.0 eth0: hardware isn't capable of remote wakeup
[Sat May  3 07:47:11 2014] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
---------------------------------------------
```

---

### Post by pqwoerituytrueiwoq on 2014-05-07
Looks like it was a kernel issue, seems to be fixed in the 3.12.18+ kernel that i got via the rpi-update command (if it does not crash by tomorrow i will mark this as as solved)

---

