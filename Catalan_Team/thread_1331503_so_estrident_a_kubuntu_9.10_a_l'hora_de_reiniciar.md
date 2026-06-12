---
title: "so estrident a kubuntu 9.10 a l'hora de reiniciar"
date: 2009-11-19
forum: Catalan Team
---

### Post by pepitu on 2009-11-19
Bones, aquest no sé si és un problema massa greu per al funcionament de l'ordinador però és molest. Cada cop que reinicio l'ordinador em fa un piiiip llarg i estrident abans d'apagar-se. Això ja em va passar amb la instal·lació, quan vaig reiniciar el sistema acabat de instalar, i em passa sovint, diria que no sempre, quan apago o reinicio l'ordinador. Tinc instal·lat Kubuntu Karmic.

A algú li passa el mateix? 

gràcies i salut!

---

### Post by orestesmas on 2009-11-20
Si, a mi també em passa, però només en 1 de 3 PC que tinc amb la karmic.

Per mi que és algun problema amb el Kernel, i concretament amb el mòdul que controla el so que es produeix a través de l'altaveu intern del PC, perquè el piiiip sona quan l'escriptori ja s'ha tancat, i el kernel està desactivant tots els subsistemes.

Com a problema addicional m'he trobat que l'autocompleció en un terminal de text "real" (no una consola dins les X) també emet pitos desagradables, cosa que deu estar relacionada amb l'anterior.

Ara se m'acut que podries provar de desactivar el mòdul de control de l'altaveu del pc (que es diu "pcspkr"), posant una línia que digui "blacklist pcspkr" (sense les cometes) dins el fitxer "/etc/modprobe.d/blacklist-altaveu.conf", i reiniciar. A veure si això resol el problema.

---

### Post by pepitu on 2009-11-20
Bé doncs, fins a nou avís, el tema està solucionat. El que he fet és editar l'arxiu que m'ha dit l'Orestes amb aquesta comanda al terminal:

```
kdesudo kate /etc/modprobe.d/blacklist-altaveu.conf
```

S'ha obert un fitxer en blanc i li he enganxat la línia: blacklist pcspkr

He desat, he reiniciat i no ha pitat.

Gràcies Orestes!

Salut

---

