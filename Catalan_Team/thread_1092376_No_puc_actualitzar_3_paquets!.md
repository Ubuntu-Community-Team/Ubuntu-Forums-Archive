---
title: "No puc actualitzar 3 paquets!"
date: 2009-03-10
forum: Catalan Team
---

### Post by tanreb20 on 2009-03-10
Bon dia! Fa uns dies que estic tenint problemes per actualitzar el sistema(linux mint - ubuntu 8.19)

Quan em recomaana alguna actualització em surten 3 paquets que no puc seleccionar. Com es veu a la imatge.

He intentat fer uns updates i upgrades, treure els paquets trencats etc...

Fa uns dies vaig toquetejar el kernel i en vaig instalar un que no em va funcionar, el vaig desinstalar i esborrar els arxius del kernel. Pt tenir alguna cosa a veure?

[[IMG]http://img142.imageshack.us/img142/1130/capturaj.th.png[/IMG]](http://img142.imageshack.us/my.php?image=capturaj.png)

[IMG]http://img142.imageshack.us/img142/967/screenshot01.png[/IMG]

---

### Post by oriolsbd on 2009-03-10
Prova de mirar les dependències que tenen. Potser és dels paquets que has borrat.

Per a fer-ho, obre el Synaptic. Busca algun dels tres paquets i, fent clic amb el botó dret, mira'n les propietats. A la pestanya "Dependències" les podràs trobar.

Salut!

---

### Post by tanreb20 on 2009-03-10
Ho he fet i he instalat el que me sugeria pero no va.

Em surt aixo a synaptic:

[[IMG]http://img12.imageshack.us/img12/4050/capturat.th.png[/IMG]](http://img12.imageshack.us/my.php?image=capturat.png)

I si intento marcar-la per actualitzar

```
g++:
  Depén: cpp (>=4:4.3.2-2ubuntu1) però s'instal·larà 4:4.3.1-1ubuntu2
  Depén: gcc (>=4:4.3.2-2ubuntu1) però s'instal·larà 4:4.3.1-1ubuntu2

```

---

### Post by torracastanyes on 2009-03-11
Em penso que aquests paquets són del compilador que vas utilitzar per instalar el kernel aquell. Jo els eliminaría.
Mira també si per baixar-te el kernel vas activar algún repositori especial que et doni problemes amb les versions.

---

