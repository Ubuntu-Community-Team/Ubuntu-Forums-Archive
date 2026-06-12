---
title: "sons d'alerta a xubuntu"
date: 2009-02-09
forum: Catalan Team
---

### Post by SiscoGarcia on 2009-02-09
Hola,

Estic començant amb xubuntu i no me'n surto per treure el sorollet d'alerta que fa quan demanes alguna cosa impossible o contradictòria (per exemple ara que m'havia empenyat a posar l'accent a la r enlloc de l'o); també passa quan tanques la màquina, no sé on he d'anar per tal de treure-ho.

Amb gnome ja ho tinc apamat, és a "Sistema>Preferències>So>Sons>>reprodueix el so d'alerta", i llavors el desmarques i ja està. Doncs amb xfce porto tota la tarda/vespre d'ahir i ja fa una estona que hi lluito i no ho trobo:(

---

### Post by tanreb20 on 2009-02-09
Si et refereixes als **beep** aqui tens la solució.

editar l'arxiu /etc/modprobe.d/blacklist

```
sudo vim /etc/modprobe.d/blacklist

```
i afegir:

```
#Módulo de pitidos de sistema
blacklist pcspkr
```

i si vols treure el soroll JA

```
sudo rmmod pcspkr
```

---

### Post by SiscoGarcia on 2009-02-10
Moltíssimes gràcies tanreb20, n'estava ben tip dels beeps :)

---

### Post by tanreb20 on 2009-02-10
Ecantat d'haver-te pogut ajudar!

Hauries de marcar l'apunt (post) com a SOLVED (thread tools o algo aixi)

---

### Post by SiscoGarcia on 2009-02-10
> **tanreb20 said:**
> Ecantat d'haver-te pogut ajudar!

Hauries de marcar l'apunt (post) com a SOLVED (thread tools o algo aixi)

Tens raó, de fet me'n faig un fart de dir-ho, però hores d'ara no hi ha l'opció, precisament [l'altre dia en parlàvem]("http://ubuntuforums.org/showthread.php?t=1059995"). T'adjunto una captura de les opcions que dóna el "Thread Tools".

De tota manera, reanomenaré el fil a [RESOLT] tal com jo mateix proposava ;)

EDITO: Doncs ara resulta que ni editant puc canviar el nom del fil. Crec recordar que abans es podia fer :(

Tant se val, [APUNT]("http://bloc.eurion.net/archives/2009/traduccio-del-terme-post%C2%BB/") RESOLT

---

### Post by papapep on 2009-02-11
Thread != post, així doncs, Fil != apunt, en conclusió:

**Fil** resolt :-P

---

