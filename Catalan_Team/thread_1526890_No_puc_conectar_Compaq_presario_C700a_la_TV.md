---
title: "No puc conectar Compaq presario C700a la TV"
date: 2010-07-08
forum: Catalan Team
---

### Post by moringas on 2010-07-08
Hola tinc un portatil Compaq Presario C700. Anava amb Vista i m'acabo de instal·lar l' Ubuntu 10.04. 

El problema és que volia conectar el portatil a la tv a través d'un cable VGA que va a la tv amb tres cables de video compost  i un jack a RCA pel so. A la TV però, no hi surt res, només la pantalla en blau però de tant en tant surt un tros de l'escriptor, pero malament de colors i de resolució. El cable, en principi, esta bé, és nou... Sembla com si em faltes instalar algun driver o algu perquè em reconeixi la sortida VGA.
Em sembla que la targeta grafica que tinc és Mobile GM965/GL960 Integrated graphics controller.

Si algú sap com ho he de fer... Gràcies

---

### Post by wgarcia on 2010-07-09
La teva targeta gràfica és una Intel integrada. És possible que el problema sigui amb els nous mòduls gràfics integrats als últims nuclis que fa servir l'ubuntu lucid. Per provar si és això pots fer el següent. Reinicia l'ordinador, i quan surt la pantalla "grub" per escollir l'arrencada prem la tecla "e". 

Això t'obrirà un editor senzill on veuràs una sèrie de línies. Busca la que comença amb "linux" (possiblement s'estengui per més d'una línia), i hauria d'acabar amb "quiet splash". Posa't al final d'aquesta línia i escriu "nomodeset". Per tant s'hauria de veure al final com "quiet splash nomodeset".

Prem "esc" i arrenca l'ubuntu com habitualment. 

Això anularà (per una sola vegada de moment) alguns dels mòduls nous del nucli, prova si ara pots connectar la TV. 

Si funcionés es podrà posar aquest canvi de forma permanent, canviant alguns arxius del grub, o almenys fins que no arreglin aquests mòduls que de moment aquestes targetes gràfiques  Intel no poden fer servir.

---

