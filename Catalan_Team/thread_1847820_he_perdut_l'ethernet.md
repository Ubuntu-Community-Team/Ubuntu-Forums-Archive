---
title: "he perdut l'ethernet"
date: 2011-09-21
forum: Catalan Team
---

### Post by gunyoles on 2011-09-21
hola a tothom, ahir al apagar l'ordinador hem va sortir un missatge que no vaig tenir temps de llegir i avui hem trobo que no va l'ethernet. He mirat la configuració i es veu tot be, he canviat el cable i res. en canvi si que connecta via wifi o via umts. Algú li ve al cap alguna possible solució. gracies
](*,)

---

### Post by wgarcia on 2011-09-21
A vegades m'ha passat que he canviat alguna cosa en la configuración del network-manager i em deixava sense ethernet. La manera que ho he arreglat, no sé si et funcionarà, és editar el fitxer /etc/NetworkManager/NetworkManager.conf i canviar la línia que posa Managed=false a Managed=true. Editar amb 
sudo gedit /etc/NetworkManager/NetworkManager.conf 

Algú altre potser et recomani instal·lar "wicd" i desinstal·lar network-manager, però jo sempre ho he pogut solucionar tot amb network-manager i és el programa per defecte en pràcticament totes les distribujcions de Linux.

Ara és estrany que de sobte deixi de funcionar si no has tocat res.

---

