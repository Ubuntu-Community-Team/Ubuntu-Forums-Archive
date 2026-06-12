---
title: "Madwifi falla"
date: 2009-08-28
forum: Catalan Team
---

### Post by rottenroger on 2009-08-28
Bones!!!

M'he registrat finalment a aquest forum al no trobar sol.lució a un problema recurrent que ja fa temps que tinc...
El Mad wifi.

L'he instal.lat ja diverses vegades durant la meva vida ubuntaire, però misteriosament em va desapareixent.... un dia, de cop i volta, em desapareix el gestor de xarxes sense fil...
m'ha passat amb el intrepid ibex i amb el jaunty jackalope....
No ho entenc.... l'instal.lo, funciona correctament i de cop i volta un dia desapareix.

Crec el tema va relacionat amb les actualitzacions, i sospito que més concretament quan se m'actualitza el kernel.... però com que sóc novell en linux i encara no se ben be que em pesco he hagut de recorrer a descriure aqui el meu problema....

A que es degut? Algú ha tingut aquest problema abans?

Salutacions gnurdials a tothom! :)

---

### Post by guillemsola on 2009-08-28
Hola,

pot ser que quant instal·les el madwifi fas un configure, make, make-install?

Ho dic perquè aleshores el que fas és compilar un driver com a modul per a la versió de kernel que tens instal·lat a l'ordinador.

Aleshores quant tens una actualització del kernel aquest no ve amb el modul per al wifi compilat per tu i per tant cal tornar-lo a compilar un altre cop per la nova versió de kernel.

Si el driver que fas servir no està incorporat a la branca del kernel que fas servir "de sèrie" em temo que hauràs de compilar-lo cada vegada que actualitzis el kernel.

salutacions

---

### Post by rottenroger on 2009-08-28
doncs si, l'has clavao!
su do make install...

i doncs com ho faig ara??

gràcies per la resposta!!!! no sabia una cosa anés lligada amb l'altra!

---

### Post by guillemsola on 2009-08-28
> i doncs com ho faig ara??

Doncs abans de permetre un update de kernel assegurat de tenir ganes de compilar de nou.

O bé busca una versió d'ubuntu més nova que inclogui suport per a la teva tarja wifi "de sèrie". En compte que potser no existeix encara.

salut!

---

### Post by papapep on 2009-08-28
Jo diria, sense ser un gran entès en el tema, que amb el controlador ath5k que amb la 9.04 crec que ja ve amb el nucli (fins la 8.10 s'havia d'instal·lar amb el paquet linux-backports-modules-intrepid),t'hauria de funcionar i no et caldria compilar.

Per poder saber si vaig ben orientat, o no, caldria que enganxessis el resultat d'executar:

```
lspci
```

a un terminal.


*Referències:*
* [https://help.ubuntu.com/communi*ty/WifiDocs/Driver/Madwifi#Ubuntu%208.10%20(Intrepid](https://help.ubuntu.com/communi*ty/WifiDocs/Driver/Madwifi#Ubuntu%208.10%20(Intrepid)
* [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

