---
title: "Identificació tarja wifi integrada"
date: 2009-12-17
forum: Catalan Team
---

### Post by lluisalguero on 2009-12-17
Hola,
a veure si em se explicar. A partir de voler fer anar la wifi del meu portàtil, he estat llegint un futimé de webs i per fi l'he pogut fer anar, però em queda un petit dubte.

Al fer un iwconfig

```
lluis@lluis-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
lluis@lluis-laptop:~$ 

```

el que seria suposo la tarja wifi (eth2) no em surt res, quan a tots el tutorials he vist que dona detalls sobre la tarja, xarxa que està connectada, etc.

al fer lspci en una de les línees trobo
```
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

i ara la meva pregunta: està funcionant la meva tarja wifi amb un driver genèric? o bé, com puc fer per a que el iwconfig em reconegui la tarja.

Moltes gràcies a tots...mentre espero la vostra resposta, continuo investigant per si trobo alguna cosa

P.D.: es que estic fent una auditoria de seguretat de la meva xarxa :-\"

---

