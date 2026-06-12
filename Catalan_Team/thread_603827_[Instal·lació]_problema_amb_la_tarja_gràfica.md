---
title: "[Instal·lació] problema amb la tarja gràfica"
date: 2007-11-05
forum: Catalan Team
---

### Post by -xavi- on 2007-11-05
Bones,

sóc usuari de windows però de tant en tant feia servir una knoppix instal·lada en una segona partició del disc dur; però m'han parlat molt bé de Ubuntu i m'he decidit a provar-lo.

porto uns quants dies barallant-me amb els cd's de ubuntu (7.10, 7.04 i 6.xx no el recordo) i tinc el problema que he vist en varios fòrums de les targetes gràfiques ATI/Radeon (La meva gràfica és una RADEON X700 (512 MB))

Sé que aquest problema ha estat comentat en més d'un fil. Com per exemple el ([http://ubuntuforums.org/showthread.php?t=405683](http://ubuntuforums.org/showthread.php?t=405683)) però el que m'agradaria saber és com aconseguir que s'iniciï la instal·lació.

A mi no em passa del menú inicial on et pregunta quin tipus d'instal·lació vols fer. Hi ha alguna manera de carregar i instal·lar en modo text? perquè el fitxer aquest "xorg.conf" que veig que s'ha de modificar, no es pot modificar fins que tens la distro instal·lada, oi?

Bé, aviam si algú em pot orientar una mica o si no hi ha res a fer... doncs m'ho trec del cap :D

Merci!

---

### Post by lluisanunez on 2007-11-05
Necessites el CD alternatiu (alternate CD). Pots descarregar la imatge ISO d'aquí
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Per descarregar, omple el formulari amb les teves opcions i marca la casella del final de tot.
Després rebota i apareixerà una opció per a insta&#320;lar en mode text

---

### Post by papapep on 2007-11-05
Prova posant l'opció "noapic" (sense cometes, clar) a la pantalla de selecció de instal·lacions.

---

### Post by -xavi- on 2007-11-05
oh! merci!

no vaig llegir bé la pàgina aquella de descàrrega. Ara ja s'està baixant aviam si funciona.

I això que em comentes (papapep), on ho haig de posar? o sigui... en les versions que provava d'instal·lar, jo apretava F6 i em sortia una cosa que deia "quiet splash" i la borrava perquè així ho havia vist buscant pel google.

gràcies,
Xavi.

---

### Post by papapep on 2007-11-05
> Després rebota

Aquesta "anglosaxonada" teva Lluïsa, m'ha fet riure una bona estona imaginant-me el pobre Xavi fotent bots davant l'ordinador.... :-D

Xavi: el tema del "noapic", símplement darrera el xurro de opcions i directives que hi ha, deixes un espai i ho afegeixes.

---

### Post by -xavi- on 2007-11-05
Bé! ubuntu instal·lat! :popcorn:


ara... el que suposo que serà la meva creu.. la tarja gràfica aquesta...

Em surten 3 opcions... arrencar normal, arrencar en mode segur i memtest... doncs bé, si poso arrencar normal, s'apaga la pantalla i no fa res.

Si selecciono el mode segur arrenca bé (només consola i puc veure tots els fitxers i carpetes) però no sé què fer :p suposo que he d'editar el fitxer aquell xorg.conf? he de seguir algun post en especial? vaia desastre que sóc... xD

Bé, espero almoines i gràcies per les ajudes

---

### Post by papapep on 2007-11-05
Hauries d'explicar què has fet (si fer servir l'alternate o posar el noapic) per que algú altre que es trobi amb el teu problema ho tingui clar.

Respecte la teva targeta gràfica, aquí:

