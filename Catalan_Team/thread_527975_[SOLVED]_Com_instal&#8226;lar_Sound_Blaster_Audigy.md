---
title: "[SOLVED] Com instal&#8226;lar Sound Blaster Audigy ?"
date: 2007-08-17
forum: Catalan Team
---

### Post by Lluc on 2007-08-17
Hola soc un usuari molt novell, molt molt molt insisteixo!

No tinc ni idea de com instal&#8226;lar la targeta de so! Em podríeu donar un cop de ma, siusplau? :confused:

---

### Post by papapep on 2007-08-17
Benvingut Lluc!!

Prova teclejant això en un terminal:

```
 sudo asoundconf set-default-card Audigy

```

A veure si et funciona.

---

### Post by Lluc on 2007-08-17
No fa res! 

No se q deu ser, pq en la informació del maquinari sur q esta instal·lat i amb els divers que recomana la web oficial de Ubuntu el &#8220;emu10k1&#8221; per la targeta en qüestió...

alguna idea?

moltes gracies!

---

### Post by CarlesOriol on 2007-08-17
Mira que no tinguis activada per bios la targeta de so de la placa base i l'ordinador estigui funcionant per aquesta.

Jo tinc una audigy 2 ZS platinum Pro connectada a un ubuntu studio (tot i que abans l'havia provat amb un Dapper) i no vaig haver de fer res especial per que em funciones.

Vaig tenir algun problema amb la selecció dels ports de midi al rack però era un tema molt concret.

---

### Post by Lluc on 2007-08-17
Si esta desactivada! o he fet per hardware, ja q en windows també em donava errors... i a la bios no apareixia la opció, així q vai fer-ho manualment... 

Gracies!

---

### Post by papapep on 2007-08-17
Això significa que un cop activada per maquinari ja et funciona correctament?

---

### Post by Lluc on 2007-09-08
Ja esta!!!
> 
Ha sido al cliclar al control de volumen, me he ido a la pestaña "conmutadores" y por defecto viene seleccionada la opcion "Audigy Analog/Digital Output jack" pues la he <desmarcado> y, seguidamente problema resuelto la audigy canta que se las pela ^^

---

