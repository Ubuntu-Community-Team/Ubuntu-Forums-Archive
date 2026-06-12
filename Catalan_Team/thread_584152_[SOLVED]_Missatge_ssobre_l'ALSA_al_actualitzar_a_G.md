---
title: "[SOLVED] Missatge ssobre l'ALSA al actualitzar a Gutsy 7.10"
date: 2007-10-20
forum: Catalan Team
---

### Post by friviere01 on 2007-10-20
:) En actualitzar de 7.04 a 7.10 m'ha sortit un missatge amb instruccions per detectar la tarja de so, que feia referència  a l'ALSA.

Malauradament el missatge ha desaparegut abans que el pogués anotar i ara no tinc so. No he aconseguit recuperar el missatge del syslog ni d'enlloc.

Algú li ha passat alguna cosa semblant, o sap de quin missatge es tracta, és a dir, què és el que he de fer, per detectar la tarja de so?:(

---

### Post by CarlesOriol on 2007-10-21
Paco?

Comprova que realment no tinguis so. El gutsy ha canviat (tal com fa el compiz i el beryl) el controlador de volum principal entre  master a pcm. Comprova als mescladors que totes les opcions estiguin activades.

La detecció de la targeta de so hauria de funcionar en qualsevol cas independentment que la tinguessis o no al moment d'insta&#320;lar-ho.

Si no és així digue'ns quina targeta de so tens per veure que podem fer.

---

### Post by friviere01 on 2007-10-21
Precisament el missatge parlava també de PCM. Ara ho recordo!:)
Tots els controls estan activats a Alsamixer, però qualsevol aplicació amb so dóna error:

* Monitor de volum:
"No es pot connectar al servidor de so. Executeu 'esd' a la línia d'ordres"
(Després de fer esd al terminal res no canvia).

* Enregistrador de só:
"Els vostres paràmetres de captura d'àudi són invàlids. Corregiu-los als paràmetres Multimèdia."

PiTiVi::
esdsink.c(263): gsd_esdsink_open(): /bin1/esdsink1: can't open connection to sound server.

---

### Post by CarlesOriol on 2007-10-23
I canviant el esd per l'alsa amb: gstreamer-properties?

---

### Post by friviere01 on 2007-10-23
El tema s'ha resolt en instal·lar les actualitzacions proposades avui. Ja puc escoltar videos i convertir-los amb ffmpeg!

Gràcies  Carles

---

