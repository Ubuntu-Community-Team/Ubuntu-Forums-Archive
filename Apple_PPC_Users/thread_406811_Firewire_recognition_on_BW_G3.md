---
title: "Firewire recognition on B/W G3"
date: 2007-04-11
forum: Apple PPC Users
---

### Post by dllg on 2007-04-11
I have a 350MHZ Blue & White G3.  I have Feisty Fawn installed on an internal drive.  Feisty seems to work great except for not being able to mount my 500 GB external HD (Maxtor OneTouch III).  It sees it in the device manager and all the kernel modules seem to be loaded, but when I plug the external HD in it gives the following error message (I also have the results of lspci and lsmod included):

root@gerber-ubuntu:~# dmesg | tail -n 30
[  687.856120] pcilynx0: SelfID packet 0x817f8cd4 rcvd
[  707.847598] ieee1394: sbp2: Error logging into SBP-2 device - timed out
[  707.850659] sbp2: probe of 0010100300256f7c-0 failed with error -16
[  707.850685] ieee1394: bus_rescan_devices had an error
[  708.125586] scsi3 : SBP-2 IEEE-1394
[  709.135761] pcilynx0: bus reset interrupt
[  709.135941] pcilynx0: SelfID process finished (phyid 1, root)
[  709.135955] pcilynx0: SelfID packet 0x807f8492 rcvd
[  709.135967] pcilynx0: SelfID packet 0x817f8cd4 rcvd
[  729.127439] ieee1394: sbp2: Error logging into SBP-2 device - timed out
[  729.131121] sbp2: probe of 0010100300256f7c-0 failed with error -16
[  729.131147] ieee1394: bus_rescan_devices had an error
[  729.405482] scsi4 : SBP-2 IEEE-1394
[  730.415616] pcilynx0: bus reset interrupt
[  730.415792] pcilynx0: SelfID process finished (phyid 1, root)
[  730.415806] pcilynx0: SelfID packet 0x807f8492 rcvd
[  730.415818] pcilynx0: SelfID packet 0x817f8cd4 rcvd
[  745.555190] pcilynx0: bus reset interrupt
[  745.555236] pcilynx0: SelfID process finished (phyid 0, root)
[  745.555250] pcilynx0: SelfID packet 0x807f8c56 rcvd
[  749.415649] pcilynx0: bus reset interrupt
[  749.415828] pcilynx0: SelfID process finished (phyid 1, root)
[  749.415842] pcilynx0: SelfID packet 0x807fc494 rcvd
[  749.415855] pcilynx0: SelfID packet 0x817f8cd6 rcvd
[  750.407282] ieee1394: sbp2: Error logging into SBP-2 device - timed out
[  750.407643] sbp2: probe of 0010100300256f7c-0 failed with error -16
[  750.407665] ieee1394: bus_rescan_devices had an error
[  750.680928] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0010b92100a0afc0]
[  750.681300] ieee1394: Node suspended: ID:BUS[0-00:1023]
GUID[0010100300256f7c]
[  750.950004] scsi5 : SBP-2 IEEE-1394


root@gerber-ubuntu:~# lspci
00:00.0 Host bridge: Motorola MPC106 [Grackle] (rev 40)
00:0d.0 PCI bridge: Digital Equipment Corporation DECchip 21154 (rev 02)
00:10.0 VGA compatible controller: ATI Technologies Inc Rage 128 RE/SG
01:00.0 FireWire (IEEE 1394): Texas Instruments PCILynx/PCILynx2 IEEE
1394 Link Layer Controller (rev 02)
01:01.0 IDE interface: Silicon Image, Inc. PCI0646 (rev 07)
01:05.0 Class ff00: Apple Computer Inc. Paddington Mac I/O
01:06.0 USB Controller: OPTi Inc. 82C861 (rev 10)


root@gerber-ubuntu:~# lsmod | grep 1394
ieee1394              430800  2 sbp2,pcilynx
root@gerber-ubuntu:~#

---

### Post by sarge84 on 2007-05-07
I have the exact same problem.

I have a 350 mhz B&W G3 and a FireWire external drive and it will not mount.  When I enter dmesg, lspci, and lsmod grep | 1394 my results are exactly the same.

Perhaps someone with a bit more knowledge could shed some light on the situation as I really would prefer to use FireWire over USB 1.1 due to the speed.

---

### Post by macabro22 on 2007-12-22
bump! here is my /var/log/syslog.

Something seems to be wrong with ieee1394

```
Dec 23 00:06:54 localhost syslogd 1.4.1#21ubuntu3: restart.
Dec 23 00:06:54 localhost anacron[6548]: Job `cron.daily' terminated (exit status: 1) (mailing output)
Dec 23 00:06:55 localhost anacron[6548]: Normal exit (1 job run)
Dec 23 00:09:01 localhost /USR/SBIN/CRON[19436]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec 23 00:17:01 localhost /USR/SBIN/CRON[25793]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 23 00:35:50 localhost -- MARK --
Dec 23 00:39:01 localhost /USR/SBIN/CRON[19099]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec 23 00:55:50 localhost -- MARK --
Dec 23 01:00:01 localhost /USR/SBIN/CRON[19274]: (root) CMD (/etc/webmin/bandwidth/rotate.pl)
Dec 23 01:00:02 localhost syslogd 1.4.1#21ubuntu3: restart.
Dec 23 01:02:33 localhost kernel: [ 4053.212619] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Dec 23 01:02:33 localhost kernel: [ 4053.212634] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0010b92100f32fb7]
Dec 23 01:02:50 localhost kernel: [ 4070.556880] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Dec 23 01:02:51 localhost kernel: [ 4071.508030] ieee1394: Error parsing configrom for node 0-00:1023
Dec 23 01:02:51 localhost kernel: [ 4071.508126] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Dec 23 01:02:57 localhost kernel: [ 4077.485300] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[0010b92100f32fb7]
Dec 23 01:09:01 localhost /USR/SBIN/CRON[19379]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec 23 01:11:35 localhost kernel: [ 4594.794369] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
Dec 23 01:11:35 localhost kernel: [ 4594.794377] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
Dec 23 01:11:35 localhost kernel: [ 4594.794385] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
Dec 23 01:11:35 localhost kernel: [ 4594.795074] cs: memory probe 0xb0300000-0xb03fffff: excluding 0xb0300000-0xb030ffff
Dec 23 01:17:01 localhost /USR/SBIN/CRON[19437]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

What to do?

---

### Post by woopud on 2007-12-23
dllg, how did you gt feisty installed on your blue & white ?   I can't get it to boot from the LiveCD, which CD image did you use ?

Bert

---

### Post by macabro22 on 2007-12-24
ok.

Removing and loading the firewire module solves the issue for me. 

Maybe someone should file this as a bug. I don't know how to do that.

```

sudo rmmod ohci1394
sudo modprobe ohci1394
```

---

