---
title: "Firefox se'm bloqueja"
date: 2012-12-29
forum: Catalan Team
---

### Post by idrox on 2012-12-29
Bon dia, companys!

Tinc un problema amb el firefox i és que cada cop més sovint se'm bloqueja, bloquejant-me també tot l'ordinador.

Em passa quan tinc "moltes" pestanyes obertes (ho poso entre cometes perquè a vegades tenint-ne només 4 o 5 ja em passa) o amb pàgines com tumblr o youtube (sense necessitat de reproduir vídeos, sovint amb la portada també se'm bloqueja). A vegades si m'espero mig minut em surt una finestra de que hi ha un script no suportat, i que si el vull aturar. Llavors, aturant-lo acostuma a tornar a funcionar. Però el que em passa més sovint és que se'm bloqueja del tot l'ordinador i l'he de reiniciar "a lo bèstia", treient la bateria i tornant-la a posar.

Tinc ubuntu 12.04 i Firefox 17.0.1. Alguna possible solució? Gràcies!

---

### Post by wgarcia on 2012-12-30
Segons el que expliques sembla un problema que afecta el sistema gràfic, per això se't bloqueja com dius l'ordinador. Pot ser algun malfuncionament del Firefox o d'algun complement, si en tens d'instal·lats. 

En comptes de reiniciar l'ordinador, hi ha un parell de coses que pots fer o provar. 

1) Potser matant el procés del Firefox et deixa tornar a tenir control de l'ordinador, però com tens bloquejada la interfície gràfica no t'ho deixa fer des de l'escriptori. Per això pots accedir a una consola, matar el procés, i tornar a l'escriptori a veure si s'ha desbloquejat. Per accedir a la consola pots fer CTRL-ALT-F1, on CTRL és la tecla de control, ALT la tecla alt, i F1 la tecla de Funció 1. S'obrirà una consola demanant-te l'usuari i la clau. Un cop oberta, a la línia d'ordres, entrant

```
killall firefox
```

Això tancarà el procés penjat de firefox. Per tornar a la interfície gràfica l'ordre és CTRL-ALT-F7. 

2) En cas que en tornar a la interfície gràfica encara continués penjada, es pot matar la interfície gràfica sense sortir de l'ordinador. Per això es va a la consola com abans, i a la consola s'entra l'ordre següent:

```
sudo service lightdm restart
```

Això et portarà a la pantalla d'inici, si tens configurat passar per ella en arrencar l'ordinador, o directament a l'escriptori en cas que no ho tinguis configurat. 

El desavantatge d'aquest últim procediment és que es tanca tot el que hi havia a l'escriptori, per exemple si estaves editant un document es perdria el que s'havia fet.

---

