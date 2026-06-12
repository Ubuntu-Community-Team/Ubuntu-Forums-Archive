---
title: "Jaunty: gestor d'actualitzacions"
date: 2009-04-29
forum: Catalan Team
---

### Post by Daerun on 2009-04-29
No sé si això és un "problema" o és que la Jaunty és així, però el Gestor d'Actualitzacions no funciona com en anteriors versions; quan hi ha actualitzacions, s'obre directament el Gestor, capturant l'atenció, y en cap moment apareix una icona d'avís a l'àrea de notificació, de manera que si tanco el gestor perquè estic treballant, després he de recordar jo mateix que tenia actualitzacions :P Això és algun mal funciomanent, o realment ja és així? I si és així, hi ha alguna manera de configurar-ho perquè funcioni com abans?

---

### Post by kukat on 2009-04-29
mmm...a mi em passa el mateix! i la veritat es que m'agradava més com es feia amb l'Intrèpid....

---

### Post by oriolsbd on 2009-04-29
A mi també em passa el mateix. És més, m'havia fixat que m'obre la finestra, però no m'havia fixat que no hi ha la icona de notificació. A mi també m'agrada molt més el sistema antic.

---

### Post by Daerun on 2009-04-29
Entenc, per tant, que no és cap problema, si no que és així...


EDITO: efectivament, és així, ja s'han "queixat" a l'[Ubuntu Brainstorm](http://brainstorm.ubuntu.com/idea/19283/) :P

---

### Post by RainCT on 2009-04-29
Sí, és així (doneu les gràcies al gran equip de "Desktop DX" -o com es digui- de Canonical). El tema ja es va discutir a mort a la llista ubuntu-devel però així s'ha quedat; recentment han creat una llista de correu específica per a parlar de temes d'aquest tipus i si ho recordo bé pot ser que a la Karmic acabin de matissar el nou funcionament del gestor d'actualitzacions.

El canvi es pot desfer amb l'ordre: ```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

---

### Post by Daerun on 2009-04-30
Això fa que funcioni com en versions anteriors? :D

---

### Post by PatrickVogeli on 2009-04-30
jo trovo que aixi com ho han deixat... aixo ja fa mes pudor que el windows..

---

### Post by Daerun on 2009-05-01
Home, jo no diria tant, però que és molest i poc pràctic (per allò de que si tanques el Gestor i te n'oblides, després et quedes sense actualitzacions) sí que ho diria...

---

### Post by RainCT on 2009-05-02
> **Daerun said:**
> Això fa que funcioni com en versions anteriors? :D

Exacte.

---

### Post by torracastanyes on 2009-05-02
Perdoneu, però em sembla que no n'hi ha prou. Ho he provat en dues màquines i la finestra del gestor ja no s'obre sola, però la icona no apareix. Com ho he de fer, per posar-la?

---

### Post by Daerun on 2009-05-07
A mi sí que se m'ha arreglat; han entrat ja dues actualitzacions amb la aparició de la icona famosa, a tu no?

---

### Post by torracastanyes on 2009-05-07
De moment, no.
De fet, ja em van entrar actualitzacions mentre ho provaba, i com que no em va avisar, ho vaig deixar com al principi.

---

### Post by torracastanyes on 2009-05-13
Ja he trobat la icona !!!

Tal com li va passar al MiquelBLL, era un problema de l'àrea de notificacions.

[http://ubuntuforums.org/showthread.php?t=1150651](http://ubuntuforums.org/showthread.php?t=1150651)

---

