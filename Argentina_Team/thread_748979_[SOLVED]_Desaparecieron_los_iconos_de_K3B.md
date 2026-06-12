---
title: "[SOLVED] Desaparecieron los iconos de K3B"
date: 2008-04-08
forum: Argentina Team
---

### Post by Air23 on 2008-04-08
Hola, tengo un pequeño problema y quizas alguien me puede ayudar.
Ayer estuve toqueteando demasiado /usr/share/icons via sudo nautilus y me empezaron a faltar iconos aunque lo solucione reinstalando desde synaptic los inonos predeterminados. Pero hoy al abrir K3B me encontre con que este no tiene ningun icono (no el icono del programa sino los de adentro del programa, los de los menus). 
Abriendolo desde una terminal me aparece lo siguiente

```
juan@HAL9000:~$ k3b
kdecore (KIconLoader): ERROR: Error: standard icon theme "crystalsvg"  not found!
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
juan@HAL9000:~$ (K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_DRW_1814BLT to device /dev/scd0
/dev/scd0 resolved to /dev/scd0
/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 3, id: 0, lun: 0
(K3bDevice::Device) /dev/scd0: init()
(K3bDevice::Device) /dev/scd0 feature: CD Mastering
(K3bDevice::Device) /dev/scd0 feature: CD Track At Once
(K3bDevice::Device) /dev/scd0 feature: DVD Read (MMC5)
(K3bDevice::Device) /dev/scd0 feature: DVD+R
(K3bDevice::Device) /dev/scd0 feature: DVD+RW
(K3bDevice::Device) /dev/scd0 feature: DVD+R Double Layer
(K3bDevice::Device) /dev/scd0 feature: DVD-R/-RW Write
(K3bDevice::Device) /dev/scd0 feature: Rigid Restricted Overwrite
(K3bDevice::Device) /dev/scd0 feature: Layer Jump Recording
(K3bDevice::Device) /dev/scd0 unknown profile: 2
(K3bDevice::Device) /dev/scd0: dataLen: 60
(K3bDevice::Device) /dev/scd0: checking for TAO
(K3bDevice::Device) /dev/scd0: checking for SAO
(K3bDevice::Device) /dev/scd0: checking for SAO_R96P
(K3bDevice::Device) /dev/scd0: checking for SAO_R96R
(K3bDevice::Device) /dev/scd0: checking for RAW_R16
(K3bDevice::Device) /dev/scd0: checking for RAW_R96P
(K3bDevice::Device) /dev/scd0: checking for RAW_R96R
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE dataLen = 56
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE successful with reported length: 52
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via GET PERFORMANCE: 3
(K3bDevice::Device) /dev/scd0 : 13850 KB/s
(K3bDevice::Device) /dev/scd0 : 11080 KB/s
(K3bDevice::Device) /dev/scd0 : 5540 KB/s
(K3bDevice::DeviceManager) setting current write speed of device /dev/scd0 to 13850
/dev/scd0 resolved to /dev/scd0
(K3bDevice::DeviceManager) dev /dev/scd0 already found
(K3bDevice::DeviceManager) found config entry for devicetype: ASUS DRW-1814BLT
(K3bDevice::Device) /dev/scd0: Device reports bogus disc information length of 24
First sec data area: 43:41:33 (LBA 196608) (402653184
Last sec data area: 553:42:61 (LBA 2491711) (5103024128 Bytes)
Last sec layer 1: 00:00:00 (LBA 0) (0 Bytes)
Layer 1 length: 00:00:01 (LBA 1) (2048 Bytes)
Layer 2 length: 553:42:61 (LBA 2491711) (5103024128 Bytes)
DiskInfo:
Mediatype:       DVD+R
Current Profile: DVD+R
Disk state:      empty
Empty:           1
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          1
Capacity:        510:01:29 (LBA 2295104) (4700372992 Bytes)
Remaining size:  510:01:29 (LBA 2295104) (4700372992 Bytes)
Used Size:       00:00:00 (LBA 0) (0 Bytes)
Devices:
------------------------------
Blockdevice:    /dev/scd0
Generic device: 
Vendor:         ASUS
Description:    DRW-1814BLT
Version:        1.13
Write speed:    22160
Profiles:       DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Read Cap:       DVD-ROM, DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+RW Dual Layer, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Write Cap:      DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump
Reader aliases: /dev/scd0
------------------------------
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE dataLen = 56
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE successful with reported length: 52
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via GET PERFORMANCE: 3
(K3bDevice::Device) /dev/scd0 : 13850 KB/s
(K3bDevice::Device) /dev/scd0 : 11080 KB/s
(K3bDevice::Device) /dev/scd0 : 5540 KB/s
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype application/x-trash
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype application/octet-stream
k3b: WARNING: Pixmap not found for mimetype inode/directory
k3b: WARNING: Pixmap not found for mimetype text/plain
```

Ya probe desinstalando totalmente K3B e instalandolo de nuevo y nada.
MI version de ubuntu es 7.10.

Alguna sugerencia de como arreglarlo???
Muchas gracias

---

### Post by Hei Ku on 2008-04-08
Por casualidad borraste los iconos de Crystal?? Ese es un tema de iconos de KDE, que parece estar buscando.

---

### Post by Air23 on 2008-04-09
> **Hei Ku said:**
> Por casualidad borraste los iconos de Crystal?? Ese es un tema de iconos de KDE, que parece estar buscando.

Gracias por responder.
Lo habia borrado. Pero lo instale de nuevo desde synaptic (el paquete se llama kde-icons-crystal) pero no cambio nada.

Ademas me parece que busca un tema de iconos llamado "crystalsvg" (que recuerdo haber eliminado) pero no se de donde sacarlo ya que en synaptic no existe nada con ese nombre (tampoco en Gnome-look)

---

### Post by Hei Ku on 2008-04-09
buscalo en kde-look

---

### Post by Air23 on 2008-04-09
> **Hei Ku said:**
> buscalo en kde-look

En Kde-look encontre unos iconos de nombre Crystalsvg ([http://www.kde-look.org/content/show.php/Crystal+SVG?content=8341](http://www.kde-look.org/content/show.php/Crystal+SVG?content=8341)) pero dice que esta version esta discontinuada y que para actualizaciones vaya a Crystal Proyect  que es un tema de iconos para Gnome que ya tengo instalado.

---

### Post by Hei Ku on 2008-04-09
entraste a la configuracion del K3B, a la parte de Temas, y probaste cambiarlo desde ahi?

---

### Post by Air23 on 2008-04-09
> **Hei Ku said:**
> entraste a la configuracion del K3B, a la parte de Temas, y probaste cambiarlo desde ahi?

Ante todo gracias de nuevo por responder al toque.
En Settings>Configure k3b>Themes solo cambia el fondo de la parte en que te da opciones de que hacer (cd de audio, cd de datos, etc).

Igual lo acabo de arreglar. Baje de kde-look los iconos mas parecidos que encontre a los crystalsvg (llamados mycrystalblue), los descomprimi en /usr/share/icons y cambie el nombre de la carpeta por crystalsvg y listo: el k3b los usa sin problemas.

Muchas gracias de nuevo por la ayuda

---

