---
title: "Tema: Programació:Ajuda construcció de paquet Debian"
date: 2010-06-13
forum: Catalan Team
---

### Post by Catalanoic on 2010-06-13
Hola, estic fent exercicis de programació, en ubuntu he fet un programet simple amb el Lazarus amb poques forms, per provar sabeu, després he instalat el InstalJammer que serveix per crear executables d'instalacio multiplataforma, per instalar programes tan en windows com en linux,freebsd, zip, tar, però la part de linux, m'agradaria apendre a crear un paquet debian .deb que copiï els fitxers del programa i una icona al menu d'Aplicacions i tota la resta. Em podeu ajudar en aquest tema, no en sé res d'això, vaig peix i perdut i necessitaria un pas a pas o un tutorial. 

Gràcies per avançat!!!):P

---

### Post by epileg on 2010-06-13
Jo de tu comneçaria descomrpimint un packet deb qualsevol, per veure com estan construïts. Pots fer proves creant a dins d'un directori buit, tota l'estructura de directoris i fitxers (amb els permisos adequats) que vols posar al sistema destinatari, + un directori anomenat «DEBIAN» a on aniran el fitxer «control», el «md5sum» i si calgués els fitxers «preinst», «postinst», «prerm» i/o «postrm», que com et pots imaginar, aquest fitxers només son scripts que s'executen automàticament abans i després d'insta&#320;lar i d'eliminar, per tant han de tenir permisos d'execució. Un cop fet això,des del mateix lloc a on estigui el directori arrel a on ho has posat tot, executa $ dpkg-deb -b nom_del_directori.
Fes proves. Bona sort! ;-)

Salut.

---

### Post by papapep on 2010-06-13
Hola, Catalanoic.

Una persona que et podria ajudar amb experiència sobre el tema (la qual jo no tinc) és en [Siegfried]("https://wiki.ubuntu.com/RainCT") (RainCT), que és MOTU d'Ubuntu i DC de Debian. Segur que si obres un fil de conversa a la [llista de correu Info]("http://llistes.cpl.upc.edu/listinfo/ubuntucat-info") es donarà per al·ludit. Per aquí s'hi passa a vegades, però va atabalat i tens més probabilitats de que segueixi la llista. :)

---

### Post by Catalanoic on 2010-06-14
> **epileg said:**
> Jo de tu comneçaria descomrpimint un packet deb qualsevol, per veure com estan construïts. Pots fer proves creant a dins d'un directori buit, tota l'estructura de directoris i fitxers (amb els permisos adequats) que vols posar al sistema destinatari, + un directori anomenat «DEBIAN» a on aniran el fitxer «control», el «md5sum» i si calgués els fitxers «preinst», «postinst», «prerm» i/o «postrm», que com et pots imaginar, aquest fitxers només son scripts que s'executen automàticament abans i després d'insta&#320;lar i d'eliminar, per tant han de tenir permisos d'execució. Un cop fet això,des del mateix lloc a on estigui el directori arrel a on ho has posat tot, executa $ dpkg-deb -b nom_del_directori.
Fes proves. Bona sort! ;-)

Salut.

Ho provo ara mateix, gràcies, ja diré per aqui què m'ha sortit.

---

### Post by Catalanoic on 2010-06-14
> **papapep said:**
> Hola, Catalanoic.

Una persona que et podria ajudar amb experiència sobre el tema (la qual jo no tinc) és en [Siegfried]("https://wiki.ubuntu.com/RainCT") (RainCT), que és MOTU d'Ubuntu i DC de Debian. Segur que si obres un fil de conversa a la [llista de correu Info]("http://llistes.cpl.upc.edu/listinfo/ubuntucat-info") es donarà per al·ludit. Per aquí s'hi passa a vegades, però va atabalat i tens més probabilitats de que segueixi la llista. :)
  ok, papapep, contactaré amb ell i em posare a la llista.

---

