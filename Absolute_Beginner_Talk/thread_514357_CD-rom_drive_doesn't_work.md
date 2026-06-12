---
title: "CD-rom drive doesn't work"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by purplearcanist on 2007-07-31
The cd-rom drive on my Ubuntu dell inspiron 1420 doesn't work.  Yesterday it worked.  Today, the cdrom doesn't display on the desktop, even though it responds when booting.

Here is my /etc/fstab/ in case this helps (i modified the last two lines).

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9beec4c3-bb5f-49cc-aa41-c945dd977217 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2630afb1-5048-4b57-b997-30ce75f12142 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto    0       0
UUID=c3e75511-0261-4c4a-8284-7c258dfc8e27  /boot ext3 defaults 0 0
# 1002 is the USB group
none /proc/bus/usb usbfs devgid=1002,devmode=666 0 0

---

### Post by lisati on 2007-07-31
The best thing I can think of to ask at the moment is this: Is it due for a cleaning of the laser lens?

---

### Post by purplearcanist on 2007-07-31
no. I checked the laser lens, it is clean.

---

### Post by purplearcanist on 2007-08-01
tap

---

### Post by asmoore82 on 2007-08-01
is there a disc in the drive?

---

### Post by purplearcanist on 2007-08-01
The disc icon doesn't show up even when there is a disc in the drive.

---

### Post by asmoore82 on 2007-08-01
immediately after putting a disc in the drive and waiting for it to settle
run in terminal ...

```
~ $ dmesg | tail -n 20
```
and post

---

### Post by purplearcanist on 2007-08-01
dmesg | tail -n 20
[   97.500000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[   97.500000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[   97.508000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
[   97.508000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[   97.816000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
[   97.816000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
[   97.884000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[  113.436000] eth1: no IPv6 routers present
[ 4417.624000] ata1.00: exception Emask 0x2 SAct 0x10000 SErr 0x0 action 0x2 frozen
[ 4417.624000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x10000 FIS=004040a1:00000008)
[ 4417.624000] ata1.00: cmd 61/02:80:b4:22:f7/00:00:0b:00:00/40 tag 16 cdb 0x0 data 1024 out
[ 4417.624000]          res 40/00:80:b4:22:f7/00:00:0b:00:00/40 Emask 0x2 (HSM violation)
[ 4417.932000] ata1: soft resetting port
[ 4418.104000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 4418.104000] ata1.00: configured for UDMA/133
[ 4418.104000] ata1: EH complete
[ 4418.108000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 4418.108000] sd 0:0:0:0: [sda] Write Protect is off
[ 4418.108000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 4418.108000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by apswartz on 2007-08-01
You have tried other CDs?

---

### Post by purplearcanist on 2007-08-01
I have tried several different CDs.  None of them work.

---

### Post by apswartz on 2007-08-01
Can you boot a LiveCD?

---

### Post by purplearcanist on 2007-08-02
I need more help.
tap

---

### Post by apswartz on 2007-08-02
purplearcanist,
The reason I asked about booting from a LiveCD was to help see if it is a hardware issue or a software issue. If you cannot boot from a LiveCD it is probably hardware related. If the boot from a LiveCD works, it is probably related to the software.

---

### Post by purplearcanist on 2007-08-02
Sorry, I didn't see that post.

Anyway, to answer your question, I can boot from the live cd.

Just so you know, this problem occurs on gusty.

---

### Post by apswartz on 2007-08-02
All this mounting business is much more complicated then it used to be whe you had to mount these things manually!

What is the contents of your /etc/fstab.pre-uuid file.
```
cat /etc/fstab.pre-uuid
```

Also, after you try to read a cd, give us the contents of the following command...
```
 tail -25 /var/log/messages 
```

---

### Post by apswartz on 2007-08-02
> **purplearcanist said:**
> Just so you know, this problem occurs on gusty.

Oh, maybe you need to ask this on the Gutsy forum.

---

### Post by purplearcanist on 2007-08-02
cat /etc/fstab.pre-uuid
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4adbefdc-53c3-4c23-804b-d4237965f0f9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=68b5b06c-0944-5594-d7fb-6ea16a5f7fbf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
# UNCONFIGURED FSTAB FOR BASE SYSTEM


tail -25 /var/log/messages
Aug  2 11:02:54 dell kernel: [   43.704000] NET: Registered protocol family 31
Aug  2 11:02:54 dell kernel: [   43.704000] Bluetooth: HCI device and connection manager initialized
Aug  2 11:02:54 dell kernel: [   43.704000] Bluetooth: HCI socket layer initialized
Aug  2 11:02:54 dell kernel: [   43.724000] Bluetooth: L2CAP ver 2.8
Aug  2 11:02:54 dell kernel: [   43.724000] Bluetooth: L2CAP socket layer initialized
Aug  2 11:02:55 dell kernel: [   44.000000] Bluetooth: RFCOMM socket layer initialized
Aug  2 11:02:55 dell kernel: [   44.000000] Bluetooth: RFCOMM TTY layer initialized
Aug  2 11:02:55 dell kernel: [   44.000000] Bluetooth: RFCOMM ver 1.8
Aug  2 11:03:09 dell kernel: [   58.456000] NET: Registered protocol family 10
Aug  2 11:03:09 dell kernel: [   58.456000] lo: Disabled Privacy Extensions
Aug  2 11:03:09 dell kernel: [   58.456000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  2 11:03:25 dell dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Aug  2 11:04:07 dell kernel: [  116.608000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Aug  2 11:04:07 dell kernel: [  116.608000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Aug  2 11:04:07 dell kernel: [  116.612000] Kill switch must be turned off for wireless networking to work.
Aug  2 11:04:08 dell kernel: [  117.516000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Aug  2 11:04:08 dell kernel: [  117.516000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Aug  2 11:04:08 dell kernel: [  117.848000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
Aug  2 11:04:08 dell kernel: [  117.848000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
Aug  2 11:04:08 dell kernel: [  117.896000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug  2 11:04:09 dell kernel: [  118.068000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
Aug  2 11:04:09 dell kernel: [  118.068000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
Aug  2 11:04:16 dell dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Aug  2 11:04:16 dell dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Aug  2 11:04:16 dell dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers

---

### Post by purplearcanist on 2007-08-02
tap, need some help

---

### Post by apswartz on 2007-08-02
Since you are running Gutsy instead of Feisty you might try asking at the Gutsy forum. Perhaps others have had similar issues. I think we have exhausted the usual suspects and I can't see where the cd drive is even being detected (based on your logs). Sorry. :(

---

