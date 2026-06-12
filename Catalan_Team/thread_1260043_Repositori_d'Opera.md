---
title: "Repositori d'Opera"
date: 2009-09-07
forum: Catalan Team
---

### Post by Daerun on 2009-09-07
Des de fa uns quants dies, després de cada actualització apareix un avís que diu que en refrescar la llista de repositoris, el d'Opera ha fallat; i és cert, si refresco manualment també dóna un error. Algú en sap res, d'això?

El tinc d'aquesta manera (no sigui que l'hagin canviat o alguna cosa :P)

deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

---

### Post by jodufi on 2009-09-09
Hola Daerun,

No se quin Ubuntu estàs utilitzant, però segur que ho tens mal configurat. Si tens l'Ubuntu Jaunty 9.04 hauries de tenir:

```
deb http://archive.canonical.com/ jaunty partner
```

o

```
deb http://deb.opera.com/opera/ stable non-free
```

Però sembla que la segona opció no funciona des de fa poc.
Per a obtenir més informació, consulta aquesta web:

[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by Daerun on 2009-09-10
Gràcies Jodufi :D El repositori que tenia és el que apareixia a tots els tutorials quan ho vaig consultar fa uns mesos :P

---

