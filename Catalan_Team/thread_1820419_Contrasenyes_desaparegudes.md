---
title: "Contrasenyes desaparegudes"
date: 2011-08-07
forum: Catalan Team
---

### Post by Kette on 2011-08-07
Tinc un problema molt greu: avui ha engegat el computador una filla meva, s'ha "logejat" correctament, després d'una estona he intentat entrar jo i no em reconeix la contrasenya. He provat amb els altres dos usuaris i tampoc reconeix cap d'elles, només el de la filla que s'ha connectat primer.
Aquest fet ja m'havia passat fa pocs dies però en aquest cas l'únic que podia entrar era jo, ho vaig resoldre amb un "sudo passwd *usuari*" tornant a posar-li les contrasenyes perdudes. Ara no ho puc fer, sóc l'únic que esta en el grup "sudoers".
El computador corre amb 11.04 i és l'unic SO instal·lat, per tant tampoc veig el GRUB per entrar en "recovery mode".
Que puc fer?

---

### Post by wgarcia on 2011-08-08
Per veure el grub en començar, just després dels missatges inicials del sistema prem la tecla Majúscula (Shift).

---

### Post by Kette on 2011-08-08
Moltes gràcies wgarcia, encertat com sempre.
Ja he resolt el problema, torno a tenir la meva contrasenya i he canviat les dels altres usuaris que no funcionaven.
I ara la pregunta del milió: com coll..s s'han canviat les contrasenyes? he trobat que tinc dos fitxers "shadow", un, com crec que ha de ser: "shadow" i l'altre: "shadow-". El final és - i no ~. Creieu que te res a veure? Per cert, també tinc dos "gshadow" en les mateixes condicions. És normal això?
Gràcies

Editat:
com una imatge val més que mil paraules... aquesta és la sortida de terminal:
```
eugeni@principal:/etc$ls -l | grep shadow
-rw-r-----   1 root    shadow    910 2011-07-21 22:56 gshadow
-rw-------   1 root    root      922 2011-07-21 22:20 gshadow-
-rw-r-----   1 root    shadow   1708 2011-08-08 20:15 shadow
-rw-------   1 root    root     1834 2011-07-21 22:55 shadow-
```

---

### Post by kimet on 2011-08-08
No crec que estigui habilitada la caducitat de contrasenyes a ubuntu.
De totes maneres ho pots comprovar amb chage.
**chage -l usuari** o **sudo chage -l root**

---

### Post by Kette on 2011-08-09
No kimet, no esta habilitada. Enganxo la sortida del meu usuari:
```
eugeni@principal:~$chage -l eugeni
Últim canvi de contrasenya				: ago 08, 2011
La contrasenya caduca					: mai
Contrasenya inactiva					: mai
El compte caduca					: mai
Número mínim de dies entre canvi de contrasenya		: 0
Número màxim de dies entre canvi de contrasenya		: 99999
Número de dies d'avís abans que la contrasenya expiri	: 7

```
El que m'amoïna és l'existència d'aquest dos fitxers acabats amb "-", autèntiques "ombres" dels altres, no crec que sigui normal. Els puc esborrar?

---

### Post by kimet on 2011-08-09
Son copies de seguretat, revisa el manual.
**man shadow**

Si encara estas amoïnat pots passar el rkhunter i el chkrootkit.

Salut.

---

### Post by Kette on 2011-08-09
Gràcies kimet. Hi faré una ollada.
Ja puc donar la consulta com resolta.

---

