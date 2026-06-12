---
title: "Teclat personalitzat"
date: 2009-01-12
forum: Catalan Team
---

### Post by tanreb20 on 2009-01-12
Hola companys.

Tinc un Toshiba A210 i evidentment és un d'aquells amb botonets personalitzables(internet, media, play/pause, stop, etc...)

M'agradaria saber si hi ha alguna manera de configurar les teclas, ja que només funciona la de internet, pero no les de musica.

Algu sap algun programa o algo?

Gráaaaaaaacies!

---

### Post by RainCT on 2009-01-14
Sistema -> Preferències -> Dreceres de teclat.

Aix... Mira que n'és de difícil! (Bé, millor espero a que em diguis que et funciona :P).

---

### Post by tanreb20 on 2009-01-14
Ehmm.. si si aixo u he provat.

Em detecta casi totes les teclas (menys la de media) pero després quan intento fer-le ssevrir en algun programa no van!

---

### Post by lluisanunez on 2009-01-15
Quan no existien al menú les dreceres de teclat, jo configurava les tecles amb aquesta ordre al terminal i l'editor de configuració del Gnome. Potser et funciona:
```
xev | grep keycode --line-buffered
```Et sortirà un quadret gràfic, aleshores si pitges la tecla que vols configurar, el terminal et retornarà una cosa com:
```
 
state 0x0, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
state 0x40, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,

```
en aquest cas era la tecla "Windows" i el valor que ens interessava saber és Super_L
Aleshores obres l'editor de configuració gconf-editor, i vas a apps > metacity > global_keybindings
Selecciones un "run command #" que estigui lliure i en el camp "disabled" fent doble clic li entres el valor de la tecla que vols configurar
Ara al gconf-editor vas a apps > metacity > keybinding commands i selecciones el command # que has activat abans, i li entres el comandament de terminal de l'aplicació que vols arrencar amb la tecla.

---

