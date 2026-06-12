---
title: "&quot;Desmuntar volum&quot; al menu contextual de gnome"
date: 2011-06-03
forum: Catalan Team
---

### Post by Pablitus on 2011-06-03
Hola,

Algú sap o se li acut alguna manera de canviar o editar les opcions que surten en el menú contextual de gnome.

Voldria canviar l'opció "Treu la unitat de forma segura" que surt a l'escriptori per alguns dispositius per "Desmunta el volum".

He provat de crear una nova acció amb el "nautilus-actions" però no me n'he sortit. També he provat de cercar pel els fitxers fitxers de configuració per aquestes opcions i tampoc, no sé massa bé ni que hauria de buscar...

Gràcies!

---

### Post by wgarcia on 2011-06-03
No es massa fàcil, es fa amb un programa que es diu "nautilus-actions". 

sudo apt-get install nautilus-actions

No sé massa bé com va perquè ho vaig fer ja fa molt de temps (ni tan sols a Ubuntu, ho vaig fer a Fedora i ja no tinc accés a aquella instal·lació). 

Obre el programa un cop instal·lat i aquí pots crear "Nova acció de Nautilus". Per afegir una entrada al menú contextual a un element s'ha d'escollir "Selecció" ("Localització" és pel menú contextual clicant sobre l'escriptori). Veuràs una sèrie de pestanyes, una d'elles per entrar la comanda que vols executar amb la teva entrada de menú, i també li podràs posar el títol "Desmuntar...". 

Ja ens explicaràs si ho has pogut fer i com ho has fet exactament. No sé si podràs eliminar l'altra entrada però, això és per afegir la nova.

---

