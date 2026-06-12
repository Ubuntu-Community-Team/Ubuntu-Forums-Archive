---
title: "Mandriva"
date: 2009-12-10
forum: Catalan Team
---

### Post by Comuner on 2009-12-10
Hola tothom! Fa poc m'he comprat un netbook i per defecte em be amb Mandriva. El portàtil no te gaire historia... 512 de RAM un processador a 1,6 i 120 de HD.... 
 El cas es que a aquesta distribució Linux no m'acaba de fer el pes. Jo a la meva màquina porto Ubuntu i trobo q Mandriva li falta alguna cosa. 

 La questió es que m'agradaria posar-me un altre distribució Linux pero no se quina aniria be per el portàtil.

Alguna suggerencia? Estic obert a qualsevol cosa.

---

### Post by kukat on 2009-12-10
No l'he provada, però jo diria que amb la versió d'Ubuntu per a portàtils, t'aniria de meravella!

[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)


I si amb 512 de RAM et va un poc lent, pots instal.lar-li l'entorn gràfic XFCE que utilitza menys recursos que GNOME (el que ve per defecte amb Ubuntu)


Ací et diuen com fer-ho: [http://www.ubuntu-es.org/?q=node/118018](http://www.ubuntu-es.org/?q=node/118018)

També comenten LXDE, que encara és mes lleuger.......depenent de com et vaja de ràpid tria un o altre....

:)

---

### Post by Comuner on 2009-12-10
Gracies per contesta kukat! Em miraré el ubuntu amb aquest entorn gràfic que te molt bona fila...espero no tindre problemes ;) ademés per ho q he vist està molt ben explicat
 Aquest cap de setmana ja tinc feina!!! jejeje

Saluts!!

---

### Post by jdk9 on 2009-12-10
Home, el Ubuntu Netbook va bé per aquestes màquines, i per ficar-te l'XDE (perdò, XFCE), no sé, a mi no em va agradar.

Salut!

---

### Post by kukat on 2009-12-10
Tot i que és una mica diferent del GNOME (el sistema gràfic per defecte a Ubuntu), el XFCE és més lleuger. 
De totes formes pots elegir amb quin gestor de finestres arrancar al menú de "login", cada vegada que vulgues. 

Per si vols pegar-li una mirada a la guia: [http://ubuntuforums.org/showthread.php?t=1217332](http://ubuntuforums.org/showthread.php?t=1217332)

El nostre company Miquel Ubuntero va fer una guia del Xubuntu (Ubuntu amb XFCE). 

De totes formes, si et va de meravella amb GNOME, no cal fer res...però igual et va una mica lent...

---

### Post by SiscoGarcia on 2009-12-10
> **jdk9 said:**
> Home, el Ubuntu Netbook va bé per aquestes màquines, i per ficar-te l'XDE, no sé, a mi no em va agradar.

Què vols dir quan dius XDE? LXDE? XFCE? KDE? Ho dic perquè pot portar a confusió ja que XDE no és cap tipus d'escriptori però s'assembla a aquests altres.

En qualsevol cas, pels gustos els colors... i els sabors. I d'això estem parlant, dels [sabors]("https://wiki.ubuntu.com/CatalanTeam/Recursos/Versions_Ubuntu") d'ubuntu ;)

---

### Post by orestesmas on 2009-12-10
Sembla que s'està estenent la llegenda urbana que XFCE és un escriptori lleuger, però jo sempre que l'he provat no l'he trobat pas tant ràpid com diuen.

I és que, si bé sobre el paper hauria de ser més ràpid, resulta que moltes distribucions (Ubuntu entre elles) me li casquen l'OpenOffice per escriure cartetes, el Firefox de navegador, i el Thunderbird com a client de correu, i ja em teniu les pobres màquines (que acostumen a tenir pocs recursos, d'aquí que usin XFCE) arrossegant-se per terra.

I no parlem de la resta d'aplicacions, ja siguin de KDE o Gnome, que per poder funcionar han de carregar en memòria un caramull de llibreries que no contribueixen precisament a la lleugeresa.

