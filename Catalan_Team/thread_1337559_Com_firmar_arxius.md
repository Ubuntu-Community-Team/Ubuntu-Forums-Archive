---
title: "Com firmar arxius"
date: 2009-11-25
forum: Catalan Team
---

### Post by tanreb20 on 2009-11-25
Hola!

Jo m'en recordo que fins no fa gaire a l'ubuntu (als de la UAB puc) podia firmar arxius (signar) de tal manera que per obrir-lo s'havia de posar una contrasenya.

Ara no trobo aquesta opció, m'agradaria firmar determinats arxius, per protegir-los. Crec que també esta el directori HOME protegit, aixì ho vaig marcar a la instal·lació....

Com podria tornar a activar aquesta opció? Sabeu de que parlo?

---

### Post by CarlesOriol on 2009-11-26
En gnome.

Instal.la seahorse i seahorse-pluggin.

Al seahorse crees una clau.

(Reinicies sessio' d'usuari o el nautilus)

I ara tens un menu contextual als arxius per XIFRAR o signar. (Atencio' la signatura és la creacio' d'un arxiu adjunt amb informacio' per garantir que l'arxiu original és teu)

Recorda de fer copies de seguretat de les claus privades que si les perds ja et pots despedir dels arxius.

---

### Post by orestesmas on 2009-11-26
En qualsevol.

Obres un terminal, et poses al directori on hi ha el fitxer a xifrar (per comoditat) i executes:
```

gpg -b nom_del_fitxer

```

Això, com diu el Carles, crea una signatura separada del fitxer (amb extensió .sig). Afegint l'opció "-a" al gpg aconsegueixes que la signatura sigui en text clar (amb extensió .gpg), en lloc d'una signatura binària. Això és útil per signar correus electrònics.

Si vols una signatura adossada al final del fitxer, has de canviar l'opció "-b" per "-s". Però compte! un fitxer binari "per se" normalment no tolerarà que li afegeixis res al darrere (però això varia segons el tipus de fitxer i l'aplicació que el tracta). L'aspecte del fitxer creat és el mateix que si fos xifrat. De fet, em sembla que està xifrat i signat, o sia que per verificar la signatura has de fer:
```

gpg --verify fitxer.gpg

```
i per obtenir el fitxer original has de fer com si desxifressis:
```

gpg -d fitxer.gpg

```

Si tens un fitxer de text pla i el vols "envoltar" d'una signatura també en text clar, llavors l'opció és "--clearsign"

Resumint:

gpg -b fitxer
   -> Crea una signatura binària en un fitxer apart amb extensió .sig.

gpg -b -a fitxer
   -> Crea una signatura en text clar en un fitxer apart amb extensió .asc

gpg -s fitxer
   -> Xifra i signa el fitxer original, i retorna el resultat en un fitxer binari amb extensió .gpg

gpg -s -a fitxer
   -> Xifra i signa el fitxer original, i retorna el resultat en un fitxer de text clar amb extensió .asc

gpg --clearsign
   -> (Útil per a fitxers originals de text clar) Envolta el fitxer original d'una signatura en text clar i li dóna extensió .asc

Potser tot plegat és una mica rotllo, però també és interessant. T'animo a fer les provatures pertinents.

---

### Post by CarlesOriol on 2009-11-27
Forestes (la resta :-) és una pregunta no un flame)

Despres de llegir la teva resposta m'ha entrat curiositat... i el kgpg?

He fet una prova, i com a equivalent al seahorse de gtk em sembla prou bo i ràpid, però en kde tenim dreceres equivalents al dolphin o konqueor per signar / xifrar arxius?

---

### Post by orestesmas on 2009-11-28
Doncs mira, fa unes versions del KDE això encara ho estaven passant al KDE4, però ara ho acabo de tornar a provar amb el KDE 4.3.3 (repositoris PPA de Kubuntu) i si, tant al Dolphin com al Konqueror hi ha un menú contextual amb les opcions pertinents. De fet, en teoria, des de qualsevol programa de KDE ha de funcionar igual, perquè aquesta funcionalitat està programada separadament de qualsevol programa.

Com a mostra una captura: A la imatge es mostra un fitxer xifrat i el menú contextual que es desplega en clicar el botó dret del ratolí.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=137909&stc=1&d=1259432104[/IMG]

Pots veure que a la carpeta hi ha un fitxer xifrat. El menú contextual ofereix l'opció "Obre amb KGpg" (la frase no és massa escaient) que el que fa és desxifrar-lo i desar-lo desxifrat a la mateixa carpeta. L'opció de xifrar-lo en aquest cas no és útil, però és la que escolliríem en cas de voler xifrar un fitxer qualsevol (ens pregunta per la clau o claus a utilitzar per xifrar, que seran els qui podran desxifrar-lo després). Finalment, l'opció "Mostra el fitxer desencriptat" el mostra en una finestra apart.

---

