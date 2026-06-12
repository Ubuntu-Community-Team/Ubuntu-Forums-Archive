---
title: "Software compat-wireless"
date: 2009-06-07
forum: Catalan Team
---

### Post by akyra on 2009-06-07
Hola de nou.

Intentant solucionar els problemes de poca potencia de recepcio del senyal de wifi, he trobat el programe "compat-wireless" que està dins dels "linux-backports-modules-jaunty".

Que són els linux-backports-modules-jaunty? Per què serveixen?

Algú ha probat el compat-wireless? Sembla que pot augmentar el senyal de recepció del wifi.

Jo he trobat aquest link per si algú li interessa

[http://linuxwireless.org/en/users/Download]("http://linuxwireless.org/en/users/Download")

Salutacions

---

### Post by PatrickVogeli on 2009-06-07
el compat-wireless son drivers de tarjes wifi més actualitzats. Els backports-modules actualitzen els drivers del kernel de Jaunty a uns de més actuals.

Pots comprovar quins fitxers i moduls inclou el paquet backports-module pel kernel 2.6.28-11-generic aqui: [http://packages.ubuntu.com/jaunty/amd64/linux-backports-modules-2.6.28-11-generic/filelist](http://packages.ubuntu.com/jaunty/amd64/linux-backports-modules-2.6.28-11-generic/filelist)

salut

---

### Post by akyra on 2009-06-09
Jo els vaig instalar des del sinaptic, però després que s'ha de fer per utilitzar-los?

Gracies

---

### Post by PatrickVogeli on 2009-06-09
no res, un cop instal·lat ja ho utilitzes.

---

### Post by akyra on 2009-06-09
Ho sigui que no hi ha cap problema per instalar.los?

Una vegada instalats els  linux-backports-modules-jaunty, han d'apareixer més programes per instal·lar en el sinaptic? que fan exactament (o no exactament)? És bo instalar·los?

Disculpa la ignorancia.

---

### Post by PatrickVogeli on 2009-06-09
Bé doncs, anem per parts:

Tal com t'he dit, el compat-wireless son drivers de tarjes inalambriques actualitzats. Anem a posar un exmple (fictici):

Posem per cas que el kernel 2.6.26 té el driver 1.0 del chip inalambric rt2500 i que el kernel 2.6.30 n'inclou la versió 2.3.

Doncs bé, si el nostre sistema fa servir el kernel 2.6.26, l'unica manera d'aconseguir aquest nou driver seria instal·lant un kernel més nou, amb el problema que no sempre és possible o factible, i que fent-ho perdem altres coses. En el cas d'ubuntu, hi ha els drivers propietaris (nvidia, ati, alguns atheros etc) que si ens compilem el nostre kernel, els haurem d'instal·lar tots de manera manual i pot ser un maldecap.

La solució és el compat-wireless, que inclouria el driver 2.3 llest per a compilarse i instal·lar-se sobre el kernel 2.6.26, junt amb tot el que es necessita.

Instal·lant el backport modules fem això, actualitzar drivers, que podem ser de so, de xarxa, etc. Així, hi ha alguns equips que la wireless no els funciona de serie, però que si instal·lant aquest paquet soluciona el problema. Pot ser que la versió nova suporti més funcions, optimitzi el rendiment, arregli algun problema amb el driver vell, etc.

Sobre si et calen o no, si es bo o dolent.. es facil de saber. Si no has notat cap millora no et calen, però tampoc estorven. Si has notat que millora, t'els quedes. Si empitjora, desinstal·la-ho i reinicia.

I no, no veuras més programes enlloc, ja que simplement son drivers, no pas cap programa per a res.

salut

---

### Post by akyra on 2009-06-09
Ets bo Patrick!

Això és el que jo dic una explicació clara.
Ja els he instal·lat, per tant el compat-wireless ja que instal·lat, i a veure que pasa.

Adeu i gracies.

---

### Post by akyra on 2009-06-09
Ja els he instal·lat, i no he notat cap millora.

Primer he desactivat el madwifi i he reiniciat i no em detectava la meva xarxa (moltes de altres, però no la meva), he tornat a reiniciar i el mateix resultat.

Finalment he tornat a activar el madwifi i tot com abans.

Bé seguiré provant.

Adeu

---

### Post by pserra on 2010-01-25
q

---

### Post by akyra on 2010-01-26
He canviat l'ordinador i no necessita compta-wireless.

---

