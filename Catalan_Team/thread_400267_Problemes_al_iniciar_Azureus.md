---
title: "Problemes al iniciar Azureus"
date: 2007-04-03
forum: Catalan Team
---

### Post by jraulbc on 2007-04-03
Hola de nou,

Al posar en marxa l'Azureus, just quan acaba de carregar els torrents i s'ha obert la finestra es tanca. He provat a posar-lo en marxa des del terminal per vore si sortia un error i ha sortit el següent:

[INDENT]burriel@jraulbc-desktop:~$ azureus
DEBUG::Tue Apr 03 15:17:18 CEST 2007::com.aelitis.azureus.core.networkmanager.VirtualChannelSelector::select::272:
  Caught exception on selector.select() op: Operation not permitted
    NonBlockingReadWriteService$1::runSupport::80,AEThread::run::69
java.io.IOException: Operation not permitted
        at sun.nio.ch.EPollArrayWrapper.epollCtl(Native Method)
        at sun.nio.ch.EPollArrayWrapper.updateRegistrations(EPollArrayWrapper.java:202)
        at sun.nio.ch.EPollArrayWrapper.poll(EPollArrayWrapper.java:183)
        at sun.nio.ch.EPollSelectorImpl.doSelect(EPollSelectorImpl.java:65)
        at sun.nio.ch.SelectorImpl.lockAndDoSelect(SelectorImpl.java:69)
        at sun.nio.ch.SelectorImpl.select(SelectorImpl.java:80)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualChannelSelectorImpl.select(VirtualChannelSelectorImpl.java:446)
        at com.aelitis.azureus.core.networkmanager.VirtualChannelSelector.select(VirtualChannelSelector.java:272)
        at com.aelitis.azureus.core.clientmessageservice.impl.NonBlockingReadWriteService$1.runSupport(NonBlockingReadWriteService.java:80)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=6247, tid=3084684192
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid6247.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)
burriel@jraulbc-desktop:~$ [/INDENT]

Per la qual cosa he deduït que es tracta d'un problema amb Java. He buscat per Internet i en el forum en espanyol d'ubuntu he trobat referències al mateix problema,

[http://www.ubuntu-es.org/index.php?q=node/41898](http://www.ubuntu-es.org/index.php?q=node/41898)

i una solució que no m'ha resultat

[http://www.ubuntu-es.org/index.php?q=node/41591](http://www.ubuntu-es.org/index.php?q=node/41591)

Continuant buscant he trobat açò

[https://launchpad.net/ubuntu/+bug/86103/](https://launchpad.net/ubuntu/+bug/86103/)

per la qual cosa sembla que el problema és un "bug" identificat per la comunitat, però com jo no controlo molt d'anglès, no n'he tret molt de clar (encara que m'ha semblat que no apareixia una solució).

Alguna idea? Gràcies!

jraulbc

---

### Post by MeneK on 2007-04-04
Prova amb:

```
sudo update-alternatives --config java
```

I escull el gij-wrapper o, si la tens instal·lada, la versió 6 de java (és la que faig servir jo en Feisty).

---

### Post by jraulbc on 2007-04-15
> **MeneK said:**
> Prova amb:

```
sudo update-alternatives --config java
```

I escull el gij-wrapper o, si la tens instal·lada, la versió 6 de java (és la que faig servir jo en Feisty).

Hola MeneK,

Triant la versió 6 de java, continua fallant. I amb gij-wrapper, el programa es posa en marxa normalment, però no descarrega res i quan surtes es penja i cal forçar la sortida. Quina versió de java deuria tindre per a Ubuntu 6.10? Com puc saber quina versió tinc instal·lada?

Gràcies pels comentaris

jraulbc

---

### Post by CarlesOriol on 2007-04-15
Has provat d'eliminar la carpeta: /home/elteusuari/.azureus després de fer tots els canvis que has dit?

---

### Post by jraulbc on 2007-04-16
> **CarlesOriol said:**
> Has provat d'eliminar la carpeta: /home/elteusuari/.azureus després de fer tots els canvis que has dit?

Hem sembla que he fet això, encara que he arribat a la solució d'una manera un poc rocambolesca:

1. En el forum d'Ubuntu.es he vist que alguns participants comentaven que havien solucionat el problema eliminant la carpeta .azureus. Ho he provat, però en lloc d'eliminar la carpeta l'he reanomenat per no perdre-la.

2. L'Azureus s'obria i he pogut tornar a descarregar alguns dels torrents que estava baixant (passant l'arxiu torrent de la carpeta reanomenada a la nova i especificant la mateixa carpeta de descàrrega). L'Azureus no es tancava però no descarregava res. I a més, al sortir del programa es penjava.

3. He reanomenat les dos carpetes recuperant la .azureus original però li he substituit l'arxiu azureus.config per el mateix arxiu de la nova carpeta (pensant que es podia tractar d'un problema de configuració d'Azureus). I la cosa a funcionat i m'ha tornat a descarregar tots els arxius tal com s'havien quedat abans.

Una història rocambolesca, però ha funcionat...

Gràcies a tots! :D

---

