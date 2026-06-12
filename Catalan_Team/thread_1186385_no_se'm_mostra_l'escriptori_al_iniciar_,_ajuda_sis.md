---
title: "no se'm mostra l'escriptori al iniciar , ajuda sisplau!!"
date: 2009-06-13
forum: Catalan Team
---

### Post by raverr on 2009-06-13
Hola !

Utlimament estic treballant amb la versio 8.10 d'ubuntu i resulta que avui al iniciar el meu portatil he tingut la desagradable sorpresa de que l'escriptori, no se perquè, no s'em visualitza com toca.

Veig la pantalla de càrrega d'ubuntu. Veig la pantalla de nvidia. Veig la pantalla de carrega de l'escriptori ( pantalla de color rosa - marronos .. amb el punter del ratoí ).

Llavors accedeixo al "escriptori".. on no apareix res, només veig el punter del ratolí i tot negre. S'em executa el pigdin ( programa que tinc per defecte que s'executi al iniciar ) i el protector de claus ( la finestreta que demana password per accedir a internet) si introdueixo el password pigdin es conecta.

Pero no tinc ni icones, ni barres, alt+f2 no funciona ni tampoc cap shortcut .

No he tocat RES i sempre que començo a habituarme a treballar normalment sota ubuntu em trobo amb algun pal d'aquests finalment esta resultat que estic reinstalant mes vegades ubuntu que windows. . .

Que puc fer ? Estic mig desesperat perque necesito TREBALLAR amb dades que tinc dintre de l'ordinador.

Gràcies :(

editat: He trobat informació , mes aviat poca, diuen que matant el nautillus es soluciona alguna cosa ( no del tot ) que es un bug o algo , pero no puc fer-ho donat que no tinc accés al terminal :(

---

### Post by SiscoGarcia on 2009-06-14
No sé si et servirà perquè pel que dius sí que et carrega les X, però podries provar a obrir-te una consola amb "Ctrl+Alt+F1" i escriure-hi "startx" a veure si així t'arranca les X (no recordo si s'havia de fer com a administrador -sudo-). Per provar-ho no perds res (si no et funciona pots tornar a l'escriptori amb "Ctrl+Alt+F7").

---

### Post by PatrickVogeli on 2009-06-15
si dius que vols provar matant la consola.. ctrl+alt+f1, posa el teu usuari i la contrasenya i despres fes un killall nautilus

salut

---

### Post by akyra on 2009-06-15
Si necessites treure les dades de l'ordinador per poder guardar-les, pots fer-ho des del grub, i iniciar en mode texte.

A mi m'estava passant que depen com quan mostrava l'escriptori m'apareixien barres verticals i havia de desenxufar a la brava amb el botó de engegar de l'ordinador. Com a dada curiosa es que em demanava la clau de la xarxa wifi.

No sé si ho fas o no amb wifi, pèrò pots provar a engegar-lo amb cable de xarxa?, que no tinguessis algun problema amb el network-manager.

Adeu

---

### Post by raverr on 2009-06-23
gracies, finalment vaig reinstalar i fora .. :(

---

