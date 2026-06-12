---
title: "impressora en xarxa"
date: 2007-04-12
forum: Catalan Team
---

### Post by montse on 2007-04-12
Hola,

estic en xarxa amb un pc que duu Windows i que té una impressora (Epson Stylus) connectada. Des de l'Ubuntu puc enviar coses a imprimir, però no em fa cas de les opcions d'impressió (color i qualitat). I en una ocasió va imprimir un full tot en negre (però no puc reproduir les circumstàncies particulars).
Algun suggeriment?

---

### Post by basdala on 2007-04-16
Aquestes coses acostumen a ser un problema bé del Samba bé del servei d'impressió. A més a més, les configuracions de color només s'apliquen quan tanques i tornes a obrir el diàleg de propietats -a mi m'ho fa així... també m'hi vaig tornar imbècil per configurar una làser meva.

El millor que pots fer és pujar a Feisty -ara que ja casi la treuen- i, si continua fallant, compilar el CUPS tu mateixa des dels sources que distribueixen a la web -a mi això em va solucionar tots els problemes amb una Brother HL-1430.

---

### Post by CarlesOriol on 2007-04-16
Quin model?

---

### Post by montse on 2007-04-16
Epson Stylus Color 400.

Això de compilar els fonts és una mica massa advanced per a mi...

---

### Post by eselma on 2007-04-17
> **basdala said:**
>  El millor que pots fer és pujar a Feisty -ara que ja casi la treuen- i, si continua fallant, compilar el CUPS tu mateixa des dels sources que distribueixen a la web -a mi això em va solucionar tots els problemes amb una Brother HL-1430.

Ep! la meva dona té una làser HL-1430, que aparentment és una impressora del tipus GDI, i li ha anat perfectament amb els controladors CUPS que duia la Mandrake 2005, i d'ençà de llavors, amb Samba i NFS (+Kubuntu dapper o Edgy)  hi puc imprimir (em sembla que amb el mateix controlador de la HL-1250). No vaig haver de compilar res. Compilar CUPS dins d'una distro (sense començar de zero) en la meva experiència equival a problemes.

---

