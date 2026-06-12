---
title: "Clonar H.D. amb Ubuntu"
date: 2009-04-02
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2009-04-02
Bon dia.
Tinc un H.D. 8 GB reconegut com sdb a Ubuntu.
Un altre H.D. 16 GB com sdc.

He fet des de Terminal: sudo dd if=/dev/sdb of=/dev/sdc bs=1MB

El resultat ha estat que al disc de 16 GB tinc un clon perfecte del de 8 GB però m'ha quedat un espai lliure sense particionar de 8 GB.

La meva pregunta es: Com es pot fer, si es possible, per que el resultat fos amb tot el disc de 16 GB ja aprofitat. O sigui, particionat completament en una única partició de 16 GB?

Salutacions cordials, Miquel.

---

### Post by papapep on 2009-04-02
[gparted]("http://packages.ubuntu.com/intrepid/gparted") et farà la feina.

---

### Post by Miquel Ubuntero on 2009-04-02
Hola Papapep.
Ja m'he insta&#320;lat Qparted. Segons he pogut veure, és un editor de particions. He provat d'eliminar les 2 particions d'uns 7 GB que tinc al disc de 16 GB. Les he esborrat, però no puc crear una única partició de 16 GB, només puc crear 2 de 7 GB.
Amb l'editor de particions d'Ubuntu GParted tampoc ho he pogut so&#320;lucionar.
Si no trobo cap eina per fer un clon d'un disc més petit que un altre, estic pensant d' insta&#320;lar de nou Ubuntu al de 16 GB dient-li "utilitza l'espai sencer", a veure que tal?
Salutacions, Miquel.
Ah! i gracies ;)

---

### Post by papapep on 2009-04-02
No entenc massa quin problema hi ha per redimensionar la partició...

Assumeixo que tens el disc que vols remenar (el de 16GB) desmuntat. A partir d'aquí, el gparted (suposo que Qparted igual) no m'ha tingut mai cap problema per a fer coses així.
Entenc, pel que dius, que has esborrat les dades que havies copiat amb **dd**, per tant tens el disc "verge". Torna a provar a fer una sola partició, i a veure quin error et diu el Gparted. Alguna cosa deu dir quan tu li demanes per a fer una sola partició amb tot l'espai, i no et deixa, no??

---

### Post by Miquel Ubuntero on 2009-04-02
> **papapep said:**
> No entenc massa quin problema hi ha per redimensionar la partició...

Assumeixo que tens el disc que vols remenar (el de 16GB) desmuntat.
Sí desmuntat.
 A partir d'aquí, el gparted (suposo que Qparted igual) no m'ha tingut mai cap problema per a fer coses així.
Entenc, pel que dius, que has esborrat les dades que havies copiat amb **dd**, per tant tens el disc "verge".
Si sense dades.
 Torna a provar a fer una sola partició, i a veure quin error et diu el Gparted. Alguna cosa deu dir quan tu li demanes per a fer una sola partició amb tot l'espai, i no et deixa, no??
Si inetento crear una nova partició no hem deixa fel-la de 16 GB. Simplement no puc posar més de 7.20 Gb. 
Adjunto una captura. A veure que et sembla.

---

### Post by papapep on 2009-04-02
Jo el Qtparted no l'he fet servir mai, però no pots carregar-te les 3? (això sembla, no?) particions que hi ha, per començar de 0 a sdf?

---

### Post by indiosincracia on 2009-04-02
Has de borrar l'extended.

---

### Post by PatrickVogeli on 2009-04-02
es normal que no puguis, per alla al mig hi tens una particio de 376 mb. Si no la borres, no podras pas fer una unica particio de 16gb.

salut!

---

### Post by Miquel Ubuntero on 2009-04-03
Hola de nou.
Avui he tornat a fer el mateix que air, o això crec, i si que he pogut eliminar totes les particions. Buff, per fi.

Ara estic pensant d'utilitzar remastersys en el h.d. petit, per més tard instal·lar la meva iso al h.d. més gran.

El primer que vaig provar per clonar, no hem va agradar. Perqué hem deixaba uns espait buit sense particionar.

Gracies a tots. Fins aviat.

---

### Post by CarlesOriol on 2009-04-05
Jo coincideixo amb l'indiosincracia i en PatrickVogeli sols cal eliminar la partició swap, després eliminar la extended on està contiguda i canviar la mida de la primera partició. Tot això es pot fer fàcilment amb el gparted.

Deixar un espai per la swap en aquest disc no sé si és massa bona idea, ja que probablement no serà prou gran per ser útil i si és un disc d'estat sòlid (pendrive, sds o similars) et reduirà considerablement la vida del dispositiu.

---

### Post by Miquel Ubuntero on 2009-04-05
> **CarlesOriol said:**
> Jo coincideixo amb l'indiosincracia i en PatrickVogeli sols cal eliminar la partició swap, després eliminar la extended on està contiguda i canviar la mida de la primera partició. Tot això es pot fer fàcilment amb el gparted.

Deixar un espai per la swap en aquest disc no sé si és massa bona idea, ja que probablement no serà prou gran per ser útil
Pregunta: Es pot insta&#320;lar Ubuntu sense swap? No! Oi?

 i si és un disc d'estat sòlid (pendrive, sds o similars) et reduirà considerablement la vida del dispositiu.
Ostres! No ho sabia. Per què redueix la vida del pendrive?

Gracies.

---

### Post by RainCT on 2009-04-06
Nota al marge: QtParted (si és que amb Q vols dir Qt) està sense mantenir fa temps (i de fet ja no està inclós a la Jaunty); és millor no fer-lo servir.


En quant a la pregunta del pendrive, perquè només s'hi pot escriure un nombre determinat de vegades i a la memòria SWAP s'hi està escrivint constantment.

---

### Post by CarlesOriol on 2009-04-07
[http://en.wikipedia.org/wiki/Flash_memory](http://en.wikipedia.org/wiki/Flash_memory)

Mira l'apartat memory wear. Bàsicament ve a dir que les memories tipus flash (o discs sòlids) tenen un nombre limitat de cops que es poden esborrar (cada cop que canvies una dada esborres i escrius). Diu normalment es poden garantir 100.000 cops... (he vist a altres llocs que parlen que la vida mitja és entre 1 i 5 milions d'escriptures)

---

### Post by Miquel Ubuntero on 2009-04-07
Hola companys.
Moltes gracies per les vostres explicacions.
En qualsevol cas penso que si és pot escriure més de 100.000. cops, probablement molt abans ja canviaré de clau usb.
Salut!

---

### Post by guillemsola on 2009-04-09
Hola,

jo també afegiria que si fas servir un pendrive com a disc dur a fstab el muntis amb l'opció NOATIME ja que així redueix una mica les escriptures que es fan. A google surten moltes pàgines sobre com, per exemple, posar a la memòria la carpeta d'arxius temporals i coses així per estalviar escriptures al disc. 

Jo personalment tinc un debian en un pendrive i el vaig formatejar amb ext2 per estalviar el journaling encara que no se si pel que costa un pendrive val  la pena filar molt prim.

salut

---

