---
title: "error amb sun-java6-doc"
date: 2009-08-02
forum: Catalan Team
---

### Post by sakuraya on 2009-08-02
Bon dia.

Des de fa temps, cada cop que faig canvis amb Synaptic o altres tipus de modificacions, a la terminal em surt un error amb Paquet sun-java6-doc. Concretament aquestes pantalles:
_______________________________
S'està configurant sun-java6doc (6-14-0ubuntu1.9.04) ...
This package is an installer package, it does not actually contain the JDK documentation. You will need to go download one of the archives:

   jdk-6u10-docs.zip  jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/à](http://java.sun.com/javase/downloads/à) configurant sun-java6-doc (6-14-0ubuntu1.9.04) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download. The file should be owned by root.root and be copied to /tmp.

Press RETURN to try again, 'no' + RETURN to abort: 
__________________________________________________________


Després, tot i fer el que indica, tant dient NO, surt error.




He provat a desinstal.lar per Synaptic java6 però tot continua igual. Sé que això em dona diversos errors, com per exemple no em deixa obrir alguns programes com p.ex. Frostwire.

¿Sabeu com ho puc solucionar?

Molte gràcies.

---

### Post by oriolsbd on 2009-08-02
Hola, 

Has provat a desinstal·lar només aquest paquet? El sun-java6-doc. Jo diria que no és necessari, i quan desinstal·les el Java no se't desinstal·la aquest paquet.

Salut!

---

### Post by sakuraya on 2009-08-04
Gràcies Oriolsbd,

Efectivament, a través del Synaptic he anat desinstal.lant tots els arxius de la versió 6 que es la que em dona problemes. Ara funciona perfectament.

Moltes gràcies. La sol.lució més fàcil ha estat la millor, després de donar-li tantes voltes... Merci:P:P

---

