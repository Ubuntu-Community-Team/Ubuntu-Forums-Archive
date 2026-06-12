---
title: "Ubuntu em compte malament el tamany dels fitxers"
date: 2012-02-03
forum: Catalan Team
---

### Post by sianeu on 2012-02-03
D'un temps ençà, ubuntu 11.10 em fa els fitxers mès grans del que en realitat son. Posaria la ma al foc que al principi no passaba, peró el cas es que ara em passa fins i tot des del CD en Live.

Adjunto dos imatges on es pot veure la diferencia de tamany que detecten Windows i Ubuntu, i la diferencia de tamany en una descàrrega d'un fitxer.

D'on pot venir el problema?

---

### Post by wgarcia on 2012-02-03
Jo suposo que aquesta diferència ja hi era i no t'havies fixat, i em sembla que és un tema comú a tots els sistemes Linux.

L'explicació que he trobat buscant una mica és la següent:

Windows mesura els fitxers usant "megabytes falsificats", on un megabyte equival a 1000 kibibytes.

Els sistemes Linux mesuren els fitxers per mebibytes, on un mebibyte equival a 1024 kibibytes, i per tant el número que veus és més gran. Aquesta és la forma informàtica correcta de mesurar l'espai d'emmagatzematge als discos. 

Els fitxers òbviament, si són els mateixos però vistos des de dos sistemes operatius diferents, tenen la mateixa grandària. Simplement la forma de mesurar-los és diferent.

---

### Post by CarlesOriol on 2012-02-03
wgarcia, no estic d'acord. Tot i que els fabricants de discs i suports d'emmagatzenament si fan aquesta cosa tant bruta ni l'explorer del windows ni el nautilus de linux ho fan.

---

### Post by CarlesOriol on 2012-02-03
A més en qualsevol cas la mida seria a la inversa.

Crec que més aviat pot ser que estiguem en un sistema ntfs o fat i mentre que el windows mira la mida del fitxer el linux mira la mida de l'espai que ocupa aquest fitxer al disc.

---

### Post by CarlesOriol on 2012-02-03
Per cert qui arrodonix a la baixa (truncant) és el terminal quan li demanem "human" 

ls -lh

---

### Post by sianeu on 2012-02-03
Fixeu-vos en la captura de la baixada:

- En la web te 19.4 Mb
- En la finestreta de baixada del nautilus te 19.4 Mb
- La carpeta on ja está descarregat (carpeta de l'usuari /home) diu 20.4 Mb

---

### Post by CarlesOriol on 2012-02-03
Hi torno: Crec que més aviat pot ser que estiguem en un sistema ntfs o fat i mentre que el windows mira la mida del fitxer el linux mira la mida de l'espai que ocupa aquest fitxer al disc.

---

### Post by sianeu on 2012-02-03
Descarregant el fitxer directament a un USB (ntfs o fat32) pasa exactament el mateix. Ho dic per descartar problemes amb el disc dur.

---

### Post by wgarcia on 2012-02-04
@CarlesOriol, gràcies per les explicacions, ja dic que el que he posat és l'explicació que he trobat. 

Doncs serà el que dius que "mentre que el windows mira la mida del fitxer el linux mira la mida de l'espai que ocupa aquest fitxer al disc."

---

### Post by sianeu on 2012-02-04
No es el cas. Podeu comprobar-ho amb el vostre Ubuntu: Descarregueu-vos qualsevol fitxer (en el meu cas el Gimp de softcatalà), i veureu que la mida que indica la pàgina, la mida que compte el nautilus al descarregar i la mida un cop descarregat, es exactament la mateixa.

---

### Post by wgarcia on 2012-02-05
Doncs a veure si algú amb més coneixements tècnics ens pot aclarir el què...

---

### Post by sianeu on 2012-02-07
Bé, sembla que el problema es de la versió 11.10. En les versions anteriors no em passa.

Llavors ho he provat amb el Live-CD 11.10 en l'altre ordinador (encara te instal·lada la 11.04) i ha reproduït l'error. Abans ho havia provat amb la versió instal·lada i mesurava be, d'aquí que penses que era cosa del meu ordinador.

Podríeu confirmar-me si us passa el mateix? ja sigui amb la 11.10 instal·lada o des de LiveCD.

La diferencia de tamany no es massa gran per ser una qüestió de mesura de fitxer o espai en disc?

---

### Post by wgarcia on 2012-02-07
I no serà el tipus de format del disc? Les versions recents d'Ubuntu venen amb l'ext4 per defecte, però em sembla que l'11.04 ja hi venia.

---

### Post by sianeu on 2012-02-07
De tota manera, des de LiveCD no te importancia. I per si un cas vaig provar-ho amb el disc dur desconnectat amb el mateix resultat.

A tu no et passa?

---

### Post by wgarcia on 2012-02-08
He mirat el tamany d'un arxiu des de la terminal amb "ls -s" i em surt més petita que si la miro des de Nautilus.

Mirant una mica més he trobat aquest missatge de fòrum que diu una altra vegada que l'explicació és la diferència entre Mib i Mb. El Nautilus informa els tamanys en Mb i per tant dividex per 1000 per mostrar el número que veus. Si utilitzes Mib has de dividir per 1024, i per tant el tamany surt més petit. 

És a dir suposa't que baixes un fitxer amb 1024 bytes. "ls -s" dirà que té 1 MiB, mentre que Nautilus dirà que tens 1024/1000 = 1,024 MB. 

Suposo que es fa així per fer el Nautilus més amigable, perquè l'usuari pugui calcular en el sistema decimal en comptes d'aquesta altra conversió 1024 bytes = 1 Mib que no és tan intuïtiva.

Referència: [http://ubuntuforums.org/showthread.php?p=11354521](http://ubuntuforums.org/showthread.php?p=11354521)

---

### Post by sianeu on 2012-02-08
Sí, sembla que aquesta es l'explicació. Ubuntu medeix per 1000 en lloc de 1024 com fins ara. No m'agrada, per que entre altres coses un indicador d'una bona descàrrega era la coincidència de tamany.

La veritat es que no veig clar que no sigui un error. En fi.....

---

### Post by sianeu on 2012-02-08
En un altre lloc diuen que es Gnome3 el que a passat a medir-ho d'aquesta manera. Però potser el que has apuntat (i he comprovat en el meu) de fer **ls -s** ho desmentiria.... o no?

---

### Post by wgarcia on 2012-02-08
Em sembla que qui ho mesura així, en MB, o millor dit ho mostra així, és el Nautilus, que com dius depèn de Gnome. El sistema operatiu segueix treballant en MiB, com mostra el fet que les eines de sistema mostrin la grandària dels fitxers amb aquesta unitat de mesura.

---

### Post by sianeu on 2012-02-08
Deixem-ho així.
El sistema (Terminal) mesura en MiB (divideix per 1024), mentre gnome3 (nautilus) ho fa en MB (divdeix per 1000). O multiplica depèn de si vas amunt o avall.

Gràcies per l'ajut.

---

### Post by wgarcia on 2012-02-09
L'única correcció per tancar per la meva part aquest fil és que 1MB = 1000 kbytes (i no 1000 bytes com deia a dalt).

---

### Post by Lalaith on 2012-02-09
si és una qüestió de conversió, no podria haver-hi alguna opció de Nautilus a les preferències que et permetés canviar d'una escala a l'altre? L'he cercat a "preferències" dins del menú "edita" i no ho he trobat, però potser sí que es troba l'opció en algun lloc més amagat... o sino, deu ser quelcom senzill de fer, no?

---

