---
title: "problem withk3b"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by medphys on 2007-08-14
Hi all;

Am new to Ubuntu having installed 7.04 a few days ago.  Having problems with K3B.  I can load it from sudo k3b but not from the shortcut on the applications panel.  The following are the errors that I get:

dan@dan-ubuntu:~$ sudo k3b
Password:
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
dan@dan-ubuntu:~$ kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
kdeinit: Shutting down running client.
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_IDE_DVD_ROM_16X to device /dev/hdd
Mapping udi /org/freedesktop/Hal/devices/storage_model_Verbatim_522452AL to device /dev/hdc
/dev/hdd resolved to /dev/hdd
/dev/hdd is block device (64)
/dev/hdd seems to be cdrom
(K3bDevice::Device) /dev/hdd: init()
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/hdd: MODE SENSE length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/hdd: MODE SENSE with real length 65535 failed.
(K3bDevice::Device) /dev/hdd: modeSense 0x05 failed!
(K3bDevice::Device) /dev/hdd: Cannot check write modes.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/hdd: MODE SENSE length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/hdd: MODE SENSE with real length 65535 failed.
/dev/hdc resolved to /dev/hdc
/dev/hdc is block device (0)
/dev/hdc seems to be cdrom
(K3bDevice::Device) /dev/hdc: init()
(K3bDevice::Device) /dev/hdc feature: CD Mastering
(K3bDevice::Device) /dev/hdc feature: CD Track At Once
(K3bDevice::Device) /dev/hdc unknown profile: 2
(K3bDevice::Device) /dev/hdc: dataLen: 60
(K3bDevice::Device) /dev/hdc: checking for TAO
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /root/.DCOPserver_dan-ubuntu__0
and start dcopserver again.
---------------------------------

KDE Daemon (kded) already running.
kbuildsycoca running...
Reusing existing ksycoca
(K3bDevice::Device) /dev/hdc: checking for SAO
(K3bDevice::Device) /dev/hdc: checking for SAO_R96P
(K3bDevice::Device) /dev/hdc: checking for SAO_R96R
(K3bDevice::Device) /dev/hdc: checking for RAW_R16
(K3bDevice::Device) /dev/hdc: checking for RAW_R96P
(K3bDevice::Device) /dev/hdc: checking for RAW_R96R
(K3bDevice::ScsiCommand) failed: 
                           command:    GET PERFORMANCE (ac)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::Device) /dev/hdc: GET PERFORMANCE length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    GET PERFORMANCE (ac)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::Device) /dev/hdc: GET PERFORMANCE with real length 2048 failed.
(K3bDevice::Device) /dev/hdc:  Number of supported write speeds via 2A: 11
(K3bDevice::Device) /dev/hdc : 9152 KB/s
(K3bDevice::Device) /dev/hdc : 8448 KB/s
(K3bDevice::Device) /dev/hdc : 7040 KB/s
(K3bDevice::Device) /dev/hdc : 5632 KB/s
(K3bDevice::Device) /dev/hdc : 4224 KB/s
(K3bDevice::Device) /dev/hdc : 2816 KB/s
(K3bDevice::Device) /dev/hdc : 2112 KB/s
(K3bDevice::Device) /dev/hdc : 1760 KB/s
(K3bDevice::Device) /dev/hdc : 1408 KB/s
(K3bDevice::Device) /dev/hdc Invalid DVD speed: 704 KB/s
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
(K3bDevice::DeviceManager) setting current write speed of device /dev/hdc to 0
/dev/hdd resolved to /dev/hdd
(K3bDevice::DeviceManager) dev /dev/hdd already found
/dev/hdc resolved to /dev/hdc
(K3bDevice::DeviceManager) dev /dev/hdc already found
(K3bDevice::DeviceManager) found config entry for devicetype: IDE DVD-ROM 16X
(K3bDevice::DeviceManager) found config entry for devicetype: Verbatim 522452AL
kio (KSycoca): ERROR: No database available!
kio (KMimeType): WARNING: KServiceType::offers : servicetype KDEDModule not found
Devices:
------------------------------
Blockdevice:    /dev/hdd
Generic device: 
Vendor:         IDE
Description:    DVD-ROM 16X
Version:        2.02
Write speed:    0
Profiles:       DVD-ROM, CD-ROM
Read Cap:       DVD-ROM, CD-ROM
Write Cap:      Error
Writing modes:  None
Reader aliases: /dev/hdd
------------------------------
Blockdevice:    /dev/hdc
Generic device: 
Vendor:         Verbatim
Description:    522452AL
Version:        68S1
Write speed:    0
Profiles:       CD-ROM, CD-R, CD-RW
Read Cap:       CD-ROM, CD-R, CD-RW
Write Cap:      CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R
Reader aliases: /dev/hdc
------------------------------
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.


Can anyone tell me what I need to do to launch the program from the applications panel.?

Checked the shortcut and it is launching from /usr/bin.

Thank you in advance.

---

### Post by skymera on 2007-08-14
application>sound + videos> k3b

try reinstall

sudo aptitude reinstall k3b

---

### Post by medphys on 2007-08-16
Skymera;

Thank you for the response.  Tried reinstalling as you suggested.  Seems that everything in KDE and K3B has root permissions.  Do I need to change them?  Shouldn't the permissions be for my login and not root?

Thank you for your help.

---

### Post by stchman on 2007-08-16
> **medphys said:**
> Hi all;

Am new to Ubuntu having installed 7.04 a few days ago.  Having problems with K3B.  I can load it from sudo k3b but not from the shortcut on the applications panel.  The following are the errors that I get:

dan@dan-ubuntu:~$ sudo k3b
Password:
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0

Thank you in advance.

The problem I have had with K3B on some machines is that the ~/.kde folder somehow gets owned by root.  That is why you can sudo k3b.

The fix is to do the following:


```

sudo chown -R $USER:$USER ~/.kde
chmod -R 755 ~/.kde

```

This usually fixes the problem.  The $USER is the user currently logged in.

---

