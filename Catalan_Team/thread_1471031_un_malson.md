---
title: "un malson"
date: 2010-05-03
forum: Catalan Team
---

### Post by Haliotis on 2010-05-03
Hola, ara deu fer un anyet que ja estic fent servir ubuntu, primer el jaunty i ara seguia amb el Karmic
Avui estic flipant...
estava amb el terminal intentant instaL3Lar un programa per treballar, graficar, etc.. dades oceanogràfiques. Es diu Ocean Data View ( [http://odv.awi.de/en/home/](http://odv.awi.de/en/home/) ). L'estava intentant instaL3lar a una carpeta dins el meu usuari, des de la consola...
m'he baixat l'arxiu d'internet, l'he descomprimit, i quan m'he adonat que no feia falta tenir privilegis d'administrador per executar l'arxiu d'instal·lació. He clicat directament sobre l'arxiu en sí...
llavors quan em demanava la carpeta on instal·lar-lo, he cancel·lat la instal·lació, i des de la consola he anat a borrar únicament la carpeta que havia creat per instal·lar-lo que tenia només permisos per root.
Quan me n'he adonat, se m'havien borrat TOTS els arxius del meu usuari excepte 3 carpetes, que s'han salvat no sé amb quin criteri.
No entenc si he posat malament l'ordre en el terminal... (que juraria que no, i ho he mirat mil cops) o si al cancel·lar la instal·lació del odv, s'ha col·lapsat i m'ho ha borrat...
Ara feia mesos que no feia còpies de seguretat, i tenia molts molts treballs fets del màster que simplement m'acaben de desaparèixer.
(curiosament les carpetes que s'han salvat són de les assignatures que encara no he acabat)
doncs bé, agrarïria qualsevol tipus d'ajut per recuperar els arxius que no he estat capaç de trobar a la paperera...
i també agraïria qualsevol tipus d'explicació al que ha passat.
Moltíssimes gràcies per tot, i sento si el to és una mica desesperant.
Max

---

### Post by wgarcia on 2010-05-03
Per veure què pots haver entrat per esborrar els teus arxius pots provar entrar "history" a la línia de comandes, et mostrarà les últimes comandes i potser identifiquis algun "rm -fr *" o coses com aquestes que et poden esborrar tot sense avisar. 

Suposo que el programa que estaves intentant instal·lar és de confiança i no pot incloure comandes com les que es mencionen a 
[http://ubuntuforums.org/announcement.php?f=206](http://ubuntuforums.org/announcement.php?f=206)
on es mostren diverses comandes malintencionades que poden portar l'usuari a esborrar les seves dades. 

En quant als arxius perduts, hi ha força esperances perquè encara hi són al disc, sols que ara no estan referenciats. 

Per recuperar els arxius perduts hi ha diverses eines, pots provar buscar a Internet les següents:

foremost
scalpel
Magic Rescue

En cada cas t'explicaran com fer-los servir per recuperar els arxius. 

El que és important és que no copiïs arxius nous al disc abans d'intentar la recuperació, perquè els arxius nous poden reescriure l'espai on tens els teus arxius vells, que encara hi són però que ara no estan referenciats i per tant el sistema considera que pot escriure a sobre en quant necessiti l'espai.

---

### Post by Haliotis on 2010-05-03
Gràcies wgarcia
Sí en principi el programa és de confiança, no sóc pas el primer que el faig servir, i dins de la oceanografia tothom el fa servir.. dels meus companys sé que l'han fet servir en windows i en mac, i no les hi ha passat res chungu... No sé, en fi, quan hagi recuperat documents indagaré més, a veure..
i sobre la recuperació, moltíssimes gràcies... m'has deixat una mica me&#347; tranquil.
Ara estic fent anar el magic rescue, i no tinc clar que em pugui recuperar tots els documents en openoffice, ja que no em sembla que siguin un dels formats suportats, però jo aniré provant...
Si funciona tot correctament intentaré mirar amb deteniment lo de l'Ocean Data View i ho penjaré al post.
Gràcies per enèssima vegada,
Max

---

### Post by wgarcia on 2010-05-03
El Magic Rescue va amb "receptes" on es defineixen els diferents formats que es poden recuperar. 

Les receptes estan a /usr/share/magicrescue/recipes/ , fixa't si estan suportats els documents openoffice.

---

### Post by kimet on 2010-05-03
Mira que aquestes carpetes no hagin canviat d'usuari i siguin propietat de root.

Salut.

---

### Post by papapep on 2010-05-04
Haliotis, NO hauries de fer servir el sistema de fitxers d'on vols recuperar les dades. O sigui, que hauries de arrencar l'ordinador d'"autos" amb un CD en viu o un pendrive, i executar les eines de recuperació de dades des de la RAM. Sinó, pots estar sobrescrivint les dades que t'importen sense adonar-te'n. Encara seria millor clonar les particions a  un disc dur nou i treballar allà, però ja no sé si t'és possible fer-ho.

Salut (suposo que no caldrà repetir-te mai més lo de les còpies de seguretat, oi?)

---

### Post by epages on 2010-05-04
> **kimet said:**
> Mira que aquestes carpetes no hagin canviat d'usuari i siguin propietat de root.

Salut.

Una forma ràpida de verificar-ho (NOMÉS UTILITZAR EN CAS D'EMERGÈNCIA AMB MOLT DE COMPTE! POT SER PERILLÓS!):
- Tecles ALT+F2
- Introdueix instrucció "gksudo nautilus"
- Introdueix la teva contrasenya
- Amb el nou explorador de fitxers que se't obrirà podràs veure i manipular (i compte, també esborrar!) tots els fitxers del sistema.

Sort!
Eduard

---

### Post by Haliotis on 2010-05-04
gràcies kimet i epages, ho he comprovat, i les carpetes i els arxius simplement no existeixen...
he pogut comprovar que només s'han salvat alguns documents que estaven fets amb win i que el nom tenia una codificació no vàlida...
wgarcia, sí sí, lo de mirar les receptes del Magic rescue ho ha mirat i allà no hi apareix cap .odt de l'openoffice... Ara porta quasi un dia recuperant coses amb el magicrescue, després provaré els altres programes que em vas dir per recuperar altres tipus d'arxiu...
papapep, cert he après la lliçó...
el teu pos l'he llegit una mica tard, però estic guardant tot el que em va recuperant a una carpeta a la partició del sistema de fitxers, /media/recuperados així em recomenava el tutorial de magic rescue, precisament per no trepitjar els arxius que estem intentant recuperar...
Moltíssimes gràcies a tots, vaig poder mirar la carpeta on m'ho esta recuperant, i sembla que m'anava trobant cosetes... fins i tot arxius que no em sonava haver tingut mai al meu ordinador... despre&#347; vindràla feina de reclassificar-ho tot en les careptes que tenia abans, i no em sembla poca feina, la veritat... No hi ha cap manera de recuperar l'estructura de les carpetes, oi?
quan acabi amb tot, faré còpia de seguretat, i intentaré esbrinar què va ser el causant del problema...
gràcies per enèssima vegada,
fins aviat
Max

---

### Post by Haliotis on 2010-05-06
Hola, gràcies a tots sincerament.
Vaig fent resum dels avenços...
Finalment vaig fer servir el Magic rescue (que és molt fàcil de fer servir) per recuperar jpg, docs, mp3, i alguna cosa més...
Però realment el programa que és el millor és scalpel... el vaig fer servir després i em va recuperar bastants arxius (alguns m'han quedat igualment corruptes i tal, però és més del que esperava).
l'Scalpel cal editar-lo per tal que et recuperi només el que vols.. és per això que posaré aquí el seu funcionament i l'afegitó que vaig haver de fer pq també em salvés els openoffice (em va salvar un treball a mig fer!!! :p)
en fi, primer de tot l'instalem
```
sudo apt-get install scalpel
```
Després anirem a configurar-lo
```
gedit /etc/scalpel/scalpel.conf
```
Amb això se'ns obre una finestra del Gedit on totes les línies tenen # al davant, és a dir que només són comentaris. Es tracta d'anar descomentant les línies de codi que ens interessa que busqui i salvi l'scalpel.
Els documents d'openoffice i els mail de thunderbird no s'hi troben per defecte, però si afegim aquestes línies al final del document obert amb gedit, tot arreglat:
```

#---------------------------------------------------------------------
# OPENOFFICE FILES
#---------------------------------------------------------------------
	odt y   20000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.textPK META-INF/manifest.xmlPK????????????????????
	ods y   10000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.spreadsheetPK  META-INF/manifest.xmlPK????????????????????
	odp y   10000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.presentationPK META-INF/manifest.xmlPK????????????????????
#	odg y   10000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.graphicsPK META-INF/manifest.xmlPK????????????????????
#	odc y   10000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.chartPK    META-INF/manifest.xmlPK????????????????????
#	odf y   10000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.formulaPK  META-INF/manifest.xmlPK????????????????????
#	odi y   10000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.imagePK    META-INF/manifest.xmlPK????????????????????
#	odm y   10000000    PK????????????????????????????mimetypeapplication/vnd.oasis.opendocument.text-masterPK  META-INF/manifest.xmlPK????????????????????
#	sxw y   10000000    PK????????????????????????????mimetypeapplication/vnd.sun.xml.writerPK  META-INF/manifest.xmlPK????????????????????
#---------------------------------------------------------------------
# THUNDERBIRD FILES
#---------------------------------------------------------------------
#	msf y   10000000    //\s<!--\s<mdb:mork:z\sv="1.4"/>\s-->?<\s<(a=c)>\s//\s(f=iso-8859-1)    //\s<!--\s<mdb:mork:z\sv="1.4"/>\s-->?<\s<(a=c)>\s//\s(f=iso-8859-1)    NEXT
#	actual Local Folder data files, no way to tell end so grab 100MB
	NONE    y   100000000 From????????????????????????????X-Mozilla-Status:\s?????X-Mozilla-Status2:    NEXT

```
Fixeu-vos que en el meu cas només estan descomentades les primeres línies per salvar documents de l'openoffice, aquí cadascú que faci el que pugui.
I quan tanquem el gedit, podem seguir escrivint al terminal, i executarem l'scalpel amb la següent ordre:
```
sudo scalpel /dev/sda7 -b -o /media/GENOMA/oo_recovered/
```
on sda7 era la meva partició de documents on havia perdut els arxius i GENOMA era el disc dur extern. oo_recovered és el nom on guardarà els arxius que vagi salvant en subcarpetes ordenades segons els tipus d'arxiu. oo_recovered és un nom que vaig triar jo, i el mateix scalpel et crea la carpeta (no cal que hi sigui prèviament)
i ja està :)
A més informar-vos, que vaig poder trobar una còpia de seguretat de l'1 de desembre... que no és genial, però millor del que em pensava... Parlant amb un amic, m'ha recomanat [https://www.dropbox.com/]("https://www.dropbox.com/") pq es facin còpies de seguretat automàtiques. Encara no ho he provat, però he après la lliçó.
Doncs bé, no ho marco com a solved (tampoc sé com s'ha de fer), però ara quan ho tingui tot una mica me&#347; endreçat, (ara tinc un munt d'arxius a ordenar) i hagi fet la còpia de seguretat provaré de tornar a instal·lar l'Ocean Data view, i intentaré esbrinar què va fallar, i ho comentaré per aquí (per si algú més s'hi troba) i ja el marcaré com a SOLVED.
Moltíssimes gràcies a tothom per tot
m'encanta linux :)
Max

---

### Post by papapep on 2010-05-06
Max, enhorabona per haver pogut (ni que sigui parcialment) superar el daltabaix. I també moltes gràcies per compartir la teva experiència. Sempre hi haurà algú que la pugui aprofitar (ni que sigui per recordar quant d'importants arriben a ser les còpies de seguretat :P)

---

### Post by Haliotis on 2010-05-17
En fi, finalment ha acabat el malson. Avui ja he ordenat totes els arxius salvats, he fet la còpia de seguretat, i he tornat a instal·lar l'Ocean Data View. I la instal·lació no m'ha donat cap tipus de problema. Funciona perfectament... Així que no entenc que podria haver passat, potser es va creuar alguna ordre que jo posava pel terminal amb alguna ordre de la cancel·lació de la instal·lació del programa.
En fi, espero haver sabut posar bé lo de [SOLVED].
I gràcies a tothom :)
Max

---

