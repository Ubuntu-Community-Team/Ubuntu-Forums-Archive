---
title: "NFS bloqueja l'escriptori"
date: 2007-08-21
forum: Catalan Team
---

### Post by guillemsola on 2007-08-21
Hola

Fa dies que tinc un enllaç a un disc mitjançant NFS a una altre màquina. No habia experimentat cap problema per accedir-hi fins que des de fa poc quant ho intento fer l'escriptori de l'ubuntu es penja. Li costa molt de respondre i desapareixen totes les icones. Fins que no tanco el nautilus no recupero l'escriptori.

Per altra banda mentre succeeix aixó arrenco un terminal i accedeixo sense problemes als disc muntat amb NFS i puc manipular els fitxers.

Tinc un 7.04 instalat desde 0 pero recordo que amb l'anterior versió també vaig tenir problemes similars amb un muntatge SAMBA.

Alguna idea? 
gràcies

---

### Post by guillemsola on 2007-08-22
Posteriorment no arrencava bé l'escriptori al reiniciar la màquina i el mateix sistema ha decidit no carregar la paperera a l'escriptori (m'ha informat amb una finestreta groga).

Jo per si un cas he desabilitat tots les icones de l'escriptori amb gconf-editor. Ara sembla més estable però encara es penja quant li rota, sobretot al intentar entrar amb nautilus al muntage samba d'un petit NAS o al dics NFS.

salut!

---

### Post by CarlesOriol on 2007-08-22
Sona a problema físic de la xarxa i no del protocol.

Com ho tens conenctat?

---

### Post by guillemsola on 2007-08-22
Uhmm jo havia descartat problemes de conexionat pq faig servir tota aquesta infraestructura amb altres màquines sense problemes.

De fet ho tinc tot centralitzat en un switch de 8 ports.

Ara posats a sospitar de hardware potser m'inclinaria per la tarjeta de xarxa de la màquina 

```
Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
```

 encara que en general funciona bé, de fet l'accés a internet no presenta cap problema, igual que les coneccions ssh a altres màquines, mai hi he vist cap incidència

Salut!

---

