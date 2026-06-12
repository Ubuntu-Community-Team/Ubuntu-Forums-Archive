---
title: "Ubuntu - Kubuntu"
date: 2009-12-13
forum: Catalan Team
---

### Post by sumba on 2009-12-13
Hola a tots.
Soc un nouvingut a ubuntu i n'estic aprenent.
Com a bon nouvingut, probo tot allò que legeixo als diferents fòrums i llocs web.
Ara tinc un petit problema i necessitaria el vostre ajut.
Vaig instalar Ubuntu, m'en vaig sortint, pero seguidament vais instalar paralelament el Kubuntu.
Ara voldria treure el Kubuntu i deixar el Ubuntu sol.
Em pot orientar algu??.
Gràcies per endevant

Joan

---

### Post by jdk9 on 2009-12-13
Suposo que el vas instal·lar en una altra partició del disc dur, pel que dius. En el cas que sigui així, desde Ubuntu, vés a sistema / administració / gparted (en el cas de que no el tinguis instal·lat, executa un terminal i escriu sudo apt-get install gparted). Allà veuràs les diferents particions del disc dur. Suprimeixes les dos del kubuntu (la del sistema de fitxers i l'swap).
Un cop eliminades, engeges un terminal i escrius sudo update-grub2 (així actualitzaras el Grub). Crec que es fa així, després t'ho confirmo (o que diguin el contrari altres membres del forum)

Salut!

---

### Post by sumba on 2009-12-13
Gràcies jdk9
Mentre espero que confirmis, si pots, he instalat gparted.


Com que primer vaig instalar ubuntu, em suposo que he de mantenir /sda1, /sda2 i /sda5... i esborrar /sda6 i /sda7.

Gràcies altre cop

---

### Post by SiscoGarcia on 2009-12-13
> **sumba said:**
> Com que primer vaig instalar ubuntu, em suposo que he de mantenir /sda1, /sda2 i /sda5... i esborrar /sda6 i /sda7.

Pel que comentes a l'hora de fer les instal·lacions no has separat l'arrel (/) de les dades personals (/home), és cert?

Si és així, pots provar el que dius i no crec que hi hagi problema perquè tens l'arrencada a sda1 (tinguis a mà alguna eina de recuperació de l'arrencada, per si de cas).

Una altra possibilitat és que aprofitis l'ocasió i, arrancant des d'un CD autònom (LiveCD) amb el particionador desfacis tot el que no és sda1 i creïs una partició /home i una nova swap (deixant la sda1 tal com la tens).

---

### Post by lluisanunez on 2009-12-14
Per una altra vegada, no necessites insta&#320;lar dos Ubuntus en dues particions només pel gestor d'escriptori. Pots tenir més d'un gestor insta&#320;lat (Gnome, XFCE, KDE, Enlightenment...) i triar-lo al menú de login > sessions
Per inta&#320;lar un gestor d'escriptori fas:
```
sudo aptitude install xubuntu-desktop
```

---

### Post by sumba on 2009-12-16
Com bon aprenent, m'ha sortit tot al reves.   ;-)

Moltes gràcies a tot hom que s'ha interessat en aquest tema.

Fins aviat

---

### Post by falsospam on 2010-01-01
Com pot esser, despres de lleguir aquest post vaig instalar GNOME sobre Kubuntu 9.10 (AMD) i cap problema, unes setmanes despres instalo en lórdinador dún company el Karmic-Koala de catalana (64b) i res de res que no troba GNOME-DESKTOP ?? Com pot esser??
Algú m'ho explica?

---

### Post by orestesmas on 2010-01-01
Perquè la distribució que vas instal·lar tu és una Kubuntu, que porta el KDE i no el Gnome per defecte. Si vols instal·lar el Gnome posteriorment, has d'instal·lar el paquet "gnome-desktop".

---

### Post by falsospam on 2010-01-02
> **orestesmas said:**
> Perquè la distribució que vas instal·lar tu és una Kubuntu, que porta el KDE i no el Gnome per defecte. Si vols instal·lar el Gnome posteriorment, has d'instal·lar el paquet "gnome-desktop". Justa a la fusta! Aixo hem refereixo no hem troba el paquet "gnome-desktop" en amb S.O. de Karmic-Koala 9.10 de 64 Bits, quan abans si que ho feia. Alguna opcio mes?

---

### Post by CarlesOriol on 2010-01-02
Insta&#320;lar-lo?

sudo apt-get install ubuntu-desktop

---

### Post by falsospam on 2010-01-02
Fins ara he probat:

1º sudo aptitude install ubuntu-desktop
...Res "Hem diu que no s'ha trovat aptitude"
2ª sudo apt-get aptitude
   sudo aptitude install ubuntu-desktop
...Res "Hem diu que no s'ha trovat el paquet ubuntu-desktop"
3ª sudo apt-get install ubuntu-desktop
...Res "Hem diu que no s'ha trovat el paquet ubuntu-desktop"

