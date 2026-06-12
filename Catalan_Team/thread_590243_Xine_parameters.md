---
title: "Xine parameters"
date: 2007-10-24
forum: Catalan Team
---

### Post by farigola on 2007-10-24
Hola 

Després de fer l'actualització a la gutsy he vist que diferents components del meu ordinador no funcionen com per exemple l'audio. Al intentar reproduir una peça musical des de Amarok surt el missatge:

La sortida d'àudio no està disponible; el dispositiu està ocupat.
xine parameters: 

He intentat refer la pròpia instal·lació de xine pero no funciona. 
Sabeu que

Equipo AMD 64 
Gutsy KDE

Gràcies

---

### Post by orestesmas on 2007-10-25
Anem a mirar el hardware que tens i els permisos.

Obre un terminal (Konsole) i posa'ns la sortida de les ordres següents:

lspci -v (només cal la part del "multimedia audio controller")
lsmod (llista tots els mòduls carregats en el nucli)
groups (llista els grups als quals pertany el teu usuari)
ls -l /dev/snd/  (llista dispositius ALSA i permisos)

---

### Post by farigola on 2007-10-28
Hola, Crec que aquí està tot.
no he trobat /dev/snd doncs no existeix. Hi ha un tema a comentar. Des de l'eina d'administració del sistema he vist que l'ordinador afectat no disposa de cap dispositiu MIDI ALSA per seleccionar. 



00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: Elitegroup Computer Systems Unknown device a88d
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


 lsmod
Module                  Size  Used by
ipv6                  257700  10
af_packet              21896  2
rfcomm                 38684  2
l2cap                  22788  11 rfcomm
bluetooth              52324  4 rfcomm,l2cap
ppdev                   9348  0
powernow_k8            11916  0
cpufreq_userspace       4116  0
cpufreq_ondemand        8084  1
cpufreq_conservative     6560  0
cpufreq_powersave       1792  0
cpufreq_stats           5508  0
freq_table              4740  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
ac                      5252  0
video                  17164  0
container               4608  0
sbs                    18568  0
button                  8080  0
dock                    9476  0
battery                10116  0
sbp2                   23304  0
lp                     11460  0
fuse                   44948  0
sky2                   44932  0
rtc                    13208  0
parport_pc             36132  1
parport                35656  3 ppdev,lp,parport_pc
nvidia               6218832  24
psmouse                38672  0
k8temp                  5760  0
pcspkr                  3072  0
serio_raw               7044  0
agpgart                33584  1 nvidia
shpchp                 33556  0
pci_hotplug            31288  1 shpchp
i2c_nforce2             6144  0
i2c_core               25104  2 nvidia,i2c_nforce2
evdev                  10240  3
ext3                  129928  1
jbd                    53416  1 ext3
mbcache                 8324  1 ext3
sg                     36124  0
sd_mod                 29200  3
ide_cd                 31776  0
cdrom                  36512  1 ide_cd
sata_nv                19460  2
usb_storage            71744  0
libusual               17552  1 usb_storage
ohci1394               35760  0
ieee1394               94904  2 sbp2,ohci1394
ata_generic             7556  0
libata                125040  2 sata_nv,ata_generic
scsi_mod              146828  5 sbp2,sg,sd_mod,usb_storage,libata
amd74xx                14364  0 [permanent]
ide_core              114772  3 ide_cd,usb_storage,amd74xx
ohci_hcd               21764  0
ehci_hcd               35084  0
usbcore               136088  5 usb_storage,libusual,ohci_hcd,ehci_hcd
thermal                13448  0
processor              23984  2 powernow_k8,thermal
fan                     4868  0
capability              5000  0
commoncap               7424  1 capability

groups
jordi adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin vboxusers

---

### Post by orestesmas on 2007-10-28
Bé, la cosa sembla clara: de la llista de mòduls (drivers) carregats, no n'hi ha cap que sigui driver de la targeta de so. Aquests comencen per "snd-".

Per què no l'ha carregat? probablement el maquinari no està suportat o el nucli no ha sabut relacionar l'identificador del dispositiu amb el driver que li dóna suport.

