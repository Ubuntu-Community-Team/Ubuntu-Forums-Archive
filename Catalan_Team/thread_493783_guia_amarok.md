---
title: "guia amarok"
date: 2007-07-06
forum: Catalan Team
---

### Post by PellRoja on 2007-07-06
pels amants de amarok, he creat una guia per treure-li el maxim suquet

[http://www.informatics.cat/wiki/index.php/Amarok](http://www.informatics.cat/wiki/index.php/Amarok)

editat ;)

---

### Post by prostata on 2007-07-06
molt i molt bona aquesta guia, només que he fet lo de gravar  CD però el k3b que el tinc instal-lat no arrenca, ¿alguna suggerència???

---

### Post by PellRoja on 2007-07-06
t' arranca be el k3b sense executar-lo des de amarok?

directament no arranca, o surt algun error? ;)

---

### Post by prostata on 2007-07-06
> **PellRoja said:**
> t' arranca be el k3b sense executar-lo des de amarok?
[B]
si...[/B]

directament no arranca, o surt algun error? ;)

**directament no arrenca....**

---

### Post by patrickfromspain on 2007-07-07
arranca el k3b des d'un terminal i diguen's quin error t'hi surt.

---

### Post by prostata on 2007-07-09
això es el que em surt per terminal:
```
josep@josep-desktop:~$ k3b
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
josep@josep-desktop:~$ kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_DVDRAM_GSA_4165B to device /dev/scd0
/dev/scd0 resolved to /dev/scd0
/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 1, id: 0, lun: 0
(K3bDevice::Device) /dev/scd0: init()
(K3bDevice::Device) /dev/scd0 feature: CD Mastering
(K3bDevice::Device) /dev/scd0 feature: CD Track At Once
(K3bDevice::Device) /dev/scd0 feature: CD-RW Media Write Support
(K3bDevice::Device) /dev/scd0 feature: DVD Read (MMC5)
(K3bDevice::Device) /dev/scd0 feature: DVD+R
(K3bDevice::Device) /dev/scd0 feature: DVD+RW
(K3bDevice::Device) /dev/scd0 feature: DVD+R Double Layer
(K3bDevice::Device) /dev/scd0 feature: DVD-R/-RW Write
(K3bDevice::Device) /dev/scd0 feature: Rigid Restricted Overwrite
(K3bDevice::Device) /dev/scd0 unknown profile: 2
(K3bDevice::Device) /dev/scd0: dataLen: 60
(K3bDevice::Device) /dev/scd0: checking for TAO
(K3bDevice::Device) /dev/scd0: checking for SAO
(K3bDevice::Device) /dev/scd0: checking for SAO_R96P
(K3bDevice::Device) /dev/scd0: checking for SAO_R96R
(K3bDevice::Device) /dev/scd0: checking for RAW_R16
(K3bDevice::Device) /dev/scd0: checking for RAW_R96P
(K3bDevice::Device) /dev/scd0: checking for RAW_R96R
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/scd0 : 5540 KB/s
(K3bDevice::Device) /dev/scd0 : 2770 KB/s
(K3bDevice::DeviceManager) setting current write speed of device /dev/scd0 to 5540
/dev/scd0 resolved to /dev/scd0
(K3bDevice::DeviceManager) dev /dev/scd0 already found
(K3bDevice::DeviceManager) found config entry for devicetype: HL-DT-ST DVDRAM GSA-4165B
Devices:
------------------------------
Blockdevice:    /dev/scd0
Generic device: 
Vendor:         HL-DT-ST
Description:    DVDRAM GSA-4165B
Version:        DL03
Write speed:    8467
Profiles:       DVD-ROM, DVD-R secuencial, DVD-R Doble capa secuencial, DVD-R doble capa salteado, DVD-RAM, DVD-RW sobreescritura restringida, DVD-RW secuencial, DVD+RW, DVD+R, DVD+R doble capa, CD-ROM, CD-R, CD-RW
Read Cap:       DVD-ROM, DVD-R, DVD-R secuencial, DVD-R doble capa, DVD-R Doble capa secuencial, DVD-R doble capa salteado, DVD-RW, DVD-RW sobreescritura restringida, DVD-RW secuencial, DVD+RW, DVD+R, DVD+RW doble capa, DVD+R doble capa, CD-ROM, CD-R, CD-RW
Write Cap:      DVD-R, DVD-R secuencial, DVD-R doble capa, DVD-R Doble capa secuencial, DVD-RW, DVD-RW sobreescritura restringida, DVD-RW secuencial, DVD+RW, DVD+R, DVD+R doble capa, CD-R, CD-RW
Writing modes:  SAO, TAO, En bruto, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Sobreescritura restringida
Reader aliases: /dev/scd0
------------------------------
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
First sec data area: 43:41:33 (LBA 196608) (402653184
Last sec data area: 199:10:05 (LBA 896255) (1835530240 Bytes)
Last sec layer 1: 00:00:00 (LBA 0) (0 Bytes)
Layer 1 length: 00:00:01 (LBA 1) (2048 Bytes)
Layer 2 length: 199:10:05 (LBA 896255) (1835530240 Bytes)
(K3bDevice::Device) READ CAPACITY: 155:28:47 other capacity: 00:00:00
DiskInfo:
Mediatype:       DVD-R
Current Profile: DVD-ROM
Disk state:      complete
Empty:           0
Rewritable:      0
Appendable:      0
Sessions:        1
Tracks:          1
Layers:          1
Capacity:        155:28:48 (LBA 699648) (1432879104 Bytes)
Remaining size:  00:00:00 (LBA 0) (0 Bytes)
Used Size:       155:28:48 (LBA 699648) (1432879104 Bytes)
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/scd0 : 5540 KB/s
(K3bDevice::Device) /dev/scd0 : 2770 KB/s
```

