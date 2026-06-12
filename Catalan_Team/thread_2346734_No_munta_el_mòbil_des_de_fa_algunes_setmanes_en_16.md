---
title: "No munta el mòbil des de fa algunes setmanes en 16.04"
date: 2016-12-18
forum: Catalan Team
---

### Post by jinglada on 2016-12-18
No recordo exactament quant temps fa. Va començar muntant-se i desmuntant-se aleatòriament, però des de fa unes setmanes ja no el veu. Pensant que es tractava del connector del mòbil vaig anar a una botiga d'informàtica i el connecten al w2 i es munta. No se m'havia acudit. Entro en w2 al meu portàtil i es munta. He cercat per internet i he trobat això: [http://www.taringa.net/post/linux/16922861/Conectar-movil-Android-a-Ubuntu-mediante-MTP.html](http://www.taringa.net/post/linux/16922861/Conectar-movil-Android-a-Ubuntu-mediante-MTP.html) i això: [https://ubuntuforums.org/showthread.php?t=2312327&highlight=go-mtpfs](https://ubuntuforums.org/showthread.php?t=2312327&highlight=go-mtpfs), on precisament al migrar a 16.04 es va solucionar el problema. Voldria l'opinió dels experts abans de tocar res. Gràcies.

---

### Post by wgarcia on 2016-12-19
No sé si serà el mateix, però a mi em passa recentment que de vegades tots els dispositius USB (discos externs, memòries, mòbils) es deixen de muntar, i la solució és eliminar una carpeta i reiniciar, perquè aquesta carpeta es regenera automàticament. La carpeta en qüestió es:

```

.config/nautilus

```

El que faig és, des d'una terminal i des de la meva carpeta d'inici:

```

mv .config/nautilus .config/nautilus.bak

```

i reinicio. A partir d'aquí els dispositius es tornen a muntar i la carpeta es recrea. No tinc cap personalització al nautilus, suposo que si se'n té, amb aquesta solució es perdria. Tampoc he investigat més perquè això passa i si hi ha algun informe d'error al respecte

---

### Post by jinglada on 2016-12-19
Gràcies, wgarcia!

Va funcionar una mica unes hores!

---

