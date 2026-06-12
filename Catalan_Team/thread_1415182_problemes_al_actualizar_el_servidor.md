---
title: "problemes al actualizar el servidor"
date: 2010-02-24
forum: Catalan Team
---

### Post by jaumety on 2010-02-24
Hola bone, tinc un servidor amb ubuntu server 9.04 que al fer apt-get update em dona aquest error:
W: Ha ocurrido un error durante la verificación de la firma. El repositorio no se ha actualizado y se usarán los archivos de índice anteriores. Error de GPG: [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates Release Las siguientes firms fueron inválidas: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Imposible obtener [http://es.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://es.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release)

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas

Com ho he de fer per que no em doni aquest error?

Gràcies.

---

### Post by papapep on 2010-02-24
Enganxan's aquí, o a [http://pastebin.ubuntu.com](http://pastebin.ubuntu.com) i posa'ns la url si és molt llarg, el contingut del que tens dins /etc/apt/sources.list.

---

### Post by jaumety on 2010-02-25
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

---

### Post by papapep on 2010-02-25
Podries provar:

Ves al Synaptic (Sistema > Administració > Gestor de paquets Synaptic), i ves a Paràmetres > Dipòsits > Autenticació > Restaura els valors per defecte.

Després tria un altre servidor que no sigui el "es". Qualsevol centre-europeu sol anar prou bé.

Actualitza la base de paquets: tanca el Synaptic i fes a un terminal:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

A veure si així ja no mostra l'error. Si segueix fallant encara ens queda una bala al carregador.

---

### Post by jaumety on 2010-02-25
tinc un problema, i és que no tinc entorn gràfic, com ho puc fer per restaurar els valors per defecte?.

---

### Post by SiscoGarcia on 2010-02-25
Una opció és editar el fitxer /etc/apt/sources.list i canviar "es" per "hu" d'Hongria, per exemple. Un cop fet això, actualitzes i a veure què.

En el teu cas seria:

```
deb http://hu.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://hu.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb http://hu.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://hu.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb http://hu.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://hu.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://hu.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://hu.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb http://hu.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://hu.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://hu.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://hu.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse


deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse 
```

Sort ;)

---

### Post by jaumety on 2010-02-25
perfecte, he canviat el servidor per "hu" i ... oli en un llum.

Gràcies!

---

### Post by SiscoGarcia on 2010-02-25
Doncs ara que ja tens el problema resolt pots posar-te les fonts de caliu, per exemple ;)

És a Sistema>Administració>Fonts de programari>Altres>Servidor ftp de caliu (crec que es diu així).

---

### Post by jaumety on 2010-02-25
ja ho faria, el problema, com ja he dit avans és que no tinc entorn gràfic i no se com canviar les fonts de programa.

---

