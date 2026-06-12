---
title: "problema modem vodafone desprès d'actualitzar a 9.10 Karmic"
date: 2009-11-10
forum: Catalan Team
---

### Post by ifanlo on 2009-11-10
Hola!

Disposo d'un mòdem Vodafone que amb la Jaunty m'anava molt bé, però desprès de l'actualització a Kàrmic, no me'l reconeix.  

Si inicio el sistema amb el nucli anterior (2.6.28-16-generic) tot va bé... la sortida del dmesg:

```
[ 2939.016056] usb 3-2: new full speed USB device using uhci_hcd and address 10
[ 2939.180366] usb 3-2: configuration #1 chosen from 1 choice
[ 2939.187721] usb-storage: probe of 3-2:1.0 failed with error -1
[ 2939.216105] usb 3-2: USB disconnect, address 10
[ 2939.952074] usb 3-2: new full speed USB device using uhci_hcd and address 11
[ 2940.172903] usb 3-2: configuration #1 chosen from 1 choice
[ 2940.180064] usb-storage: probe of 3-2:1.0 failed with error -5
[ 2940.180096] option 3-2:1.0: GSM modem (1-port) converter detected
[ 2940.180347] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 2940.187419] usb-storage: probe of 3-2:1.1 failed with error -5
[ 2940.187453] option 3-2:1.1: GSM modem (1-port) converter detected
[ 2940.187693] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 2940.190004] usb-storage: probe of 3-2:1.2 failed with error -5
[ 2940.190035] option 3-2:1.2: GSM modem (1-port) converter detected
[ 2940.207050] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 2940.213121] usb-storage: probe of 3-2:1.3 failed with error -1
```I a partir d'aquí, tot bé, seleccionar des del Network Manager, connectar, etc...

Però amb el nou kernel (2.6.31-14-generic) sembla que vulgui, però no; a més sembla que vulgui montar la memoria flash del módem com una unitat de magatzemament i finalitza desconnectant el dispositiu.  La sortida del dmesg:
```
[  367.945093] usb 3-2: new full speed USB device using uhci_hcd and address 3
[  368.108899] usb 3-2: configuration #1 chosen from 1 choice
[  368.190578] Initializing USB Mass Storage driver...
[  368.192791] scsi6 : SCSI emulation for USB Mass Storage devices
[  368.193051] usb-storage: device found at 3
[  368.193056] usb-storage: waiting for device to settle before scanning
[  368.193064] usbcore: registered new interface driver usb-storage
[  368.193070] USB Mass Storage support registered.
[  368.200093] usb 3-2: USB disconnect, address 3
[  368.936141] usb 3-2: new full speed USB device using uhci_hcd and address 4
[  369.099876] usb 3-2: configuration #1 chosen from 1 choice
[  369.122150] scsi10 : SCSI emulation for USB Mass Storage devices
[  369.122413] usb-storage: device found at 4
[  369.122417] usb-storage: waiting for device to settle before scanning
[  369.161725] usbcore: registered new interface driver usbserial
[  369.161753] USB Serial support registered for generic
[  369.161857] usbcore: registered new interface driver usbserial_generic
[  369.161861] usbserial: USB Serial Driver core
[  369.179835] USB Serial support registered for GSM modem (1-port)
[  369.179929] option 3-2:1.0: GSM modem (1-port) converter detected
[  369.180107] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB0
[  369.180128] option 3-2:1.1: GSM modem (1-port) converter detected
[  369.180228] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB1
[  369.180247] option 3-2:1.2: GSM modem (1-port) converter detected
[  369.180335] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB2
[  369.180367] usbcore: registered new interface driver option
[  369.180371] option: v0.7.2:USB Driver for GSM modems
[  374.120816] usb-storage: device scan complete
[  374.123786] scsi 10:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  374.126781] scsi 10:0:0:1: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[  374.150749] sr1: scsi-1 drive
[  374.150970] sr 10:0:0:0: Attached scsi CD-ROM sr1
[  374.151093] sr 10:0:0:0: Attached scsi generic sg2 type 5
[  374.151308] sd 10:0:0:1: Attached scsi generic sg3 type 0
[  374.175711] option: option_instat_callback: error -108
[  374.177010] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  374.177039] option 3-2:1.0: device disconnected
[  374.177171] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  374.177206] option 3-2:1.1: device disconnected
[  374.177333] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  374.177363] option 3-2:1.2: device disconnected
[  374.288054] usb 3-2: reset full speed USB device using uhci_hcd and address 4
```i a partir d'aquí, va repetint continuament desde la línia que diu ...
```
option 3-2:1.2: GSM modem (1-port) converter detected
...
```Amb excepció de les que fan referència a usb-storage i scsi.

Per arrodonir, emergeix una finestra d'error:
```
no se pudo montar VMC LITE 9.3.6  Error mounting: mount exited with exit code 32: mount: block device /dev/sr1 is write-protected, mounting read-only
mount: /dev/sr1 already mounted or /media/VMC LITE 9.3.6   busy

```¿Algú s'ha barallat ja amb aquest problemo?

Gràcies,

---

### Post by papapep on 2009-11-10
Ei! Benvingut al fòrum, Ismael! :D

Enganxa el que et surti d'un:

```
lsusb
```

a veure com t'identifica exactament el módem l'Ubuntu.

PS: els d'"Alaska y Los Plasmoides" no havien plegat fa temps de "lo dolents" que eren??? :P

---

