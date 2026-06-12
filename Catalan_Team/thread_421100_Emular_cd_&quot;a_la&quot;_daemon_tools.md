---
title: "Emular cd &quot;a la&quot; daemon tools"
date: 2007-04-24
forum: Catalan Team
---

### Post by boriffus on 2007-04-24
Hola.
Algu coneix cap aplicació per a l' ubuntu que permeti crear unitats de cd/dvd virtuals per carregar-hi imatges iso, mdf... Amb la passada versió (la 6.??) vaig estar buscant i no vaig trobar res, i la nova la vaig instal·lar tot just ahir, i tampoc no ho he mirat, però com que he trobat aquest fòrum he pensat que potser algú de vosaltres ho sap. Gràcies!

Salut!

---

### Post by marcoil on 2007-04-24
> **boriffus said:**
> Hola.
Algu coneix cap aplicació per a l' ubuntu que permeti crear unitats de cd/dvd virtuals per carregar-hi imatges iso, mdf...

A Linux no s'empren unitats, sinó que tots els dispositius als que vols accedir es *munten* a un lloc determinat de l'arbre d'arxius (que comença a */*).

Pots veure els diferents dispositius i a on estan muntats amb la comanda *mount* sense arguments. Per modificar aquesta llista, has d'emprar *mount* com a súper-usuari (és a dir, amb *sudo*).

Fer accessible una imatge ISO a qualsevol directori (que ja existeixi) es pot fer emprant el dispositiu loop, que fa que qualsevol arxiu aparegui com un dispositiu:

```
$ sudo mount -t iso9660 -o loop imatge.iso /media/tmp
```
Això és equivalent a carregar un CD (o DVD) al directori */media/tmp*.

Quan hagis acabat d'emprar la imatge, pensa a desmuntar-la emprant

```
$ sudo umount /media/tmp
```

Esper que t'hagi estat d'ajut!

---

### Post by boriffus on 2007-04-24
És clar! En què estaria jo pensant... Per això les meves recerques sobre un programa que ho fés no donaven cap resultat, i és que no cal cap programa! 

Moltes gràcies per la resposta, per un moment, he vist "la llum"!
boriffus

---

