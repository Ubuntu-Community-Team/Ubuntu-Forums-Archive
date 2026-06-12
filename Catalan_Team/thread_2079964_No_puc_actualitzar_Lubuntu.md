---
title: "No puc actualitzar Lubuntu"
date: 2012-11-02
forum: Catalan Team
---

### Post by Arteazul on 2012-11-02
Hola tots.

Ja fa un pareil de setmanes que quan tracte d'actualitzar el meu lubuntu del notebook, hem dona el següent missatge:

El sistema de paquets està malmès

Comproveu si esteu utilitzant dipòsits de tercers. Si aquest és el cas, és recomanable que els inhabiliteu, ja que són una font habitual de problemes.
Addicionalment, hauríeu d'executar l'ordre següent en un terminal: apt-get install -f

Detalls:

Els paquets següents tenen dependències sense satisfer:

libc6: Depends: libc-bin (= 2.15-0ubuntu10) però 2.15-0ubuntu10.3 està instal·lat
libc6-dev: Depends: libc6 (= 2.15-0ubuntu10.2) però 2.15-0ubuntu10 està instal·lat
           Depends: libc-dev-bin (= 2.15-0ubuntu10.2) però 2.15-0ubuntu10.3 està instal·lat

Algú em podría ajudar? Moltes gràcies :)

---

### Post by 19preguntes on 2012-11-03
Hola,
he trobat aquest [enllaç]("http://askubuntu.com/questions/203301/how-to-safely-upgrade-from-ubuntu-12-04-to-12-10") (en anglès) on expliquen com eliminar els dipòsits de tercers. Però vaja, potser és més prudent que t'esperis a que et respongui algú més expert ;)

Salut!

---

### Post by Arteazul on 2012-11-03
Doncs no ho conseguisc arreglar amb estos consells. Són molt diferents, però moltes gràcies. A veure si algú més expert em pot dir alguna cosa. Gràcies.

---

### Post by wgarcia on 2012-11-03
Suposo que hauràs provat primer el que et suggereix el missatge d'error, o sigui obrir una terminal i entrar la següent instrucció:

```
sudo apt-get install -f
```

Si això no ho arregla pots provar:

```
sudo apt-get update
```

seguit de 

```
sudo apt-get dist-upgrade
```

o sinó directament

```
sudo apt-get install libc6 libc6-dev
```

---

### Post by Arteazul on 2012-11-03
Doncs ja ho havia intentat i ho he tornat a intentar, però ni així. He provat també tots els teus passos, he tractat d'actualitzar després, i no ha funcionat...

---

### Post by Arteazul on 2012-11-03
jo, desespere un poc... des de que no puc actualitzar l'ordinador, comença a anar molt pitjor... Vinga, una ajudeta :)

---

### Post by wgarcia on 2012-11-04
Prova la següent seqüència a veure si ho arregla:

```
sudo apt-get remove libc6 libc6-dev
sudo apt-get update
sudo apt-get upgrade
```

Si així s'acaba d'actualitzar després pots intentar

```
sudo apt-get install libc6 libc6-dev
```

---