---

### Post by vila-seca on 2007-07-09
Té pinta a bug... 

[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/103075](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/103075)



> **prostata said:**
> això es el que em surt per terminal:
```
josep@josep-desktop:~$ k3b
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
josep@josep-desktop:~$ kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_DVDRAM_GSA_4165B to device /dev/scd0
/dev/scd0 resolved to /dev/scd0
/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 1, id: 0, lun: 0
(K3bDevice::Device) /dev/scd0: init()
(K3bDevice::Device) /dev/scd0 feature: CD Mastering
(K3bDevice::Device) /dev/scd0 feature: CD Track At Once
(K3bDevice::Device) /dev/scd0 feature: CD-RW Media Write Support
(K3bDevice::Device) /dev/scd0 feature: DVD Read (MMC5)
(K3bDevice::Device) /dev/scd0 feature: DVD+R
(K3bDevice::Device) /dev/scd0 feature: DVD+RW
(K3bDevice::Device) /dev/scd0 feature: DVD+R Double Layer
(K3bDevice::Device) /dev/scd0 feature: DVD-R/-RW Write
(K3bDevice::Device) /dev/scd0 feature: Rigid Restricted Overwrite
(K3bDevice::Device) /dev/scd0 unknown profile: 2
(K3bDevice::Device) /dev/scd0: dataLen: 60
(K3bDevice::Device) /dev/scd0: checking for TAO
(K3bDevice::Device) /dev/scd0: checking for SAO
(K3bDevice::Device) /dev/scd0: checking for SAO_R96P
(K3bDevice::Device) /dev/scd0: checking for SAO_R96R
(K3bDevice::Device) /dev/scd0: checking for RAW_R16
(K3bDevice::Device) /dev/scd0: checking for RAW_R96P
(K3bDevice::Device) /dev/scd0: checking for RAW_R96R
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/scd0 : 5540 KB/s
(K3bDevice::Device) /dev/scd0 : 2770 KB/s
(K3bDevice::DeviceManager) setting current write speed of device /dev/scd0 to 5540
/dev/scd0 resolved to /dev/scd0
(K3bDevice::DeviceManager) dev /dev/scd0 already found
(K3bDevice::DeviceManager) found config entry for devicetype: HL-DT-ST DVDRAM GSA-4165B
Devices:
------------------------------
Blockdevice:    /dev/scd0
Generic device: 
Vendor:         HL-DT-ST
Description:    DVDRAM GSA-4165B
Version:        DL03
Write speed:    8467
Profiles:       DVD-ROM, DVD-R secuencial, DVD-R Doble capa secuencial, DVD-R doble capa salteado, DVD-RAM, DVD-RW sobreescritura restringida, DVD-RW secuencial, DVD+RW, DVD+R, DVD+R doble capa, CD-ROM, CD-R, CD-RW
Read Cap:       DVD-ROM, DVD-R, DVD-R secuencial, DVD-R doble capa, DVD-R Doble capa secuencial, DVD-R doble capa salteado, DVD-RW, DVD-RW sobreescritura restringida, DVD-RW secuencial, DVD+RW, DVD+R, DVD+RW doble capa, DVD+R doble capa, CD-ROM, CD-R, CD-RW
Write Cap:      DVD-R, DVD-R secuencial, DVD-R doble capa, DVD-R Doble capa secuencial, DVD-RW, DVD-RW sobreescritura restringida, DVD-RW secuencial, DVD+RW, DVD+R, DVD+R doble capa, CD-R, CD-RW
Writing modes:  SAO, TAO, En bruto, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Sobreescritura restringida
Reader aliases: /dev/scd0
------------------------------
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
First sec data area: 43:41:33 (LBA 196608) (402653184
Last sec data area: 199:10:05 (LBA 896255) (1835530240 Bytes)
Last sec layer 1: 00:00:00 (LBA 0) (0 Bytes)
Layer 1 length: 00:00:01 (LBA 1) (2048 Bytes)
Layer 2 length: 199:10:05 (LBA 896255) (1835530240 Bytes)
(K3bDevice::Device) READ CAPACITY: 155:28:47 other capacity: 00:00:00
DiskInfo:
Mediatype:       DVD-R
Current Profile: DVD-ROM
Disk state:      complete
Empty:           0
Rewritable:      0
Appendable:      0
Sessions:        1
Tracks:          1
Layers:          1
Capacity:        155:28:48 (LBA 699648) (1432879104 Bytes)
Remaining size:  00:00:00 (LBA 0) (0 Bytes)
Used Size:       155:28:48 (LBA 699648) (1432879104 Bytes)
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/scd0 : 5540 KB/s
(K3bDevice::Device) /dev/scd0 : 2770 KB/s
```

---

### Post by patrickfromspain on 2007-07-12
no te bona pinta... igual te mes a veure amb el dcopserver que amb el k3b..

---

### Post by antoniu on 2008-03-02
quan entro al link d'informaticat em surt una pàgina porno

---

### Post by papapep on 2008-03-02
Si :-D em fa l'efecte que el nostre company té un petit problema amb el seu domini.

---

### Post by patrickfromspain on 2008-03-02
Aqui igual! Pagina porno xD

---

### Post by almogabber on 2008-03-02
Ostres quin susto!!!! :confused: :lolflag:

---

### Post by PellRoja on 2008-03-02
Perdoneu el canvi de domini. Peró era per passar el web a millor vida.

[http://www.informatics.cat](http://www.informatics.cat)

[http://www.informatics.cat/wiki](http://www.informatics.cat/wiki)

Ostres em fa rabia que el domini l' hagi agafat una empresa de publicitat porno. Ja podria hever sigut qualsevol altre de links normals. :(

Nose si hi ha alguna manera de alertar algun lloc, que aquest domini passa a ser per contingut adult, ja que potser algun filtre web o deu passar.

---

