---
title: "convertir audio de pel·lícules a mp3"
date: 2010-06-12
forum: Catalan Team
---

### Post by marmotona on 2010-06-12
He mirat els posts sobre conversors d'audio i cre que no n'hi ha cap que s'acabi d'ajustar al que necessito.

Resulta que he descarregat un reguitzell de pel·lícules que el meu reproductor no sap llegir a causa del format d'audio. Crec que només reprodueix mp3. He buscat i provat diversos conversors però no me'n surto.

El que més m'han recomanat és el winff, però no el sé configurar perquè em passi el so dels videos a mp3. Algú el coneix?. Si en sabeu algun altre de més fàcil me'l podeu recomanar. Gràcies.

---

### Post by epileg on 2010-06-12
has provat amb «oggconvert»?

---

### Post by kimet on 2010-06-12
Amb avidemux es pot fer  sense separar l'audio del video.

Però no seria millor buscar un reproductor adient o instal.lar el codec corresponent al format en qüestió?

Salut.

---

### Post by marmotona on 2010-06-12
> **epileg said:**
> has provat amb «oggconvert»?

No. No el coneixia aquest programa per convertir a format ogg. Però el format ogg farà que pugui reproduir les pel·lícules com si fossin format avi i amb àudio mp3?.

---

### Post by marmotona on 2010-06-12
> **kimet said:**
> Amb avidemux es pot fer  sense separar l'audio del video.

Però no seria millor buscar un reproductor adient o instal.lar el codec corresponent al format en qüestió?

Salut.

L'Avidemux és massa sofisticat i no hi veig cap menú per convertir el format d'àudio a mp3.

Afegir còdecs al reproductor?. Com es deu fer?. És un simple reproductor de USB, molt senzill, però investigaré si això és possible.

---

### Post by epileg on 2010-06-13
> **marmotona said:**
> No. No el coneixia aquest programa per convertir a format ogg. Però el format ogg farà que pugui reproduir les pel·lícules com si fossin format avi i amb àudio mp3?.

No, el format de sortida serà Theora per al vídeo i vorbis per a àudio. Ambdós codecs lliures, i per tant, sense problemes a l'hora de reproduir-los. Però si el WinFF (basat en el ffmpeg) no et converteix correctament els teus vídeos, dubto que el oggconvert ho faci. Tot és provar-ho.

Salut.

---

### Post by wgarcia on 2010-06-13
El millor és assegurar-se tenir tots els codecs, i per això la millor opció es habilitar els repositoris "medibuntu".

---

### Post by kimet on 2010-06-13
> **marmotona said:**
> L'Avidemux és massa sofisticat i no hi veig cap menú per convertir el format d'àudio a mp3.

Només has de: 

