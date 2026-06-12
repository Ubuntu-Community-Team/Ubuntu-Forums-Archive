---
title: "A l'eliminar arxius, no van a la paperera i s'eliminen directament"
date: 2010-08-04
forum: Catalan Team
---

### Post by joaquimrubio on 2010-08-04
Ubuntu 10.04 baixat d'aquesta web d'Ubuntaries i desat en una memòria flash. Instal·lat en un disc dur on només hi ha aquest S.O. La instal·lació va anar com una seda. I tot funciona bé llevat d'algún detall, com ara que a l'eliminar un arxiu no s'emmagatzema a la paperera sino que s'elimina directament.

No és un problema greu per a mi, ja que he creat una nova carpeta i els deso allí fins eliminar-los definitivament, però ignoro si passa a més usuaris. 

També, quan obro la paperera, triga molt temps a acabar de carregar-se.

També, ignoro si té alguna relació, baixant un llibre electrònic per llegir en el Papyre, m'ha quedat enganxat a l'escriptori i no el sé eliminar ni via consola amb el sudo.

---

### Post by kimet on 2010-08-04
La paperera hauria d'estar a /home/usuari/.local/share/trash, pot ser que el que estigui malament sigui la dredera??
 
Per altre part pots provar d'eliminar un archiu i després buscar-lo amb find, p.e.
```
find . -name exemple.txt
```

salut.

---

### Post by joaquimrubio on 2010-08-05
Gràcies Kimet. 

Seguint aquest camí que dius arribo a la carpeta de la paperera i hi ha tot lo que he eliminat a la paperera. Però si accedeixo a la paperera fent clic a la icona de la paperera que hi ha a l'escriptori, després de força estona, s'obre una paperera buida.

També acabo de provar que passa si clico sobre l'ordre de "Buida la paperera",  i lo que succeeix és que s'acompleix l'ordre i la paperera es buida realment, excepte una de les carpetes de la paperera on hi posa "info". Aquesta carpeta, però, també la puc esborrar manualment. 

Aleshores l'únic problema que queda és que al fer clic a la icona de la paperera s'obre una paperera que no mostra el seu contingut. Quelcom realment curiós. No es cap problema, ii menys ara que he aprés com accedir-hi.

Sembla com si el problema s'hagues arreglat, ja que a continuació he fet la prova d'eliminar un arxiu per buscar-lo amb l'ordre find i ara sí que m'apareix a la paperera quan faig doble cilc sobre aquesta icona. 

Per tant, dono el tema per resolt.

Gràcies, Kimet.

---