El CD que vaig utilitzar el trovareu a "http://ftp.caliu.cat/pub/distribucions/ubuntu-cat/kubuntu-darrera-escriptori-amd64-CatalanRemix.iso"
El tema es que no recordo com ho vaig fer l'ultima vegada, fara prop d'un mes. I no se que faig malament o si es que hi ha algun problema als repositoris?

---

### Post by kimet on 2010-01-02
No serà que el paquet es diu "gnome" simplement.

[http://packages.ubuntu.com/karmic/gnome](http://packages.ubuntu.com/karmic/gnome)

Salut.

---

### Post by falsospam on 2010-01-02
Hey gracies al teu link crec que s'ha de fer :
apt-get install gnome-desktop-environment
 de totes formes ara no ho puc provar ja que no tinc la maquina aqui, ja os ho comentare....

---

### Post by kimet on 2010-01-02
A mi em sembla que es  ```
aptitude install gnome
``` i prou. De totes maneres pots prova-ho de totes dues maneres.

salut

---

### Post by orestesmas on 2010-01-02
> **falsospam said:**
> Fins ara he probat:
3ª sudo apt-get install ubuntu-desktop
...Res "Hem diu que no s'ha trovat el paquet ubuntu-desktop"

El tema es que no recordo com ho vaig fer l'ultima vegada, fara prop d'un mes. I no se que faig malament o si es que hi ha algun problema als repositoris?

El paquet "ubuntu-desktop" és als repositoris segur.

Deixa'm aventurar-me: potser vas instal·lar el sistema sense connexió a internet? En aquest cas, potser només tens posats els repositoris del CD, que són una versió reduïda del total perquè per qüestions d'espai no hi cap tot al CD.

Si és així caldrà que activis algun servidor
Ves al menú principal -> Sistema -> KPackagekit -> Arranjaments -> Edita les fonts de programari -> pestanya "Programari Kubuntu" i a lallista desplegable "Baixa de:" escull el servidor que vulguis. Personalment et recomano el de Caliu, que trobaràs a Altres -> Espanya -> ftp.caliu.cat.

A veure si és això, perquè altrament no té explicació lògica amb la informació que ens facilites.

---

### Post by kimet on 2010-01-02
Si, es cert que existeix:
[http://packages.ubuntu.com/karmic/ubuntu-desktop](http://packages.ubuntu.com/karmic/ubuntu-desktop)
Però la quantitat de "palla" és considerable :P.

---

### Post by orestesmas on 2010-01-02
Vols dir que la quantitat de dependències és elevada? Potser si, però:

[LIST=1]
[*]Això passa en qualsevol escriptori. El KDE que duu la Kubuntu també té les seves dependències.
[*]Algunes dependències com ara el cups, l'alsa o l'xorg són comunes a tots els escriptoris, i a la Kubuntu ja estan instal·lades. Per tant, no compten a efectes de l'espai addicional requerit.
[*]Amb les capacitats de disc d'avui en dia, tenir 2 o més escriptoris instal·lats i poder triar quin utilitzes en cada sessió no suposa cap mena de problema. Fins i tot amb 2 o 3 escriptoris diferents, una instal·lació típica d'ubuntu probablement ocupa menys que una de windows 7.[/LIST]

Per tant, jo no em preocuparia especialment de les dependències.

---

### Post by kimet on 2010-01-02
No home no, volia dir que aquest metapaquet instal.la molts programes que no son imprescidibles. Troboo més pràctic instalar els paquets bàsics i escollir entre les aplicacións que més ens agraden de cada escriptori.

Salut i bon any.

---

### Post by CarlesOriol on 2010-01-02
Sí, però també et garanteix la funcionalitat.

Per exemple la insta&#320;lació del kde sense el kubuntu-desktop et deixarà un sistema amb kde però amb un munt de problemes.

---

### Post by CarlesOriol on 2010-01-02
Per cert.
Pel que dius tens un pollastre important al sources.list.
Algun repositori t'està amargant l'existència.

Pots copiar l'arxiu /etc/apt/sources.list per que el veiem.

---

### Post by falsospam on 2010-01-03
Com puc fer per pujar-vos un fitxer en lloc de copiar el contingut?

---

### Post by jdk9 on 2010-01-03
>  una instal·lació típica d'ubuntu probablement ocupa menys que una de windows 7.

Cert del tot!

Si tens problemes amb el repositoris, mira't [aquesta pàgina]("http://repogen.simplylinux.ch/"), a mi em va fer molt de servei sobretot després de tenir problemes amb els repositoris.

Apa salut!

---

### Post by falsospam on 2010-01-05
El problema era que en ser una instalació nova, que mo tenia conexio a internet perque falla el WIFI no s'ha actualitzat i no permetia instalar els paquets ja que no tenia els repositoris. Despres de actualizar via Ethernet ha funcionat ha instalat el gnome-desktop
Gracies a tots !!

---

