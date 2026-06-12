---
title: "WUBI: ara tinc MBR i GRUB alhora..."
date: 2010-12-04
forum: Catalan Team
---

### Post by mrc2407 on 2010-12-04
Bones!!!

He instal·lat Ubuntu 10.10 a través de WUBI a un Windows 7 Professional de 64 bits i no m'ha saltat cap error, he reiniciat l'ordinador i m'ha saltat el MBR (el boot loader de Windows) per triar el SO que vull fer servir. Si entro a Windows 7 va bé, però si entro a Ubuntu des del MBR em porta al GRUB de linux, i allà torno a poder triar entre Ubuntu i Windows. Si aquí li dic Ubuntu, es queda penjat i no fa res...

Alguna idea? Pot ser que desinstal·lant GRUB des d'un CDlive d'Ubuntu funcioni?

Gràcies!

---

### Post by wgarcia on 2010-12-05
Primer assegura't en quin disc vols instal·lar el grub, per exemple un dins d'ubuntu amb la instrucció

sudo fdisk -l 

des d'una terminal et mostrarà les diverses particions dels teus discos. Suposem que le disc on veus que està muntat ubuntu (mirant on tens muntat "/" o altres particions que hagis creat per ubuntu) és "/dev/sda". Ara dones

sudo update-grub

i després

sudo grub-install /dev/sda

Si el disc on tens ubuntu instal·lat no és "sda" substitueix-lo adequadament. Això t'hauria d'instal·lar el grub al MBR (master boot record) del disc.

---

