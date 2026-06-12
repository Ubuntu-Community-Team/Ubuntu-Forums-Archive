---
title: "No es mostra la informació de la pantalla als paràmetres del sistema"
date: 2017-11-07
forum: Catalan Team
---

### Post by tafol on 2017-11-07
Hola, Intentava saber la resolució de pantalla que tinc i en els paràmetres del sistema > Pantalles es mostra un missatge que diu: "No s'ha pogut obtenir la informació de la pantalla". A què pot ser degut?
Adjunte captura del missatge i dels detalls del meu sistema.
Salutacions i gràcies.

---

### Post by wgarcia on 2017-11-08
Possiblement s'ha remogut el paquet "unity-control-center" del sistema.

Prova:

```
sudo apt install unity-control-center --reinstall
```

a veure si ho soluciona.

---

### Post by tafol on 2017-11-08
Doncs sí que era això. És curiós perquè fins i tot havia desaparegut el resultat "Pantalles" del cercador d'aplicacions (del dash) i ara amb l'ordre que em comentes, torna a aparèixer. Moltes gràcies.
Nota: cal marcar d'alguna manera com a resolt aquest fil?

---

### Post by wgarcia on 2017-11-09
Sí, gràcies, va bé que ho marquis com a "Solved" per si algú/na cerca pel mateix problema.

---

