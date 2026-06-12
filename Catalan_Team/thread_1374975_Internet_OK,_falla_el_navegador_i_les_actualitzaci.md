---
title: "Internet OK, falla el navegador i les actualitzacions"
date: 2010-01-07
forum: Catalan Team
---

### Post by Pijus on 2010-01-07
Ja fa una setmana que he instal.lat el 9,10 Karmic Koala, la torre és un IBM Thinkpad de fa 6 o 7 anys...Pentium4 i 500Mb de RAM, que amb el 8.04 anava la mar de be!
Amb el 9.10 instal.lat, no consegueixo que funcioni ni el Firefox ni les actualitzacions... si que hi ha connexió a internet operativa perquè el Empathy s'em connecta be. Quan intento actualitzar el llenguatge, em diu que 'No s'ha pogut obtenir http:....' amb totes les direccions que surten, em dona el mateix error.

Entenc que no cal reconfigurar la connexió perquè funciona, he buscat al manual de Ubuntu (en anglés) i dona instruccions per reconfigurar-la per a adreces estátiques, i si ho faig, llavors no hem funciona res (ni el Empathy).

Buscant pel google he trobat diferents problemes, que sembla que es sol·lucionaven instal.lan un nou gestor de xarxes (wicd)... però com el empathy funciona, entenc que no caldria. He provat amb l'ordre 'sudo pppoeconf', i deprés del test que fa, em diu:
"...the Acces Concentrator of your provider did not respond. Please check your network and modem cables (ja ho havia fet, fins i tot he canviat el cable... i tot igual) Another reason for the scan failure may also be another running pppoe process which controls the modem."

Tinc un portàtil amb el Bill Finestres funcionant, des de on envio aquest missatge, però si l'apago tampoc hi ha manera...

Si algú em dona més pistes, us ho agrairé eternament (al menys, fins la propera actualització).

Salutacions i gràcies per endavant, de part d'un novell ubuntaire.

Pijus.

---

### Post by CarlesOriol on 2010-01-07
No tens ben configurat al router (o a la conexió) el servidor de DNS. (el que tradueix les noms d'adreces tipus [www.elquesigui.cat](www.elquesigui.cat) amb adreces IP 23.45.34.23 (exemple))

Prova de configurar un public com el 8.8.8.8 de google.

---

