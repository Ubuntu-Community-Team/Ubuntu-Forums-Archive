---
title: "error humà, navegador per defecte"
date: 2009-08-15
forum: Catalan Team
---

### Post by egin on 2009-08-15
hola a tothom,

La qüestió és que he entrat al firefox amb permisos root i el sistema ha detectat aquesta acció com si fos d'un nou explorador i  per error he acceptat amb que aquest fos el navegador per defecte.

L'efecte és que ara no puc veure les adreces d'interès i m'agradaria desfer aquest aquest error i que sigui el firefox normal el navegador per defecte.

algú em podria donar un cop de mà?

moltes gràcies.

---

### Post by papapep on 2009-08-16
> L'efecte és que ara no puc veure les adreces d'interès i m'agradaria desfer aquest aquest error i que sigui el firefox normal el navegador per defecte.

Ja estàs al Firefox "normal". No n'hi ha dos (excepte que en tinguis dos instal·lats).
L'únic que hauríes de fer és obrir el Firefox des del teu usuari no-administrador, i hauries de trobar-ho tot com estava.
Per cert, emprar el navegador o qualsevol altra aplicació, especialment les que accedeixen directament a internet, és un suïcidi a nivell de seguretat. Els hi deixes la porta oberta fins la cuina (no és ben bé així, però gairebé) :)

---

### Post by egin on 2009-08-16
hola papapep,

gràcies per al teva resposta.

La veritat es que tens raó en que és el mateix firefox, però llavors com és que em demanava si el firefox, amb permisos root, volia ser el navegador per defecte? O el que seria el mateix, com puc desfer això?

El missatge d'error que indica el firefox és aquest: "les adreces d'interès i l'historial no seran funcionals perquè un dels fitxers del firefox l'utilitza una altre aplicació. Cert programari de seguretat podria estar provocant aquest problema"

De moment encara no he trobar la solució :S.

Al respecte d'entrar amb permisos root, estava intentant actualitzar el programari independentment de les llibreries d'ubuntu ja que he instal·lat el firefox 3.5 manualment. Però tindré en compte la teva aclaració per no tornar a caure en aquest error.

Salut

---

### Post by papapep on 2009-08-16
Firefox crea un perfil per a cada usuari que l'executa. Per a ell, root és un usuari com un altre. Per tant, si executes el Firefox des del teu usuari normal, t'hauràs de trobar tot com estava, ja que accedirà al perfil del teu usuari amb les adreces d'interés i personalitzacions que tinguessis. Si no ho fa així és que alguna cosa falla, però sol funcionar correctament.

Respecte el tema de actualitzar programari com a root independentment de les llibreries de l'ubuntu, no té res a veure amb executar Firefox com un usuari o un altre, crec que estàs barrejant conceptes. 
Si tens qualsevol dubte no tinguis problema en plantejar-lo abans d'inventar, que a vegades una pregunta a temps estalvia molts maldecaps ;)

---

### Post by egin on 2009-08-16
> **papapep said:**
>  Si tens qualsevol dubte no tinguis problema en plantejar-lo abans d'inventar, que a vegades una pregunta a temps estalvia molts maldecaps ;)

Comentar que no invento res, que aquesta forma d'actualitzar està penjada a internet a varis fòrums però tens raó en dir que és arriscada i que es millor utilitzar d'altres.

En tot cas, algú coneix aquest error del firefox per poder solucionar-lo?

salut

---

### Post by papapep on 2009-08-16
> Comentar que no invento res, que aquesta forma d'actualitzar està penjada a internet a varis fòrums però tens raó en dir que és arriscada i que és millor utilitzar d'altres.


És que aquesta NO és (en cap cas) una forma d'actualitzar programari. Si cal, dona'm més referències a veure per on van els trets dels fòrums que esmentes.

> En tot cas, algú coneix aquest error del firefox per poder 
solucionar-lo?

Quin error?? El de que et mostri perfils diferents per a diferents usuaris, vols dir això??

---

### Post by egin on 2009-08-16
"les adreces d'interès i l'historial no seran funcionals perquè un dels fitxers del firefox l'utilitza una altre aplicació. Cert programari de seguretat podria estar provocant aquest problema"

aquest error

---

### Post by papapep on 2009-08-16
I aquest error en quina situació exacta se't produeix? recorda que nosaltres no som davant el teu ordinador. Tot el que ens expliquis farà que poguem entendre el problema, o no.

---

### Post by egin on 2009-08-16
tens raó, pensava que era un error més usual i més fàcil de solucionar.

He esborrat el firefox i l'he tornat a instal·lar i el problema segueix igual (això no és windows, es nota XD) i he provat d'entrar un altre cop amb permisos de root i així si que funciona perfectament.


Se m'acudeixen un parell de solucions:

- Modificar el lloc on designa ubuntu l'explorador per defecte i dir-li que executi amb usuari normal (especulació)

- tirar pel dret i crear un perfil firefox i dir-li on  te tots els arxius de configuració /home/usurari/.mozilla/"nosekemés".

Però cap de les dues se com es fan i tot són especulacions.

Salut

---

### Post by papapep on 2009-08-17
> Se m'acudeixen un parell de solucions:

