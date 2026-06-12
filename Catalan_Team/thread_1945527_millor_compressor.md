---
title: "millor compressor"
date: 2012-03-23
forum: Catalan Team
---

### Post by jinglada on 2012-03-23
Bon dia,
vull comprimir la imatge del HD del DVD que va petar per guardar-la per si més endavant em cal intentar altres recuperacions. He mirat el fòrum on es recomana ZIP, GZIP, tar.bz2 i també l'ajuda.ubuntu.cat on a /9.10/hardware/ca/disks.html diu que el format .tar.lzma normalment ofereix la millor compressió.

Per aquest cas concret de la imatge del HD del DVD, quina compressió em recomaneu?

Gràcies a la bestreta.

---

### Post by kimet on 2012-03-23
Faig servir un programa que es diu lrzip.
```
lrztar arxiu-o-carpeta
``` per comprimir
```
lzrtar -d arxiu
```per descomprimir

Aquí hi ha informació de la wiki d'arch
 [https://wiki.archlinux.org/index.php/Lrzip](https://wiki.archlinux.org/index.php/Lrzip)
Les opcions amb lzo i zpaq no m'han funcionat mai, penso que es per qué no tinc prou memoria ram.

---

### Post by jinglada on 2012-03-23
> **kimet said:**
> Faig servir un programa que es diu lrzip.
```
lrztar arxiu-o-carpeta
``` per comprimir
```
lzrtar -d arxiu
```per descomprimir

Aquí hi ha informació de la wiki d'arch
 [https://wiki.archlinux.org/index.php/Lrzip](https://wiki.archlinux.org/index.php/Lrzip)
Les opcions amb lzo i zpaq no m'han funcionat mai, penso que es per qué no tinc prou memoria ram.

Gràcies kimet

Ja l'estic instal·lant ja que el .tar.lzma porta dues hores llargues i "només" ha comprimit 9 GB de les 230 GB que té la imatge.

---

### Post by jinglada on 2012-03-23
> **jinglada said:**
> Gràcies kimet

Ja l'estic instal·lant ja que el .tar.lzma porta dues hores llargues i "només" ha comprimit 9 GB de les 230 GB que té la imatge.

En 20 minuts ha fet un fitxer de 9 GB, o sigui 6/0,8 (=7,5) vegades més ràpid ja que comprimeix un 20% més que el lmza, oi que és això?

---

### Post by jinglada on 2012-03-23
kimet, ara veig que segons el wiki la instrucció que em dones és per a directoris, i jo he de comprimir un fitxer; fixa't:

----------------------------------
Compression of directories (recursive) requires lrztar which first tars the directory, then compresses the single file just like tar does when users compress with gzip or xz (tar zcf ... and tar Jcz ... respectfully).

This will produce an LZMA compressed archive "foo.tar.lrz" from a directory named "foo".

$ lrztar foo

This will produce an lzma compressed archive "bar.lrz" from a file named "bar"

$ lrzip bar

For extreme compression, add the -z switch which enables ZPAQ but takes notably longer than lzma.

$ lrztar -z foo

For extremely fast compression and decompression, use the -l switch for LZO.

$ lrzip -l bar
----------------------------------

He provat $ lrzip fitxer_imatge i va superlent, amb 20 minuts ha fet 450 KB. Ara provo amb la opció -l i veig que corre més o menys com lrztar.

---

### Post by kimet on 2012-03-23
> kimet, ara veig que segons el wiki la instrucció que em dones és per a directoris, i jo he de comprimir un fitxer; fixa't:

Funciona també per a fitxers el que pasa es que un fa servir tar i l'altre zip. 

Jo sempre faig servir el lrztar, les altres opcions em donen error de manca d'espai a buffers. De totes maneres 250gb...Fes proves amb fitxer petits i evalua quin va millor. Un altre cosa es la compressió final, tingues en compte que fitxers de video pot ser que resultin de igual mida que l'original, no es comprimeixen (o ja están comprimits).

Salut.

---

### Post by jinglada on 2012-03-23
> **kimet said:**
> Funciona també per a fitxers el que pasa es que un fa servir tar i l'altre zip. 

Jo sempre faig servir el lrztar, les altres opcions em donen error de manca d'espai a buffers. De totes maneres 250gb...Fes proves amb fitxer petits i evalua quin va millor. Un altre cosa es la compressió final, tingues en compte que fitxers de video pot ser que resultin de igual mida que l'original, no es comprimeixen (o ja están comprimits).

Salut.

Gràcies kimet! De moment no em dóna cap error; el que passa és que m'acapara molta cpu i no em deixa fer gaire res.

Els fitxers obtinguts amb el photorec són .mpg, que són comprimibles, en teoria, almenys al passar-los a .avi es comprimeixen força entre un 75 i un 90%. Tanmateix ara el compressor porta un 33% i el fitxer és de 75 GB cosa que vol dir que resultarà un fitxer de més de 225 GB quan l'original és de 233 GB, o sigui que em sembla que no comprimeix gens ni mica.

Quan he provat lrztar no informava del progrés; potser si es posa l'opció -i (show compressed file information)... 

Aniré fent proves i ja informaré.

Salut.

---

### Post by CarlesOriol on 2012-03-24
el xz és la evolució del lzma. prova'l

---

### Post by jinglada on 2012-03-24
> **CarlesOriol said:**
> el xz és la evolució del lzma. prova'l

Gràcies, Carles,

He posat: xz -v image2 i al cap d'1 hora de funcionament em dóna 

2,7 %    4790 Mib / 6520 MiB = 0,735    1,7 MiB/s   1 d 15 h

(Completion percentage, compressed size, uncompressed size,  compression  ratio, speed, and estimated time remaining) 

No sé si val la pena tenir l'ordinador engegat gairebé 2 dies per reduir 233 a 175-185 GB, estalviant 60-50 GB, que quan tingui els vídeos recuperats i  ordenats ja podré esborrar la imatge.

Aquest xz, per defecte comprimeix amb un nivell 6 (0-9) i el lrzip 7 però en canvi amb 5-6 hores ja va comprimir un 33%.

Resumint, l'xz, amb les opcions per defecte, i sobre una imatge de disc que conté vídeos .mpg, comprimeix un 20-30% (en aquest moment el ràtio és 0,79) a una velocitat de 1,6-1,7 MiB/s

---

