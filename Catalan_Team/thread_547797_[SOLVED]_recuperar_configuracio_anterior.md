---
title: "[SOLVED] recuperar configuracio anterior"
date: 2007-09-10
forum: Catalan Team
---

### Post by pserra on 2007-09-10
Hola companys,
avui amb l'automatix he baixat un driver   per nvidia (tinc aquesta tarja) I sorpresa.... al reiniciar no funciona.... em queda la pantalla en gris.
Hi ha alguna manera re restaurar canvis?
Crec recordar que els canvis de configuració es guarden en un arxiu  i hi ha manera de desfer canvis.Quin archiu és?   
Gràcies

---

### Post by pespin on 2007-09-10
El fitxer que busques segurament és el de configuració del xserver. El pots trobar a:

```
/etc/X11/xorg.conf
```

De totes maneres em sembla que hi ha una ordre/programa que reescriu el fitxer xorg.conf i el deixa  com està per defecte.

---

### Post by pserra on 2007-09-10
[COLOR=Navy]Gràcies Pespin,
ja he pogut 'ressucitar' el meu Ubuntu, he hagut de canviar el nom del xconf i ja està.....  Ja m'havia passat fa temps i no vaig guardar 'la recepta' de com solucionar-lo... Ara ho faré.....
Tinc el problema que quan vull instal·lar alguna cosa  com avui des de Automatix em surt que hi han controladors Nvidia per instal·lar i com que no acaba d'anar gaire fi, em tempto d'instal·lar-lo i ja desprès 'peta'.
Gràcies
[/COLOR]

---

### Post by papapep on 2007-09-10
T'aconsello fervorosament que et carreguis l'Automatix, ha portat problemes a massa gent. Sembla que li cal un periode llarg per a madurar.

---

### Post by pserra on 2007-09-11
Si el eliminaré, 
recordo que un dia vaig instal·lar el Beryl des de l'automatix i em 'petava'  l'Ubuntu,
de fet no ho he provat més. Tinc un portàtil de 5  anyets.... i crec que el beryl necessita una mica de potencia...
Merci pels consells Papapep, sempre van bé.

---