He estat fent una petita cerca per internet i sembla que el teu maquinari està suportat pel driver "snd_hda_intel", però alguns parlaven de la versió 1.0.15 d'ALSA, mentre que la Gutsy porta la 1.0.14. Total, que si es confirma el que et dic, o bé t'hauràs d'esperar a que ubuntu incorpori la nova versió d'ALSA, o bé te l'hauràs de baixar i compilar-la a mà. No és complicat, però és emprenyador, perquè cada vegada que s'actualitza el nucli has de recompilar de nou.

De moment pots fer "sudo modprobe snd-hda-intel" a veure si es queixa o no. Després de fer-ho, executa el programa "alsamixer" des de la consola. Si no dóna error és que ja tens accés a la targeta de so.

---

### Post by CarlesOriol on 2007-10-29
Un dia ens has d'explicar com fas el grep KDE ;-)

---

### Post by CarlesOriol on 2007-10-29
> **farigola said:**
> dispositiu MIDI ALSA per seleccionar. 


Eps... Anem per parts. El so digital i el midi son dues coses diferents.
Primer localitzem el problema de l'audio i després amb eines com el timidity pots cercar al fòrum com configurar el midi.

---

### Post by farigola on 2007-10-29
Gràcies per els vostres comentaris. Aquest vespre intentaré fer les proves indicades per l'Orestes. De totes maneres he vist que hi ha molts usuaris que tenen el mateix problema i crec que cap d'ells disposa d'una solució. Amd 64, Gutsy
De ben segur que això tindrà solució, ja que no crec que jo sigui l'únic mortal amb aquesta configuració.
Gràcies per les vostres aportacions. En breu tindreu resposta.

---

### Post by farigola on 2007-10-29
Després de seguir les vostres indicacions el sistema contesta amb el següent error
Jordi@farigola:~$ sudo modprobe snd-hda-intel

FATAL: Module snd_hda_intel not found

Doncs ja tinc un problema.

Estic una mica sorprès per el comportament d'aquesta versió. Sota el meu punt de vista penso que noves versions consoliden anteriors. Potser estic confós i no tinc raó, però després d'haver utilitzat aquest ordinador correctament amb l'anterior versió i veure que ara no tinc altre que fer una compilació, llavors, quedo un xic atemorit. Això no està a l'abast de tothom. Sort que hi ha gent com vosaltres que sous autèntics pous de ciència.

---

### Post by farigola on 2007-10-30
Hola he vist que a la plana principal de ALSA http://www.alsa-project.org/main/index.php/Main_Page" hi ha la versió actual del driver. No se tindré la paciència suficient d'esperar a que Ubuntu incorpori el driver doncs això és una batalla ja personal a casa, jo amb la defensa de Linux i al dona constantment amb la retòrica de que amb Windows tot això no passava. (lla veritat sigui dita, fot molt).
De totes maneres, segueixo a la recerca d'informació.

---

### Post by farigola on 2007-11-14
Desprès de moltes proves he instal·lat un paquet linux-sound-base_1.0.15-2_all.deb  de la llista de paquets d'Ubuntu, gràcies aquest paquet he vist com s'ha instal·lat un dispositiu MIdi trought port-0 - Alsa drive. Fins ara no havia vist res en la secció MIDI. De totes maneres, no aconsegueixo activar l'audio de l'equip. 

No tinc coneixements com per anar més lluny amb aquest tema. El comentari fet per l'Orestes de compilar resulta complicat. Estic per comprar  una targeta que funcioni per l'equip tot i que això es podria definir com tirar la tovallola i poc intel·ligent. 
Al executar sudo modprobe snd-hda-amd i el mateix per intel. El sistema diu que no s'ha trobat el mòdul. Jo tinc un AMD

Abans no tenia el directori SND. Ara si que el tinc

---

### Post by farigola on 2007-11-16
He instal·lat una nova targeta de so a l'ordinador, concretament la Trust SC-5200 El sistema la ha detectat sense cap problema i funciona perfectament.

No és la solució més adient ni tècnica, però de ben segur que el coneixement adquirit és important.

---

