---
title: "Allotjar Web en desktop o Server?"
date: 2010-02-03
forum: Catalan Team
---

### Post by Manelitu on 2010-02-03
Hola Ubuntaires !

Tinc que albergar 2 pàgines webs en un ordinador normal i corrent, Intel Core 2Duo-2GBRAM-160GBHD, però nose si instal·lar la versió server (que la desconec totalment) o la versió desktop que es deixa remanar més.

Si instal·lo la versió server amb els paquets LAMP, suposo que serà més segura i robusta però per el contrari menys managable si haig de trateixar amb ella.

Si instal·la la versió desktop i despres afegixo apache,sql,php; nose si tindre algun problema de robustesa o seguretat.

El ordinador només faria aquesta funció.

Que opineu companys?

---

### Post by kukat on 2010-02-03
La versió Server et dona a escollir els serveis que donarà la màquina quan estas instal·lant la distribució: correu, dns, apache, etcètera etcètera, i aquesta no porta sistema gràfic per defecte (no se si hi ha opció per escollir-ho ne la instal·lació, però jo el vaig instal·lar i no tenia entorn gràfic).

Una vegada instal.lat el Server, pots instal.lar l'entorn gràfic que vulgues. Si només és per allotjar webs, jo optaria per no posar-li entorn, o per posar-li'n un lleuger.

Si esculls Desktop, una vegada instal·lat tendries que posar-li els serveis desitjat, però ja et dic, Ubuntu no és com Windows XP i Windows Server. Perfectament en un Desktop pots fer un Server com qualsevol!! ;)

Salut!

---

### Post by grind_lant on 2010-02-05
efectivament, si no et vols complicar la vida i no saps com fer anar bé el terminal et poses la 'desktop' i llavors instal·les l'Apache o el que sigui i apa.

---

### Post by PellRoja on 2010-02-06
Em sembla que els dos el mateix sistema, l'únic que varia és la instal·lació

---

### Post by Manelitu on 2010-02-08
Bé doncs, posaré el desktop.

Alguna suggerencia sobre les particions? O les deixo per defecte com les instal·la el ubuntu?

---

### Post by tanreb20 on 2010-02-09
Una bona idea seria modificar-ho per tal qeu et posi la /var en una separada, o la /home.

Aixi si canvies el sistema, o actualitzes, no perdries les pagines, no?

---

