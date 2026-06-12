---
title: "[SOLVED] Problema Amb Partició Ntfs"
date: 2007-11-13
forum: Catalan Team
---

### Post by kukat on 2007-11-13
Hola a tots!!

Tinc un petit problema amb una partició NTFS, que ara la necessite, però des de primera hora m'ha donat aquest error:

$MFTMIrr does not match $MFT (record 0). Failed to mount "/dev/sda3":Input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows TWICE. The usage of the /f parameter is very important! If you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/ directory, (e.g./dev/mapper/nvidia_eahaabcc1). 

Quant faig a consola sudo mount /dev/sda3 hem diu:can't find /dev/sda3 in /etc/fstab or /etc/mtab.

No està ben muntada? O es algun altre problema?

---

### Post by RainCT on 2007-11-13
El missatge d'error aquest et diu ben clarament que sembla ser que hi ha algun error amb el sistema d'arxius, i el que has de fer: Entra al windows, obre-hi una consola (Inici -> Executa -> "cmd") i executa-hi "chkdsk /f", i per acabar torna a iniciar l'ordinador dos cops, els dos cops entrant al Windows.

Ja has provat això?

---

### Post by kukat on 2007-11-13
Ups!!! La veritat es que ho havia llegit, però no entenia per a que deuria servir aixó... Doncs si, la solució era eixa. Es veu que el disc tenia alguns errors, o alguna cosa així. 
Disculpeu les molèsties. (un servidor ja s'ha carregat moltes vegades l'ubuntu i el windows i no sabia que fer...:oops:

---

