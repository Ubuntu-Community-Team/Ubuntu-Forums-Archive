---
title: "fitxers fantasma (hi son pero no es veuen)"
date: 2009-02-22
forum: Catalan Team
---

### Post by sianeu on 2009-02-22
Estic intentant (altre cop) instal·lar el Mythtv amb un nou manual que he trobat. Abans de instal·lar el programa mythtv he fet una cerca amb "locate" per eliminar qualsevol referencia del programa d'instal·lacions anteriors. He elimitat tots els fitxers trobats mitjançant el nautilus com a superusuari (sudo nautilus).

Fins aquí tot bé. Però abans de donar-ho per fet he tornat a fer la recerca amb locate per assegurar-me que no quedava cap referència al programa. La sorpresa ha estat tornar a veure tots els fitxers que havia eliminat, i més gran encara quan torno a iniciar el nautilus i, aparentment, no hi son. Reiniciar el ordinador tampoc ha cambiat res: pel nutilus no es veuen, però el locate els detecta allà on eren.

Algú sap que passa?

Salut

---

### Post by oriolsbd on 2009-02-22
El "locate" en realitat no busca físicament els fitxers que existeixen en el disc, sinó que ho busca en una base de dades que s'ha d'anar actualitzant. Per això troba els resultats tan ràpid.

Segur que algú altre et podrà dir la comanda exacta per a actualitzar-la, però em sona que es fa de manera automàtica cada cop que es reinicia l'ordinador, de manera que si pares i tornes a engegar, crec que t'hauria de funcionar. Ostres, aquesta última frase m'ha sonat molt a quan utilitzava Windows!!!! :-)

Per cert, per cercar fitxers directament al disc, has d'utilitzar la comanda "find". Per exemple:

find / -name *.txt

Et buscaria tots els fitxers amb extensió txt del teu ordinador (a partir del directori "/").

Salut!

---

### Post by sianeu on 2009-02-22
Reiniciant simplent, no actualitza, ja et dic. Però no sabia lo de la base de dades del locate. Gracies.

Salut

---

### Post by papapep on 2009-02-22
Per actualitzar la base de dades:

```
sudo updatedb
```

---

