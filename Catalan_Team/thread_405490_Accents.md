---
title: "Accents"
date: 2007-04-09
forum: Catalan Team
---

### Post by jmaspons on 2007-04-09
Com que suposo que deu ser un problema habitual recupero el truc que en CarlesOriol va penjar en un altre [post]("http://ubuntuforums.org/showthread.php?t=379992") per solucionar els problemes amb els accents:

SOLUCIÓ:
Editar l'arxiu /etc/environment (obre com a root amb qualsevol editor de textos, utilitzant alt+F2 per exemple). Cal afegir-hi:
```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"

LC_ALL=ca_ES.UTF-8
LANGUAGE=ca_ES.UTF-8
LC_TYPE=ca_ES.UTF-8
LC_MESSAGES=ca_ES.UTF-8
LANG=ca_ES.UTF-8
```

Salut i que aprofiti!

---

### Post by RainCT on 2007-04-11
Un dubte... No ha canviat a ca_AD ara?

---

### Post by CarlesOriol on 2007-04-11
Fins que tinguem ca_CA (he he!!!) o ca_PC.

---

### Post by RainCT on 2007-04-11
Per al ca_CA ho tens difícil, "CA" és Canadà, i "PC"... no comments xDD

---

### Post by CarlesOriol on 2007-04-12
Mentre al futur no ens facin escriure la normalització constitucional europea: 

 aqecaciavv_PC

Allò que els catalans anomenem català i a valencia valencià... o millorant-lo per integrar els companys de ses illes ;-)))).

---

