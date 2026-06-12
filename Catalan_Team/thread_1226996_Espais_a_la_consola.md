---
title: "Espais a la consola"
date: 2009-07-30
forum: Catalan Team
---

### Post by pauelmaco on 2009-07-30
Hola

Avui m'he preguntat com es deu poder fer una cosa, que a priori sembla molt tonta, però que en dos anys de fer servir linux mai m'havia pregunat ni habia necessitat. 

Suposem que estem a la consola i tenim una carpeta que es diu: "Super Ubuntu" (per posar un nom, no us penseu que tinc carpetes així :P). La comanda per entrar-hi seria "cd", però no puc pas posar "cd Super Ubuntu" perquè intentaria entrar a la carpeta Super i no la trobaria. per això, hi ha albun símbol que signifiqui un espai per a la consola?

Merci!

---

### Post by gmunioz on 2009-07-30
Hola pau...:

" "

cd "Super Ubuntu"

---

### Post by PatrickVogeli on 2009-07-30
una altra manera: cd Super\ Ubuntu

salut

---

### Post by papapep on 2009-07-30
Tots els caràcters "no normals", s'han "d'escapar" (traducció literal i barroera de "scape"). Tal i com ha comentat en Patrick, posant davant l'espai, que per a l'ordinador també és un caràcter com qualsevol altre encara que no el veiem, una contrabarra "\" el sistema accepta l'espai. Això, l'escapament, es pot aplicar a molts altres caràcters "estranys" en diverses situacions, no només en aquest.

Salut.

---

### Post by pauelmaco on 2009-07-30
Moltes Gràcies! M'heu tret el dubte de sobre :D

---

### Post by quitus on 2009-07-30
Hi ha una eina molt útil, per entrar en una carpeta posem les primeres lletres del nom de la carpeta i premem el tabulador, apareix la resta del nom tot solet.


salut

---

### Post by iSoc on 2009-08-21
Gracies molt útil em vaig tornar boig per poder donar permisos per consola a un script que es deia així Send To i posava això a la consola chmod +x Send To i sempre em deia arxiu no trobat. I e provat fent chmod +x Send\ To i a funcionat perfectament. Lo del tabuladoe no ma funcionat si el nom esta partit Send To nomes em treia Send, un salut i gracies.

---

