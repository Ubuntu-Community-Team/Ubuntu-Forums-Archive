---
title: "Problemes amb CmapTools en Ubuntu Linux"
date: 2010-04-03
forum: Catalan Team
---

### Post by aperezb on 2010-04-03
CmapTools és una eina per fer mapes mentals i conceptuals, crec que de codi obert, però segur gratuïta, prou utilitzada en l'àmbit educatiu.

Dons bé, venia fent-la servir en una altra distribució (Linkat) però he hagut un problema amb CmapTools en Ubuntu Linux 64bits: La finestra d'edició no presentava informació de cap mena ni la capsa d'edició a dins d'ella.

Com que no dec ser l'únic, escric aquest missatge.

Mercès a "yothere" i "ollenotna"
 (a [http://ubuntuforums.org/showthread.php?t=879568](http://ubuntuforums.org/showthread.php?t=879568))
citant a "Markus"
 (a [https://answers.launchpad.net/ubuntu/+question/18055](https://answers.launchpad.net/ubuntu/+question/18055))
el vaig poder arreglar:

El CmapTools incorpora un jre a /(path_to_IHMC_CmapTools)/jre
Si tenim instal·lat un jre (jo tinc el de sun java 6 instal·lat amb synaptic) i esborrem o reanomenem la carpeta (directori) jre a dins del directori de IHMC_CmapTools, el problema desapareix.

Serveix almenys en
CmapTools 4.16 en Ubuntu 7.10
CmapTools 5.03 and Ubuntu 9.10

Àngel

---

