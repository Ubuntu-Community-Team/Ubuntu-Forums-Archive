---
title: "Problemes Ubunut + Vista"
date: 2009-08-21
forum: Catalan Team
---

### Post by kabardino on 2009-08-21
Hola a tots!
Us explico el meu problema per veure si alguna ànima caritativa té solució als meus problemas :p .

Fa un mes que tinc un nou portàtil “Acer serie aspire” (Proc. 2nuclis AMD, 4Gb memòria, 1Gb Gràfica ATI). Veia con Windows Vista pre-instal•lat, i.e., no tinc ni CD de Windows ni de drvers. 
Fa una setmana, vaig comença a buscar informació per instal•lar una partició amb el S.O. Ubuntu al meu PC conservant Windows (ja que necessito una partició amb Windows per treballar amb programes de CAD per els estudis, sinó no el tindria) i creia que estava preparat, però res més lluny…
Inicialment, el meu equipo venia amb 4 particions del disc; 2 petites amb els arxius de recuperació, y dos més grans para programes i dades.
La partició de dades la vaig transformar en la meva partició per a Ubuntu, fent-ne d’ella una ext3 per a /, una ext3 per a /home i la partició swap. Vaig acabar d’instal•lar Ubuntu i quan vaig reiniciar l’ordinador vaig haver de “recuperar “ Windows Vista.

Ara ve la part més “divertida”:
Una cop reparat Vista, el GRUB no m’apareixia, doncs vaig posar el CD d’Ubuntu i m’obligava a tornar a instal•lar-lo como si mai ho hagués fet, el vaig tornar a instal•lar, llavors va tornar a aparèixer el GRUB; vaig intentar tornar a entrar a Vista i em va demanar tornar a restaurar-lo i vaig dir que no.

Situació actual:
El GRUB no apareix, en el seu lloc m’apareix l’error 22 del GRUB. No puc accedir a Vista i a Ubuntu només puc accedir amb el CD i em segueix demanant que l’instal•li un cop més.

Llavors, que puc fer? se que no feu miracles, però si algú em pot fer un cop de mà seria de gran ajuda.

Moltes gràcies, i perdo per la parrafada.

---

### Post by SiscoGarcia on 2009-08-23
Aquesta seria una opció: [http://tinyurl.com/ldfwgz](http://tinyurl.com/ldfwgz)

Prova i ja diràs ;)

---

### Post by kabardino on 2009-08-24
El meu problema no és exactament que no pugui arregla el grub, sinó la instal·lació simultania dels dos sitemes operatius

---

### Post by SiscoGarcia on 2009-08-25
No sé si acabo d'entendre't, en qualsevol cas pots mirar amb l'editor de particions (GParted) del CD autònom com tens el disc dur.

Pel que dius encara conserves el Vista però no hi pots accedir, és cert? Si és així diria que es pot resoldre restaurant el grub; si no és així prova a reinstal·lar-ho un altre cop seguint [aquest manual]("https://wiki.ubuntu.com/CatalanTeam/Recursos/ArrencadaDualAmbWindows"), per exemple.

Ja diràs.

---

### Post by jaume69 on 2009-09-02
[QUOTE="Kabardino"]Inicialment, el meu equipo venia amb 4 particions del disc; 2 petites amb els arxius de recuperació, y dos més grans para programes i dades.
La partició de dades la vaig transformar en la meva partició per a Ubuntu, fent-ne d’ella una ext3 per a /, una ext3 per a /home i la partició swap. Vaig acabar d’instal•lar Ubuntu i quan vaig reiniciar l’ordinador vaig haver de “recuperar “ Windows Vista.[/QUOTE]
Pot ser el problema està que havies de crear partició nova i redimensionar les de Windows.

Ara venen amb tantes particions els PCs nous?..
Jo només tenia de série: C: , Recovery.

Per **Google** pots trobar o buscar algun programa o solució per recuperar el Grub windows(error 22).

---

