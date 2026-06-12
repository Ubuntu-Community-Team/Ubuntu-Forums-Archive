---
title: "grep -r &quot;&quot; ."
date: 2010-05-24
forum: Catalan Team
---

### Post by manelfus on 2010-05-24
Hola algu sap perque serveix aquest comandament ?   [COLOR="Red"]grep -r "" .[/COLOR]
es bastant "matrixero"  semblant al de veure tot el llistat del directori    "ls -R /"

salut   Manel

---

### Post by wgarcia on 2010-05-25
"grep" busca un text dins d'un arxiu, i "-r" és una opció perquè busqui recursivament dins de carpetes. Però tal com ho poses li falta especificar la carpeta de partida i el text a buscar, per exemple si tinguessis una carpeta "Docum" i donessis aquesta instrucció des de la carpeta on està "Docum":

grep "a" -r Docum

et mostraria tots els arxius (no binaris) on es troba el caràcter "a" dins de la carpeta Docum i les seves subcarpetes.

---

