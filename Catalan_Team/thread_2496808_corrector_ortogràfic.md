---
title: "corrector ortogràfic"
date: 2024-04-13
forum: Catalan Team
---

### Post by josep-maria on 2024-04-13
Tinc un pc nou, i no funciona el corrector ortogràfic. Amb el pc vell sí que anava bé, sense que jo hagués fet res.
He mirat a: sistema > preferències > personal > suport d'idioma, i diu català a dalt de tot.
Tinc l'ubuntu 23.10, mate 1.26.2, processador i5-7500
No he vist cap post anterior del mateix problema.

---

### Post by wgarcia on 2024-04-14
Vols dir que no funciona a alguna aplicació concreta? A quina?

---

### Post by josep-maria on 2024-04-14
No funciona enlloc, per exemple aquí mateix. M'ha subratllat gairebé tot aquest text.

---

### Post by wgarcia on 2024-04-14
Mira si el suport d'idioma està instal·lat completament. Per això potser el més fàcil és obrir una terminal i entrar

```
gnome-language-support
```

(tot i que és l'escriptori MATE, fa servir moltes eines de Gnome perquè MATE és un derivat)

Si falta alguna cosa t'ho dirà.

---

### Post by josep-maria on 2024-04-15
Diu això:
gnome-language-support: no s'ha trobat l'ordre

Si miro a suport d'idioma, diu això:
[https://blocs.tinet.cat/tokra/files/2024/04/Captura-de-pantalla-a-2024-04-15-11-34-33.png](https://blocs.tinet.cat/tokra/files/2024/04/Captura-de-pantalla-a-2024-04-15-11-34-33.png)

---

### Post by wgarcia on 2024-04-16
Sembla que finalment li van canviar el nom, perquè és això mateix que mostres. I si surt així, sembla que el suport d'idioma està instal·lat correctament i de forma completa. 

Però per assegurar-se, prova des d'una terminal a veure si realment estan instal·lats els paquets d'idioma, per exemple per al Libreoffice:

```
dpkg -l libreoffice-l10n-ca
```

---

### Post by josep-maria on 2024-04-19
Diu això:

dpkg -l libreoffice-l10n-ca
Desitjat=desconegUt/Instal·la/elimina(R)/Purga/retín(H)
| Estat=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Estat,Err: majúsc.=dolent)
||/ Nom                 Versió                   Arquitectura Descripció
+++-===================-========================-============-=================>
ii  libreoffice-l10n-ca 4:7.6.5-0ubuntu0.23.10.1 all          office productivi>
lines 1-6/6 (END)

---

### Post by wgarcia on 2024-04-20
La línia que posa "ii" diu que aquest paquet està instal·lat.

El paquet de llengua, almenys pel que fa al libreoffice, sí que està instal·lat. Tot i que aquest paquet és per la interfície d'usuari, no per als diccionaris de correcció ortogràfica. Els diccionaris haurien d'estar instal·lats si tens configurat el català. 

Per veure si el català és realment la llengua que té els sistema definit, des d'una terminal, es pot mirar la sortida de l'ordre:

```
locale
```

---

### Post by josep-maria on 2024-04-22
contesta això:

LANG=ca_ES.UTF-8
LANGUAGE=ca:en
LC_CTYPE="ca_ES.UTF-8"
LC_NUMERIC=ca_ES.UTF-8
LC_TIME=ca_ES.UTF-8
LC_COLLATE="ca_ES.UTF-8"
LC_MONETARY=ca_ES.UTF-8
LC_MESSAGES="ca_ES.UTF-8"
LC_PAPER=ca_ES.UTF-8
LC_NAME=ca_ES.UTF-8
LC_ADDRESS=ca_ES.UTF-8
LC_TELEPHONE=ca_ES.UTF-8
LC_MEASUREMENT=ca_ES.UTF-8
LC_IDENTIFICATION=ca_ES.UTF-8
LC_ALL=

---

### Post by wgarcia on 2024-04-23
També es veu tot correcte. Potser millor mirar en una aplicació concreta, a veure si es pot identificar perquè no fa la correcció ortogràfica correcta. Per exemple, al libreoffice Write, al menú Eines -> Llengües ... -> General, tens escollit el català? I a "Eines d'ajuda" o similar, està marcada la correcció ortogràfica?

Una altra cosa, mira si està "hunspell" instal·lat, que el LibreOffice (i el Firefox) fan servir per a la correcció ortogràfica:

```
dpkg -l hunspell*
```

Si surt "un":

```
sudo apt install hunspell-ca
```

---

### Post by josep-maria on 2024-04-23
Diu això:

dpkg -l hunspell*
Desitjat=desconegUt/Instal·la/elimina(R)/Purga/retín(H)
| Estat=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Estat,Err: majúsc.=dolent)
||/ Nom                       Versió          Arquitectura Descripció
+++-=========================-===============-============-====================>
un  hunspell                  <cap>           <cap>        (no hi ha cap descri>
ii  hunspell-ca               3.0.7+repack1-5 all          Catalan dictionaries>
un  hunspell-dictionary       <cap>           <cap>        (no hi ha cap descri>
un  hunspell-dictionary-ca    <cap>           <cap>        (no hi ha cap descri>
un  hunspell-dictionary-en    <cap>           <cap>        (no hi ha cap descri>
un  hunspell-dictionary-en-au <cap>           <cap>        (no hi ha cap descri>
un  hunspell-dictionary-en-ca <cap>           <cap>        (no hi ha cap descri>
un  hunspell-dictionary-en-gb <cap>           <cap>        (no hi ha cap descri>
un  hunspell-dictionary-en-us <cap>           <cap>        (no hi ha cap descri>
un  hunspell-dictionary-en-za <cap>           <cap>        (no hi ha cap descri>
un  hunspell-dictionary-es    <cap>           <cap>        (no hi ha cap descri>
ii  hunspell-en-au            1:2020.12.07-2  all          English (Australia) >
ii  hunspell-en-ca            1:2020.12.07-2  all          English (Canada) dic>
ii  hunspell-en-gb            1:7.5.0-1       all          English (GB) diction>
ii  hunspell-en-us            1:2020.12.07-2  all          English_american dic>
ii  hunspell-en-za            1:7.5.0-1       all          English (South Afric>
lines 1-21/21 (END)

---

### Post by josep-maria on 2024-04-23
Si faig: sudo apt install hunspell-ca, diu això:

hunspell-ca ja està en la versió més recent (3.0.7+repack1-5).
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 0 no actualitzats.

---

### Post by wgarcia on 2024-04-23
Doncs una altra cosa que està bé. Mira doncs al LibreOffice si l'idioma està definit com a català, i si està marcat que faci la correcció ortogràfica.

---

### Post by josep-maria on 2024-04-26
He pogut arreglar-ho al writer, fent:
eines > ortografia > opcions > edita = standard-català
Però això que escric ara al forum continua malament.

---

### Post by wgarcia on 2024-04-26
Si fas servir el Firefox com a navegador, mira si a Configuració -> General -> Llengües està el català definit com a llengua del navegador.

---

### Post by josep-maria on 2024-04-27
Si al firefox faig: paràmetres > llengua i aparença > llengua
Diu això:

Trieu la llengua en què es mostraran els menús, els missatges i les notificacions del Firefox.
Català
Verifica l'ortografia a mesura que s'escriu

Està ben definit, però me n'he adonat que no corregeix paraules angleses, tot i que a paràmetres>llengua hi diu català. Si vull eliminar Englis(US), no em deixa.

---

### Post by josep-maria on 2024-04-27
Cada cop que vull enviar un missatge de correu, surt una finestreta dient:
"hi ha hagut un error! S'han detectat errors d'ortografia al missatge"

---

### Post by wgarcia on 2024-04-27
Al Firefox, al meú paràmetres > llengua i aparença > llengua

Trieu la llengua en què es mostraran els menús, els missatges i les notificacions del Firefox.

A "Alternatives", està posat el català en primera posició?

Després mirem el Thunderbird, si és el que fas servir per enviar correu electrònic.

---

### Post by josep-maria on 2024-04-28
Sí, el català és a dalt de tot. A "defineix alternatives" diu:
Català
English (US)
He volgut esborrar English (US) i no em deixa.

---

### Post by wgarcia on 2024-04-28
Quan estàs editant un missatge a aquest fòrum al Firefox, si cliques amb el botó dret del ratolí a la finestra d'edició del missatge, et surt un menú contextual una opció del qual és "Llengües", i si desplegues aquesta opció, està marcat el català com a llengua?

També surt "verifica l'ortografia" al menú contextual i ha d'estar marcat.

---

### Post by josep-maria on 2024-04-28
Ara va bé. He fet clic al botó dret, i hi he afegit el "diccionari català" i el "Catalan language pack". També va bé als missatges del correu-e. 
Però quan ficava el català als paràmetres > llengua > alternatives del firefox, no funcionava. Només ha anat bé quan ho he fet aquí a la quick reply.
Gràcies.

---

