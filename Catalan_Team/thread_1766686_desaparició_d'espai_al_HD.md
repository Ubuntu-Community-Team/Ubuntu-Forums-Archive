---
title: "desaparició d'espai al HD"
date: 2011-05-24
forum: Catalan Team
---

### Post by jinglada on 2011-05-24
Tenia entre 15 i 20 GB lliures i tot d'una m'he quedat sense espai. 

És pot saber quins fitxers s'han creat últimament per a intentar esbrinar que ha passat?

Gràcies a la bestreta.

---

### Post by wgarcia on 2011-05-25
Si obres una terminal, i entres:

du > fitxers.txt

Et crearà un fitxer anomenat "fitxers.txt" i posarà una llista de tot el teu "home" amb els fitxers que hi ha i el seu tamany. Potser aquí pots esbrinar si hi ha fitxers grans que pots eliminar. 

També pots mirar el directori /tmp, però aquest directori es neteja en cada arrencada i si ha fitxers grans aquí s'haurien d'esborrar.

---

### Post by jinglada on 2011-05-25
Moltes gràcies wgarcia!

He fet servir "du -a --time -S > fitxers.txt". Tanmateix no hi tinc cap fitxer gran amb data d'ahir.

---

