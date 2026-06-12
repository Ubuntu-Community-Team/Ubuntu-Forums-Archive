---
title: "Lentitud en la primera càrrega del firefox"
date: 2015-04-29
forum: Catalan Team
---

### Post by Ddac on 2015-04-29
Bones,

Acabo d'instal·lar ubuntu 14.04.2 en el meu maquinari (dell inspiron i7 12Gb ram). És un ordinador amb windows 8 instal·lat en el qual ja havia 5 particions prévies de fàbrica amb sistema de particionat GPT. 
Vaig particionar manualment el disc dur amb gparted i vaig instal·lar ubuntu (adjunto les dues captures de pantalla del gparted abans i després d'instal·lar ubuntu). Em trobo amb vàries coses a la vegada:
**Primer** que ara el windows em tarda el doble de temps a carregar (abans 20 segons i ara gairebé 45s, ubuntu 37s des del grub). No sé si hi deu haver algun problema en les particions o en el seu ordre.
**Segon**, em trobo que el firefox tarda uns 10 segons a carregar per primera vegada, mentre que la segona i successives vegades que l'executo tarda milèssimes). 

Em centro primerament amb el problema del firefox, (doncs el windows tampoc el faré servir massa tot i que em preocupa la baixada de rendiment en l'arrencada). Adjunto també dues captures (imatges 1 i 2) on mostro l'inici del firefox per primera vegada, executat des d'una terminal i una segona captura amb l'inici del firefox per segona vegada també executat des d'una terminal. Desconec la difrència de misstage així com el significat entre les dues captures (imatges 1 i 2)

P.D: Veient que en la part inferior de la finestra  del firefox m'apareixia un missatge amb el següent text: 'Mozilla firefox seems slow...to..start'  Learn how to speed it' vaig executar la proposta i em trobo amb que Firefox tarda una mica menys en executar-se per primera vegada (uns 8 segons ara). No ho entenc massa. 

Gràcies

---

### Post by wgarcia on 2015-04-29
A mi el Firefox també em triga uns 10 segons en carregar per primer cop, així que deu ser normal, potser com dius carrega molta cosa a memòria i per això triga tant.

---

### Post by Ddac on 2015-04-29
Ja t'entenc, tot i que se'm fa extrany perquè un amic, en un portàtil de fa 8 anys i amb linux mint, triga en arrencar el firefox encara no 3 segons. Potser és ubuntu que deu anar diferent. En canvi, el libre office es carrega bastant més ràpid quan ho faig per primera vegada, uns 4 segons.

---

### Post by wgarcia on 2015-04-30
Potser el Mint carrega el firefox a memòria a l'arrencada de l'usuari? Pot ser interessant investigar perquè triga el firefox, jo ho atribuïa a què és un programa que ha de llegir moltes configuracions, però potser sigui una altra cosa. Un experiment que pots fer és obrir el firefox a un usuari diferent que el teu, l'usuari visitant o un usuari nou, però si es tracta d'un ordinador nou no crec que sigui alguna cosa que tens al teu usuari que alenteixi l'arrencada.

---

### Post by Ddac on 2015-05-08
Ok, merci. Ja he deixat de preocupar-me per això. Entenc que deu ser normal. 

Gràcies de nou ;)

---

