---
title: "Reproductors multimedia"
date: 2007-08-24
forum: Catalan Team
---

### Post by muleta on 2007-08-24
Com s'activen les funcions multimedia?.

He instal·lat un futimer de programes de reproducción i de gravació de música i pel·lícules pero no funciona res, ni tan sols reprodueixen CDs de música super legals i originals.

Curiosament, la unitat òptica llegeix perque em va permetre instal·lar l'Ubuntu.

---

### Post by Ferri on 2007-08-24
Per reproduir DVD necessites alguns códecs que no et venen d'entrada perquè no són lliures.
Des de terminal activa les fonts de Medibuntu:
```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
I després:
```
sudo apt-get install libdvdcss2 w32codecs
```
Si ja has instal·lat algun reproductor, segurament ja ho tindràs tot a punt.

---

### Post by muleta on 2007-08-24
Se m'han actualitzat tots el programes de reproducció però continuen fent el mateix:

No reprodueixen desde el fitxer, desde la vista previa de l'amule, desde el DVD ni s'obren els programes desde Aplicacions-So i video. Els únics que fal alguna cosa son el gxine, que em crea un rectangle fix enmig de la pantalla (fins que tanco l'ordinador) i el VLC, que em reprodueix l'imatge sense sò fins que es penja.

Tot això ja m'ho feien abans d'instal·lar els codecs.

---

### Post by pespin on 2007-08-24
Ugh, que extrany, deu ser cosa dels 64 bits o alguna cosa que hauràs tocat sense donar-te'n compta :mad:

EDIT--- proba a córrer els reproductors des de la terminal ('totem', 'mplayer', 'vlc', etc.), a veure si trobes alguna informació sobre el que falla

---

### Post by muleta on 2007-08-24
Com es fa?.

---

### Post by lluisanunez on 2007-08-24
Obre un terminal i escriu "gxine" o "vlc" o el que vulguis. Al terminal et poden sortir missatges que indiquin quin problema hi ha. Copia'ls i envia'ls aqui.

---

### Post by muleta on 2007-08-24
GÜAIIIII...

Aquesta m'obre el requadret ditxós, amb la diferència de que s'esborra en tancar el terminal.

---

### Post by pespin on 2007-08-24
Si, quan obres un programa amb la terminal normalment "es queda pillat per la terminal" i al tancar la terminal el tanques o simplement donant-li a CTRL+c

Prova amb altres programes de video, a veure si algun deixa anar alguna info util. Normalment la comanda per a engegar-los sol ser el nom o les inicials del programa

---

### Post by muleta on 2007-08-24
> **lluisanunez said:**
> Obre un terminal i escriu "gxine" o "vlc" o el que vulguis. Al terminal et poden sortir missatges que indiquin quin problema hi ha. Copia'ls i envia'ls aqui.

La de VCL em respon: "bash: vcl: command not found".

Igualment Codeine, Kaffeine,  mdplayer movie player...

El Totem fa això i es queda penjat.

---

### Post by pespin on 2007-08-24
Jeje però el que ens interessa en aquest cas (corrent-lo des de terminal) és els missatges que deixa anar a la consola quan funciona.

Els altres donen "command not found" perquè no era aquella la ordre :)

---

### Post by muleta on 2007-08-24
Ah, doncs, quina?.

Només hi he escrit els noms dels programes, un cada vegada.

---

### Post by pespin on 2007-08-24
Prova el totem, que ja l'has arrancat, i espera a veure si surt alguna info a la terminal (ordre -> totem)

Si tens instal·lat el Kaffeine -> kaffeine

Fixat que estan en minúscula! :)

---

### Post by muleta on 2007-08-24
kaffeine:

"DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: Invalid Service : kritahistogramdocker.desktop
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
0
QLayout "unnamed" added to QWidget "unnamed", which already has a layout

---

### Post by muleta on 2007-08-26
> **lluisanunez said:**
> Obre un terminal i escriu "gxine" o "vlc" o el que vulguis. Al terminal et poden sortir missatges que indiquin quin problema hi ha. Copia'ls i envia'ls aqui.

Intento esbrinar si em falten codecs o si funcionen els programes reproductors, ara que utilitzo la versió de 32 bits i després d'instal·lar els codecs no lliures que em va passar en Ferri.

Els resultats que obtinc són aquests. Algú em pot traduïr alguna conclusió?:

---

### Post by pespin on 2007-08-26
El mplayer si no t'arranca es perquè tal i com diu el help que surt quan l'executes , has d'executar l'ordre 'mplayer' com a minim amb un paràmetre 'fitxer'. 

es a dir:

```
mplayer /ruta/fitxer
```

Per lo demés sembla que el dvd no té "DVD encrypted support". Jo personalment no sé com solucionar això, ja que no acostumo a veure pelis ni coses d'aquestes jeje

---

### Post by muleta on 2007-08-26
He volgut llegir un DVD que es veu perfectament a la tele i que es véia en tots els visors de Windows.

El fet que no es pugui reproduïr aquí vol dir que amb els codecs de Linux no podré gravar pel·lícules que pugui visionar a la tele?.

L'únic reproductor que, després de dir-me tot allò, s'ha posat a funcionar ha estat el VCL.

Potser trobant la diferència entre aquest i els altres sabriem quins còdecs em calen.

És que no en tinc ni idea de tot això, les suites per a Windows s'encarregaven de resoldre-m'ho i ara potser hauré de fer un curs de multimedia.

Crec que "tiraré pel dret" i em llançaré a gravar una película, a veure què passa, com recomanen els savis.

---

### Post by pespin on 2007-08-26
> El fet que no es pugui reproduïr aquí vol dir que amb els codecs de Linux no podré gravar pel·lícules que pugui visionar a la tele?.

El fet que ara tu no tinguis els codecs no vol dir gaire cosa, simplement que has d'instal·lar-los. Ara bé, el que s'ha d'instal·lar t'ho haurà de dir una altra persona en aquest cas. :)

> i ara potser hauré de fer un curs de multimedia.

S'aplica el mateix, no has de fer cap curs de res, simplement instal·lar els codes necessaris xDDDD

Jo acostumo a instal·lar tots els gstreamer, no se si està ben fet però bueno. Aquí estan els paquets:

```
sudo aptitude install gstreamer0.10-alsa gstreamer0.10-plugins-bad-dbg gstreamer0.10-audiosink gstreamer0.10-plugins-bad-doc
  gstreamer0.10-x gstreamer0.10-plugins-base-dbg gstreamer0.10-fluendo-mpegdemux
  gstreamer0.10-plugins-base-doc libgstreamer0.10-0 gstreamer0.10-plugins-ugly gstreamer0.10-colorspace
  gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-good
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-farsight gstreamer0.10-pitfdll gstreamer0.10-videosink
  gstreamer0.10-plugins-ugly-dbg gstreamer0.10-lame gstreamer0.10-plugins-good-dbg
  gstreamer0.10-plugins-ugly-doc gstreamer0.10-plugins-good-doc gstreamer0.10-plugins-bad-multiverse-dbg
  gstreamer0.10-plugins-bad gstreamer0.10-doc gstreamer0.10-fluendo-mp3 gstreamer0.10-gl
  gstreamer0.10-esd libgstreamer0.10-ruby1.8 gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-ugly-multiverse-dbg libgstreamer0.10-dev gstreamer0.10-sdl
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-gnonlin gstreamer0.10-tools
  gstreamer0.10-gnonlin-dev libgstreamer0.10-0-dbg