Si voleu llegir un estudi una mica documentat sobre el tema podeu mirar [http://ktown.kde.org/~seli/memory/desktop_benchmark.html](http://ktown.kde.org/~seli/memory/desktop_benchmark.html)

En resum: no s'hi val a repetir tòpics sense haver-los experimentat abans. Jo recomano provar totes les opcions possibles abans de decidir-se per una en concret.

---

### Post by SiscoGarcia on 2009-12-10
> **orestesmas said:**
> Sembla que s'està estenent la llegenda urbana que XFCE és un escriptori lleuger, però jo sempre que l'he provat no l'he trobat pas tant ràpid com diuen.

No sé si s'està estenent ara aquesta llegenda o ja fa temps que corre; de fet, jo me la vaig creure fins que vaig veure un altre estudi (per cert, molt interessant el que proposes) que comparava les escriptoris XFCE, Gnome i LXDE (diria que el KDE no hi era, potser per una altra llegenda) amb les aplicacions nadives i va desmitificar l'XFCE, que va resultar més pesant fins i tot que Gnome. (Sento no poder acompanyar la font, no l'he trobada, però es documentava cronometrant el temps que trigava en carregar aplicacions nadives de cada escriptori).

> **orestesmas said:**
> En resum: no s'hi val a repetir tòpics sense haver-los experimentat abans. Jo recomano provar totes les opcions possibles abans de decidir-se per una en concret.

És el que deiem dels colors i els sabors ;)

---

### Post by kukat on 2009-12-11
ajjjaj

Probablement siga cert. Jo tinc a un PC amb 128 de RAM l'Ubuntu Karmic Koala amb Fluxbox!!! Però no se....aquest tipus d'escriptori si que és un poc estrany!!!
Però he vist coses realment magnífiques amb Fluxbox! (altra cosa es saber configurtar-les!)
[http://www.fluxbox.org/screenshots/](http://www.fluxbox.org/screenshots/)

Jo el que faria és instalar el Karmic Koala amb **ext4 **(que va més ràpid) i provar els diferents entorns gràfics si veus que vols més rapidesa. 


Per a instal.lar-los:

Gnome (per defecte)
Kde : sudo apt-get install kubuntu-desktop ([tutorial i comentaris]("http://paraisolinux.com/instalar-kde-en-ubuntu-karmic-9-10/"))
XFCE :sudo apt-get install xubuntu-desktop
LXDE: sudo aptitude install lxde ([tutorial i comentaris]("http://vladimirklimsa.com/2009/01/lxde-instalacion-y-customizacion-en-ubuntu/"))
Fluxbox: sudo aptitude install fluxbox  ([tutorial i comentaris]("http://ubuntuforums.org/showthread.php?t=1159530"))

Una vegada instales l'escriptori que vulgues, en la pantalla de "login", en "Sessió", pots elegir l'entorn gràfic.

---

### Post by jdk9 on 2009-12-11
> **SiscoGarcia said:**
> Què vols dir quan dius XDE? LXDE? XFCE? KDE? Ho dic perquè pot portar a confusió ja que XDE no és cap tipus d'escriptori però s'assembla a aquests altres.

Error corretgit, mersi!

> **orestesmas said:**
> Sembla que s'està estenent la llegenda urbana que XFCE és un escriptori lleuger, però jo sempre que l'he provat no l'he trobat pas tant ràpid com diuen.

I és que, si bé sobre el paper hauria de ser més ràpid, resulta que moltes distribucions (Ubuntu entre elles) me li casquen l'OpenOffice per escriure cartetes, el Firefox de navegador, i el Thunderbird com a client de correu, i ja em teniu les pobres màquines (que acostumen a tenir pocs recursos, d'aquí que usin XFCE) arrossegant-se per terra.

Amén!

---

### Post by Comuner on 2009-12-16
Senyors, i senyores, jo no entenc massa d'informàtica. Soc un usuari normalet que li agrada ubuntu (i latres distribucions linux) per la sencillesa i claretat del SO. Es rapid i fiable. Però el portàtil que em vaig comprar se'm va petar ahir després de 3 dies d'utilitzar-lo! A mi mandriva no em va agrdar gens, tmb es cert que el portàtil no era massa bo. El fet es q al final he tingut q agafar-me un amb XP; ara li estic posant el ubuntu q em va recomanar kukat. Ja os diré q tal funciona pq només arrancar el netbook nou amb xp... PLONC! ja em va fallar un parell de programas....  ayyyyyyy q ben acostumat que estic.

---

### Post by CarlesOriol on 2009-12-18
També hi ha una llegenda al fòrum que explica que el papapep va anar a cercar un usuari que escrivia estil "pq x q" i li va fer menjar el teclat.

Però no pateixis ningu' no ha aconseguit demostrar-ho.

---

### Post by jdk9 on 2009-12-19
> **Comuner said:**
> Senyors, i senyores, jo no entenc massa d'informàtica. Soc un usuari normalet que li agrada ubuntu (i latres distribucions linux) per la sencillesa i claretat del SO. Es rapid i fiable. Però el portàtil que em vaig comprar se'm va petar ahir després de 3 dies d'utilitzar-lo! A mi mandriva no em va agrdar gens, tmb es cert que el portàtil no era massa bo. El fet es q al final he tingut q agafar-me un amb XP; ara li estic posant el ubuntu q em va recomanar kukat. Ja os diré q tal funciona pq només arrancar el netbook nou amb xp... PLONC! ja em va fallar un parell de programas....  ayyyyyyy q ben acostumat que estic.

Jo hem vaig passar a Ubuntu perquè cada 2 mesos em petava el Windows.

Però que ha fallat? Diga-ho, que potser és una tonteria ;)

---

