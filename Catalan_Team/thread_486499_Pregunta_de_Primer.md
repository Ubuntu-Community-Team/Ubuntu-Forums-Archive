---
title: "Pregunta de Primer"
date: 2007-06-28
forum: Catalan Team
---

### Post by prostata on 2007-06-28
A part de syanptic o Adept per instal-lar o des instal-lar programes, voldria  fer servir les commandes per terminal, aixì si vull instal-lar per exemple google earth, thunderbird 2.0 o qualsevol altre programe per terminal, quina és la sentencia estandard??

Gràcies

PD i per des-instalar??

---

### Post by nvteighen on 2007-06-28
(Lástima que no sepa el hermoso catalá, pero creo haber entendido tu mensaje perfectamente)
La forma más común para instalar y desinstalar a través del terminal es:
```

sudo apt-get update
sudo apt-get install *nombre*

```
(El primer comando es para ver si hay nuevos paquetes. El segundo es el que instala; el nombre del paquete es el que aparece en Synaptic)

Para desinstalar:
```

sudo apt-get remove *nombre*

```

Y el nombre es el que aparece en Synaptic.

---

### Post by telejet on 2007-06-28
a part del apt-get també pots utilitzar gdebi (no per terminal) només obrint un arxiu .deb descarregat i te l'instal·la.

Per terminal també pots utilitzar per terminal el dpkg per instal·lar paquets .deb descarregats fent dpkg -i nom.deb

Per coses com el google-earth de la web et descarregues un fitxer .bin. Primer l'has de fer executable amb chmod +x GoogleEarthLinux.bin
i seguidament l'executes fent ./GoogleEarthLinux.bin i llestos

Fins ara,

Ivan

---

### Post by marcoil on 2007-06-28
Si entens l'anglès, aquí tens dues bones guies sobre l'ús d'apt:

Apt-get Guide - Linuxhelp Wiki
[http://wiki.linuxhelp.net/index.php/Apt-get_Guide](http://wiki.linuxhelp.net/index.php/Apt-get_Guide)

APT HOWTO
[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)

---

