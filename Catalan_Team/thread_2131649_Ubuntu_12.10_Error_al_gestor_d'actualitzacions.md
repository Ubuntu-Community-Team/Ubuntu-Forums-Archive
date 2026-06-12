---
title: "Ubuntu 12.10 Error al gestor d'actualitzacions"
date: 2013-04-02
forum: Catalan Team
---

### Post by fvilaubi on 2013-04-02
Des de fa uns dies al arrencar el gestor d'actulaitzacions em deixa una icona rodona vermella amb franja horitzontal blanca (com un senyal de prhibit el pas) i em diu que executi "apt-get" des d'un terminal.
Si faig "apt-get update" des d'un terminal 
> Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) quantal-backports/universe Translation-ca     
Err [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) quantal/restricted Sources                    
  404  Not Found
S'ha baixat 1714 kB en 37s (46,2 kB/s)                                         
S'està llegint la llista de paquets… Error!
W: S'ha produït un error durant la verificació de la signatura. El dipòsit no està actualitzat i s'emprarà el fitxer d'índex anterior. Error del GPG: [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release: Les signatures següents són invàlides: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: S'ha produït un error amb el GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release: Les signatures següents són invàlides: BADSIG 32B18A1260D8DA0B Launchpad PPA for YannUbuntu
W: S'ha produït un error amb el GPG: [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) quantal Release: Les signatures següents són invàlides: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: No s'ha pogut obtenir [http://extras.ubuntu.com/ubuntu/dists/quantal/Release](http://extras.ubuntu.com/ubuntu/dists/quantal/Release)  

W: No s'ha pogut obtenir [http://es.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources](http://es.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources)  404  Not Found

W: No s'ha pogut obtenir gzip:/var/lib/apt/lists/partial/es.archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-amd64_Packages  Encountered a section with no Package: header

W: No s'ha pogut obtenir gzip:/var/lib/apt/lists/partial/es.archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-i386_Packages  Encountered a section with no Package: header

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/es.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-ca
E: No s'han pogut analitzar o obrir les llistes de paquets o el fitxer d'estat.

Alguna idea de que fer?

Francesc.

---

### Post by wgarcia on 2013-04-02
Mira si el que posa en aquest comentari:

[http://ubuntuforums.org/showthread.php?t=2122816&p=12544355#post12544355](http://ubuntuforums.org/showthread.php?t=2122816&p=12544355#post12544355)

et serveix per arreglar-ho.

---

### Post by fvilaubi on 2013-04-03
Ha funcionat perfecte!

Ahir em va passar també al portàtil de casa, que també te el 12.10, aquest vespre provaré si li funciona.
Molt agraït pel teu comentari,

Francesc.

---

### Post by fvilaubi on 2013-04-03
Per cert, no trobo com marcar [SOLVED] al post.
Com ho puc fer?

---

### Post by wgarcia on 2013-04-03
Això ha canviat des que van actualitzar el programari d'aquests fòrums. Abans hi havia una opció a "Thread tools", però ara s'ha de clicar "Edit post" al primer missatge, després "Go advanced" a sota de l'editor, i un cop fet això es veu una pestanya "Prefix" a dalt de tot que té una opció per posar "[Solved]", força complicat, oi?

---

