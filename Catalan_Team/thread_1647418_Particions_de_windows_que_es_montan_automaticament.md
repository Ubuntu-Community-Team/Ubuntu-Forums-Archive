---
title: "Particions de windows que es montan automaticament a l'inici"
date: 2010-12-17
forum: Catalan Team
---

### Post by akyra on 2010-12-17
Hola gent,

Ahir em vaig instalar el "ntfs-conf" i a l'acabar d'instalar em va marcar les carpetes que són particions de windows. Al acceptar es montan automàticament quan engego l'ordinador i m'apareixen en el escriptori, i no les puc desmontar a no ser que sigui superusuari.

Voldria que aquestes particions no es muntesin automàticament, com feia fins ara, ja que són carpetes que no hi accedeixo pràcticament mai i si vull,  només haig de clickar a sobre de la partició en el Nautilus.
Si que vull es que es montin els dispositius externs, també com fins ara.

Algú sap com es fa?

Salutacions.

---

### Post by wgarcia on 2010-12-17
Vols dir que vols que discs USB es muntin abans d'iniciar l'escriptori o en volumns concrets i no a /media? Això ho pots fer amb el fitxer /etc/fstab, em sembla que el ntfs-config és per muntar les particions ntfs del disc intern.

---

### Post by akyra on 2010-12-19
Bé, ja ho solucionat.

Al instal·lar el "ntfs-conf" m'ha modificat el "fstab" afegint les linees de codi corresponent a les particions de windows, però ha guardat una copia del "fstab" antic, que es diu "fstab-ntfs-config-save". En aquest arxiu està com el tenia originalment, així que només he tingut que canviarlo de nom per tornar el fstab que tenia anteriorment.

La diferencia entre el "fstab" original i el que ha creat el "ntsf-config" era que afegia aquestes linies entre la partició de "/home" i la de "swap", de forma que les muntava automàticament al inciar la sesió:

> proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=59e51ba4-7771-471f-93a2-18ba91c2dd28	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda7 :
UUID=9a173726-00bb-423d-9f4f-7f0db97a40c6	/home	ext4	defaults	0	2
#Entry for /dev/sda3 :
UUID=4A6FEC9E736B3373	/media/DATOS	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda2 :
UUID=2252F5F352F5CC13	/media/Vista	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda1 :
UUID=C62CF3CB2CF3B491	/media/WinRE	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda6 :
UUID=c304b894-a35c-4de2-acf5-189d6dcbfbe5	none	swap	sw	0	0

Bé, ho deixo per si algú li pot fer falta.

Salutacions.

---

