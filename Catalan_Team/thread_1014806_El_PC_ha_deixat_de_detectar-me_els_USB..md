---
title: "El PC ha deixat de detectar-me els USB."
date: 2008-12-18
forum: Catalan Team
---

### Post by Jayhawker on 2008-12-18
Inexplicablement, Ubuntu ha deixat de detectar-me els USB, de tal manera que quan connecto un memory stick no hi ha manera de passar informació perquè el PC ni s'entera. Què ha passat i com puc solucionar-ho?

---

### Post by lesergi on 2008-12-18
Per favor, connecta l'USB, espera't uns 5 segons i copia'ns el que et surt a la consola a l'executar 'dmesg' :wink:

---

### Post by Jayhawker on 2008-12-18
> **lesergi said:**
> Per favor, connecta l'USB, espera't uns 5 segons i copia'ns el que et surt a la consola a l'executar 'dmesg' :wink:

Consola és terminal?

Si és així, el que es repeteix sistemàticament és "device descriptor read/64, error -32" rere de cada usb.

---

### Post by lesergi on 2008-12-19
Correcte, consola és terminal.

Jo també vaig tenir eixe mateix problema, i després de calfar-me molt el cap i mirar en tots els llocs l'únic que em va funcionar va resetejar la BIOS llevant la pila, esperant uns segons i tornant-la a posar, d'aquesta manera els controladors de l'USB a la BIOS es reinicien.

Ja em contes!

---

### Post by Jayhawker on 2008-12-19
> **lesergi said:**
> Correcte, consola és terminal.

Jo també vaig tenir eixe mateix problema, i després de calfar-me molt el cap i mirar en tots els llocs l'únic que em va funcionar va resetejar la BIOS llevant la pila, esperant uns segons i tornant-la a posar, d'aquesta manera els controladors de l'USB a la BIOS es reinicien.

Ja em contes!

Moltes mercès per la resposta que penso tenir en compte. De tota manera, no estic gaire avesat a les interioritats dels ordinadors. Et faria res indicar-me aproximadament per on puc trobar la pila, o és fàcilment visible? Suposo que deu ser d'aquestes planes, metàl·liques, que semblen una pastilla una mica gran, oi?

Merci de nou.

---

### Post by lesergi on 2008-12-19
No és gens complicat. Està a la placa base i es veu a simple vista. Es gris i prou gran, hauràs de polsar una petita palanqueta perquè salte la pila.

---

