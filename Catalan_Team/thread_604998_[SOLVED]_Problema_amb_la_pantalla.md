---
title: "[SOLVED] Problema amb la pantalla"
date: 2007-11-06
forum: Catalan Team
---

### Post by carlesbm on 2007-11-06
Hola Ubuntaires.

   Tinc un problema amb el meu ubuntu, he intentat de cambiar la resolució de la pantalla que inicialment era 1024x768 per una de superior ja que m'he comprat un monitor LCD de LG i volia mirar de ajustar tot el que es pugués. Però resulta que he posat una resolucio que no funciona i ara quan es carrega la imatge del escriptori hem surt deformada i no puc obrir els menus , doncs no ser on hi ha el punte.

   La meva pregunta es; Hi ha alguna forma de poder entrar i restaurar la configuració original? 

Moltes gracies

---

### Post by papapep on 2007-11-06
Fes a un terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

i configura una resolució que sàpigues que et funcionarà.

---

### Post by carlesbm on 2007-11-06
Gracies Josep

  M'ha funcionat perfectament, i ara molt millor encara doncs ara he pogut ajustar la resolucio al valor de treballa del monitor.

---

