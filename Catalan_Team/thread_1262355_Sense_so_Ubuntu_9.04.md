---
title: "Sense so Ubuntu 9.04"
date: 2009-09-09
forum: Catalan Team
---

### Post by migjorn on 2009-09-09
Hola a tothom.

Acabo d'instal·lar la Jaunty 9.04 neta en el portàtil de la meva dona, i no puc escoltar cap audio, ni tan sols en la pantalla d'entrada.

He seguit [això]("http://ubuntuforums.org/showthread.php?t=1130384"), bàsicament la primera entrada, però després d'una bona estona barallant-me no he pogut aconseguir res.

Així, doncs, seguint les instruccions del post ho tinc tot configurat amb el pulse audio server, però quan vaig la prova de so (Sistema/preferencies/so), no passo d'un so pràcticament inaudible.

Si faig lspci:

> 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

Alguna idea de per on seguir?

Gràcies de bestreta.

---

### Post by cadebou on 2009-09-27
Si el portàtil és un HP mini i no sents so pels altaveus però sí pels auriculars, tens aquest bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942)

---

### Post by PatrickVogeli on 2009-09-27
ens hauries de dir quin portatil es!

---

### Post by papapep on 2009-09-27
Una opció és que tinguis algun control del mesclador al mínim o emmudit. Si executes a un terminal "alsamixer" veuràs tots els controls i podràs verificar si tots estan com han d'estar.

---

