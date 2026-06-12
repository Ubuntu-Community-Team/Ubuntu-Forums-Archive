---
title: "problemes amb el sudo (/etc/sudoers)"
date: 2009-07-13
forum: Catalan Team
---

### Post by tanreb20 on 2009-07-13
Hola...

Avui volia afegir el meu usuari (alorma) al sudo, i he intentat modificar el /etc/sudoers.

Quan anava a fer-ho m'ha donat un error de només lectura, i evidentment... com no he fet un chmod 755...

Ara resulta que no puc fer CAP operació amn el sudo, em diu que ha d tenir permissos 0440, pero no el puc modificar, que puc fer per restaurar els permissos originals?

---

### Post by papapep on 2009-07-13
No entenc el que expliques: si has pogut modificar els permisos del fitxer, com és que ara no pots tornar-los a canviar? amb quin usuari li has posat els 755???

---

### Post by tanreb20 on 2009-07-13
he posat els permissos 755 amb el root

ara no em deixa modificar-lo, ni tan sols puc entrar amb el root.

l'error és el seguent (d qualsevol operació sudo)
```

sudo: /etc/sudoers is mode 0755, should be 0440
```

---

### Post by papapep on 2009-07-13
Doncs arrenca amb un CD viu, munta el sistema de fitxers del disc, i modifica els permisos del fitxer.

---

### Post by tanreb20 on 2009-07-13
ja... pero hi ha alguna manera d fer-ho snse liveCD?

---

### Post by oriolsbd on 2009-07-13
No n'estic segur, però crec que només ho podràs modificar amb un LiveCD perquè, com que el fitxer està amb permisos incorrectes, no pots executar cap "sudo".

Quant al problema que tenies, el fitxer "sudoers" no es pot modificar amb cap editor de la forma habitual, sinó que cal fer-ho amb la comanda:
```
sudo visudo
```

Si t'hi fixes, a les primeres línies del "sudoers" ho indica. Només es pot modificar d'aquesta manera precisament per seguretat. T'obrirà el fitxer amb un editor que es diu "nano". Jo només el coneixia d'haver-lo sentit, no l'havia utilitzat mai. No és molt difícil d'utilitzar. Et mous amb les tecles de direcció, modifiques el que vulguis, i per sortir fas "Ctrl+X" (et demanarà si vols acceptar les modificacions o no).

Salut!

---

### Post by PatrickVogeli on 2009-07-14
podries provar de fer una arrancada en mode recovery, on estaras com a root. Així hauries de poder fer-ho.

salut

---

### Post by Tomàs M. on 2009-07-14
> **PatrickVogeli said:**
> podries provar de fer una arrancada en mode recovery, on estaras com a root. Així hauries de poder fer-ho.

salut

Exacte:

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)
i
[http://forum.ubuntu-fr.org/viewtopic.php?pid=1150772](http://forum.ubuntu-fr.org/viewtopic.php?pid=1150772)

Sort!

---

