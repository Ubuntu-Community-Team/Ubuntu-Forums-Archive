---
title: "Impossible la instal·lació de l'ubuntu en el pc de sobretaula"
date: 2009-09-03
forum: Catalan Team
---

### Post by jnnadal on 2009-09-03
Bones a tots, fa uns anys vaig tenir instal·lades les versions 6, i més tart la 7 al meu ordinador de sobretaula. Més tart però, vaig haver tornar al windows per qüestions de treball i d'estudis. Així i tot vaig continuar amb l'ubuntu al portàtil.
La meva sorpresa arriba quan, fa uns mesos, vaig intentar tornar instal·lar l'ubuntu al sobretaula i em va resultar impossible. El que passa és que quan carrega el live cd i va aproximadament per la meitat hem salta la línia d'ordres. A l'inici de la línia hem surt la paraula initramfs entre parèntesi. He intentat intal·lar altres distribucions però el problema persisteix; fins i tot he provat d'instal·larlo en una màquina virtual dins el windows però m'ha resultat impossible.
Si qualqú sap alguna solució estaria molt agraït que me la remetés.
Si alguna cosa no s'entén no dubteu a demanar.

---

### Post by papapep on 2009-09-03
No és molt habitual trobar-se, avui en dia, amb casos així, tot i que no és impossible, com és obvi. El que jo provaria primer, abans de trencar-me més les neurones, és a descarregar la versió alternate:

Per a Intel32: [http://releases.ubuntu.com/jaunty/ubuntu-9.04-alternate-i386.iso](http://releases.ubuntu.com/jaunty/ubuntu-9.04-alternate-i386.iso)

Per a 64 bits: [http://releases.ubuntu.com/jaunty/ubuntu-9.04-alternate-amd64.iso](http://releases.ubuntu.com/jaunty/ubuntu-9.04-alternate-amd64.iso)

Això t'intentarà instal·lar directament l'Ubuntu, sense liveCD, i amb entorn de text. Exactament el mateix, però menys "bonico". Molts cops solventa el tema.

Sort, salut i benvingut al fòrum. 


PD: no estaria malament passar-te pel fil de benvinguda per a fer-nos cinc cèntims sobre tu ;)

---

### Post by jnnadal on 2009-09-04
He intentat instal·lar l'ubuntu 7.04 en mode text, ja que tenia la versió de dvd; però continua el mateix problema. Ara hem diu que no detecta el lector de cdrom. No tinc ni idea de com solucionar-ho.

---

### Post by papapep on 2009-09-04
Doncs igual és que realment et falla el lector de CD/DVD...

---

### Post by jnnadal on 2009-09-04
Però és un poc estrany que només sigui amb linux que hem doni aquest error, mentre que amb l'xp o fins i tot amb un hackintosh no hem doni cap problema. 
Crec que finalment hauré de donar per acabats els meus intents de posar l'ubuntu a l'ordinador de casa.

---

### Post by ilku on 2009-09-04
Jo provaria una versió mes moderna, la 9.04 esta bé. I si encara et dona problemes prova a fer-ho desde un llapis de memòria, per si es un problema del lector de CD. (sempre que puguis iniciar des de USB i no tinguis cap altre aparell de CD per intercanviar).

---

### Post by totalkiller on 2009-09-04
A mi em va passar un cop i ho vaig solventar amb un startx

---

### Post by jnnadal on 2009-09-04
i com es fa això?

---

### Post by jerec on 2009-09-04
> **totalkiller said:**
> A mi em va passar un cop i ho vaig solventar amb un startx

Vinga, a veure qui la diu mes grossa!

Moltes de les distribucions Live CD, tenen la opció de verificar la integritat del CD/DVD, amb això et pots fer una idea de si esta ben "cremat" o de si el teu lector, tal i com et diuen, pot ésser que no llegeixi correctament.

A mes, no estaria del tot malament mes informació de la maquina, versió, etc que tens i que et dona problemes.

---

### Post by jnnadal on 2009-09-05
> **jerec said:**
> Vinga, a veure qui la diu mes grossa!

Moltes de les distribucions Live CD, tenen la opció de verificar la integritat del CD/DVD, amb això et pots fer una idea de si esta ben "cremat" o de si el teu lector, tal i com et diuen, pot ésser que no llegeixi correctament.

A mes, no estaria del tot malament mes informació de la maquina, versió, etc que tens i que et dona problemes.

És un pentium d 950, placa intel DZGIS946, nvidia 8600gt, 3gb ram, 3 discs durs d'un TB en total. El lector és philips, encara que no tinc ni idea de quin model és.

---

### Post by jerec on 2009-09-05
D950, això es un dual Core a 3,4Ghz i una nvidia. La veritat que no hauries de tenir problemes, jo verificaria:

1º Descartar que el lector no estigui cascat i que el CD/DVD funcioni (prova'l en una altre maquina)
2º Quan dius que et va a la consola, pots fer-hi alguna cosa a la consola¿? Pots anar a /var/log a veure els logs del sistema?
3º Quina versió Live proves? la de 32 o la de 64 bits, amb el teu processador pots instal·lar tranquil·lament la de 64bits

---

