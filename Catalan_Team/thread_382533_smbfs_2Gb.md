---
title: "smbfs 2Gb"
date: 2007-03-12
forum: Catalan Team
---

### Post by CarlesOriol on 2007-03-12
Quan creo un arxiu de més de 2 Gb a una unitat ntfs remota connectada per samba em dona un error indicant que he superat la mida màxima.

Algú sap con evitar-ho?

---

### Post by basdala on 2007-03-15
És una limitació del protocol SMB, si no m'equivoco. A Windows té un "apaño" per evitar aquest problema (els XP anteriors a SP1 donaven aquest error també), però és possible que el Samba no. Prova de fer servir un servidor FTP o el protocol FTP over SSH.

---

