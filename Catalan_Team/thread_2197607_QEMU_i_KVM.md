---
title: "QEMU i KVM"
date: 2014-01-04
forum: Catalan Team
---

### Post by akyra on 2014-01-04
Hola a tothom després de temps sense apareixer.

Bé, he instalat al meu cosí l'Ubuntu 13.10, ja tenim un nou usuari, i ara li volia posar una màquina virtual.
Fins ara havia utilitzat VirtualBox o VmWare, però he trobat algun article relacionat amb KVM i amb QEMU i que la versió 13.10 ja ho porta incorporat i volia saber si teniu alguna experiencia amb aquest tipus de software. Agrairia documentació i feedback de les sensacions d'aquest producte envers els altres productes comercials.

Jo en el meu ordinador no tinc la posibilitat de virtualització per hardware, però he vist que funciona molt bé igualment, i jo tinc el Ubuntu 12.04 de 64 bits.

Tinc una mica de dubtes a com utilitzar els dispositius de CD/DVD, que m'obliga a tenir amb CD abans d'engegar la maquina virtual sinó em dóna un error a l'inicar la maquina virtual o m'obliga a reinciar la maquina virtual.

Pel contrari he vist que els dispositus USB 2.0 no cal fer res més que seleccionar-lo, automàticament queda aplicat i es pot utilitzar

Sabeu si hi ha alguna manera que es pugui activar el CD/DVD sense haver de reinciar la màquina virtual?

El Hipervisor que faig funcionar és el Virtual Machine Manager 0.9.1, no sé si hi ha algun de millor.



Salutacions.

---

### Post by CarlesOriol on 2014-01-10
Hola Akira.
El kvm (qemu) és una eina collonuda per virtualitzar servidors. I amb el client remot virt-manager és molt fàcil de configurar. Et permet sense complicacions fer funcionar les màquines virtuals com a serveis.
Però si el que vols és virtualitzar un entorn d'escriptori el virtualbox o el vmware son la teva opció. Acceleració gràfica i fins i tot 3d en algunes configuracions.

Els cds/dvds millor que treballis amb imatges i no amb el suport directament.

Respecte a l'us de usb cal activar o desactivar els perifèrics que vols usar en la màquina virtual (en els entorns d'escriptori és molt senzill).

Carles

---

### Post by Miquel Ubuntero on 2014-01-20
Estic d'acord amb el Carles, fa temps que virtualitzo i, després de provar altres opcions, sempre torno al virtualbox. Sempre treballo amb imatges i no amb CDs tal com també comenta en Carles.
Salut!

---

