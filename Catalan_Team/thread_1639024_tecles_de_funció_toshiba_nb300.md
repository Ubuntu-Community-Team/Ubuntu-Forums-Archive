---
title: "tecles de funció toshiba nb300"
date: 2010-12-06
forum: Catalan Team
---

### Post by samarcanda on 2010-12-06
Hola, 
Despres d'instal.lar kubuntu al meu netbook, només hi ha un petit  problema amb les tecles de funcio FN.
i es que no les reconeix en absolut, el que mes m'interessa es poder baixar la intensitat de la lluentorn de la pantalla per estalviar energia i allargar una mica la duració de la bateria....
La verirtat, he buscat per internet i no trobo cap solució.


Moltes gácies

---

### Post by kimet on 2010-12-06
Si té una bios phoenix has d'instal.lar el mòdul omnibook.
Mira per aquí:
[http://ubuntuforums.org/archive/index.php/t-316358.html](http://ubuntuforums.org/archive/index.php/t-316358.html)
Una vegada instal.lat l'has de carregar amb els paràmetres que corresponguin:
```
sudo modprobe omnibook ectype=15 userset=1
``` etc.
(aquest ectype es variable i depén del model d'ordinador, pots anar provant del 10 al 15)
I comprovar que s'ha creat el fitxer /proc/acpi/omnibook/lcd o /proc/omnibook/lcd i si canviat el valor "n" canvia la intensitat.
```
echo n > /proc/omnibook/lcd 
```
Després crear un script que asociat a una combinació de tecles pugi o baixi la intensitat.(A mí les tecles fn no m'han funcionat mai).

Salut.

pd. em sembla que n ha de ser del 1 al 7.

---

### Post by samarcanda on 2010-12-08
Arreglat, despres de molta feina he conseguit carregar el modul i la intensitat de la pantalla ha canviat de cop i
la aplicació de kde per controlar la bateria i la lluentor ja funciona. De moment amb aixó em va be, encara que les tecles fn segueixen sense fer res.

Moltes gracies.

---

