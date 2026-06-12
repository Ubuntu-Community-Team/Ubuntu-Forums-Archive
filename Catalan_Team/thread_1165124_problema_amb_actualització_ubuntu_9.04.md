---
title: "problema amb actualització ubuntu 9.04"
date: 2009-05-20
forum: Catalan Team
---

### Post by loles on 2009-05-20
Hola!

Avui mateix he tingut un problema amb l'actualització de la versio 8.10 a la 9.04 (o alguna cosa així són els números)

bo la cosa, es que quan ja estava a punt de instal·lar-se totes les actualitzacions, despres d'haver baixat tot lo necesari. L'ordinador s'ha apagat. No sé si per l'estalvi d'energia o perque s'ha apagat sol.

El cas es que ara quan l'engege m'apareix aquest missatge d'error. La pantalla negra i amb lletres blanques:

Minimal BASH. like line editing is supported. for the first word, TAB lists possible command completios. anywhere else TAB lists the possible completions of a device/filename.

grub>


Que he de fer, presione TAB i m'apareixen una llarga llista de comands, pero no sé el que he de fer per a continuar la instal·lació.O... cancelar-la i tornar al ubuntu d'abans!!!


Agrairia molt la vostra col·laboració

Gràcies

---

### Post by papapep on 2009-05-20
El que jo faria, és desar les dades importants (com intentes fer a l'altre fil) i, un cop fet, reinstal·lar de cero l'Ubuntu, respectant la partició /home al reinstal·lar, dient-li que ni la toqui ni la formati.

---

### Post by loles on 2009-05-20
hola!

aixo que hem dius no se molt be com fer-ho. pots explicarmeu detalladament?

amb un livecd accedisc a les dades de la particio pero no les de home, com puc instal·lar l'ubuntu conservant les dades de home? eixa opcio apareix clara???


ara el que hem passa (despres d'haver iniciat amb un live cd) es que passa la pantalla eixa del grub i es queda en la primera pantalla de l'ubuntu. fique el meu nom i la contrasenya i es queda en la pantalla rosa.

ara que puc fer??? amb l'anterior actualitzacio ja em va passar i vaig ficar unes ordres i es va continuar la instal·lacio, pero ja he ficat les mateixes i no funciona...

---

### Post by papapep on 2009-05-20
> aixo que hem dius no se molt be com fer-ho. pots explicarmeu detalladament?


Si volguessis reinstal·lar, en el moment que l'instal·lador et pregunta si vols agafar tot el disc dur o fer un particionat manual, se li ha de dir que es vol fer manual. 
Suposant que tinguis dues particions (una per / i una altra per al /home) més la d'intercanvi, li hauries de dir que formati la que correspon a / però que no toqui ni formati la /home a fi de mantenir les teves dades i configuracions que hi tens dins. 
Fet això, l'instal·lador hauria de continuar i, en acabar, t'hauries de trobar el sistema plenament funcional amb els teus fitxers i dades del /home intactes. 

Si no tens clar com fer el particionat de manera manual, busca alguna referència a internet, que n'hi ha un munt, no és complicat però, com moltes coses, si no s'ha fet sembla qui-sap-què.

[Aquí]("http://www.guia-ubuntu.org/index.php?title=Instalaci%C3%B3n_est%C3%A1ndar"), en trobaràs una de prou interessant.

---

