---
title: "Hola, sóc nova! Petit problema amb VLC"
date: 2009-02-24
forum: Catalan Team
---

### Post by Picarona on 2009-02-24
Hola a tots i permeteu-me donar-vos les gràcies. Fa tot just un mes que vaig decidir donar el pas i instal.lar Ubuntu. Gràcies a vosaltres he pogut anar solucionant molts dels dubtes que tenia sobre les aplicacions, com instal.lar i demés.

Però tinc un petit problema amb VLC que és el següent:

Quan vull obrir un fitxer (amb "Open File") que es troba al DVD, al CD-Rom o al segon disc dur només em deixa accedir a la meva carpeta d'usuari i al primer disc dur.

Com ho puc solucionar? Segur que és una bajanada però per més que he buscat no trobo resposta.

Moltes gràcies a tots!!!

---

### Post by papapep on 2009-02-24
Benvinguda al fòrum, Picarona

Abans que res, et demanaria que fessis una bona llegida al [fil pels nouvinguts]("http://ubuntuforums.org/showthread.php?t=599965"), per veure com intentem funcionar.

Respecte el que preguntes, doncs no tenim massa informació. El segon disc és intern? l'has formatat? amb quin sistema de fitxers??

Executa això a un terminal, i enganxa el resultat aquí mateix, si us plau:

```
sudo fdisk -l /dev/sd*
```

```
cat /etc/fstab
```

---

