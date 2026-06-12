---
title: "Signar i Xifrar amb la clau ACCV Generalitat Valenciana"
date: 2009-08-19
forum: Catalan Team
---

### Post by sebastia2000 on 2009-08-19
Salut.
Fa poc he demanat la "firma digital" da la autoritat Certificadora de la Generalitat Valenciana.
Et donen  dos fitxers amb extensió .p12, uno per firmar i altre per xifrar.

Ubuntu 9.04 te per defecte el programa Seahorse per a gestionar i utilitzar les claus PGP (crec qeu estic dient-ho bé).

La meua pregunta:

1. Es poden afegir aquestos fitxers de la ACCV al software aquest i utilitzar-los per xifrar o signar amb el menu contextual que apareix en el nautilus?

Quan ho intente,e a mí em demana generar-les de noves (que a més pareixen d'altre format)i jo voldria utilizar les que ja tinc que m'ha proporcinat la GVA.


Gràcies.

---

### Post by epileg on 2009-08-19
hola,

Tot i que els dos fitxers que t'ha proporcionat l'autoritat certificadora de la Generalitat Valenciana i el GnuPG usen el sistema de claus públiques i privades per a signar i xifrar correus, fitxers, etc. entre ells no son compatibles. El Seahorse és un front end per a GnuPG.

Les claus (pública i privada) que t'han proporcionat et poden servir per a signar/xifrar correus electrònics, des del thunderbird ho podràs fer tot important les claus a: Edita => Preferències => Avançat => Certificats => Visualitza els certificats. També les pots fer servir des del firefox per a autentificar que ets tu quan has de fer alguna gestió telemàtica, com per exemple la presentació de la declaració de renda via Internet.

Si vols tindre un parell de claus del GnuPG ho pots fer de manera molt fàcil des del mateix seahorse. Aquesta et servirà també per a signar i/o xifrar correus electrònics i fitxers.

Salut.

---

### Post by epileg on 2009-08-19
... per cert, pots tindre les dues claus al client de correu Thunderbird tot i que aquest no te suport directe per a GPG, amb l'extenció Enigmail les podràs utilitzar perfectament. Al repositori d'ubuntu hi és (recorda insta&#320;lar també la traducció al Català/Valencià) ;-)

Salut.

---

### Post by sebastia2000 on 2009-08-20
Gràcies epileg per la teva explicació, ja em quede més tranquil sabent que no son compatibles, el que sí vaig fer anit es instal.lar el driver de nisu ([http://dwnl.nisu.org/](http://dwnl.nisu.org/)) i espere testejar-lo avuí, em conformaré amb el aixo.

Per cert, si utilitze una clau generada pel GnuPG per xifrar/signar fitxers...
Ón es queden guardades les claus?
Ho dic per que en cas de reinstal.lar el SO, o dur material xifrat cap a altre ordinador meu...necesitaré la clau priovada generada amb GnuPG.

Gràcies pel teu temps epileg.

;-)



PD:  Ja m'he respost, gràcies.
[http://www.alcancelibre.org/staticpages/index.php/manual-pgp-seahorse/print](http://www.alcancelibre.org/staticpages/index.php/manual-pgp-seahorse/print)
Pareix que seahorse  pot exportar la clau i sino es fa en línia de comandaments.

---

### Post by CarlesOriol on 2009-08-20
Al seahorse tens la opcio' d'exportar la clau privada.

---

### Post by epileg on 2009-08-21
Pots fer còpia de seguretat de les claus desades amb GnuPG des del mateix seahorse, tant les teves (públiques i privades) com les d'altri.

Tingues en compte que quan xifres un fitxer fas servir la clau pública del destinatari, per tant, només ell(s) podrà desxifrar-lo, o sigui que si vols poder desxifrar-lo tu a posteriori, afegeix-te a la llista de destinataris.

Salut,

P.D. perquè serveix el «nisu» aquest?

---

### Post by epileg on 2009-08-22
No en se el motiu però el seahorse no exporta les claus privades! Per fer una còpia de les claus públiques i privades jo de tu ho faria directament des de la línia d'ordres:

$ gpg --armor --output «fitxer_de_sortida» --export-secret-key «filtre» // exporta la clau privada

$ gpg --armor --output «fitxer_de_sortida» --export «filtre» // exporta la clau pública

altres odres per a gpg:

$ gpg --gen-key //gernera un parell de claus (pública i privada)

$ gpg --list-keys //llista totes les claus públiques.

$ gpg --list-keys «filtre» //llista les claus públiques però filtrades

$ gpg --list-secret-keys //llista les claus privades, també es pot filtrar

$ gpg --delete-secret-key ClauID //per a esborrar la clau privada

$ gpg --delete-key ClauID //per a esborrar la clau pública. si hi ha una clau privada associada a la pública que vols esborrar, no et deixarà. primer esborra la privada.

etc.

més informació: $ man gpg

Salut,

---

### Post by sebastia2000 on 2009-08-25
[http://www.nisu.org/](http://www.nisu.org/)

Si no m'enganye, nisu és el equip de desenvolupament (desenrrollament, jejeje) del softwarre/driver del clauer digital. idcat i el el de accv, per cert, deuen ser molt bons per a que la "Generalidad de todos los valencianos" accepte un projecte comú.

Salut!!

---