- Modificar el lloc on designa ubuntu el explorador per defecte i dir-li que executi amb usuari normal (especulació)

El lloc on se li indica els programes preferits és:

Sistema > Preferències > Aplicacions preferides > Pestanya "Internet"

- Quina versió de Firefox tens, i com l'has instal·lat?
- Quan l'executes com a "root", com ho fas?
- Si l'executes com el teu usuari normal, què deixa de fer bé? no troba les adreces d'interés?

> He esborrat el firefox i l'he tornat a instal·lar i el problema segueix igual (això no és windows, es nota XD)

No, sota cap punt de vista ho són d'iguals. Ni pel bo, ni pel dolent.

---

### Post by egin on 2009-08-19
Hola papapep,

> - Quina versió de Firefox tens, i com l'has instal·lat?
- Quan l'executes com a "root", com ho fas?
- Si l'executes com el teu usuari normal, què deixa de fer bé? no troba les adreces d'interés?- Faig servir el firefox 3.5 i l'he instal·lat desempaquetant a la carpeta /opt/

- Executo mitjançant  ```
$sudo firefox
``` - Apart de no trobar les adreces d'interès no grava cap mena d'historial ni cookies ni res més enllà de navegar. El que si que es mantenen són les contrasenyes desades i complements del firefox.

Si no trobo la solució l'esborraré i instal·laré la versió beta dels repositoris i a córrer... però no se com es posa en català :-(

Salut!

---

### Post by papapep on 2009-08-19
Un comentari previ. Quan es posa codi, l'etiqueta adequada és "CODE /CODE", que es genera amb el símbol # del menú d'edició d'apunts, i queda de la següent manera:

```
això és codi, una ordre de l'intérpret d'ordres, codi de programació, el que sigui
```

La "QUOTE /QUOTE", el que té una bafarada de text al menú, es fa servir per citar el que altres han dit abans.

No és que s'acabi pas el món per no fer-ho així, però volia explicar-ho ;)

Retornant al tema del fil:

Prova a executar la ordre sense el sudo, recorda que en cap cas és necessari, i molt menys recomanable, executar el navegador com a usuari amb drets totals d'administració:

```
firefox
```

A veure com et va tot plegat així.

---

### Post by egin on 2009-08-19
dons amb ```
firefox
``` no canvia res :S

---

### Post by papapep on 2009-08-19
Donat que, pel que sembla, has estat fent coses com a root sense controlar gaire el què, potser seria recomanable tornar-lo a descarregar, o, si encara tens el tar.gz, descomprimir-lo (com a usuari normal) on vulguis i provar de nou amb aquesta nova "instal·lació", sense executar-lo com a root.

Respecte els preferits i demés, dins /home/elteuusuari/.mozilla/firefox, de la teva instal·lació de repositori del Firefox, hauries de tenir un fitxer de nom profiles.ini i un directori de nom considerablement críptic, el meu es diu s8sl9njz.default, el **contingut** del qual si el copies a un de semblant (que no igual) que hauries de tenir sota la teva instal·lació manual del Firefox, al lloc que pertoqui, hauria de passar les dades que vols a aquest últim, si no vaig errat.

---

### Post by egin on 2009-08-19
> **papapep said:**
> Donat que, pel que sembla, has estat fent coses com a root sense controlar gaire el què, potser seria recomanable tornar-lo a descarregar, o, si encara tens el tar.gz, descomprimir-lo (com a usuari normal) on vulguis i provar de nou amb aquesta nova "instal·lació", sense executar-lo com a root.

Respecte els preferits i demés, dins /home/elteuusuari/.mozilla/firefox, de la teva instal·lació de repositori del Firefox, hauries de tenir un fitxer de nom profiles.ini i un directori de nom considerablement críptic, el meu es diu s8sl9njz.default, el **contingut** del qual si el copies a un de semblant (que no igual) que hauries de tenir sota la teva instal·lació manual del Firefox, al lloc que pertoqui, hauria de passar les dades que vols a aquest últim, si no vaig errat.

gracies per tot!

Al final he instal·lat el firefox 3.5 dels repositoris, ja que no he pogut solucionar el problema, i aquest ja funciona correctament però no se com es posa en català i no ho trobo enlloc :s (ara està amb anglès)

Com es fa? o no es pot??

Salut!

---

### Post by oriolsbd on 2009-08-20
Et pots baixar el paquet en català per al Firefox 3.5 del rebost de Softcatala:
[http://www.softcatala.org/wiki/Rebost:Paquet_catal%C3%A0_per_al_Firefox](http://www.softcatala.org/wiki/Rebost:Paquet_catal%C3%A0_per_al_Firefox)

Salut!

---

### Post by egin on 2009-08-25
> **oriolsbd said:**
> Et pots baixar el paquet en català per al Firefox 3.5 del rebost de Softcatala:
[http://www.softcatala.org/wiki/Rebost:Paquet_catal%C3%A0_per_al_Firefox](http://www.softcatala.org/wiki/Rebost:Paquet_catal%C3%A0_per_al_Firefox)

Salut!

Moltes gràcies Oriolsbd, no pensava que fos tan fàcil.

Salut!

---

