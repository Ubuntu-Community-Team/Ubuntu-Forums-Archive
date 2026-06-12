---
title: "Problemes"
date: 2007-03-26
forum: Catalan Team
---

### Post by kerubin on 2007-03-26
Molt bones. Fa quasi una setmana que he instal·lat l'Ubuntu i abans de fer-ho ja tenia notícia dels problemes que pot haver-hi amb segons quin maquinari.
Suposo que puc anar arreglant els petits errors i/o problemes que vagi trobant amb una mica de temps i tranquilitat tot i que encara estic molt peix en aquests temes.
Però el que em sembla que escapa al meu coneixement i a la meva escassa paciència és precisament la meva impressora.
És una HP-Deskjet 920 series i he provat amb tot el que he trobat tant per fòrums com per pàgines oficials. He instal·lat el foomatic i he instal·lat la impressora amb un dels controladors de la llista que et trobes en el menú d'instal·lació. La impressora sembla que hi és i l'ordinador no diu pas que no la detecti, sinó que es queda com si imprimís i la impressora no treu res, ni tan sols dona senyals d'estar treballant.
Per cert, si no és nota prou els meus coneixements tant d'informàtica en general com de programació són molt escassos.

Gràcies d'antuvi i felicitacions per la traducció del sistema.

---

### Post by orestesmas on 2007-03-26
Aquesta impressora està perfectament suportada. Fins i tot deu haver-hi un driver pel CUPS desenvolupat per la mateixa HP. Crec recordar que el driver es troba en el paquet "hpijs" o "hpoj"

Instal·la aquest paquets (si no els tens ja). Jo et recomano que configuris la impressora a través de la interfície web ([http://localhost:631)](http://localhost:631)). MIra d'instal·lar el controlador que et marca com a "recomanat", que segurament NO serà el meteix que et posava el foomatic (per més seguretat pots desinstal·lar el foomatic aquest).

A veure què tal.

---

### Post by CarlesOriol on 2007-03-27
Jo tampoc no veig cap problema.

Si vols fer un cop d'ull : [http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_920C](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_920C)

L'instal·lació dels paquets fes la en l'ubuntu (synaptic, apt-get, adept...) millor que no ho baixis de hp.

---

### Post by kerubin on 2007-04-01
Gràcies per l'ajuda, suposo que tot plegat hauria de funcionar, però he tingut una apagada a casa i la impressora no s'encén. No crec que tingui a veure amb l'Ubuntu, però que podria ser?
Gràcies de nou i a reveure!

---

### Post by kerubin on 2007-04-04
He aconseguit que s'encengués l'impressora, però estic com abans i he seguit tots els vostres consells. Que més podria fer?

---

### Post by RainCT on 2007-04-06
Prova també des de Sistema -> Preferències -> Impressores, jo he instal·lat dos HP des d'allà i m'han funcionat a la primera (una Deskjet no-me'n-recordo-què i una Photosmart C3180, amb la que també puc escanejar des del Kooka).

---

### Post by orestesmas on 2007-04-08
Realment ho has provat via [http://localhost:631](http://localhost:631) ?? Què et passa si ho intentes per aquesta via?

---

### Post by 11hjpphty76lkjj on 2007-04-09
Sorry I can't answer in your language so I hope this helps.

For HP printers please use:  [http://hplip.sf.net](http://hplip.sf.net)

To configure the printer run:

```
hp-setup
```

If you get a bad command when running the above upgrade to the latest version from the website above.

Hope this helps.

A

---

