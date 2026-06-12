---
title: "Recuperar dades en Ext4 amb extundelete"
date: 2009-05-28
forum: Catalan Team
---

### Post by kukat on 2009-05-28
He baixat el programari [extundelete]("http://extundelete.sourceforge.net/") i l'he compilat.

Primer amb l'Ubuntu no em deixava ja que estava la partició on es troba el que vull recuperar muntada, i he decidit fer-ho des de Debian.

kukatdebian:/home/kukat/Desktop/extundelete-0.0.8/src# ./extundelete /dev/hda6 --restore-directory /home/kukat/Imatges
WARNING: Extended attributes are not restored.
Loading group metadata ... 746 groups loaded.
Loading journal descriptors ... extundelete: extundelete.cc:1567: void init_journal(struct_ext2_filsys*, journal_superblock_t*): Assertion `be32_to_cpu(&tmp) == 0xc03b3998U' failed.
Avortat


Però em surt eixie error. Algú sap el que pot ser??? 

Salut!

---

