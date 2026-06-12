---
title: "Firefox"
date: 2022-10-14
forum: Catalan Team
---

### Post by jorto on 2022-10-14
Bona nit, he actualitzat l'ordinador de Ubuntu 20.04 al 22.04. El Firefox em funcionava perfecte però ara no sé m'obre ni aquest ni el Chrome. Ho intento però no fa res....pensa una estona i es penja. He intentat reinstal·lar però tampoc....sabeu que puc fer?

---

### Post by ffp on 2022-10-17
Hola,
Pots provar de executar firefox per terminal. Obre el terminal (Ctrl + Alt + T), escriu firefox pica enter, i a veure quins errors troba (els escriurà al terminal).
Lamentablement Ubuntu 22.04 ha passat el firefox des d'un .deb a snap, durant l'actualització ha de migrar les dades existents a snap, i sembla que a vegades falla.
Jo personalment vaig fer una instal·lació nova de firefox-esr, que no depèn de snap.

---

### Post by wgarcia on 2022-10-18
Potser sigui per algun problema de Wayland i  targeta gràfica. Prova d'iniciar la versió "Ubuntu a xorg" (ho pots escollir des de la pantalla inicial d'entrada de l'usuari) a veure si el Wayland és el problema.

---

