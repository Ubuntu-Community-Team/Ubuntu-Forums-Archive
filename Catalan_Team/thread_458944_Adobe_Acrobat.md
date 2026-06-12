---
title: "Adobe Acrobat"
date: 2007-05-30
forum: Catalan Team
---

### Post by prostata on 2007-05-30
Sabeu si hi ha versió per a Ubuntu de adobe acrobat??? pel que vull fer adobe reader no em serveix per a res...

gràcies

---

### Post by CarlesOriol on 2007-05-30
Hi ha eines per fer gairebé tot el que fas amb creació/modificació amb l'acrobat en els repositoris estandards.

Digues que vols fer i et guiem.

Carles Oriol

---

### Post by prostata on 2007-05-30
> **CarlesOriol said:**
> Hi ha eines per fer gairebé tot el que fas amb creació/modificació amb l'acrobat en els repositoris estandards.

Digues que vols fer i et guiem.

Carles Oriol

Per exemple (com amb windows), crear pdf's a partir d'una URL

---

### Post by CarlesOriol on 2007-05-30
Fàcil.

Aquí si surt un kdeista ens dirà que en kde sols has d'imprimir. Es veritat, en kde és més sencill ja ho tens tot preparat.

En gnome pots insta&#320;lar el programa cups-pdf i configurar la impresora virtual.

i encara tens un altre mètode que serveix per milions d'altres casos. Sempre pots imprimir en gairebé tots els programes a un arxiu en format .ps (postscript) aquests arxius es poden convertir a pdf (ja que son cosins) amb l'eina ps2pdf. Aquesta jo fins i tot la tinc posada a l'execució d'arxius ps i així els puc convertir a cop de ratolí.

---

### Post by CarlesOriol on 2007-05-30
NOTA DE FORMAT.

La opció QUOTE serveix per quant en un fil tens moltes respostes i vols fer referència a una en contret, ho notifiques amb el quote.

En aquest cas, on no tenim respostes creuades, amb el quick reply n'hi ha prou.

---

### Post by prostata on 2007-05-30
> **CarlesOriol said:**
> Fàcil.

Aquí si surt un kdeista ens dirà que en kde sols has d'imprimir. Es veritat, en kde és més sencill ja ho tens tot preparat.

En gnome pots insta&#320;lar el programa cups-pdf i configurar la impresora virtual.

i encara tens un altre mètode que serveix per milions d'altres casos. Sempre pots imprimir en gairebé tots els programes a un arxiu en format .ps (postscript) aquests arxius es poden convertir a pdf (ja que son cosins) amb l'eina ps2pdf. Aquesta jo fins i tot la tinc posada a l'execució d'arxius ps i així els puc convertir a cop de ratolí.

Si, però... ;-)

mira per exemple aquesta web:  [http://www.wikilearning.com/curso_de_linux_para_novatos_brutos_y_extremadamente_torpes-wkc-509.htm](http://www.wikilearning.com/curso_de_linux_para_novatos_brutos_y_extremadamente_torpes-wkc-509.htm)

és cert que puc imprimir en un postcrip la pàgina, però sols aquesta pàgina, per contra si faig servir (en windows) acrobat puc fer tot un PDF de la web i desprès imprimir-la tota a l'hora, ¿m'explico??, doncs això és el que vull fer, per exemple.

---

### Post by orestesmas on 2007-05-30
No conec res que faci impressions recursives de webs (suposo que és això el que vols). Potser es podria fer baixant-te la web amb wget i després utilitzar el konqueror (controlat via DCOP) per anar imprimint les pàgines d'una en una. No és que sigui ciència nuclear, però s'ha de saber fer.

De tota manera, en la web que en mostres jo diria el següent:

1) Són només 30 capítols, és assumible fer-ho a mà pàgina a pàgina.
2) Les pàgines tenen molta publicitat i altres elements indesitjats. Seria molt millor utilitzar una utilitat com l'endollable "scrapbook" del firefox per tal de retallar els trossos de la pàgina que t'interessen, i en acabat, imprimir-les de forma "neta".

---

### Post by prostata on 2007-05-31
> **orestesmas said:**
> No conec res que faci impressions recursives de webs (suposo que és això el que vols). Potser es podria fer baixant-te la web amb wget i després utilitzar el konqueror (controlat via DCOP) per anar imprimint les pàgines d'una en una. No és que sigui ciència nuclear, però s'ha de saber fer.

De tota manera, en la web que en mostres jo diria el següent:

