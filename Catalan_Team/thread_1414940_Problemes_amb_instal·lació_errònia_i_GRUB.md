---
title: "Problemes amb instal·lació errònia i GRUB"
date: 2010-02-24
forum: Catalan Team
---

### Post by mrc2407 on 2010-02-24
Aviam com explico això...

Tinc un ACER ASpire 5738z amb Windows Vista, i he volgut instal·lar una distribució d'Ubuntu pròpia feta amb Remastersys ([http://art.ubuntuforums.org/showthread.php?t=1414001](http://art.ubuntuforums.org/showthread.php?t=1414001)). La instal·lació ha anat bé, però no m'he adonat que tenia un disc dur extern USB enxufat al portàtil i Ubutnu s'ha instal·lat allà. Quan me n'he adonat, he desmuntat  des d'un altre ordinador la partició del disc dur extern on havia instal·lat Ubuntu, però ara no puc engegar l'ordinador Acer que us comento perquè em dóna un error del GRUB:

Grub loading.
error: no such disk
grub restore>

Puc carregar Ubuntu 9.10 (distribució oficial) amb LiveCD, però no sé si així puc arreglar alguna cosa... Pel que jo entenc, el disc dur intern del portàtil Acer està bé, només que hi ha el GRUB instal·lat i que intenta carregar-se però no troba el lloc correcte.

Què em recomaneu que faci? Torno a instal·lar Ubuntu en la partició aquesta del disc dur extern? Servirà d'alguna cosa? O hi ha alguna altra manera de desinstal·lar el GRUB? Puc fer alguna cosa des del LiveCD? Tampoc tinc el disc d'instal·lació de Windows Vista perquè venia instal·lat directament quan vaig comprar l'ordinador.

---

### Post by wgarcia on 2010-02-24
Hauràs de reinstal·lar el grub al MRB del disc des del qual vols iniciar l'ordinador. Quina versió de grub tens, la 1 o la 2?

---

### Post by mrc2407 on 2010-02-24
Doncs no ho sé, però la meva distribució estava basada en Ubuntu 9.10 i la vaig fer amb Remastersys, així que suposo que hi ha la que ve per defecte... De tota manera, em sembla recordar haver vist algo semblant a GRUB 1.94 beta4, és possible?

---

### Post by mrc2407 on 2010-02-24
Ja està solucionat. Al final ho he aconseguit amb el Super Grub Disk ([http://super-grub-disk.softonic.com/linux](http://super-grub-disk.softonic.com/linux)), que funciona a la perfecció i arregla tant problemes del GRUB com del gestor d'arrencada del windows. Només cal anar seguint els passos després de grabar la ISO en un cd.

Gràcies a tots :)

---

### Post by wgarcia on 2010-02-25
Me n'alegro. Doncs si havies vist "1.94" tens Grub 2, que és la nova versió de Grub que s'ha començat a instal·lar a partir de la Karmic.

---

