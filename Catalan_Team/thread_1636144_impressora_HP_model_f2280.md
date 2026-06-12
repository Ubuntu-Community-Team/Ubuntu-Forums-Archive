---
title: "impressora HP model f2280"
date: 2010-12-02
forum: Catalan Team
---

### Post by josep-maria on 2010-12-02
Tinc l'ubuntu 10.10 i una impressora HP model F2280, que anava bé fins ara que he canviat el cartutx de tinta i ja no funciona gens. He tornat a donsr-la d'alta i tampoc. Les tasques d'impressió són a accesoris > gestió de les tasques d'impressió, amb l'estat de 'processant' però no s'imprimeixen.

---

### Post by wgarcia on 2010-12-03
A mi em va passar en algun moment de les actualitzacions de Lucid que també em va deixar de funcionar una impressora HP i mirant a la llista d'errors sortia que hi havia un error per a les impressores que es connecten per USB. 

El vaig arreglar configurant la impressora a través del menú del "cups" que surt quan a un navegador entres:

[http://localhost:631](http://localhost:631)

Primer vaig donar de baixa la impressora, i després la vaig tornar a donar d'alta a l'esmentat menú. Però com deia això va ser fa un parell de mesos, abans que m'actualitzés a la 10.10, i suposo que el teu problema deu ser un altre perquè aquest error que esmento ja es deu haver arreglar. Però potser ho pots provar perquè no hi ha res de més frustrant que una cosa et deixi de funcionar de sobte, sobretot quan es tracta de coses tan bàsiques com poder imprimir.

---

### Post by josep-maria on 2010-12-03
He fet això que has dit i segueix sense imprimir.

---

### Post by quitus on 2010-12-03
no se quina relació hi ha entre canviar el cartutx de tinta i que deixi de "comunicar" amb el PC. Desprès de comprovar totes les conexions (potser s'ha deixat anar alguna cosa) pots provar a instalar el HPLIP en la web només hi ha suport com a molt per la 10.04, però jo ho tinc instalat amb la 10.10 i no tinc cap problema amb una HP F4280

salut

---

### Post by wgarcia on 2010-12-04
És una impressora USB, suposo, oi? Pots provar de desendollar-la de l'USB, tornar-la a endollar, i posar a una terminal:

dmesg

i enganxar aquí les 4 o 5 últimes línies que es mostren, o les que vegis que semblen tenir relació amb la impressora.

---

### Post by josep-maria on 2010-12-04
He tornat a fer tot això que m'heu dit i ara ja funciona. Moltes gràcies.

---

