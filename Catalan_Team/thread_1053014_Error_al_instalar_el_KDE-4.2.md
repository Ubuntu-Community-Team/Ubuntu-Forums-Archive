---
title: "Error al instalar el KDE-4.2"
date: 2009-01-28
forum: Catalan Team
---

### Post by tanreb20 on 2009-01-28
Hola. Avui he intentat instalar el nou KDE-4.2

He seguit els apssos de la web, afegir el repositori

```
deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main
```

i després he afegit la clau

```
gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
```


quan intento fer un upate em surt aixo:
```

W: GPG error: http://ppa.launchpad.net intrepid Release: Les següents signatures no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 5DC4E17435661D98
W: GPG error: http://ppa.launchpad.net intrepid Release: Les següents signatures no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 2CC98497A1231595
```


Que puc fer, si faig un sudo apt-key list em surt com que la tinc pero no funciona!

---

### Post by jmaspons on 2009-01-28
A mi també em dona aquest error però això no m'ha impedit poder disfrutar del fantàstic kde 4.2. Si actualitzes amb l'"apt-get dist-upgrade"et dona algun problema?

---

### Post by lluisanunez on 2009-01-31
El mateix li ha passat a en Linus torvalds, i [s'ha passat a Gnome]("http://softlibre.barrapunto.com/article.pl?sid=09%2F01%2F25%2F1051218&from=rss")
:p

---

### Post by jerec on 2009-01-31
Aquí tens la solució del teu problema (tot i que no priva de gaudir del KDE 4.2):

Això, passa perquè launchpad ofereix firmes úniques. 
Tens un petit script que soluciona el problema.
[http://ubuntuforums.org/attachment.php?attachmentid=101390&d=1233230528]("http://ubuntuforums.org/attachment.php?attachmentid=101390&d=1233230528")


La Font d'on he extret la informació:
[http://www.genbeta.com/2009/01/30-solucion-el-error-de-verificacion-de-firmas-gpg-de-launchpad-en-ubuntu]("http://www.genbeta.com/2009/01/30-solucion-el-error-de-verificacion-de-firmas-gpg-de-launchpad-en-ubuntu")

> **lluisanunez said:**
> El mateix li ha passat a en Linus torvalds, i [s'ha passat a Gnome]("http://softlibre.barrapunto.com/article.pl?sid=09%2F01%2F25%2F1051218&from=rss")
:p

Però que te a veure això amb el que faci en Linus?????
També diu que fa servir l'Ubuntu-Kubuntu-Xubuntu-Edubuntu-Gobuntu...?????????
Que el KDE 4 te errades i esta verd, això ho sap tothom, La gent fa servir les X amb el que li be de gust.
Massa sovint relacionem Distribucions amb KDEs, Gnomes i altres i perdem el nord amb l'essència del Linux

---

