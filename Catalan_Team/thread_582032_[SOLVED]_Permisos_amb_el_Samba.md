---
title: "[SOLVED] Permisos amb el Samba"
date: 2007-10-19
forum: Catalan Team
---

### Post by jodufi on 2007-10-19
Hola de nou,

Tinc dos ordinadors connectats entre ells mitjançant Samba. Tot funciona perfectament excepte que només puc llegir, tot i tenir desactivada l'opció de només lectura.

Mirant el fitxer/etc/samba/smb.conf al final hi tinc:

```

[Portatil]
path = /home/laia
available = yes
browsable = yes
public = yes
writable = yes

```

Què faig malament?

Salut

---

### Post by siscuboontu on 2007-10-19
Hola jodufi,

Acabo de llegir el teu comentari i he mirat com ho tinc jo per donar-te una possible solució però m'he trobat que hores d'ara no es veuen els dos ordinadors. Acabo d'actualitzar-me a la 7.10 aquest que estic fent servir. Fa uns dies que tinc actualitzat l'altre ordinador i no he tingut cap problema fins ara (o no me n'havia adonat). La meua pregunta és: és possible que hagi passat en actualitzar l'ubuntu de la 7.04 a la 7.10?

Gràcies.

---

### Post by papapep on 2007-10-19
> Tot funciona perfectament excepte que només puc llegir, tot i tenir desactivada l'opció de només lectura.

Ja has verificat els permisos que tens als directoris i fitxers que vols compartir?

---

### Post by siscuboontu on 2007-10-19
En el meu cas, no puc veure quins permisos té, surt un - però inactiu. L'única cosa que se m'acut és mirar-ho des de l'usuari root, ja que és el propietari segons diu.

Canvio d'usuari i us ho comunico.

---

### Post by jodufi on 2007-10-19
Com molt bé diu el papapep era un problema de permisos. 
Havia canviat tots els permisos d'usuari i de grup, però resulta que els que havia de canviar son els d'altres. Ara sembla que ja funciona, gràcies.

Per cert siscuboontu, jo estic treballant amb un ordinador amb la 7.04 i l'altre amb la 7.10 i tot sembla que funciona.

Salut

---

### Post by siscuboontu on 2007-10-19
Ho sento molt. Sóc bastant novell i no me'n surto. 

En mode gràfic no puc canviar d'usuari i entrar com a root.

Ho provo des de consola, fent "sudo -s", i intento aplicar canvis amb la comanda "chmod -R 777" i seguit de la ruta a la unitat que vull compartir, però res no canvia.

Quin problema hi ha? Alguna idea?

Gràcies.

---

### Post by jodufi on 2007-10-19
En l'Ubuntu l'usuari root està desactivat.

Si vols tocar els permisos i el propietari dels fitxers, millor fes "sudo nautilus", i tindràs el nautilus funcionant amb els permisos del root.

---

### Post by siscuboontu on 2007-10-19
Així ho faig però no canvia res quan miro el tema dels permisos a les propietats de la unitat que hi ha muntada a l'escriptori.

Moltes gràcies, però ho deixo còrrer de moment, ho reprendré en un altre moment.

---

