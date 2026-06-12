---
title: "Can't find / browse my USB flash drive."
date: 2005-08-06
forum: Absolute Beginner Talk
---

### Post by bgryderclock on 2005-08-06
Everything is working great is on my ubuntu 5.04 system, I just can't find/browse my Lexar USB jumpdrive.

I have the removeable drive and media prefenerences set to mount removeable drives when hotplugged/inserted.

The USB drive appears in my device manager:
screenshot  ---> [http://www.morningface.com/temphelp.png](http://www.morningface.com/temphelp.png)  

It shows up in the "usb viewer" application as well.  ](*,) 

What do i need to do or where do i need to look?

---

### Post by varunus on 2005-08-06
Can you post the output of the following commands in a terminal a few seconds after you insert your USB drive:
```

ps -A | grep gnome
dmesg | grep usb
```

Also, try the following in a terminal with the USB drive not connected:
```
killall gnome-volume-manager
gnome-volume-manager
#plug in the usb stick, you should see some error messages...#
```

---

### Post by jasmuz on 2005-08-06
It shows that its being done SCSI emulation for it (just like for all USB pendrives), meaning it should be under /dev/sda1, you could try mounting it to see what happens.

sudo mount /dev/sda1 /whatevermountpointyouwant

---

### Post by bgryderclock on 2005-08-06
[QUOTE=varunus]Can you post the output of the following commands in a terminal a few seconds after you insert your USB drive:
```
ps -A | grep gnome
dmesg | grep usb
```
Also, try the following in a terminal with the USB drive not connected:
```
killall gnome-volume-manager
gnome-volume-manager
#plug in the usb stick, you should see some error messages...#
```[/QUOTE]
thanks for the quick reply ^_^
```

ps -A | grep gnome
dmesg | grep usb
```
returned this:
```

user@bgryderclock:~$ ps -A | grep gnome
 7245 ?        00:00:00 gnome-keyring-d
 7251 ?        00:00:00 gnome-smproxy
 7253 ?        00:00:02 gnome-settings-
 7300 ?        00:00:00 gnome-volume-ma
 7309 ?        00:00:00 gnome-cups-icon
 7315 ?        00:00:05 gnome-vfs-daemo
 7569 ?        00:00:02 gnome-terminal
 7570 ?        00:00:00 gnome-pty-helpe
 8102 ?        00:00:03 gnome-panel

user@bgryderclock:~$ dmesg | grep usb
usbcore: registered new driver usbfs
usbcore: registered new driver hub
usb 1-2: new full speed USB device using uhci_hcd and address 2
usb 1-2.1: new full speed USB device using uhci_hcd and address 3
usbcore: registered new driver usb-storage
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
usb 1-2.1: USB disconnect, address 3
usb 1-2.1: new full speed USB device using uhci_hcd and address 4
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete

```
and
```

killall gnome-volume-manager
gnome-volume-manager
#plug in the usb stick, you should see some error messages...#

```
returned this:
```
user@bgryderclock:~$ killall gnome-volume-manager
user@bgryderclock:~$ gnome-volume-manager
manager.c/925: New Device: /org/freedesktop/Hal/devices/usb_device_5dc_a400_3000 _-1_0A4EEC05044156160505
manager.c/925: New Device: /org/freedesktop/Hal/devices/usb_usb_device_5dc_a400_ 3000_-1_0A4EEC05044156160505_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/scsi_host_2
manager.c/925: New Device: /org/freedesktop/Hal/devices/scsi_2_0_0_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/block_8_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/block_8_1
manager.c/967: Added: /dev/sda1
Error: invalid file system name ''
```

what should i do next:mrgreen:

---

### Post by pepavalle on 2005-08-06
Hola
Inserta la ubdrive y como root:
Haz ésto:
#more /etc/mtab
Tiene q aparecerte algo así:
usbfs /proc/bus/usb usbfs rw 0 0
Y añade ésto a /etc/fstab:
/dev/sdb        /mnt/usb       auto    rw,user,umask=0000      0       0

todo como root, claro

Un saludete :razz:

---

### Post by varunus on 2005-08-06
pepavalle, luckily i took spanish in HS, so I can kind of understand what you said...I don't think the problem is in his mtab.  Looks to me like "pmount", the utility that automounts USB drives, is failing.

Can you post the output of your /etc/fstab file bgryderclock?  I am willing to bet the problem is there.

---

### Post by bgryderclock on 2005-08-06
[QUOTE=varunus]pepavalle, luckily i took spanish in HS, so I can kind of understand what you said...I don't think the problem is in his mtab.  Looks to me like "pmount", the utility that automounts USB drives, is failing.

Can you post the output of your /etc/fstab file bgryderclock?  I am willing to bet the problem is there.[/QUOTE]

thanks for the reply pepavalle, i wish i took spanish in High School.  :wink:

varunus, here's my /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by bgryderclock on 2005-08-08
[QUOTE=bgryderclock]Everything is working great is on my ubuntu 5.04 system, I just can't find/browse my Lexar USB jumpdrive.

I have the removeable drive and media preferences set to mount removeable drives when hotplugged/inserted.

The USB drive appears in my device manager:
screenshot  ---> [http://www.morningface.com/temphelp.png](http://www.morningface.com/temphelp.png)  
It shows up in the "usb viewer" application as well.  ](*,) 
What do i need to do or where do i need to look?[/QUOTE]

Hey! i think i did it,

I terminal'd this:

```
sudo mkdir /mnt/usbdrv
sudo mount -t vfat /dev/sda1 /mnt/usbdrv
```

and the drive showed up. :D
it disappears again when you restart though :? 

Is there a way to make the pc run " sudo mount -t vfat /dev/sda1 /mnt/usbdrv " on startup?

------Update-------

 installed kubuntu and it work great now.

 *dancetime*

---

### Post by pjman on 2005-08-23
Hi,

I'm also having this problem with my USB Flash drive.

```

manager.c/925: New Device: /org/freedesktop/Hal/devices/usb_device_5dc_a410_3000_-1_1069A704070136021104
manager.c/925: New Device: /org/freedesktop/Hal/devices/usb_usb_device_5dc_a410_3000_-1_1069A704070136021104_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/scsi_host_3
manager.c/925: New Device: /org/freedesktop/Hal/devices/scsi_3_0_0_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/block_8_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/block_8_1
manager.c/961: Changed: /dev/sda1
manager.c/904: Added: /dev/sda1
Error: invalid file system name ''

```

Does anyone know what the " Error: invalid file system name '' " means for the gnome-volume-manager? I posted this in a different [thread](http://www.ubuntuforums.org/showthread.php?t=51766&page=1&pp=10&highlight=flash+mount) about USB Drives automounting but I haven't got a reply so I thought I'd post it here to since this is the same error I'm getting.  :wink: 

Thanks!
pjman

---

### Post by pjman on 2005-08-23
[QUOTE=pjman]Hi,

I'm also having this problem with my USB Flash drive.



Does anyone know what the " Error: invalid file system name '' " means for the gnome-volume-manager? I posted this in a different [thread](http://www.ubuntuforums.org/showthread.php?t=51766&page=1&pp=10&highlight=flash+mount) about USB Drives automounting but I haven't got a reply so I thought I'd post it here to since this is the same error I'm getting.  :wink: 

Thanks!
pjman[/QUOTE]
 I figured it out. I needed to add this line to my /etc/fstab

```

/dev/sda1       /mnt/sda1       vfat    rw,user,noauto,noatime

```
:-)

pjman

---