[http://mundogeek.net/archivos/2007/10/24/fglrx-8423-compiz-fusion-con-ati-y-aiglx/](http://mundogeek.net/archivos/2007/10/24/fglrx-8423-compiz-fusion-con-ati-y-aiglx/)

i aquí:

[http://tuxpepino.wordpress.com/2007/10/24/driver-amdati-8423-%C2%A1por-fin-aiglx/](http://tuxpepino.wordpress.com/2007/10/24/driver-amdati-8423-%C2%A1por-fin-aiglx/)

parlen de com instal·lar la nova versió del controlador propietari, el qual comenten que va prou bé.

---

### Post by -xavi- on 2007-11-05
Bé, doncs m'he descarregat el 7.10 alternate i al instalar he fer:

F2: idioma català
F6: "noapic" al final de tot el rotllo que posa en els paràmetres de la instal·lació

el que passa és que com que no m'anava bé, he començat a trastejar amb el xorg.conf i amb les mides de pantalla suportades i finalment he provat el "dpkg-reconfigure xserver-xorg" aviam si feia algo de bo i res... el mateix resultat. (ara torno a tenir el xorg.conf inicial)

Suposo que si demà (perquè avui ja no m'hi veig amb ganes) provo d'instalar els controladors de la gràfica amb els enllaços que m'has passat  no haure de reinstalar per haver reconfigurat coses amb el dpkg aquell, oi?

Bé, seguirem provant!

Edito: mmm... és normal que ho hagi de fer tot en consola? perquè si segueixo les indicacions que hi ha al primer enllaç per instal·lar el controlador parlen de fer doble click, jo ho podré fer directament des del shell oi?

Gracies,
Xavi.

---

### Post by lluisanunez on 2007-11-06
> **papapep said:**
> Aquesta "anglosaxonada" teva Lluïsa, m'ha fet riure una bona estona imaginant-me el pobre Xavi fotent bots davant l'ordinador.... :-D
Sorry, awfully sorry. És veritat que estic anglosaxonitzada. Abans de conèixer aquest fòrum fantàstic, havia de buscar-me la vida en anglès, i em vaig acostumar a insta&#320;lar-me els programes en anglès per a poder buscar els textos dels missatges d'error.
Gràcies pel NOAPIC, no ho sabia

---

### Post by cesvi87 on 2007-11-06
> **papapep said:**
> 

Respecte la teva targeta gràfica, aquí:

[http://mundogeek.net/archivos/2007/10/24/fglrx-8423-compiz-fusion-con-ati-y-aiglx/](http://mundogeek.net/archivos/2007/10/24/fglrx-8423-compiz-fusion-con-ati-y-aiglx/)



Resulta que he seguit totes les instruccions, i m'he menjat els mocs, amb lo bé que estava jo... i ara ho tinc tot en 'low' grafics, no hi ha cap manera de restaurar els valors de la gràfica o més ben dit configurar-los com estaben just en instalar l'Ubuntu 7.10? 
He seguit els passos inversos respecte el que deia el xic del blog, però continuo veient-ho tot amb molta poca resolució.

---

### Post by -xavi- on 2007-11-11
> **papapep said:**
> 

Respecte la teva targeta gràfica, aquí:

[http://mundogeek.net/archivos/2007/10/24/fglrx-8423-compiz-fusion-con-ati-y-aiglx/](http://mundogeek.net/archivos/2007/10/24/fglrx-8423-compiz-fusion-con-ati-y-aiglx/)

i aquí:

[http://tuxpepino.wordpress.com/2007/10/24/driver-amdati-8423-%C2%A1por-fin-aiglx/](http://tuxpepino.wordpress.com/2007/10/24/driver-amdati-8423-%C2%A1por-fin-aiglx/)

parlen de com instal·lar la nova versió del controlador propietari, el qual comenten que va prou bé.

Perdó pel retard, però tenia feina i no m'hi havia pogut dedicar.

He intentat seguir les instruccions per instal·lar el controlador sobretot a partir del primer enllaç; però em sembla que no ho acabo de fer bé.

Vàries consultes:

Cal generar el paquet tal i com comenten? fent "sudo ./ati-driver[...].run --buildpkg Ubuntu/gutsy ?

I, si s'ha de fer... com l'executo i on el trobo? perquè allà em diuen que faci doble click sobre el paquet però clar... si engego la sessió gràfica, se'm para la pantalla i he de continuar en modo consola...

I per últim... és normal que no pugui utilitzar el "gedit"? jo per espavilar-me i modificar fitxers de configuració ho he fet amb el vim, però no sé si m'he deixat coses.

Bé, en tot cas he llegit que les versions 7.04 i 7.10 dónen bastants més problemes que la 6.10, per un petardo com jo seria interessant que intentés instal·lar primer la 6.10 aviam com em respon la gràfica?


A reveure,
Xavi.

---

### Post by CarlesOriol on 2007-11-11
Eps... ja arriba la caballeria

Abans de res per assegurar la jugada et cal:

1. el cd ubuntu alternate
2. l'envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
3. Conexió a internet ABANS d'entrar en mode gràfic. Si pots fer-ho per cable segur que serà més fàcil

--------------------------------------------------

Passos

1. Insta&#320;les l'ubuntu alternate
2. Reinicies i s'atura
3. fas login en mode text (ctrl+alt+f2)
4. insta&#320;les l'envy des de l'adreça que t'he escrit 

```
wget [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu12_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu12_all.deb)
```

```
sudo dpkg --install envy_0.9.8-0ubuntu12_all.deb 
```

executes l'envy

```
sudo envy
```

 selecciones ati + y a canviar l'xorg + y a reiniciar

reinicies... i ja està

A més amb la versió de la setmana passada tindras AIXGL !! brutal

---

### Post by -xavi- on 2007-11-11
m'he perdut... :$

Aviam...només puc "engegar" si poso la opció inicial del "recovery mode". Si inicio normal no puc fer res; es para la pantalla i ni ctrl+alt+F2 ni res funciona; en canvi, amb el recovery mode, puc iniciar i ara ja em deixa fer un "startx" i puc veure coses (ueee).

Internet amb linux no en puc tenir de moment; però m'he descarregat l'arxiu aquell, l'he guardat en la partició del xp i després l'agafo i el copio al home del linux.

Tot i això, al fer el "sudo dpkg --install envy....." peta per tot arreu dient que no té molts paquets necessaris. Pot ser perquè estic en recovery mode?

---

### Post by CarlesOriol on 2007-11-11
Et caldrà anar descarregant els paquets de dependencies  (*.deb a archive.ubuntu.com per exemple ) des de un ordinador on tinguis internet i anar-los portant d'alguna manera. (amb un llapis de memòria o similar)

El problema és que una de les dependencies és la build-essential ... i d'aquí pengen un munt de paquets

Exactament quin portàtil és?

---

### Post by -xavi- on 2007-11-11
mmmm....

jo tinc un pc pentium4 3200MHz i la gràfica és una Radeon X700 (512MB).

Tinc ono i aquest ordinador és el que està directament connectat a internet. Tot i això, puc fer el que em dius d'anar transpassant arxius amb un pendrive.

Aniré fent això i quan torni a tenir problemes per instalar-ho (que segur que passa) ja us tornaré a empipar :p

Merci!
Xavi.

---

### Post by CarlesOriol on 2007-11-11
Eps no sé si et servirà per a res però t'he penjat per tu els controladors compilats per a gutsy (32 bits) (paquets deb) i el meu xorg.conf.

[http://www.kumbaworld.com/ati.zip](http://www.kumbaworld.com/ati.zip)

---

### Post by -xavi- on 2007-11-12
tornem-hi... 

he anat instal·lant tots els paquets que va demanant i he pogut posar bé els

-dpatch
-dpkg-dev
-libstdc++5
-debhelper
-dh-make
-fekeroot
-module-assistant
-xserver-xorg-dev

pero en la build-essential em diu que necessito el g++; i es veu que hi ha un bug perquè em demana els

g++-4.1 (4.1.2-16ubuntu2) i el libstdc++6-4.1-dev(4.1.2-16ubuntu2)

i aquests dos depenen l'un de l'altre.

Jo els estic instal·lant fent "sudo dpkg --install xxxxxxxxxx.deb"

He llegit por ahi ([https://bugs.launchpad.net/ubuntu/+source/gcc-4.1/+bug/120935](https://bugs.launchpad.net/ubuntu/+source/gcc-4.1/+bug/120935)) que hi ha aquest bug i que en teoria si tens internet no passa re, pero sino sí (el meu cas) 

què hi puc fer? en recovery mode puc intentar fer funcionar el meu cable-modem?

---

### Post by CarlesOriol on 2007-11-12
agafa els paquets que t'he preparat

---

### Post by -xavi- on 2007-11-12
ho vaig intentar ahir però no li va agradar al winrar i no ho vaig poder obrir... o ho empasto directament al ubuntu i alla ja em podré espavilar?

editat: sembla que el .zip està xungo perquè he provat amb l'ubuntu un "unzip ati.zip" i un "unzip -v ati.zip" i diu que "End-of-central-directory signature not found" i... si jo tinc la versió per 64 bits aniran bé igual?

---

### Post by CarlesOriol on 2007-11-12
```
carles@aspire5610:~/Desktop$ unzip -v ati.zip
Archive:  ati.zip
 Length   Method    Size  Ratio   Date   Time   CRC-32    Name
--------  ------  ------- -----   ----   ----   ------    ----
       0  Stored        0   0%  11-11-07 22:37  00000000  ati/
    2804  Defl:N      998  64%  11-11-07 16:19  66b08b98  ati/xorg.conf
 5604664  Defl:N  5598507   0%  11-11-07 22:36  95737b45  ati/fglrx-amdcccle_8.42.3-1_i386.deb
 7637280  Defl:N  7485331   2%  11-11-07 22:36  606639ab  ati/xorg-driver-fglrx_8.42.3-1_i386.deb
   40180  Defl:N    39751   1%  11-11-07 22:36  191a6103  ati/xorg-driver-fglrx-dev_8.42.3-1_i386.deb
 1682608  Defl:N  1682789   0%  11-11-07 22:36  15052d80  ati/fglrx-kernel-source_8.42.3-1_i386.deb
--------          -------  ---                            -------
14967536         14807376   1%                            6 files
carles@aspire5610:~/Desktop$
```

Sols per 32 bits

---

### Post by -xavi- on 2007-11-12
bé... doncs no sé com és que jo no el podia obrir; però tan és.

Això sí, ja que no puc instal·lar els paquets "manualment" podria connectar-me a internet i que ell, d'alguna manera, els pesqués de la xarxa?

He llegit algo del synaptic? o vaig errat?

I això de internet... (potser ho hauria de fer en un altre fil)

Jo tinc ONO i tinc un cable-modem. El tinc connectat al meu ordinador per cable RJ-45. He fet que em detecti les 2 targes ethernet que tinc (eth0 i eth3); la eth0 és la que va al modem pero no tinc internet així per les bones.

He de configurar alguna altra cosa? DNS?o en recovery mode me n'oblido?

---

### Post by -xavi- on 2007-11-18
uhm... bona nit

he reinstalat l'ubuntu 7.10 i, no sé com, al final he aconseguit (sempre en recovery mode perquè de l'altra manera se'm para la pantalla) que m'arrenqués "startx" i he pogut instalar l'envy. També he aconseguit que  em funcionés el modem i ha pogut descarregar els paquets per tenir bé les dependències.

Fet tot això, he engegat l'envy i he posat que instal·lés el driver ati, que després ell mateix em reconfigurés l'xorg i també ell sol ha reiniciat i... sorpresa... s'ha apagat la pantalla de nou.

Després, només iniciar l'startx se'm posava la pantalla blanca i no feia res. He apretat (CTRL + ALT + BACKSPACE) per sortir de la pantalla blanca aquesta i tornar a la de text que posa el recovery mode i un dels cops he apretat "envy -t" per intentar instalar el driver en mode text; he seguit els mateixos passos i res de res... pantalla blanca si faig startx i res de res...

Algú té alguna idea? també he instal·lat el driver d'ati que em va posar en papapep en algun dels primers enllaços d'aquest fil però tampoc em soluciona res...

Abans també he fet "sudo dkpg-reconfigure -phigh xserver-xorg" i he posat la resolució de pantalla que tinc al windows (1152x864 i les que hi ha mes avall) per assegurar-me que la pilli bé...

Em sap greu ser tant dur però això que hi ha entre Ati i jo ja comença a ser una cosa personal  :mad:

edito: ara, havent reiniciat un parell de cops, puc fer "startx" i ja no queda blanc. Lo altre... igual, al reiniciar pantalla apagada i d'aquí no es mou

---

