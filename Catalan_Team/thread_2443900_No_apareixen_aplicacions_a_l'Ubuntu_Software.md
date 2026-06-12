---
title: "No apareixen aplicacions a l'Ubuntu Software"
date: 2020-05-21
forum: Catalan Team
---

### Post by Curial on 2020-05-21
Bon dia, fa uns quants anys que no venia per aquí.):P

Resulta que després d'acutalitzar de la versió 19.10 a la 20.04 d'ubuntu quan obro lUbuntu Software no m'apareixen les opcions que apareixien en les altres versions com la de jocs, eines ofimàtiques, ciencia, etc. Tanmateix a la cerca si que apareixen algunes, no totes fins i tot algunes que sí tinc instal·lades.

Es pot fer res o és que això és així ara?

Us poso una captura de pantalla on es veuen algunes aplicacions, quan selecciono la pestanya d'Instal·lat tampoc surt res.

Salut!

---

### Post by wgarcia on 2020-05-23
Crec que en algun moment del cicle de desenvolupament va passar això que dius, però a la versió final ja estava solucionat. En tot cas pots provar de reinstal·lar el centre de programari, a veure si ho arregla. Per fer això obre una terminal amb Control-Alt-T, i entra el següent:

```
sudo apt install --reinstall gnome-software
```

---

### Post by Curial on 2020-06-03
Moltíssimes gràcies.

Finalment es va solucionar, soposo en alguna actualització, ara ja apareixen.

Salut!


[ATTACH=CONFIG]286089[/ATTACH]

---

