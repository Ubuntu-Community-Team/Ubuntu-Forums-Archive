---
title: "SOS Error al desabilitar arxiu de xarxa"
date: 2007-05-28
forum: Catalan Team
---

### Post by rajoar on 2007-05-28
Hola a tots, soc un nou usuari de kubuntu... M'he passat uns quants dies instal·lant i configurant el kubuntu... Tot m'anava molt bé, però... em va semblar que tenia fitxers nvidia que no necessitava, ja que aparentment no tenia res de nvidia... i m'he quedat sense xarxa a Internet. Es clar com no tinc connexió a Internet no sé com restaurar els fitxers desinstal·lats.
Haig de tornar a instal·laho tot des de el principi?... O puc restaura-ho, d'alguna manera, des del DVD de kubuntu 7.04 Feisty Fawn? O sabeu alguna altra solució?...

---

### Post by lluisanunez on 2007-05-28
Com vas eliminar aquests arxius? Desinsta&#320;lant amb el Synaptic o esborrant directament? Recordes on eren?

---

### Post by rajoar on 2007-05-28
No, el Synaptic el kubuntu no el te. Ho vaig fer amb el equivalent del kubuntu... Ara no recordo com es diu el gestor de paquets... El fitxer desinstal·lat em sebla que es diu nvidia-com*** Quan el vegi segur que m'enrecordaré...

---

### Post by lluisanunez on 2007-05-28
Jo no conec KDE, però i si tornes a obrir el gestor de paquets, i busques el nom exacte del paquet que vas desinsta&#320;lar i l'envies aquí?

**Editat**: i també, quina tarja de xarxa tens?

---

### Post by CarlesOriol on 2007-05-29
Crec que t'has carregat els controladors restrictius del nucli.

Fes en un terminal

sudo apt-get install linux-restricted-modules-generic

i reinicia.

---

### Post by orestesmas on 2007-05-29
Jo també sóc usuari de kubuntu, però el que tu dius no sembla específic de KDE. A mi em fa tota la pinta de que has desinstal·lat algun tipus de suport per al xipset que té la teva placa base i que, entre d'altres, deu controlar el maquinari de xarxa. NVIDIA no només fabrica targes de vídeo, sinó també xipsets.

Per casualitat recordes quins paquets vas desinstal·lar? A mi, de paquets relacionats amb nvidia no me'n surten gaires:

orestes@raimon:~$ apt-cache search nvidia
restricted-manager - manage non-free hardware drivers
smartdimmer - Change LCD brightness on Geforce 6200Go cards
xserver-xorg-video-nv - X.Org X server -- NV display driver
linux-restricted-modules-2.6.20-15-386 - Non-free Linux 2.6.20 modules on 386
linux-restricted-modules-2.6.20-15-generic - Non-free Linux 2.6.20 modules on x86/x86_64
nvidia-kernel-common - NVIDIA binary kernel module common files
nvidia-settings - Tool of configuring the NVIDIA graphics driver
cpufreqd - fully configurable daemon for dynamic frequency and voltage scaling
dmraid - Device-Mapper Software RAID support tool
nexuiz - A fast-paced 3D Ego-Shooter
nvclock - Allows you to overclock your nVidia card under GNU/Linux
nvclock-gtk - Allows you to overclock your nVidia card under GNU/Linux
nvclock-qt - Allows you to overclock your nVidia card under GNU/Linux
nvidia-xconfig - The NVIDIA X Configuration Tool
nvtv - tool to control TV chips on NVidia cards under Linux
sensors-applet - Display readings from hardware sensors in your Gnome panel
sysinfo - Simple GTK program that shows some UNIX/Linux system information
trigger - free 3D rally racing car game
trigger-data - free 3D rally racing car game - data files
linux-restricted-modules-2.6.20-15-lowlatency - Non-free Linux 2.6.20 modules on x86/x86_64
xen-restricted-modules-2.6.17-6-generic-xen0 - Non-free Linux 2.6.17 modules on x86_64 generic-xen0
linux-restricted-modules-2.6.20-16-386 - Non-free Linux 2.6.20 modules on 386
linux-restricted-modules-2.6.20-16-generic - Non-free Linux 2.6.20 modules on x86/x86_64
nvidia-glx - NVIDIA binary XFree86 4.x/X.Org driver
nvidia-glx-dev - NVIDIA binary XFree86 4.x/X.Org driver development files
nvidia-glx-new - NVIDIA binary XFree86 4.x/X.Org 'new' driver
nvidia-glx-new-dev - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver development files
nvidia-new-kernel-source - NVIDIA binary 'new' kernel module source
linux-restricted-modules-2.6.20-16-lowlatency - Non-free Linux 2.6.20 modules on x86/x86_64
nvidia-glx-legacy - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver
nvidia-glx-legacy-dev - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver development files
nvidia-kernel-source - NVIDIA binary kernel module source
nvidia-legacy-kernel-source - NVIDIA binary 'legacy' kernel module source

Com et diu el Carles Oriol, si descartem els paquets relacionats amb la gràfica el més sospitós és el linux-restricted-modules

Ara bé, ell no apunta com instal·lar-lo de nou, si no tens xarxa. Hauries d'entrar al gestor de paquets (Adept), Anar al menú Adept -> Administra els repositoris -> Pestanya "Third-Party software" i escollir "Afegir un CD-ROM"

Amb això hauries de poder afegir el CD-ROM a la llista de repositoris i instal·lar aquest paquet des del CD. Si es dóna el cas que en primer lloc va a mirar als repositoris d'internet, pots desactivar-los temporalment desmarcant la creueta que hi ha al costat del seu nom.

Recorda sempre "Recollir les actualitzacions" després de cada canvi en els repositoris.

Orestes.

---

### Post by CarlesOriol on 2007-05-30
Crec que a la versió en DVD s'inclouen els moduls restrictius. ([http://es.archive.ubuntu.com/cdimage/releases/feisty/release/ubuntu-7.04-dvd-i386.list](http://es.archive.ubuntu.com/cdimage/releases/feisty/release/ubuntu-7.04-dvd-i386.list))

Tot i que si ja has actualitzat per xarxa segurament caldrà fer el que diu l'Orestes.

El fet que es distribueixin mòduls restrictius amb programari gpl no sé si és massa correcte. Voleu que obrim un fil i en parlem?

---

