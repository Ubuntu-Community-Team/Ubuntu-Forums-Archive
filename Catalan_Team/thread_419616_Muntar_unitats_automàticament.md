---
title: "Muntar unitats automàticament"
date: 2007-04-23
forum: Catalan Team
---

### Post by lletisso on 2007-04-23
Cada cop que inicio sessió amb l'Ubuntu 7.04 he de muntar de nou les unitats
Hi ha una manera de fer-ho automàticament?
En realitat, tinc un problema amb el Thunderbird, ja que voldria compartir les carpetes amb Windows.  Les tinc en una unitat NTFS.

A més a més, els assigna nom segons l'ordre en què es munten. I si m'equivoco, ja no coincideixen amb els noms que tenien a la sessió anterior.

---

### Post by basdala on 2007-04-23
La manera més fàcil és fer el següent:

1. Instal·lar el suport per llegir i escriure NTFS des de Automatix 2 ([www.getautomatix.com](www.getautomatix.com))
2. Editar el fitxer /etc/fstab i afegir les unitats a muntar (segueix com exemple les línies que ja hi ha fetes, canviant el tipus de sistema per ntfs quan sigui necessari). Pensa a fer, abans de res, sudo cp /etc/fstab /etc/fstab.bak, per si les mosques.

si tens dubtes sobre com editar els fitxers, posteja el contingut del teu /etc/fstab i les dades de les unitats que vols muntar, així jo o algú et podrà dir que hi has d'afegir.

Sort!

---

