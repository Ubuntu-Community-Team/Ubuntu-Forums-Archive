---
title: "AMb Ubuntu 11/04 no va el wifi"
date: 2011-09-29
forum: Catalan Team
---

### Post by Jayhawker on 2011-09-29
Hola. Hi ha cap manera de solucionar el Wifi del 11/04?

El 11/4 el tinc en paral·lel amb el Windows Vista. En Windows, el Wifi no presenta problemes, però sí quan estic a l'Ubuntu. L'Ethernet si que va. I, de fet, el Wifi em diu que funciona, però no. No puc navegar ni descarregar malgrat que em diu que estic dins el Wifi.

Mercès per l'atenció.

---

### Post by wgarcia on 2011-09-29
Potser necessites algun controlador especial per a la teva targeta de wifi. 

Havies pogut connectar amb alguna altra versió d'Ubuntu? O mai no has pogut connectar?

Per veure una mica què està passant pots enganxar en un fitxer el resultat d'entrar en una terminal l'ordre:
```
ifconfig
```

i en un altre fitxer el resultat de 
```
sudo lshw
```

Si aquesta última ordre et diu "comanda no trobada" o alguna cosa així, primer hauràs de fer 
```
sudo apt-get install lshw
```

---

### Post by Jayhawker on 2011-09-30
En prenc nota. Moltes mercès. Ja comentaré com m'ha anat. :D

> **wgarcia said:**
> Potser necessites algun controlador especial per a la teva targeta de wifi. 

Havies pogut connectar amb alguna altra versió d'Ubuntu? O mai no has pogut connectar?

Per veure una mica què està passant pots enganxar en un fitxer el resultat d'entrar en una terminal l'ordre:
```
ifconfig
```

i en un altre fitxer el resultat de 
```
sudo lshw
```

Si aquesta última ordre et diu "comanda no trobada" o alguna cosa així, primer hauràs de fer 
```
sudo apt-get install lshw
```

---

### Post by Jayhawker on 2011-12-14
He instal·lat el darrer Ubuntu, i em passa una cosa curiosa, després de seguir instruccions. El Wifi aparentement sembla captar-me d'altres routers, però curiosament no el meu. Llavors, he optat per instal·lar el meu router en Wifi ocults, i aquí sembla detectar-me'l, fins i tot al capdavall d'un temps em diu que estic connectat, però no és cert, perquè em resulta impossible navegar. 

Mercès per qualsevol suggeriment i per l'atenció prestada. 


> **Jayhawker said:**
> En prenc nota. Moltes mercès. Ja comentaré com m'ha anat. :D

---

