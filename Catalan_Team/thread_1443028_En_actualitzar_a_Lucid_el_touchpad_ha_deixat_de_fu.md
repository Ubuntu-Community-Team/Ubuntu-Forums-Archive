---
title: "En actualitzar a Lucid el touchpad ha deixat de funcionar"
date: 2010-03-30
forum: Catalan Team
---

### Post by Aljullu on 2010-03-30
Hola, fa un parell de dies vaig actualitzar el meu Acer Aspire One a la versió beta de l'Ubuntu Lucid (10.04).

Vaig intentar actualitzar un cop però em vaig quedar sense connexió a Internet de manera que vaig apagar a mitja actualització (encara estava a la fase en què es baixaven els fitxers).

A partir de llavors el touchpad va deixar de funcionar: ni el botó de l'esquerra, ni el de la dreta, ni moure el ratolí.

Després, utilitzant un ratolí USB, vaig actualitzar confiant que això solucionaria l'error. Però no.

Porto tota la tarda buscant la solució per Internet i no me'n surto. He vist que molta gent feia referència a la combinació de tecles Fn + F7, que permet activar o apagar el touchpad. Però ho he provat diverses vegades i no ha funcionat.

També m'he mirat el wiki de l'Ubuntu:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
on diu que s'ha d'instal·lar el paquet xserver-xorg-input-all. Ho he provat i tampoc m'ha sol·lucionat el problema.

També he trobat un fòrum
[http://ubuntuforums.org/showthread.php?t=928052&page=2](http://ubuntuforums.org/showthread.php?t=928052&page=2)
on es deia que s'havien d'inserir unes línies al fitxer /etc/X11/xorg.conf. Aquest fitxer jo no el tinc, però tot i crear-lo i afegir-hi les línies, el problema no s'ha solucionat.

També he trobat un fòrum (no recordo quin) on recomenaven escriure les dues següents línies al terminal:
sudo modprobe -r psmouse
sudo modprobe psmouse
ho he provat però no m'ha servit de res.

Ja no sé què més pot ser. Algú en té una idea? Pot ser problema del nucli que no em reconegui el maquinari?

Moltes gràcies!

---

### Post by oriolsbd on 2010-03-31
Hola, Aljullu.

Lucid Lynx encara és una versió Beta. És possible que es tracti d'un bug que hauria d'estar arreglat per a la versió final. Pots mirar d'obrir un bug per tal que s'ho mirin.

Salut!

---

### Post by PatrickVogeli on 2010-03-31
ho sento, no se com ajudar-te, sols volia dir:

**que lleig el Lucid Lynx!!!!**

Salut!

---

### Post by wgarcia on 2010-03-31
Hi ha molts informes recent d'errors semblants al Launchpad, i sembla que l'última actualització de xserver-xorg-input-synaptics ho arregla.

---

### Post by Aljullu on 2010-04-01
> **wgarcia said:**
> Hi ha molts informes recent d'errors semblants al Launchpad, i sembla que l'última actualització de xserver-xorg-input-synaptics ho arregla.

Cert, amb la darrera actualització s'ha arreglat.

La veritat és que m'extranyava que en una beta hi hagués un error així. Tot i això, tot va bé si acaba bé!

Gràcies!

---

