---
title: "Traductor [office]"
date: 2007-07-23
forum: Catalan Team
---

### Post by prostata on 2007-07-23
Sabeu si hi ha dins els repositoris Ubuntu algun traductor de llenguatges de per exemple català-castellà a angles?? A windows hi han molts per exemple powertranslator pro que es poden integrar perfectament amb el word. Doncs quelcom així o encara que no s'hi integri, també m'aniria prou bé.

Gràcies

---

### Post by RainCT on 2007-07-23
No sé si et servirà per de diccionari català <-> anglès tens el "qdacco" al Synaptic, simple però eficaç, i a més Open Source. Jo el faig servir cada dos per tres :).

Pàgina oficial (amb consultes via web): [http://www.catalandictionary.org/catala/](http://www.catalandictionary.org/catala/)

---

### Post by prostata on 2007-07-24
> **RainCT said:**
> No sé si et servirà per de diccionari català <-> anglès tens el "qdacco" al Synaptic, simple però eficaç, i a més Open Source. Jo el faig servir cada dos per tres :).

Pàgina oficial (amb consultes via web): [http://www.catalandictionary.org/catala/](http://www.catalandictionary.org/catala/)


ja he instal-lat el gdacco, però no el veig per en lloc, ¿em pots "orientar" una miqueta?
gràcies

---

### Post by papapep on 2007-07-24
Al menú no sé on para, és qüestió de buscar-lo, però si fas Alt+F2 s'obrirà un diàleg on podràs posar "qdacco" i executar-lo.

---

### Post by ernestux on 2008-04-05
Acabo d' instal·lar qdacco, perquè necessitava traduir un text, però he vist que només és un diccionari i no un  traductor.
De traductor de textos en català-castellà-francès-anglès-alemany  he trobat aquest en línia, que no està malament:

**[http://traductor.gencat.net/](http://traductor.gencat.net/)**

I català-castellà:  

** [http://www.softcatala.org/traductor/](http://www.softcatala.org/traductor/)**

Ernest

---

### Post by xavi on 2008-04-06
Hola a tothom:

Cal que conegueu l'**Apertium**, amb llicència GPL!: [http://apertium.sf.net]("http://apertium.sf.net").

Es pot fer servir per xarxa per traduir parells d'idiomes (català < - > castellà va molt bé i mooooolt més ràpid que el de gencat, català < - > francès diuen que va bé - jo no sé francès - , i català < - > anglès per ara és molt limitat, però millorant amb el temps).

També es poden traduir documents sencers amb format odt inclòs. 

I el que el fa més interessant, és que ja han tret el paquet per debian... (i està als dipòsits d'Ubuntu).

Em sobta que ningú d'aquest forum LoCo Tema Catala el conegués i hagués citat abans... (jo no puc donar massa feedback en aquest fòrum, però avui m'ha donat per fer una ullada, des de fa mesos que no m'ho mirava...).

Salut 

Xavi

[http://moviments.net/cursos](http://moviments.net/cursos) 
Cursos gratuïts de GNU/Linux amb Ubuntu, entre molts altres :-) (gràcies a una subvenció pública)

---

### Post by Miquel Ubuntero on 2008-04-07
Molt be Xavi.
M'agradat molt el Apertium. Fins hi tot es pot provar sense instal·lar-ho!
Gracies per recomenar una eina tan bona.
Salut!

---

### Post by SiscoGarcia on 2008-04-07
Totalment d'acord amb el Miquel. És una bona solució que a més permet la traducció de textos sense límit de paraules (al menys més llargs que el de gencat).

Gràcies Xavi.

---

### Post by ernestux on 2008-04-09
Hola,
He instal·lat del synaptic apertium els paquets:

ii  apertium                                   1.0.3-3ubuntu1                       Shallow-transfer machine translation engine
ii  apertium-es-ca                             1.0.1-1                              Apertium language pair: Spanish<->Catalan
ii  apertium-fr-ca                             0.7-1                                Apertium language pair: French<->Catalan
ii  libapertium-1.0-0                          1.0.3-3ubuntu1                       Shared library for Apertium

.... però no trobo com fer-lo córrer, no el localitzo en cap menú,
poso a la terminal:  $ apertium    i surt:  bash: apertium: command not found
Com ?

---

### Post by pespin on 2008-04-11
Prova a buscar el executable amb la ordre:
```
sudo updatedb && locate *bin/*apertium*
```

---

### Post by ernestux on 2008-04-11
Els paquets que localitza son:
/usr/bin/apertium-filter-ambiguity
/usr/bin/apertium-gen-deformat
/usr/bin/apertium-preprocess-transfer
/usr/bin/apertium-gen-transfer
/usr/bin/apertium-gen-tagger
/usr/bin/apertium-retxt
/usr/bin/apertium-rehtml
/usr/bin/apertium-pretransfer
/usr/bin/apertium-gen-reformat
/usr/bin/apertium-validate-tagger
/usr/bin/apertium-rertf
/usr/bin/apertium-validate-transfer
/usr/bin/apertium-tagger
/usr/bin/apertium-translator
/usr/bin/apertium-destxt
/usr/bin/apertium-validate-dictionary
/usr/bin/apertium-deshtml
/usr/bin/apertium-desrtf
/usr/bin/apertium-transfer

Però no veig com executar-lo.

---

### Post by lluisanunez on 2008-04-12
Crec que l'executable és apertium-translator

També veig a la pàgina de documentació:
[http://apertium.sourceforge.net/install.html](http://apertium.sourceforge.net/install.html)
que cal insta&#320;lar també el paquet [B]lttoolbox

[/B]

---

### Post by ernestux on 2008-04-14
Hola,
Seguint les instruccions em surt:

$ apertium-translator /home/ernestux/usr/bin/apertium-es-ca es-ca txt <traducir.odt >traduir
Warning: unsupported locale, fallback to "C"
Warning: unsupported locale, fallback to "C"
Error: can't stat file '/home/ernestux/usr/bin/apertium-es-ca/trules-es-ca.xml'.

No sé que hauria de fer; Potser és millor traduir via internet, però.
Gràcies

---