1) Són només 30 capítols, és assumible fer-ho a mà pàgina a pàgina.
2) Les pàgines tenen molta publicitat i altres elements indesitjats. Seria molt millor utilitzar una utilitat com l'endollable "scrapbook" del firefox per tal de retallar els trossos de la pàgina que t'interessen, i en acabat, imprimir-les de forma "neta".

No és pot interpretar com a impressions recursives de webs, de fet am acrobat el que faig es crear un pdf a partir de la URL, indicant el nivell de profunditat, i certament hi han moltes pàgines que no em poden interesar en un moment, pero quan ja tinc el pdf és quan veig el que si m'interesa i el que no, i a leshores elimino alló que no vull, i em quedo amb el que si vull, fàcil ;-)

En el cas de l'exemple son 30 càpitols pero quan ho vaig fer, tinc el manual devant meu van sortir un cop tot  net  gaira bé 200 pàgines, que amb acrobat les vaig imprimir d'un cop i no d'una en una.

he descarregat scarpbook i el prvaré, si tinc problems t'ho dic, OK.
Gràcies

---

### Post by orestesmas on 2007-05-31
Bé, jo això ho interpreto com una impressió recursiva, però no ens barallarem per qüestions terminològiques :-)

> de fet am acrobat el que faig es crear un pdf a partir de la URL, indicant el nivell de profunditat, i certament hi han moltes pàgines que no em poden interesar en un moment, pero quan ja tinc el pdf és quan veig el que si m'interesa i el que no, i a leshores elimino alló que no vull, i em quedo amb el que si vull, fàcil 

Potser és fàcil, però també és pesat, perquè has d'anar imprimint les pàgines que vols.

Si tens el document en PostScript hi ha unes eines molt potents per eliminar pàgines, concatenar documents, etc. que pots utilitzar per acabar amb un únic document PostScript (que pots convertir a PDF) que contingui únicament allò que t'interessa. Molt més manejable.

I quan jo parlava de pàgines, em referia a pàgines HTML, no a pàgines impreses en el PDF final. 200 pàgines són moltes, però només són 30 pàgines HTML, i per imprimir-les només cal entrar en cadascuna d'elles i donar-li al botó d'imprimir. 30 vegades no són massa.

---

### Post by prostata on 2007-05-31
> **orestesmas said:**
> Bé, jo això ho interpreto com una impressió recursiva, però no ens barallarem per qüestions terminològiques :-)



Potser és fàcil, però també és pesat, perquè has d'anar imprimint les pàgines que vols.

Si tens el document en PostScript hi ha unes eines molt potents per eliminar pàgines, concatenar documents, etc. que pots utilitzar per acabar amb un únic document PostScript (que pots convertir a PDF) que contingui únicament allò que t'interessa. Molt més manejable.

I quan jo parlava de pàgines, em referia a pàgines HTML, no a pàgines impreses en el PDF final. 200 pàgines són moltes, però només són 30 pàgines HTML, i per imprimir-les només cal entrar en cadascuna d'elles i donar-li al botó d'imprimir. 30 vegades no són massa.

pot ser no me estic explicant bé, i ni que sigui per els que ens puguin llegir...

Amb la web de l'exemple, el que faig amb acrobat es crear segons el nivell definit que convingui un pdf. Un cop tinc el pdf puc veurer, avans d'imprimir, a la barra lateral esquerra, les pàgines que son insteressants per als meus objectius. Les pàgines que no vull, i sempre avans d'imprimir, sentzitllament les elimino. Un cop "depurat" sobre el mateix pdf, i sempre, repetiex-ho, sempre avans d'imprimir, el que aconseguix-ho, es obtenir un pdf final, i un cop aquest pdf final és el que jo vull a leshores es quan imprimeix-ho el document. I si, és clar, que avans l'haig de depurar de tot alló que no vull, però és que això és com és fa inclus amb qualsevol altre eine. Te un procediment previ de depuració, i un posterior d'impressió d'alló que ja vols. D'altre costat un cop feta la depuració i a part de la opció d'impressió et queda un fitxer amb pdf, perfectament consultable etc, etc,

salut

---

### Post by trinkus on 2007-06-29
Ep, no se si pixo fora de test pero per editar/modificar/canviar arxius pdf jo he provat el pdfedit i va prou be, nomes a a vegades se'm volatilitza en suprimir moltes pagines... pero va be... el pots treure del Symaptic o de [www.getdeb.net](www.getdeb.net) (una web amb molts ubuntuprograms força recomanable, d'altra banda)

Trinkus

---

