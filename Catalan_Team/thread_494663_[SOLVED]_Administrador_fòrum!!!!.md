---
title: "[SOLVED] Administrador fòrum!!!!"
date: 2007-07-07
forum: Catalan Team
---

### Post by prostata on 2007-07-07
quna vull respondre sobre el tema guia amarok de pellroja, i al moment d'afegir el contingut per terminal, no em deixa i apareix el seguent aununci:

 The following errors occurred when this message was submitted:

   1. You have included 33 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

      Images include use of smilies, the vB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

¿pots dir-me que faig malament?? es que si no com pots comprendre no puc contestar a la darrera pergunta que em fan.
Gràcies

---

### Post by CarlesOriol on 2007-07-08
Et diu que t'estas passant d'imatges, que estas limitat a 8 i n'hi ha 33.

Crec, llegint la resta del missatge, que algun caracter que estas insrint repetidament, correspon a una emoticona i això et bloqueja l'enviament.

---

### Post by prostata on 2007-07-08
> **CarlesOriol said:**
> Et diu que t'estas passant d'imatges, que estas limitat a 8 i n'hi ha 33.

Crec, llegint la resta del missatge, que algun caracter que estas insrint repetidament, correspon a una emoticona i això et bloqueja l'enviament.

si això és el que crec jo també, però no faig res més que adjuntar el resultat que em dona per consola la ordre k3b, via terminal, com a resposta a una pregunta que em fa un company. Senzillament escric a la terminal k3b, em dona un resultat i faig copy-paste, com sempre, i es a les hores quan em dona el problema, que entenc, ja que es un missatge de txt pla, i jo no i fico cap emoticon....en fin, no sé, es per això que ho preguntava, ja que si no no puc enviar al fòrum la resposta....¿tens alguna suggerència??

---

### Post by lluisanunez on 2007-07-08
Prova a posar el codi del terminal entre etiquetes <CODE> (fes servir la icona #)
Potser aixi no interpretarà els caracters com a smilies

---

### Post by prostata on 2007-07-08
Aquí hi és el problema, amb aquesta forma.

/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 1, id: 0, lun: 0
(K3bDevice::Device) /dev/scd0: init()
(K3bDevice::Device) /dev/scd0 feature: CD Mastering

la resposta per terminal és més llarga, però fixa't basicament en les lìnies (K3bDevice.....) que hi han  moltes més en la resposta de terminal, però et poso dos exemples, els quatre puntets entre Device i Device, els pren com a emoticons, és per això que no em permet enviar el missatge. L'hi enviat al seu autor un privat, i des de ell he pogut veure el problema. Per tant ara només espero que ell em respongui....

gràcies

---

### Post by lluisanunez on 2007-07-08
Però si ho poses entre les etiquetes <CODE>, surt bé:

```
/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 1, id: 0, lun: 0
(K3bDevice::Device) /dev/scd0: init()
(K3bDevice::Device) /dev/scd0 feature: CD Mastering

```

---

### Post by prostata on 2007-07-09
> **lluisanunez said:**
> Però si ho poses entre les etiquetes <CODE>, surt bé:

```
/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 1, id: 0, lun: 0
(K3bDevice::Device) /dev/scd0: init()
(K3bDevice::Device) /dev/scd0 feature: CD Mastering

```


No vaig provar de fer-lo, perque honestament no entenc exactament lo de etiquetes <CODE>, les haig de posar on i en quina forma literalment. m'agardaria saber-lo ja que suposo que més tard o més d'hora em puc trobar el mateix problema, ¿podries fer-me cinc cèntims?

Gràcies

---

### Post by papapep on 2007-07-09
Símplement has de ficar al principi del text "CODE" i al final "/CODE", sense les cometes clar, i t'ho tractarà com a codi i no interpretarà els dos punt i demés històries com a emoticones.

Per exemple, el següent: ```
Una prova de que no interpreta les emoticones :-) ;-) :-D 
```

Com pots veure no interpreta les caretes com a emoticones.

En canvi, si treus el  CODE al principi i el /CODE al final:

Una prova de que no interpreta les emoticones :-) ;-) :-D

si que ho interpreta com a emoticones.

El CODE i /CODE cal que estiguin entre els caràcters [ i ]. Ara no puc fer-ho ja que ho tracta com a codi si ho faig ;-)

---

### Post by prostata on 2007-07-09
> **papapep said:**
> Símplement has de ficar al principi del text "CODE" i al final "/CODE", sense les cometes clar, i t'ho tractarà com a codi i no interpretarà els dos punt i demés històries com a emoticones.

Per exemple, el següent: ```
Una prova de que no interpreta les emoticones :-) ;-) :-D 
```

Com pots veure no interpreta les caretes com a emoticones.

En canvi, si treus el  CODE al principi i el /CODE al final:

Una prova de que no interpreta les emoticones :-) ;-) :-D

si que ho interpreta com a emoticones.

El CODE i /CODE cal que estiguin entre els caràcters [ i ]. Ara no puc fer-ho ja que ho tracta com a codi si ho faig ;-)

Gràcies i perdona la meva "incapacitat" entenc el que dius, però no em surto. He provat el següent:

Pego el text de la terminal, a la finestra del post, per exemple aquesta.
Escric al inici l'etiqueta Code i al final del text de la terminal que he pegat a la finestra escric /Code, però a l'hora d'enviar el post no m'ho permet. Per veure el funcionament de la teva explicació, un exemple:

Code

:-)  ;-(

Sense Code: :-)

Disculpa però es que no acabo d'agafar-lo....

---

### Post by papapep on 2007-07-09
Mira, encara més simple.
Prems la icona del "quadradillu"  (#) que hi ha a la finestra de resposta dels posts, entre la bafarada i els símbols <>, això et farà aparèixer les etiquetes CODE i /CODE, dins dels respectius claudators. Tu fiques tot el que vulguis entre les dues etiquetes i ja estarà.

---

### Post by prostata on 2007-07-09
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

### Post by prostata on 2007-07-09
> **papapep said:**
> Mira, encara més simple.
Prems la icona del "quadradillu"  (#) que hi ha a la finestra de resposta dels posts, entre la bafarada i els símbols <>, això et farà aparèixer les etiquetes CODE i /CODE, dins dels respectius claudators. Tu fiques tot el que vulguis entre les dues etiquetes i ja estarà.

Gràcies, com pots veure ja li agafat el "truquillu", ara l'enviaré al col-lega que el deu estar esperant.....

---

