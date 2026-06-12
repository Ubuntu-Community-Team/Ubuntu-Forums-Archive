---
title: "atheros AR5B95 no connecta a Internet"
date: 2009-10-11
forum: Catalan Team
---

### Post by rayand65 on 2009-10-11
Tinc un portàtil Packard Bell KAV60, amb processador Intel@Atom N270, el xip per a connexió és un atheros AR5B95, i no dóna senyals de vida per a connectar-se a Internet amb l'Ubuntu. Podríeu dir-me els passos a seguir per a fer que funcioni?. Si us plau sigueu didàctics i específics, sense donar res per suposat

Gràcies

---

### Post by papapep on 2009-10-11
Sinó vaig errat, amb aquest xip et cal el mòdul (controlador) ath9k. En teoria el paquet linux-backports....uhm...no has dit quina versió de l'ubuntu tens instal·lada, oi? Faria falta saber-ho per a afinar el tret. Per cert, has provat amb la beta de la 9.10 a veure si et funciona? no seria res estrany.

---

### Post by rayand65 on 2009-10-12
> **papapep said:**
> Sinó vaig errat, amb aquest xip et cal el mòdul (controlador) ath9k. En teoria el paquet linux-backports....uhm...no has dit quina versió de l'ubuntu tens instal·lada, oi? Faria falta saber-ho per a afinar el tret. Per cert, has provat amb la beta de la 9.10 a veure si et funciona? no seria res estrany.
Tinc instal·lada la versió 9.04. Dius que amb el paquet linux-backports puc trobar l'ath9k -en teoria. Com i on puc aconseguir aquest paquet? I quin és el procediment per a instal·lar-los? Vull dir, per exemple, vaig amb aquest paquet a sistema-administració-controladors del maquinari? No sóc un expert informàtic, tan sols un usuari, i certs termes se m'escapen.

---

### Post by papapep on 2009-10-12
Efectivament, si vas a Sistema>Administració>Controladors de maquinari podria ser que allà puguis activar el controlador per a aquesta placa. Si allà ho veus, activa'l i a veure si va. Hauries de reiniciar l'ordinador un cop activat, per veure si el carrega correctament.

Si no et va així, prova a anar al Synaptic (Sistema>Administració>Gestor de paquets Synaptic) i instal·la des d'allà el paquet *linux-backports-modules-jaunty*. 
Un cop instal·lat, torna a reiniciar i a veure si funciona.

---

