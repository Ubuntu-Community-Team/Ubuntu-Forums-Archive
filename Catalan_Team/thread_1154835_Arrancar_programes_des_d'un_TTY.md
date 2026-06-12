---
title: "Arrancar programes des d'un TTY"
date: 2009-05-10
forum: Catalan Team
---

### Post by PatrickVogeli on 2009-05-10
Bones gent!

Estic fent proves dels scripts que faig servir per reduir el consum d'energia quan funciono amb bateria, i m'agradaria saber si algun hem sap dir com arrancar una aplicació amb interficie grafica desde tty (Ctrl+Alt+F1). El que vull posar per exemple gedit i que se m'obri a on tinc funcionant les X. Es possible?

Merci!

---

### Post by kimet on 2009-05-10
Hola:


```
DISPLAY=:0.0 gedit
```

Salut.

---

### Post by PatrickVogeli on 2009-05-10
gracies!

Efectivament, si ho faig desde un tty funciona, pero si ho poso al meu script d'estalvi d'energia (el tinc a /etc/pm/sleep.d i power.d) no funciona com vull. El compiz --replace em deixa sense gestor de finestres i el metacity --replace fa alguna cosa estranya. Ja he provat a posar HOME= i/o USER= i res.

seguire investigant...

salut

---

### Post by CarlesOriol on 2009-05-11
i si fas un sudo nomusuari ... per assegurar que l'script corre a l'entorn de l'usuari on fas el canvi i no en el del propietari del servei?

---

### Post by PatrickVogeli on 2009-05-11
sudo nomusuari? Si poso sudo patrick al terminal em diu que no trova la ordre patrick.. em perdo alguna cosa? Si faig su patrick ordre tampoc funciona..

---

### Post by CarlesOriol on 2009-05-11
Evidentment mesclat-ho amb el DISPLAY... 

Al teu script sudo -u usuariambx comandaaexecutar

---

### Post by PatrickVogeli on 2009-05-11
no res noi, no hi ha sort. Amb el metacity aixi no hi tinc cap problema, funciona de conya, pero quan ha d'entrar el compiz em quedo sense gestor de finestres.

Seguire provant, suposo xD

merci!

---

