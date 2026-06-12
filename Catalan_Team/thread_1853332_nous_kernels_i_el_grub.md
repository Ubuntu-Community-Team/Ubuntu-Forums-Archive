---
title: "nous kernels i el grub"
date: 2011-10-02
forum: Catalan Team
---

### Post by venusfenix on 2011-10-02
buenas,
se que la pregunta pot ser obvia, pero no per mi, des de la versio de kernel 2.6.32-26 que no instal·la cap altre kernel, hi veig que el sinaptic n'hi han de nous fins al 2.6.32-34 pero no hi surten en el grub. que tinc que fer?

gracies,

---

### Post by Miquel Ubuntero on 2011-10-02
Pot ser la resposta també és obvia. El gestor d'actualitzacions hauria d'insta&#320;lar-te tots els kernels, llevat tu li diguis el contrari.

---

### Post by venusfenix on 2011-10-02
perdona, no l'he deixat clar, si que s'actualitzen, pero no s'instal.lan, o al menys, no surt al grub, i no ho puc triar enlloc.

gracies,

---

### Post by oriolsbd on 2011-10-03
Mira d'executar el següent:
<code>sudo update-grub /dev/sda</dev>
Si tot i així no t'apareix, és que amb les noves versions no s'instal·la algun dels paquets propis del nucli (a mi m'ha passat algun cop). Obre el Synaptic i mira si hi tens algun paquet pendent d'actualitzar. Al panell inferior esquerre del Synaptic, hi ha un botó que hi posa "Estat". Si hi fas clic, al panell superior esquerre podràs filtrar pels paquets "Actualitzables".

Si no hi veus res, farem una altra cosa. Des del propi Synaptic, mira si tens instal·lats aquests paquets:
linux-headers-2.6.xxxxxxx
linux-headers-2.6.xxxxxxx-generic
linux-image-2.6.xxxxxxx-generic

En aquest cas, "xxxxxx" hauria de ser la darrera versió del nucli que tinguis disponible. Si veus que de la darrera versió del nucli no tens instal·lat algun d'aquests tres paquets, fes-ho.

Salut!

---

### Post by venusfenix on 2011-10-08
he probat la primera opcio i sembla que funciona!

gracies!!

---

