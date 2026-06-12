---
title: "encendre vino al arrancar el pc"
date: 2011-10-31
forum: Catalan Team
---

### Post by Rubunter on 2011-10-31
Hola,

Estic intentant connectar-me a l'ordinador de la feina a través de vnc. De moment ja tinc configurat el wake on lan i el ssh. Tan el client com el servidor utilitzen ubuntu 11.10.Ara m'agradaria poder connectar-me al pc via vnc sense haver de fer login a la màquina remota. Algú sap com s'ha de configurar vino/lightdm per fer-ho?

Gràcies

---

### Post by wgarcia on 2011-10-31
Penso que es pot fer definint una clau privada.

A la màquina amb el client ssh

```
ssh-keygen  -t  dsa
```

Això crea dos fitxers al directori ".ssh" de la teva carpeta d'inici: 
id_dsa (clau privada) i id_dsa.pub (clau pública). 

Afegeix el text d'id_dsa.pub a al fitxer .ssh/authorized_keys a la màquina on corre el servidor ssh.

Això t'hauria de permetre connectar-te sense clau entre les dues màquines.

---

### Post by Rubunter on 2011-10-31
Sí, gràcies, això ja ho he fet. Em referia abans de fer login amb el lightdm. És a dir, arrancar el pc amb el wake on lan, i abans de fer login amb el meu usuari, conectar al servidor vnc amb un tunel ssh.

---

