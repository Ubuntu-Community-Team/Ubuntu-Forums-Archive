---
title: "Fer fora Ubuntu One"
date: 2012-03-14
forum: Catalan Team
---

### Post by rosa d'abril on 2012-03-14
Hola,
Em vaig obrir un compte a Ubuntu One i sincronitzar alguns arxius. Però ara m'ho he pensat millor i voldria tornar a deixar Ubuntu One inactiu.
Per no emprenyar massa, he tafanejat per Internet i he trobat una pàgina on s'indica com fer-ho.
El problema és que en posar en el terminal les ordres indicades per esborrar les carpetes que usa Ubuntu One, a saber:
  	 	 	 	 	 	    [FONT=Courier New, serif]$ rm –rf ~/.local/share/ubuntuone 
$ rm –rf ~/.cache/ubuntuone 
$ rm –rf ~/.config/ubuntuone 
$ rm –rf ~/Ubuntu\ One[/FONT]
  La resposta ha estat:
rm: no s’ha pogut eliminar «–rf»: El fitxer o directori no existeix
rm: no s’ha pogut eliminar «/home/rosa/.local/share/ubuntuone»: El fitxer o directori no existeix

Algú sabria dir-me com desfer-me de l'Ubuntu One COMPLETAMENT?

---

### Post by 19preguntes on 2012-03-14
Hola,
no domino el terminal, però em sembla que si desactives la sincronització de totes les carpetes l'Ubuntu One ja no t'emprenyarà més. Si a més vols esborrar del núvol els fitxers que ja s'havien sincronitzat, pots fer-ho entrant al teu compte des de one.ubuntu.com, i després imagino que també podràs eliminar el teu compte (però això no ho he provat mai).

Si a més vols desinstal·lar l'Ubuntu One, pots fer-ho des del Synaptic. Si hi marques l'Ubuntu One per desinstal·lar, ell mateix t'indicarà tots els paquets que hi estan relacionats, i quedarà tot net.

Si vols aprendre a fer-ho des del terminal, haurem d'esperar que et respongui algú altre, perquè, com t'he dit, jo no en tinc gaire idea.

Espero que el què et dic et serveixi.

Salut!

---

### Post by wgarcia on 2012-03-15
L'error és que et sobra un guionet a l'ordre, és a dir no és 

```
rm --rf ~/.local/share/ubuntuone /CODE]

sinó

[CODE]rm -rf ~/.local/share/ubuntuone 
```

Confon perquè es veuen quasi igual, sols que el primer és "més llarg", s'uneix sol per mostrar un guionet més llarg.

Però com diu 19preguntes, potser és millor desinstal·lar l'aplicació si no la faràs servir més i inhabilitar el compte (que tampoc sé com es fa). 

Per desinstal·lar completament una aplicació, incloent els fitxers de configuració, l'ordre és:

```
sudo apt-get remove --purge ubuntu-one
```

aquí sí que porta doble guionet (la raó és que hi ha opcions que tenen un alias abreujat, com "r" i "f" al primer cas, i hi ha d'altres que no en tenen, com "purge" en el segon cas; per als abreujats es fa servir un sol guionet, mentre que per als no abreujats es fan servir dos guionets).

---

### Post by rosa d'abril on 2012-03-15
Gràcies a tots dos. M'ha anat molt bé assebentar-me de l'existència del Synaptic (molt útil) i de la conya dels guionets enganyosos. Ubuntu One gone to hell!

---

