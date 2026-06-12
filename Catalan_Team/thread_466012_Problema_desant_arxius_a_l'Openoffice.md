---
title: "Problema desant arxius a l'Openoffice"
date: 2007-06-06
forum: Catalan Team
---

### Post by Cocoguagua on 2007-06-06
Salutacions.

Tenc una Ubuntu 6.06 i resulta que els arxius de l'openoffice es desen, de forma predeterminada, a la carpeta de root. A més, desa els arxius (.odt, .doc...) només amb permisos de root i després no els puc editar com usuari.

A algú li ha succeït alguna cosa similar i en sap la solució?

Gràcies.

---

### Post by jmaspons on 2007-06-06
Com l'executes, des del menú? Pot ser que executis l'openoffice com a root?

---

### Post by Cocoguagua on 2007-06-06
He revisat el menú i l'ordre és com a usuari i no com a root.

---

### Post by papapep on 2007-06-06
I amb quin usuari t'identifiques al inici de la sessió?

---

### Post by Cocoguagua on 2007-06-06
Com usuari.

---

### Post by Ferri on 2007-06-06
La carpeta on deses els documents la pots canviar a Eines -> Opcions -> OpenOffice.org -> Camins. A la part de la dreta tries "Els meus documents" i "Edita".
No sé si amb això deixarà de desar-te els documents com si fossin de root, però.
Suposo que l'OpenOffice que tens és el que ve amb Ubuntu, no? Si no és així potser la culpa és de la manera com l'has instal·lat.
Tant si se t'arregla amb el que he dit, trobo força estrany que l'OpenOffice et pugui desar res com a superusuari amb un compte que se suposa que no té aquests privilegis. Vés a Sistema -> Administració -> Usuaris i Grups. Fes clic a "Gestiona els grups" i mira que no tinguis el teu usuari activat dins del grup de root.

---

### Post by Cocoguagua on 2007-06-06
He revisat els camins i l'usuari i em sembla que ho tenc tot correcte. Aquí podeu veure una captura d'un arxiu .odt de l'escriptori com usuari.

[[IMG]http://img70.imageshack.us/img70/4967/capturamb5.th.png[/IMG]](http://img70.imageshack.us/my.php?image=capturamb5.png)

---

### Post by CarlesOriol on 2007-06-06
Estas usant l'openoffice del l'ubuntu dapper o has instalat alguna versió desde el mateix openoffice o automatix o d'algun repositori de tercers?

La versió que inclou el Dapper té uns quants milers de linies de codis de pedaços i preconfiguracion, les altres (la del mateix upstream oppenoffice) no estan preparades ni corretgides ni adaptades.

---

### Post by Cocoguagua on 2007-06-06
Doncs és l'Openoffice del Dapper. No he instal·lat cap altre versió, ni res d'altres respostioris (a excepció d'alguns diccionaris i la traducció).

---

### Post by Cocoguagua on 2007-06-06
Ja ho he resolt. Finalment era un problema a /usr/lib/openoffice/soffice.bin (això em sembla almenys). Ara ja funciona tot correctament. 

Gràcies pel vostre interès. :p

---

### Post by papapep on 2007-06-06
Si poses quin era el problema i com ho has solucionat si algú altre s'hi troba podrà provar a veure si així també ho arregla 
Sinó només quedarà registrat el problema ;)

---

### Post by papapep on 2007-06-06
.

---

### Post by Cocoguagua on 2007-06-07
Doncs he anat a /usr/lib/openoffice i allà tenia dos arxius: soficce.bin i soffice.bin.bin. He esborrat el primer (soffice.bin) i després he canviat el nom el segon per soficce.bin, enlloc de soffice.bin.bin.

Això si, després l'openoffice es trencava cada cop que el volia tancar. Per arreglar això només s'ha d'esciure el següent a la consola: 

mv ~/.openoffice.org2 ~/Desktop/openoffice.org2

Després tot ha funcionat a la perfecció. ;)

---

### Post by papapep on 2007-06-07
> Doncs he anat a /usr/lib/openoffice i allà tenia dos arxius: soficce.bin i soffice.bin.bin. He esborrat el primer (soffice.bin) i després he canviat el nom el segon per soficce.bin, enlloc de soffice.bin.bin.
I eren iguals? Com sabies quin triar dels dos per esborrar i renanomenar?

> Això si, després l'openoffice es trencava cada cop que el volia tancar. Per arreglar això només s'ha d'esciure el següent a la consola:

mv ~/.openoffice.org2 ~/Desktop/openoffice.org2

O sigui que el que has fet, a la pràctica, és treure la carpeta de configuració del teu directori personal i enviare-lo a l'escriptori, que hauria estat el mateix que esborrar-lo, entenc. Ara el directori openoffice.org2 que tens a l'escriptori ja no et fa cap funció, per tant.

---

### Post by Cocoguagua on 2007-06-07
He trobat un fil a un fòrum en anglès en el que es deia quin dels dos soffice s'havia d'esborrar (ara no record l'URL). S'havia d'eliminar el soffice.bin i renombrar un segon (soffice.bin.bin) amb el nom del primer.

Pel que fa a (mv ~/.openoffice.org2 ~/Desktop/openoffice.org2) doncs supòs que com dius era suficient esborrar la carpeta de configuració a home. De fet un cop que ha funcionat correctament l'Openoffice he esborrat el directori que s'ha creat a l'escriptori.

---

