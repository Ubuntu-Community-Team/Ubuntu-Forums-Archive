---
title: "Error al engegar l'Eclipse"
date: 2009-04-01
forum: Catalan Team
---

### Post by christianpv on 2009-04-01
Només acceptar el lloc on es va a crear el workspace, surt una finestreta on apareix:
JVM terminated. Exit code=1
/usr/lib/jvm/java-gcj/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 818017
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-gcj/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 

no se ven bé, el que em demana, algú m'ho podria dir?;)

---

### Post by papapep on 2009-04-01
Comprova si tens instal·lat el paquet  **sun-java6-jre**. Si no el tens, instal·la'l.

Quan ho hagis fet, executa:

```
sudo update-alternatives --config java
```

i comprova que és l'opció triada de manera predeterminada. Si no ho és, fes que ho sigui.

> papapep@awacs:~$ 
[sudo] password for papapep: 

Hi ha 5 alternatives que proveeixin «java».

  Selecció     Alternativa
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2


Un cop hagis fet aquestes dues coses, torna a provar a executar l'Eclipse.

---

### Post by christianpv on 2009-04-03
continua apareguent:

JVM terminated. Exit code=1
/usr/lib/jvm/java-gcj/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 380063
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-gcj/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar

---

### Post by papapep on 2009-04-03
> JVM terminated. Exit code=1
/usr/lib/jvm/java-gcj/bin/java

A algun lloc del procés no t'ha funcionat bé.

Enganxa el que et mostri en fer:

```
sudo aptitude search jre|grep ^i
```

i

```
sudo update-alternatives --config java
```

---

### Post by christianpv on 2009-04-03
El config java em mostra açò que no és exactament el que em poses,

$ sudo update-alternatives --config java

Hi ha 4 alternatives que proveeixin «java».

  Selecció     Alternativa
-----------------------------------------------
          1    /usr/bin/gij-4.2
 +        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          3    /usr/lib/jvm/java-gcj/jre/bin/java
*         4    /usr/lib/jvm/java-6-sun/jre/bin/java

Premeu retorn per a mantenir l'opció per defecte[*], o introduïu un número de selecció:

si canvie la opció, només hi canvia (*), el (+) es queda a la mateixa posició.
digues-me si no tinc el java correcte. gràcies.

---

### Post by papapep on 2009-04-04
Quina versió d'Eclipse fas servir? és el paquet dels repositoris? 

Prova a executar a un terminal, com a usuari normal:

```
eclipse -vm /usr/lib/jvm/java-6-sun/jre/bin/java
```

a veure què diu.

---

### Post by christianpv on 2009-04-04
papapep ets un crack \\:D/ funciona!!!!!!!

---

