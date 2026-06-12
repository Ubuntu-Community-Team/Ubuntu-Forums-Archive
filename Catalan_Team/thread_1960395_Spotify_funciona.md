---
title: "Spotify funciona?"
date: 2012-04-17
forum: Catalan Team
---

### Post by slink on 2012-04-17
Hola, 

des de fa uns dies l'Spotify mostra el missatge:

> Lo sentimos, pero tu sistema operativo no es compatible con Spotify. 

T'envia a una pàgina on posa:

> Spotify para Linux
Por ser una versión preliminar, no ofrecemos soporte oficial,[blablabla] la versión para Linux sólo está disponible para suscriptores de Spotify Unlimited o Premium. 

I -quina casualitat- Spotify es penja cada 2x3...

A algú li passa el mateix?
Ho heu pogut arreglar?

Uso l'Ubuntu 10.4 i el wine 1.2.2

Gràcies

---

### Post by JoelUBNT on 2012-04-17
Hola, la versió de linux de Spotify em funciona perfectament a l'ubuntu 11.10, no cal ser usuari premium ni res d'això (malgrat el que diuen).  :guitar:

Simplement ves al centre de programari i busca l'spotify, i podràs oblidar-te del wine, per aquest programa.

Joel

---

### Post by slink on 2012-04-17
Ostres...  :confused:. 

Si, el millor serà que m'actualitzi i instal·li l'Spotify sense wine... ni contes premium...


Gràcies Joel

---

### Post by CarlesOriol on 2012-04-17
Mira a:

[http://www.spotify.com/es/download/previews/](http://www.spotify.com/es/download/previews/)

---

### Post by slink on 2012-04-18
L'Spotify ja funciona.

Moltes gràcies a tots dos!

Slink

---

### Post by U-Joan on 2012-04-26
Segur que hi ha l'Spotify al centre de programari de l'Ubuntu 11.10? A mi no em surt... :(

---

### Post by Kette on 2012-04-26
Per tenir-ho has d'instal·lar el dipòsit que el conté. Mira l'enllaç que ha posat CarlesOriol, t'ho explica perfectament.
Salut

---

### Post by U-Joan on 2012-04-29
Sí, he provat de posar en el terminal les ordres que apareixen a l'enllaç, però m'he quedat encallat a la primera perquè em respon que no reconeix l'ordre "deb".

---

### Post by 19preguntes on 2012-04-29
És que abans has de ficar al terminal:

```
sudo gedit /etc/apt/sources.list
```S'obrirà un fitxer de text, i abaix de tot del fitxer has d'afegir-hi la línia de codi que hi ha a l'enllaç que deia en CarlesOriol:[FONT=Verdana]

```
deb http://repository.spotify.com stable non-free
```[/FONT]
Desa i tanca el fitxer de text, i després ja només has de ficar al terminal la resta de coses que diu a l'enllaç.Salut!

---

### Post by Kette on 2012-04-30
> **U-Joan said:**
> Sí, he provat de posar en el terminal les ordres que apareixen a l'enllaç, però m'he quedat encallat a la primera perquè em respon que no reconeix l'ordre "deb".

Disculpa, he donat per bo que sabies com fer-ho. Afegir un dipòsit de programari amb el terminal és tal com diu “19preguntes” però tens l'opció de fer-ho de forma gràfica:
obres el centre de programari, en el menú tries “edita” i a baix de tot “fonts de programari”. En aquesta finestra selecciones la pestanya “altre programari”, prems “afegeix” i en el requadre enganxes “deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free”. Ja esta.

---

### Post by U-Joan on 2012-05-19
Gràcies per les vostres respostes. Ho he intentat de forma gràfica i a través del terminal i res. Al final em surt "No s'ha trobat el paquet spotify-client-qt".

Supòs que dec estar fent malament algun pas, però no veig quin... :(

---

### Post by wgarcia on 2012-05-19
A aquest enllaç:

[http://www.ubuntuupdates.org/ppa/spotify?dist=stable](http://www.ubuntuupdates.org/ppa/spotify?dist=stable)

discuteixen el problema que menciones. Em sembla entendre que també has d'afegir

```
deb-src http://repository.spotify.com stable non-free
```

a "sources.list" (o crear un fitxer específic per a les dues noves línies a "sources.list.d" cosa que és millor per no emmerdar el fitxer general sources.list), i no oblidar-te de fer:

```
sudo apt-get update
```

abans d'intentar instal·lar spotify.

---

### Post by U-Joan on 2012-05-19
Ho he fet, però ara em surt al terminal:

No s'ha pogut obtenir [http://repository.spotify.com/dists/stable/InRelease](http://repository.spotify.com/dists/stable/InRelease)  No s'ha trobat l'entrada «non-free/source/Sources» esperada, al fitxer Release (entrada errònia al sources.list o fitxer malformat)

E: Some index files failed to download. They have been ignored, or old ones used instead.

De fet també ho he provat amb el wine, i tampoc em va. Afegint
amb el winetricks l'Spotify he aconseguit tenir l'icona i semblava que havia d'anar bé, quan li faig clic i escric el meu usuari i contrasenya em reconeix i surt la finestra, però immediatament es bloqueja i m'apareix el següent missatge:

"The program spotify.exe han encountered a serious problem and needs to close. We are sorry for the inconvenience.
This can be caused by a problem in the program or a deficiency in wine, you may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application.
If this problem is not present under windows and has not been reported yet, you can report it at http://bugs.winehq.org"

Al primer enllaç que senyala no he trobat res, però al segon sí que he vist gent que es queixava que li apareixia el mateix missatge que a mi, però no he vist cap solució.

Com se m'està resistint l'Spotify!

---

### Post by wgarcia on 2012-05-19
Pots enganxar les línies que ara tens referents al spotify al fitxer sources.list?

---

### Post by U-Joan on 2012-05-20
Aquestes són les dues línies que hi ha al final de tot:

deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb-src [http://repository.spotify.com](http://repository.spotify.com) stable non-free

---

