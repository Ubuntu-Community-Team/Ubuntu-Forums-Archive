---
title: "Nautilus es tanca amb els usuaris"
date: 2011-10-17
forum: Catalan Team
---

### Post by akyra on 2011-10-17
Hola, torno a emprenyar una mica amb l'ubuntu 11.10 de 64 bits.

Ara resulta que el Nautilus es tanca quan estas navegant per les carpetes. A vegades puc clickar a dos o tres, a vegades a una, però s'acaba tancant.

En el cas dels dispositius USB, encara és més ràpid, quan navego per una o dos carpetes es tanca.

Algú sap que pot ser?

Gracies

---

### Post by wgarcia on 2011-10-17
Hi ha dos solucions que he vist proposades:

1) Si no fas servir el servei ubuntuone:

```
sudo apt-get purge ubuntuone-client-gnome
```

2) Altres diuen que s'ha de remoure el paquet següent:

sudo apt-get purge nautilus-open-terminal

---

### Post by akyra on 2011-10-17
Hola wgarcia,

Novament moltes gracies.

Ne estat buscant per internet i no he vist solucions sencilles.

He tret el paquet "sudo apt-get purge nautilus-open-terminal", sempre l'he tingut posat en totes les versions, i que en aquest cas no m'aparexia en el menú contextual.

Per cert també he instal·lat el paquet "nautilus-gksu" i tampoc m'apareix en el menú contextual del nautilus i també l'he desinstalat.

Com puc sabe si això ha estat reparat? Va molt bé tenir aquest dos paquets.

Salutacions

---

### Post by wgarcia on 2011-10-18
Però, s'ha arreglat? Fas servir l'Ubuntu One? Potser traient l'Ubuntu One també s'arregla i no has de treure les altres aplicacions. 

No he mirat si hi ha informes d'error sobre aquest problema, si n'hi hagués et podries subscriure i així veuràs quan alliberen la versió corregida.

---

### Post by akyra on 2011-10-18
Pel moment no utilitzu UbuntuOne, faig servir el Dropbox.

Tens rao probaré de desinstal·lar el UbuntuOne, però que té que veure amb el Nautilus?

Gracies

---

### Post by wgarcia on 2011-10-18
Em sembla que té una integració amb el Nautilus, no el faig servir tampoc i no et puc dir de segur, pero hi ha alguna integració com el Dropbox que et permet veure les carpetes i transferir coses simplemente movent els fitxers entre carpetes.

---

### Post by akyra on 2011-10-18
Gracies de nou, ho probaré aquesta nit.

---

### Post by quitus on 2011-10-18
a mi m'ha funcionat desinstal·lant l'ubuntuone.

salut

---

### Post by akyra on 2011-10-18
He desinstalat ubuntuOne, el nautilus no es tanca però segueix sense apareixa en el menú contextual l'opcio d'obrir com administrador (he instal·lat el paquet nautilus-gksu).

L'opció d'obrir en un terminal m'ha aparegut al cap d'entrar 4 vegades al nautilus, que extrany....

---

### Post by akyra on 2011-10-19
He trobat aquest link que diu que el paquet "nautilus-gksu" no funciona en aquesta nova versió de Ubuntu, així que provaré el que diu.

[http://ubuntu-cosillas.blogspot.com/2011/09/alternativa-nautilus-gksu-en-ubuntu.html]("http://ubuntu-cosillas.blogspot.com/2011/09/alternativa-nautilus-gksu-en-ubuntu.html")

Salut

---

