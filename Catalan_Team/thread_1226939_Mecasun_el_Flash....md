---
title: "Mecasun el Flash..."
date: 2009-07-30
forum: Catalan Team
---

### Post by anigwei on 2009-07-30
Hola,

No és el primer cop que escric aquí sobre aquest tema, però em té escaldadíssim!! Normalment em busco la vida per google i solc resoldre les coses, però amb el Flash... no puc!!

Quan carrego planes que tenen diversos Flashs incrustats, la màquina es posa a cent per hora fins que s'acaba penjant el Firefox. 

Abans tenia una màquina justeta (Celeron 1.8Ghz) i li fotia les culpes al pobre Celeron, però ara tinc un Pentium IV a 2.4Ghz (suficient per les meves necessitats), excepte per reproduïr Flashos... :( :(

Ja siguin planes plenes de publicitat i banners Flash (acabo per no entrar-hi), o una web plena de videos del youtube incrustats... el firefox es posa a 100 fins que ho fa penjar tot. Ho he provat també amb Opera.

No us dic amb el pobre eeePC a 900Mhz...

Un exemple de plana amb videos que em fot a cent el pobre Optiplex és aquesta: [http://www.mondigital.cat/forum/viewtopic.php?p=53536#53536](http://www.mondigital.cat/forum/viewtopic.php?p=53536#53536)

En uns vint segons, si no tanco la pestanya, el video comença a tallar-se i acaba penjant el Firefox fins que em demana un Kill -9.

Tant mal fotut està el plugin de Flash? (El d'adobe)
Teniu alguna recomanació?
També us passa?

Amb Windows el Flash es comporta perfectament fins i tot amb el meu avi Athlon a 600Mhz!!!!


Salut i gràcies!


PD: Utilitzo Jaunty, amb el Firefox actualitzat a la versió estable.
PD2: L'acceleració i tot el tema gràfic funciona perfectament (Si miro un video amb VLC la càrrega ni es mou).

---

### Post by pauelmaco on 2009-07-30
A mí no hem passa. El vas instalar d'una forma extranya? O ho vas fer per el synaptic? Vas instalar una versió beta?

Jo de tu el desinstalaria i l'instalaria buscant pel synaptic: "Restricted-estras"

---

### Post by anigwei on 2009-07-30
> **pauelmaco said:**
> A mí no hem passa. El vas instalar d'una forma extranya? O ho vas fer per el synaptic? Vas instalar una versió beta?

Jo de tu el desinstalaria i l'instalaria buscant pel synaptic: "Restricted-estras"

Sí, el vaig instal·lar pel synaptic (Total, el que fa és executar un script que es descarrega el d'adobe, no?)

De totes formes, al portàtil (eeePC) el vaig instal·lar a mà (el tgz d'adobe) i el resultat el mateix: Fregeix CPU i va lentíssim.

Sembla que sigui l'únic a qui li passa :cry:

---

### Post by pauelmaco on 2009-07-31
Mira, des de la pàgina d'adobe, et pots descarregar un .deb del flash. Aquest .deb, a mí sempre m'ha funcionat. El que no entenc és perquè has d'instalar un tgz habent-hi un .deb.

---

### Post by anigwei on 2009-07-31
> **pauelmaco said:**
> Mira, des de la pàgina d'adobe, et pots descarregar un .deb del flash. Aquest .deb, a mí sempre m'ha funcionat. El que no entenc és perquè has d'instalar un tgz habent-hi un .deb.

Sí, això és al portàtil, ho vaig fer per esgotar possibilitats..

Però a l'ordinador "gran" hi tinc el paquet de restrictred-extras:

```
andreu@optiplex:~$ dpkg --list |grep flash
ii  flashplugin-installer                      10.0.22.87ubuntu2                                       Adobe Flash Player plugin installer
ii  flashplugin-nonfree                        10.0.22.87ubuntu2                                       Adobe Flash Player plugin installer (transit
andreu@optiplex:~$ 

```

---

### Post by anigwei on 2009-07-31
> **anigwei said:**
> Sí, això és al portàtil, ho vaig fer per esgotar possibilitats..

Però a l'ordinador "gran" hi tinc el paquet de restrictred-extras:

```
andreu@optiplex:~$ dpkg --list |grep flash
ii  flashplugin-installer                      10.0.22.87ubuntu2                                       Adobe Flash Player plugin installer
ii  flashplugin-nonfree                        10.0.22.87ubuntu2                                       Adobe Flash Player plugin installer (transit
andreu@optiplex:~$ 

```

Potser no noteu el problema perquè teniu CPU potent que li fot força bruta?

---

### Post by pauelmaco on 2009-07-31
Ara tinc un bon processador (intel 2 quad core 2.5 ghz -:D de tant en tant va bé gastar-se els diners :D) però amb un pentium 3 a 660mhz, també anava bé.

---

### Post by anigwei on 2009-07-31
> **pauelmaco said:**
> Ara tinc un bon processador (intel 2 quad core 2.5 ghz -:D de tant en tant va bé gastar-se els diners :D) però amb un pentium 3 a 660mhz, també anava bé.

Llavors ja tens un dels quatre cores dedicat íntegrament al Flash ;)

Conyes a part, per eliminar més possibilitats, he esborrat pel complet els plugins de non-free, i m'he baixat el .deb que comentaves.

El resultat: El mateix :(

---

### Post by pauelmaco on 2009-07-31
Doncs noi, no ho entenc :confused: , a mí sempre m'ha funcionat.

Deu ser que els nois d'adobe et tenen una tírria especial ](*,)

---

### Post by pauelmaco on 2009-07-31
I amb altres navegadors que no són el firefox ho has provat? Potser no és cosa del flash, sinó del firefox.

Prova-ho amb l'opera o el seamonkey, potser va bé.

Sort!

---

### Post by kimet on 2009-07-31
Hola nois.

Jo per instal.alr el flashplayer sempre he descarregat el .tar de la pàgina d'adobe, l'he descomprimit i he copiat el fitxer libflashplayer.so a la carpeta de plugins de mozilla...Em sembla que no pot ser mes sencill.:D

Ara bé, la pàgina que poses de mostra també em fa pujar el consum de CPU, pero no s'em penja ni s'atura la reproducció i el meu processador es 2200 d'un sol nucli.

Una sol.lució seria bloquejar els scriptsd e la pàgina i només permetre els que vols en cada moment, hi ha complements del firefox a tal efecte, com:[https://addons.mozilla.org/ca/firefox/addon/722]("https://addons.mozilla.org/ca/firefox/addon/722"). Amb aixó bloqueiges tots els scripts de la pàgina i al clicar sobre la icona de noscript pots permetre que s'executi.

Pot ser no et serveix de res, però per si de cas...

Salut.

---

### Post by anigwei on 2009-07-31
Kimet, el que proposes pot ser una bona solució, però no deixa de ser un "workaround", jeje...

El flipant és que amb Windows mai he tingut problemes amb les mateixes maquines.

Pauelmaco, amb Opera, més del mateix. No obstant, qui fa el consum abusiu de CPU no és l'Opera sinó el OperapluginWrapper (adjunt).

Al servidor (el tinc connectat a la TV) també em dóna molts problemes quan miro el 3alacarta (flash pur i dur en Opera). És un Pentium III a 1Ghz, es porta la mar de bé amb pel·licules (via VLC), però el Flash ídem.....

Crec que sí que els d'adobe em tenen una tírria només a mi :(

---

### Post by kimet on 2009-07-31
No pots comparar el funcionament dels plugins privatius en un i altre sistema perquè obviament, no s'ha invertit el mateix en els de windous que en els de linux i el mateix passa amb el drivers de molt del hardware que hi ha al mercat. Moltes vegades els "workarounts" han sigut la única possibilitat de fer funcionar algun d'aquests components.

Per donarte una idea: Pot ser que el teu problema sigui d'incompatibilitat entre la versió de firefox i la de flashplayer? o de que no haguis desintalat completament els plugins anterior abans d'instalar els nous?.

La meva opció, potser mes militant que practica, és utilitzar els lliures, gnash o swfdec. 

Salutacions.

---

### Post by PatrickVogeli on 2009-07-31
jo diria que no s'hi pot fer massa. En la pagina aquella que has posat, fent un top sense reproduir cap video, el firefox dona un 40% de consum de cpu.. En el meu cas, que tinc un dual core a 1,66GHz, encara tinc marge per a que tot funcioni mes o menys bé, pero es possible que en d'altres maquines, com la teva, la cosa vagi pitjor.

Potser em d'acceptar el plugin de flash funciona millor a windows que a linux; o, pitjor encara, que sigui cosa del firefox.

Salut

---

### Post by oriolsbd on 2009-08-02
Hola,

Prova d'aplicar els consells que ens indiquen a SomGNU, a veure si et va millor:
[http://www.somgnu.cat/2009/08/02/accelerant-el-firefox-i-el-flash-a-ubuntu/](http://www.somgnu.cat/2009/08/02/accelerant-el-firefox-i-el-flash-a-ubuntu/)

Salut!

---

### Post by kukat on 2009-08-03
Jo, amb un AMD Athlon 2200 i 2GB de RAM em fa exactament el mateix....No es problema del firefox, es un problema del FLASH...però segur!! Si no instales el FLASH el firefox vola! XDD

Una bona solució es provar el Opera 10 beta 2, que te la modalitat "turbo" i va realment bé!

[http://www.opera.com/browser/next/](http://www.opera.com/browser/next/)

1 Inconvenient! No és lliure....

---