### Post by Arteazul on 2012-11-04
jo, doncs tampoc!! :(

Alguna altra sugerència? M'està desesperant. Jo no li he fet res :(

---

### Post by wgarcia on 2012-11-05
Però quin missatge d'error et dóna? Fixa't que de moment no ho has dit i així és molt difícil esbrinar el que està passant...

Per cert, mirant el teu primer missatge, també s'hauria de fer

```
sudo apt-get remove libc6-dev-bin
```

---

### Post by Arteazul on 2012-11-06
Hem diu el següent quand done el comandament sudo apt-get remove libc6 libc6-dev y després ja no hem deixa instalar res... què faig?:


xserver-xorg-video-sisusb : Depèn: libc6 (>= 2.7) però no serà insta&#320;lat
 xserver-xorg-video-tdfx : Depèn: libc6 (>= 2.1.3) però no serà insta&#320;lat
 xserver-xorg-video-trident : Depèn: libc6 (>= 2.7) però no serà insta&#320;lat
 xserver-xorg-video-vesa : Depèn: libc6 (>= 2.1.3) però no serà insta&#320;lat
 xserver-xorg-video-vmware : Depèn: libc6 (>= 2.4) però no serà insta&#320;lat
 xterm : Depèn: libc6 (>= 2.11) però no serà insta&#320;lat
 xz-utils : Depèn: libc6 (>= 2.7) però no serà insta&#320;lat
 yelp : Depèn: libc6 (>= 2.3.6-6~) però no serà insta&#320;lat
 zeitgeist-core : Depèn: libc6 (>= 2.4) però no serà insta&#320;lat
 zenity : Depèn: libc6 (>= 2.4) però no serà insta&#320;lat
 zip : Depèn: libc6 (>= 2.7) però no serà insta&#320;lat
 zlib1g : Depèn: libc6 (>= 2.4) però no serà insta&#320;lat

---

### Post by wgarcia on 2012-11-06
Després de 

```
sudo apt-get update
sudo apt-get upgrade
```

què et diu exactment? El que poses en el primer missatge?

---

### Post by Arteazul on 2012-11-06
Sí. NO canvia la cosa.

---

### Post by wgarcia on 2012-11-07
Una pregunta que t'hauria d'haver fet des del principi: quina actualització estàs intentant fer? D'una versió a una altra? Dins d'una mateixa versió simplement actualització de programari?

---

### Post by Arteazul on 2012-11-07
simplement actualització de programari

---

### Post by wgarcia on 2012-11-07
I quina versió d'Ubuntu tens?

Intenta també sisplau enganxar el fitxer 

```
/etc/apt/sources.list
```

a

[http://paste.ubuntu.com](http://paste.ubuntu.com)

i posa l'enllaç aquí.

---

### Post by Arteazul on 2012-11-08
Aquí el tens... :)

[http://paste.ubuntu.com/1343104/](http://paste.ubuntu.com/1343104/)

---

### Post by wgarcia on 2012-11-08
L'únic que veig que pot estar causant el problema que observes és que tens habilitada la fons de programari "backport". Aquest fons de programari fa que s'instal·lin alguns paquets que encara estan en prova. No estic segur, però potser això causi que algunes versions s'hagin creuat per a libc6. 

Es pot provar doncs inhabilitar "backport". Mira a "Paràmetres de Sistema" -> "Sistema", clica sobre "Fons de programari", i a "Actualitzacions" veuràs marcat "Backports", desmarca'l. Tanca "Fons de programari". 

Des d'una terminal prova:

sudo apt-get install --reinstall libc6

a veure què fa.

---

### Post by wgarcia on 2012-11-09
Rectifico: el dipòsit "backports" és per a programari que s'actualitza després que ha sortit la versió d'Ubuntu que s'està utilitzant. Per exemple: quan surt una nova versió d'Ubuntu la versió de Firefox pot quedar congelada fins a la següent versió, simplement rebent actualitzacions de seguretat o correcció d'errors sense avançar versió. Però a vegades es decideix actualitzar aquest programari (Firefox, LibreOffice, etc) al dipòsit "backports", sobretot quan es tracta de versions d'Ubuntu de llarg termini (LTS). 

De totes maneres per provar que no quedi, prova el que t'he dit, i si no ho arregla torna a habilitar el dipòsit "backport".

---

### Post by Arteazul on 2012-11-09
en les mateixes estic...

---

### Post by wgarcia on 2012-11-10
Pots enganxar el resultat de la següent instrucció?:

```
uname -a
```

---

### Post by Flocdemer on 2013-01-17
Has provat de mirar si hi ha paquets actualitzables?
Ho pots mirar des de sistema-gestió d'actualitzacions
També ho pots mirar fent una consulta: aptitude search "?upgradable".
Però suposo que el que vols és canviar de distribució. No ho he fet mai però no seria millor actualitzar i després pujar a una nova distribució?
També pots provar d'instal·lar els paquets que et convinguin amb la opció --reinstall d'apt-get.
De quin ubuntu es tracta i com està el fitxer /etc/apt/sources.list.

Que no en tinc ni idea, però com que veig que hi ha poc moviment...

------------------------------

ups, em sembla que m'he oblidat de llegir fins la pàgina 3...



----------------------------------------

He trobat una llista de repositoris per ubuntu precise a : 

És interessant el que està a [http://ubuntuguide.org/wiki/Ubuntu_Precise_Repositories](http://ubuntuguide.org/wiki/Ubuntu_Precise_Repositories)
**Edit the repository sources list **

La única diferència són les tres útlimes línies:
## Medibuntu - Ubuntu 12.04 "Precise Pangolin" ## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/) deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free  # Google software repository deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

Però hi ha una cosa que no entenc. Per què apareix el oneiric a sources.list?

El cas és que si tens l'oneiric aquí pots trobar els repositoris: [http://ubuntuguide.org/wiki/Ubuntu_Oneiric_Repositories](http://ubuntuguide.org/wiki/Ubuntu_Oneiric_Repositories)

---

