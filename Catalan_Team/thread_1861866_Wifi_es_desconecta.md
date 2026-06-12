---
title: "Wifi es desconecta"
date: 2011-10-16
forum: Catalan Team
---

### Post by venusfenix on 2011-10-16
buenas,
estic usant ubuntu 10.04, i em trobo que des de fa uns mesos, la wifi es desconnecta al cap d'unes hores, al principi, era només quan tirava de bateria, però cada dia mes, dura menys la connexió i tan li dona si el portàtil esta a xarxa com a bateria.
sospito que es un tema de bateria, encara es l'original, i te ja com uns 6 anys. ja n'he tingut algun problema amb l'adaptador de xarxa (corrent) i només el fet de cambiar-lo por un de nou, i els problemes s'han arreglat. ara el meu problema, es que una bateria nova ACER, costa uns 125 euros+ 30€ de transport, total que per 200€ podria comprar-me un netbook. Però abans de fer decisions i despeses, volia saber si algú de vosaltres a experimentat aquest tipus de problema, i així confirma o no si poc vindre de la bateria o d'origen per software.

moltes gracies,

---

### Post by wgarcia on 2011-10-16
Tens algun símptoma que la bateria s'exhaureix?

Si més no jo diria que la vida útil d'una bateria sol ser inferior a 6 anys. Si el deixes endollat no es desconnecta de la wifi?

---

### Post by venusfenix on 2011-10-16
com deia, al principi només em passava quan estava en modo bateria, i no passava quan estava endollat a xarxa, la veritat es que la bateria esta durant menys d'una hora, i segons amb quines aplicacions, en pot durar només 20 minuts. el tema s'estan escurçant mica a mica. aquest cap de setmana, ja ha començat a desconnectar-se la wifi encara que estigui endollat. per altre banda, el gestor d'energia marca mancança de bateria al cap de pocs minuts, i això ja passa des de fa uns mesos.
estic bastant acostumat a veure això, a la feina tenim portàtils amb leasing per 2 anys, i noto quan s'exhaureix la bateria, però la meva pregunta anava si ubuntu pot estan desconectan la wifi degut al baix rendiment de la mateixa, o baix nivel de corrent. si es així, hauré de comprar una nova, sino, hauré de buscar la causa en un altre lloc.

gracies,

---

### Post by wgarcia on 2011-10-17
Certament pot ser un problema independent de la bateria. Per això convindria saber quin tipus de targeta wifi hi ha al sistema. Per fer això obre una terminal i entra:

lspci | grep -i network

i et mostrarà el model de la targeta wifi.

---

### Post by venusfenix on 2011-10-17
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

tinc instal·lat el net5211 amb el Ndiswrapper.

alguna idea?

---

### Post by venusfenix on 2011-10-22
estic buscant per internet la manera de millora o arreglar aixo que em passa. estic llegit sobre el madwifi, i sembla ser la millor opcio per usuaris amb atheros wifi. ara, la meva pregunta es com desinstal.lar el ndiswrapper (ubuntu center?) i com instal.lar el madwifi.

merci,

---