```

---

### Post by muleta on 2007-08-26
Gràcies però no. Havia intentat gravar una pel·lícula abans i ho he tornat a provar ara amb tot això que m'has passat, però no va.

Si, a més, ja avisa el K3B de que no estic intentant gravar un fitxer ISO.

Jo crec que cap programa fa més d'allò que s'ha compromès a fer.

És molt possible que no existeixin programes per a Linux. Potse s'hagi de tenir instal·lat el Windows simultàneament perque arribi allà on el pingüí no arriba.

Jo ja l'he explorat i li he donat la seva oportunitat. Crec que és hora de començas a plegar veles.

Me'n vaig a fer un circuït amb bicicleta, pel parc, amb la meva filla, que ja ha acabat els seus deures abans que jo i em fa "pam-i-pipa".

ORREVUà!

---

### Post by pespin on 2007-08-26
> És molt possible que no existeixin programes per a Linux. Potse s'hagi de tenir instal·lat el Windows simultàneament perque arribi allà on el pingüí no arriba.

I tant que existeixen els programes per a Linux, els tens instal·lats. Com t'he dit només necesites buscar quins codecs et falten. 

Hi ha poques coses on Windows arribi i Linux no. Jo personalment utilitzo Windows només per jugar a jocs que no he aconseguit emular amb el wine. (ara mateix només l'utilitzo quan haig d'entrar a jugar al NWN2 o usar les Tools del mateix joc).

No crec que sigui greu el que et passa ara. Això si, mentres algu posteja la solució o no la troves tu potser si k hauras de fer servir windows per algunes coses, però no amb el plantejament que a Linux no es poden fer, sino que encara has d'aplicar-hi la solució. :)

PD: Pots provar a instal·lar l'automatix2, porta una opció per a instal·lar tot tipus de codecs.

---

### Post by papapep on 2007-08-26
Crec que l'únic que et cal per a poder visualitzar DVD és una llibreria en concret.

Executa en un terminal:

```
sudo apt-get install libxine-ffmpeg
```

PD No us puc deixar dos dies sols, eh!! Heu fet més posts que en tot el mes!!! :-D

---

### Post by PellRoja on 2007-08-26
xmms llegeix mp3 per defecte.

---

### Post by muleta on 2007-08-26
> **pespin said:**
> 

PD: Pots provar a instal·lar l'automatix2, porta una opció per a instal·lar tot tipus de codecs.

Ja m'he capbussat a la xarxa i he trobat això del Automatix amb advertiments i amenaces seriosos. Però h mirat el paquet i porta massa coses que no em són útils. Les que em calien ja les he pogut instal·lar.

Estic a punt de conèixer un programa que, teòricament, ho fa tot: el devede (dubto entre versions i el DVD::Rip), que necessita el Mplayer, Mencoder, DVDAuthor, VCDImager y MKisofs.

Potser que no m'embarqui a instal·lar tanta cosa. Al final, em quedaré sense espai.

Vaig a veure què diu en Papapep. Gràcies per la moral.

---

### Post by muleta on 2007-08-26
Jo ja t'ho vaig demanar que no marxessis gaire lluny :)

Sí, ja he vist que hi ha dos tipus de llibreries per a dos tipus de reproductors. La del Xine no l'hauria triat perque el programa Gxine era aquell que em creava un rectangle enmig de la pantalla.

Però t'he fet cas i mira què em surt:

---

### Post by papapep on 2007-08-26
Prova afegint un "1" al nom:

```
sudo apt-get install libxine**1**-ffmpeg
```

---

### Post by muleta on 2007-08-26
> **PellRoja said:**
> xmms llegeix mp3 per defecte.

De moment, encara no em preocupa aquest tema. Tot arribarà, si tampoc no em funcionen els reproductors de mp3. Peró gràcies.:)

---

### Post by muleta on 2007-08-26
> **papapep said:**
> Prova afegint un "1" al nom:

```
sudo apt-get install libxine**1**-ffmpeg
```
Llestos!- Em funcionen tots menys l'Mplayer. És estrany perque he llegit que té motor propi i no necessita còdecs.

Potser funcionarà quan instal·li els programes que em calen per executar el Devede.

A veure si, ara, el K3B també gravarà. Provo.

---

### Post by papapep on 2007-08-26
Sembla ser que per l'Mplayer et cal, verifica primer que no les tinguis instal·lades ja, les llibreries libdvdread3 i libdvdcss2. I com pots comprovar-ho??

Molt senzill (et sona la frase :-D), fas:

```
sudo aptitude search libdvdread3 libdvdcss2
```

A la resposta que et dóna el terminal, el primer caràcter és una lletra "**i**", això significa que ja són instal·lats. En cas contrari et posarà, probablement, una "**p**" de pendent.

Si no tens els paquets instal·lats, fes:

Si la llibreria** libdvdread3** ja la tinguèssis instal·lada, no cal que facis les dues primeres passes següents:

```
sudo apt-get install libdvdread3 
```

Un cop estigui el procés, fes:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

I ara, per acabar, fes:

```
sudo apt-get install libdvdcss2
```

En teoria, ara l'Mplayer ja t'hauria de llegir correctament discs de DVD.

---

### Post by muleta on 2007-08-27
Bon día, doncs no. No em funciona.

És possible que falti  **p   libdvdcss2-dev**?.

---

### Post by muleta on 2007-08-27
Buscant-li complements a l'Mplayer amb el Synaptic, es veu que li he instal·lat alguna cosa que no corresponia i s'ha desinstal·lat el mplayer.

Quan m'ha avisat, he resolt el conflicte i l'he tornat a instal·lar però no va.

---

### Post by muleta on 2007-08-27
Ha variat lleument.

---

### Post by papapep on 2007-08-27
Quan dius que no et funciona, què vols dir exactament??

Seria bó que invoquessis l'Mplayer (manifesta't!!!! :-D) des del terminal i així veurem si surt algun missatge que ens dona pistes.

Ja saps, símplement poses "mplayer" al terminal com a usuari "muleta".

EDICIÓ: T'has plantejat passar de l'Mplayer?? Tampoc és que et faci estrictament falta. Si és un puntillo o una necessitat real, cap problema. Però t'ho dic perquè falta, falta tampoc et fa, en principi.

---

### Post by muleta on 2007-08-27
Invocat. Sembla que no diu res especial, oi?.

---

### Post by muleta on 2007-08-27
> **papapep said:**
> 

EDICIÓ: T'has plantejat passar de l'Mplayer?? Tampoc és que et faci estrictament falta. Si és un puntillo o una necessitat real, cap problema. Però t'ho dic perquè falta, falta tampoc et fa, en principi.

Crec que sí que em fa falta. Jo ja n'havia passat però es veu que el Devedé el necessita.

I el Devedé és el millor programa que he trobat per a convertir els fitxers de video a ISO i poder-los gravar amb el K3B. En teoría és genial, en un llenguatge comprensible i em porta de la maneta, com a mi m'agrrada.

Però aquesta nit li he fet gravar una peli i, en lloc de sò, fa soroll. Ho imputo al mal funcionament del mplayer que diu necessitar. Però, si no és això, quina pot ser la causa?.

---

### Post by papapep on 2007-08-27
Fixa't què diu aquí: [http://www.rastersoft.com/programas/devede_es.html](http://www.rastersoft.com/programas/devede_es.html)

> Nota para usuarios de Ubuntu Feisty: la versión actual (a 20 de abril de 2007) de Mplayer/Mencoder de Ubuntu Feisty tiene un bug y produce un fuerte ruido en el sonido cuando se usa con DeVeDe. Mientras el mantenedor del paquete no lo soluciona, puedes usar el paquete con la versión anterior, disponible en la sección de descargas.

---

### Post by muleta on 2007-08-27
> **papapep said:**
> Fixa't què diu aquí: [http://www.rastersoft.com/programas/devede_es.html](http://www.rastersoft.com/programas/devede_es.html)

Des de l'abril, jo confiava que ja ho hagéssin arreglat. A més, la versió del Devedé, ha de ser aquella tan antiga i sense millores o pot ser la última?.

A veure si haurem arribat al quid de la qüestió;-)

---

### Post by papapep on 2007-08-27
Crec que volen dir que amb la versió més actual de DEVEDE es pot fer servir la versió que ells diuen de l'Mplayer a fi d'evitar el problema del soroll.

Puc preguntar-te perquè et cal passar a format DVD els fitxers de video?? El teu reproductor de DVD convencional no et reprodueix MPG's i AVI's directament?? T'ho dic perquè és una feinada...

---

### Post by muleta on 2007-08-27
> **papapep said:**
> 

Puc preguntar-te perquè et cal passar a format DVD els fitxers de video?? El teu reproductor de DVD convencional no et reprodueix MPG's i AVI's directament?? T'ho dic perquè és una feinada...

El probllema és que no trobo programes per a Linux que gravin altres formats no ISO.

---

### Post by papapep on 2007-08-27
> El probllema és que no trobo programes per a Linux que gravin altres formats no ISO

Crec que no t'entenc....tant el GnomeBaker, com el K3B no tenen cap problema en gravar-te el que vulguis dins un CD o DVD. Qualsevol tipus de fitxer de dades (els MPG i AVI, en el fons són dades...) se'l mengen amb molt de gust.

Un altre problema, que encara no m'has respost, és si el teu DVD els sap reproduïr després.

---

### Post by muleta on 2007-08-27
> **papapep said:**
> Crec que no t'entenc....tant el GnomeBaker, com el K3B no tenen cap problema en gravar-te el que vulguis dins un CD o DVD. Qualsevol tipus de fitxer de dades (els MPG i AVI, en el fons són dades...) se'l mengen amb molt de gust.

Un altre problema, que encara no m'has respost, és si el teu DVD els sap reproduïr després.

Doncs ara m'he perdut del tot. :confused: Per què el K3B es negava ahir a gravar-me les películes argumentant que no eren fitxers ISO i, en canvi, avui me les grava (sense sò) després de convertir-les amb el Devedé?.

El meu reproductor DVD de sobretaula reprodueix DVD, DivX, SVCD.

Hi ha reproductors mpg o avi de sobretaula?.

---

### Post by papapep on 2007-08-27
No sóc un expert en formats de video, ni en res més, però jo diria que DIVX són els fitxers AVI.

I respecte el K3B, t'asseguro que si graves fitxers MPG i AVI triant l'opció "Nou projecte de DVD de dades" (en cas de gravar DVD) t'ho ha de gravar correctament. I si no, el més probable és que no sigui culpa del K3B.

Si vols acabar d'un cop amb els dubtes, grava un DVD amb un fitxer AVI i un altre MPG i a veure què en fa el teu reproductor.

---

### Post by muleta on 2007-08-27
No us ho creureu però el meu reproductor...

LLEGEIX PERFECTAMENT ELS FITXERS AVI I MPG GRAVATS PER EL K3B, que acabo d'obtenir seguint les instruccions de Papapep.\\:D/:grin:=D>=D>=D>=D>

Com m'ha costat d'entendre una cosa tan senzilla!!. Però ja està... Finalment, un altre problema resolt.

A més, he de dir que el K3B és mega ràpid.

Ara, potser hauria de treure el mplayer, Devedé i totes les porquerietes i complements que hi he instal·lat. Hi ha alguna manera de fer-ho sense carregar-me res?.

GRÀCIES PAPAPEP i a tots els altres. Us estimoooooooooo...

---

### Post by papapep on 2007-08-27
Tot depèn de com ho hagis instal·lat.
Si ho has fet amb l'apt-get o l'aptitude (que fan la mateixa feina), simplement fes:

```
sudo apt-get (o aptitude, al teu gust) purge nom_del_paquet
```

Si ho has fet d'altra manera, doncs depèn.

Veus com amb una mica de serenitat les coses surten? Enhorabona per la teva constància. ;-)

---

### Post by muleta on 2007-08-27
Tossoderia, obstinació i caparruderia, m&#347; que res. D'aquí em ve el nick, en part.

Els complements els he instal·lat amb el Synaptic i sé que els puc desinstal·lar igual o per afegir/eliminar. El que no sé es si estan compartits per altres programes.

I tots els codecs que tan gentilment m'han passat en Pespin, Ferri, etc. No em caldran per res?. No són utilitzats pel K3B? ni pels reproductors de video?.

---

### Post by papapep on 2007-08-27
> Tossoderia, obstinació i caparruderia, m&#347; que res

Sempre he pensat que el nom no fa el fet :-)

> Els complements els he instal·lat amb el Synaptic i sé que els puc desinstal·lar igual o per afegir/eliminar. El que no sé es si estan compartits per altres programes.

Tot i que no estic acostumat al Synaptic, segur que t'avisa de què fa i deixa de fer. Pensa que NOMÉS és una màscara bonica per l'apt-get i companyia, no és que ell faci la feina, només t'amaga el terminal.
Aleshores, només has de mirar què fa abans de confirmar definitivament  la acció i ja està. Ja veuràs si pretèn desinstal·lar alguna cosa que tu no has demanat.

I si dubtes ja saps, el fòrum hi és per a això ;-)

---

### Post by Ferri on 2007-08-27
> **muleta said:**
> I tots els codecs que tan gentilment m'han passat en Pespin, Ferri, etc. No em caldran per res?. No són utilitzats pel K3B? ni pels reproductors de video?.
Sento no haver llegit tot el fil complert. Pel que fa als códecs que et vaig recomanar jo, en principi el libdvdcss2 el necessites per reproduir els DVD i w32codecs per reproduir fitxers de vídeo en formats propietaris com *.avi o *.asf.

---

### Post by muleta on 2007-08-27
Gràcies Ferri.

Només he gosat desinstal·lar l'mplayer i el Devedé. Ja no toco res més. No crec que hi hagi incompatibilitats entre el que quedi ni que m'ocupi gaire espai.

---

### Post by papapep on 2007-08-27
El sistema ja controla tant les dependències com les incompatibilitats. Aquí està la gràcia de fer servir el sistema nadiu de Debian/Ubuntu per a instal·lar paquets, que, com tu dius repetidament: "et porta de la maneta" :-D

Una altra cosa és que et sobrin o no paquets. Però l'únic perjudici objectiu que et causa és pèrdua d'espai.

Tot i això, si tu fas "sudo apt-get purge nomdelpaquet", i veus que l'apt-get només t'avisa de que t'esborrarà el paquet que tu li has dit, és que cap altre paquet el té com a dependència ni el trobarà a faltar.

---

