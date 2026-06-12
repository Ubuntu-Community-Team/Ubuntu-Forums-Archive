---
title: "Arxius ocults"
date: 2007-08-21
forum: Catalan Team
---

### Post by grundt on 2007-08-21
Hola,
m'agradaria saber que puc fer amb els arxius ocults que queden a la carpeta usuari despres d'haver instalat o desinstalat un programa.

M'agradaria eliminar-los.

---

### Post by papapep on 2007-08-21
No acabo d'entendre la teva pregunta...preguntes si hi ha algun problema en eliminar-los? o que no pots/saps eliminar-los??

Si és el primer cas, no, no hi ha problema en esborrar-los si ja has desinstal·lat el programa.

Per a propers cops, si els desinstal·les des d'un terminal amb:

```
sudo aptitude purge nom_del_programa
```

Això desinstal·la el programa i esborra els fitxers de configuració simultàniament.

Suposo que el Synaptic deu tenir alguna opció per a fer el mateix en vers de només eliminar el programa deixant els fitxers de configuració.

---

### Post by lluisanunez on 2007-08-22
Exactament, el Synaptic té l'opció "Eliminar" i "Eliminar completament" (o similar, el meu va en anglès). La segona elimina també les carpetes i arxius d'usuari.

---

