---
title: "L'escriptori no es carrega"
date: 2009-02-23
forum: Catalan Team
---

### Post by MorlanXaos on 2009-02-23
Hola tots!

Porto tota la tarda barallant-me amb un portatil DELL Latitude D620 i l'Ubuntu 8.04.

L'he instal.lat des de el Live CD, i tot bé. Però quant he arrenco des de el disc dur, i després del login, el escriptori no es carrega, es a dir que es queda penjat a la pantalla de color marró de avans de entrar-hi.

Des de la consola del modo de proba, he des-instal.lat el compiz-core i he tornat a instal.lar-lo sense que es soluciones. He fet el mateix amb ubuntu-desktop, i també sense èxit. I en aquests moments ja no se que fer.

Apreciaria si en poguéssiu donar un cop de ma. :(

---

### Post by oriolsbd on 2009-02-24
Pot ser que t'hagis quedat sense espai a alguna partició? A mi em va passar algun cop. Entra al mode consola i executa:
```
df -k
```
A veure si tens plena alguna de les particions (sobretot, mira on tinguis muntat el "/" i el "/home").

Salut!

---

### Post by MorlanXaos on 2009-02-24
Gracies Oriol,

No, el / i el Home estan al 2%. He provat una altre vegada de instalar-lo, pero aquesta vegada creant les particions manualment.

I m'he quedat exactament igual.

De totes maneres al iniciar l'Ubuntu surt un missatge que diu de que no troba un fragment de firmware i que vagi a la pagina d'Ubuntu, però francament no em dona temps a llegir-ho del tot.

Crec que avans tenia aquest ordinador amb un pendrive i el 7.10 i anava be. Ho provare.
Salut!

---

### Post by oriolsbd on 2009-02-25
Hola, per veure els missatges que et dóna a l'arrancada pots fer el següent:
```
dmesg > nom_fitxer
gedit nom_fitxer

```

De tota manera, no tinc clar si quan et dóna el missatge pots entrar al mode consola. Si no pots, em sembla que si apretes el botó de "Pausa" (el que està prop del "Impr Pant") mentre es visualitza el missatge per pantalla s'aturaran els missatges i podràs llegir-lo. No estic segur que s'aturi, però em sona haver-ho llegit en un altre missatge, i no costa res provar-ho. :-)

Salut!

---

### Post by MorlanXaos on 2009-02-25
Oriol,

Si, si podia entrar al modo consola.La tecla de pausa em sembla que la tinc gastada de tant pitjar-la però sense cap resultat.

Al final estaba tan cansat i desesperat que ja no sabia si tirar-me al tren a o la taquillera i he instal·lat el 8.10, i "voila", tot perfecte, la targeta gràfica, el wifi, el bluetooth, tot funcionant a les mil meravelles.

Disculpa que no he pogut el teu truc, pero ho provare quant tingui un moment.
Gracies per tot :guitar:

---

### Post by MorlanXaos on 2009-02-25
No puc canviar el títol del primer post per afegir [SOLVED]

---

### Post by SiscoGarcia on 2009-02-27
> **MorlanXaos said:**
> No puc canviar el títol del primer post per afegir [SOLVED]

Fins que no modifiquin el fòrum la gent d'ubuntu em temo molt que no es pot fer com parlàvem no fa gaire (mira't l'entrada #7 d'[aquest fil]("http://ubuntuforums.org/showthread.php?t=1059995")).

---

