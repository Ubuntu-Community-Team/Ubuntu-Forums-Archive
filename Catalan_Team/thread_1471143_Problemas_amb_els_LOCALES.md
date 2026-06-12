---
title: "Problemas amb els LOCALES"
date: 2010-05-03
forum: Catalan Team
---

### Post by tanreb20 on 2010-05-03
Hola! Des de l'instalacio del paquet catalá de idioma que obtinc un error cada cop que faig alguna comanda amb el termina:

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "ca_ES:ca:ca_AD:ca_ES@valencia:ca_FR:ca_IT",
	LC_ALL = (unset),
	LC_TIME = "es_ES.UTF-8",
	LANG = "es_ES.utf8@euro"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

```

Algú sap com fixar el locale catalá xq no es doni aquest error? Grácies.

---

### Post by kimet on 2010-05-03
```
dpkg-reconfigure locales
```??

Salut.

---

### Post by tanreb20 on 2010-05-03
Em temo que per molt que diu que els genera correctament, no funciona :(

---

### Post by tanreb20 on 2010-05-04
Solventat!

Al final he reinstalat els paquets d'anglés, castella i catalá, i finalment ho he pigut resoldre, ara ja tinc l'ubuntu en catalá!

---

