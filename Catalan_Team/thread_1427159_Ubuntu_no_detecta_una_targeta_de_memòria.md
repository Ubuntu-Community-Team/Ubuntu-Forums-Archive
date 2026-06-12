---
title: "Ubuntu no detecta una targeta de memòria"
date: 2010-03-11
forum: Catalan Team
---

### Post by lo gambusí on 2010-03-11
Hola!

Vull passar les fotografies de la càmera a l'ordinador i l'Ubuntu (9.10) no em detecta la targeta. He reiniciat l'ordinador amb la targeta posada i sense, l'he posat al cap d'un moment de tindre lo sistema en marxa, de seguida... totes les variables possibles i seguix sense detectar-ho. He provat amb un altre ordinador amb la mateixa versió d'Ubuntu i em dóna lo mateix problema.

La targeta en qüestió és esta: 
[IMG]http://pan9.fotovista.com/dev/9/3/04788139/t_04788139.jpg[/IMG]

Algú sabria ajudar-me?:P 

Gràcies!

---

### Post by ilku on 2010-03-12
Hola company, no crec que sigui un problema de la targeta. Em penso que es un error dels lectors de targetes i els seu mòduls, dintre del sistema.

Prova a posar en un terminal lsusb amb la targeta dintre del lector i comprova que et detecta el lector.

Segurament no veuràs res.

En aquest cas per provar pots editar el grub i on possa
defoptions= quiet splash
afegeix
pciehp.pciehp_force=1

Inicia (amb la targeta dins el lector) i a veure si te la detecta.

Buscant al google veuràs millor explicat això. Ara mateix no tinc el enllaç aquí i ho faig de memòria.

---

### Post by lo gambusí on 2010-03-12
Hola!

Gràcies per la teua ajuda.

La veritat és que no estic entenent res. He posat la targeta per fer això que dius de l'lsusb... i m'ha aparegut de cop la finestra del navegador amb totes les carpetes i les fotos O_O

A què pot deure's este moment d'il·luminació, o la meua nul·litat anterior? No entenc res realment :D

---

### Post by ilku on 2010-03-12
Quina sort!!!!

Nomes llegir el teu missatge he pensat, calla que potser amb l'actualització d'ahir del kernel potser ho van arreglar i tu aquí dient tonteries... prova-ho idiota...
Quina a sigut la meva sorpresa que no ha funcionat :(.
Així doncs m'alegro que et funcioni, jo continuaré investigant quan tingui temps.

---