-Carregar la pelicula, 
-Seleccionar "la sortida" (Al costat de la calculadora on posa "l'entrada")
-Seleccionar mp3 (a l'esquerra on hi posa audio/copiat)
-I clicar on diu "desa" i esperar.
-I veure la peli:popcorn:

---

### Post by marmotona on 2010-06-13
> **kimet said:**
> Només has de: 

-Carregar la pelicula, 
-Seleccionar "la sortida" (Al costat de la calculadora on posa "l'entrada")
-Seleccionar mp3 (a l'esquerra on hi posa audio/copiat)
-I clicar on diu "desa" i esperar.
-I veure la peli:popcorn:


A audio/copiat només em dona l'opció de "copiat". No es desplega res més.:confused:  I quan intento carregar la pel·lícula em diu que no està indexada i que he d'anar a Eines i reconstruir fotogrames. Després de fer-ho, m'avisa de que no s'ha trobat descodificador d'audio i que el desament d'A+V generarà un fitxer defectuós.

Els còdecs els dec tenir tots.

---

### Post by kimet on 2010-06-13
Has de tenir instal.lat el paquet w32codecs o w64codecs des de el repositori que t'indica l'Wgarcia.


De quin format d'audio es tracta concretament?

---

### Post by marmotona on 2010-06-13
> **kimet said:**
> Has de tenir instal.lat el paquet w32codecs o w64codecs des de el repositori que t'indica l'Wgarcia.


De quin format d'audio es tracta concretament?

No sé on son els medibuntu aquests. Jo pensava que activant els multiverse ja valia.:confused:

El format que porten les pel·lícules és quelcom semblant a AC3 o qualsevol altra cosa. Sembla que el meu reproductor USB només llegeix mp3.

---

### Post by wgarcia on 2010-06-13
Primer verifica que no els tinguis ja instal·lats mirant a Sistema -> Administració -> Fonts de programari, a la pestanya "Altre programari". 

Si no el tens, els repositoris "medibuntu" els pots instal·lar entrant la següent parrafada des d'una terminal de comandes:

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

---

### Post by marmotona on 2010-06-13
> **wgarcia said:**
> Primer verifica que no els tinguis ja instal·lats mirant a Sistema -> Administració -> Fonts de programari, a la pestanya "Altra programari". 

Si no el tens, els repositoris "medibuntu" els pots instal·lar entrant la següent parrafada des d'una terminal de comandes:

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

Tinc els repositoris, estan revisats i actualitzats però l'Avidemux continua dient que no hi ha codecs per a aquest fitxer i no em dóna la opció d'escollir el format.

---

### Post by wgarcia on 2010-06-13
I de quin format de vídeo es tracta?

---

### Post by marmotona on 2010-06-14
> **wgarcia said:**
> i de quin format de vídeo es tracta?

avi.

---

### Post by papapep on 2010-06-14
Marmotona, tal i [com t'ha comentat en Kimet abans]("http://ubuntuforums.org/showpost.php?p=9454084&postcount=10") et cal instal·lar, ara que ja tens els repositoris de Medibuntu a la vista, el paquet [w32codecs]("http://packages.medibuntu.org/lucid/w32codecs.html") (si tens l'Ubuntu de 32 bits) o [w64codecs]("http://packages.medibuntu.org/lucid/w64codecs.html") (si tens el de 64 bits).
Un cop tinguis el paquet que et pertoqui instal·lat, probablement l'Avidemux ja sàpiga què fer amb el teu vídeo.

Si fas:

```
file nom_del_fitxer_de_vídeo
```

què et diu?

---

### Post by marmotona on 2010-06-16
Em diu:

> ~$ file Alla on viuen els monstres
Alla:     ERROR: cannot open `Alla' (No such file or directory)
on:       ERROR: cannot open `on' (No such file or directory)
viuen:    ERROR: cannot open `viuen' (No such file or directory)
els:      ERROR: cannot open `els' (No such file or directory)
monstres: ERROR: cannot open `monstres' (No such file or directory)
 

---

### Post by wgarcia on 2010-06-16
Et surt que no troba el fitxer perquè el nom del fitxer té espais i això no s'intepreta bé des de la línia de comandes. 

Per tant has de posar-li cometes o usar "\ " per indicar els espais

file "Alla on viuen els montres"

o

file Alla\ on\ viuen\ els\ monstres

---

### Post by marmotona on 2010-06-17
Mireu:

> ~$ file Alla/on/viuen/els/monstres
Alla/on/viuen/els/monstres: ERROR: cannot open `Alla/on/viuen/els/monstres' (No such file or directory)
angels@angels-laptop:~$ file "Alla on viuen els monstres"
Alla on viuen els monstres: ERROR: cannot open `Alla on viuen els monstres' (No such file or directory)

---

### Post by wgarcia on 2010-06-17
Has de deixar un espai després de les barres, que a més són les barres cap endavant ("\ "), no cap darrere (/):

file Alla\ on\ viuen\ els\ monstres

---

### Post by marmotona on 2010-06-17
Així?:

> ~$ file Alla\ on\ viuen\ els\ monstres
Alla on viuen els monstres: ERROR: cannot open `Alla on viuen els monstres' (No such file or directory)


---

### Post by wgarcia on 2010-06-18
Com es veu el nom del fitxer quan fas 

ls

a la carpeta on està?

---

### Post by marmotona on 2010-06-18
Així:

> Alla on viuen els monstres.avi

---

### Post by wgarcia on 2010-06-18
Llavors la instrucció correcta és:

file Alla\ on\ viuen\ els\ monstres.avi

---

### Post by marmotona on 2010-06-18
> **wgarcia said:**
> Llavors la instrucció correcta és:

file Alla\ on\ viuen\ els\ monstres.avi

És el que jo pensava, però no. Gràcies per la teva paciència, però no va:

> ~$ file Alla\ on\ viuen\ els\ monstres.avi
Alla on viuen els monstres.avi: ERROR: cannot open `Alla on viuen els monstres.avi' (No such file or directory)

---

### Post by wgarcia on 2010-06-19
Què tal 

file Alla*

??

---

### Post by marmotona on 2010-06-19
> **wgarcia said:**
> Què tal 

file Alla*

??

Idéntica resposta.

---

### Post by wgarcia on 2010-06-19
Vols dir que et torna a dir:

Alla on viuen els monstres.avi: ERROR: cannot open `Alla on viuen els monstres.avi' (No such file or directory) 

??

---

### Post by marmotona on 2010-06-19
Sí.

Bé, no, vul dir que em respon:

> ~$ file Alla*
Alla*: ERROR: cannot open `Alla*' (No such file or directory) 			 		

---

### Post by papapep on 2010-06-19
Marmotona, 

Mira, és igual deixa el "file" i fes l'altre tema per que l'avidemux et pugui convertir d'àudio.

> Marmotona, tal i com t'ha comentat en Kimet abans et cal instal·lar, ara que ja tens els repositoris de Medibuntu a la vista, el paquet w32codecs (si tens l'Ubuntu de 32 bits) o w64codecs (si tens el de 64 bits).
Un cop tinguis el paquet que et pertoqui instal·lat, probablement l'Avidemux ja sàpiga què fer amb el teu vídeo.


---

### Post by marmotona on 2010-06-19
No hi ha cap canvi. El menú copiat de l'Avidemux no desplega cap opció.

---

### Post by papapep on 2010-06-19
Executa això a un terminal per veure si estan correctament instal·lats:

```
sudo aptitude search codecs|grep ^i
```

copia-ho i enganxa-ho, per a evitar errors tipogràfics i enganxa aquí el que et surti.

---

### Post by Diegstroyer on 2010-06-19
Proba això, posa en una terminal:

file arrossega-aquí-l'arxiu.avi

On diu arrossega-aquí-l'arxiu.avi, has de fer això mateix, botó dret sobre l'arxiu i arrossegar-lo darrera de file (amb un espai després de file), i et quedarà una cosa semblant a la ubicació de l'arxiu, més o menys així:

 file '/home/usuari/Descàrregues/Alla donde viven los monstruos.avi'

Com veus és la ruta a l'arxiu, no el nom de l'arxiu en si, la comanda que et comenten abans només serveix si tens l'arxiu dins del Home de l'usuari, fora de qualsevol carpeta.

Salut

---

### Post by marmotona on 2010-06-19
Això és el que em respon el terminal:

> i   libk3b6-extracodecs             - The KDE CD/DVD burning application library
i   non-free-codecs                 - Non-free codecs                           
i   w64codecs                       - Proprietary codec binaries, x86_64 version


---

### Post by marmotona on 2010-06-19
> **Diegstroyer said:**
> Proba això, posa en una terminal:

file arrossega-aquí-l'arxiu.avi

On diu arrossega-aquí-l'arxiu.avi, has de fer això mateix, botó dret sobre l'arxiu i arrossegar-lo darrera de file (amb un espai després de file), i et quedarà una cosa semblant a la ubicació de l'arxiu, més o menys així:

 file '/home/usuari/Descàrregues/Alla donde viven los monstruos.avi'

Com veus és la ruta a l'arxiu, no el nom de l'arxiu en si, la comanda que et comenten abans només serveix si tens l'arxiu dins del Home de l'usuari, fora de qualsevol carpeta.

Salut


  Ara sí i em respon:

> RIFF (little-endian) data, AVI, 720 x 302, 25.00 fps, video: XviD, audio: Dolby AC3 (6 channels, 48000 Hz)


Però no és el botó dret, sino l'esquerre.

---

### Post by marmotona on 2010-06-20
Entesos. Veig que tampoc no sabeu què fer. Us agraeixo igualment el temps que m'heu dedicat.

Fins una altra!.

---

