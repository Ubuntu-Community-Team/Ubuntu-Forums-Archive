---
title: "Java accents i tecles { i }"
date: 2008-12-14
forum: Catalan Team
---

### Post by PellRoja on 2008-12-14
Fa un temps que miro d'esbrinar per que no puc fer funcionar netbeans amb normalitat. El problema que tinc és que no em deixa escriure cap lletra amb accent, ni tampoc cap caràcter que usi la tecla "alt gr" o "control + Alt" per escriure. No em funcionen les claus { i } i això per programar es bastant essencial.

Per deducció he arribat a la conclusió que pot ser el java, que no tingui el teclat ven configurat. Ja que a les aplicacions normals de gnome funcionen totes les tecles, i amb el jedit ( un altre editor fet amb java) tampoc em funcionen les mateixes tecles.

he mirat i rebuscat pels fòrums de molts llocs. Però no he aconseguit res. Algú té una idea?

---

### Post by papapep on 2008-12-14
Has mirat dins /etc/netbeans.conf (o on sigui aquest fitxer), a veure quines definicions hi tens?

---

### Post by PellRoja on 2008-12-14
Si, realment no veig res que pugui definir teclat o algo semblant.

aquí tens el text del fitxer

> # ${HOME} will be replaced by JVM user.home system property
netbeans_default_userdir="${HOME}/.netbeans/6.0"

# Options used by NetBeans launcher by default, can be overridden by explicit
# command line switches:
netbeans_default_options="-J-client -J-Xss2m -J-Xms32m -J-XX:PermSize=32m -J-XX:MaxPermSize=200m -J-Xverify:none -J-Dapple.laf.useScreenMenuBar=true"
# (Note that a default -Xmx is selected for you automatically.)

# If you specify the heap size (-Xmx) explicitely, you may also want to enable
# Concurrent Mark & Sweep garbage collector. In such case add the following
# options to the netbeans_default_options:
# -J-XX:+UseConcMarkSweepGC -J-XX:+CMSClassUnloadingEnabled -J-XX:+CMSPermGenSweepingEnabled
# (see [http://wiki.netbeans.org/wiki/view/FaqGCPauses](http://wiki.netbeans.org/wiki/view/FaqGCPauses))

# Default location of JDK, can be overridden by using --jdkhome <dir>:
netbeans_jdkhome="/usr/lib/jvm/java-6-sun"

# Additional module clusters, using ${path.separator} (';' on Windows or ':' on Unix):
#netbeans_extraclusters="/absolute/path/to/cluster1:/absolute/path/to/cluster2"

---

### Post by papapep on 2008-12-14
[Aquí]("http://sites.google.com/site/netbeansscsni/Home/section-1--ide-configuration-1/1-1-2-purpose-userdir") expliquen, entre altres coses, com definir el "locale" pel Netbeans dins el netbeans.conf.

---

### Post by PellRoja on 2008-12-14
he provat 

#netbeans --locale  i uns quans locales. com ca_ES es_ES en_US

però segueix sense funcionar.

Ara he provat d'instal·lar-ho a la maquina virtual ubuntu 8.10 i allà per defecte funciona les claus. Sembla que sigui un problema d'ubuntu 8.04, ja el meu sistema i una altre maquina virtual que tinc, són 8.04 i passa en les dos.

---

### Post by PellRoja on 2008-12-14
gràcies papapep per la info.

Al he trobat una possible solució, o almenys d'on ve el problema. En l'info que m'has donat també posa com executar netbeans amb alguna altre versió de java. He buscat les versions que hi ha, i en l'arxiu de netbeans.conf he canviat la linia

# netbeans_jdkhome="/usr/lib/jvm/java-6-sun"

per la linia

netbeans_jdkhome="/usr/lib/jvm/java-1.5.0-sun-1.5.0.16"

s'executa bé, funciona les claus, però no els accents. Però amb les claus ja tinc prou per programar.

es podria dir que ja està mig solucionat.

---

### Post by jimmy85 on 2009-08-05
Jo tinc la versió 9.04 de Ubuntu i no s'em reconeixen tampoc els accents ni les claus.

He provat canviant la linia que tu dius, pero si ho faig no se m'inicia el Netbeans, sabeu com ho puc fer???

---

### Post by PellRoja on 2009-08-06
> **jimmy85 said:**
> Jo tinc la versió 9.04 de Ubuntu i no s'em reconeixen tampoc els accents ni les claus.

He provat canviant la linia que tu dius, pero si ho faig no se m'inicia el Netbeans, sabeu com ho puc fer???

Fa molt de temps d'aquest fil. al final ja no uso netbeans, amb qualsevol editor faig. De tant en quan uso geany per php.

La solució que em va funcionar millor, va ser canviar la versió de java. Tot i que llavors no anava del tot bé.

---

