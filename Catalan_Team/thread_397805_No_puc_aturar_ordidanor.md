---
title: "No puc aturar ordidanor"
date: 2007-03-31
forum: Catalan Team
---

### Post by manelolesa on 2007-03-31
Tinc instal•lat UBUNTU 6.10 i  alhora de aturar-lo es queda clavat en la pantalla amb el logotip  i la barra de progrés. Sempre el tinc que aturar am el botó.

Algú s'ha trobat amb  aquest problema.

Salut

---

### Post by CarlesOriol on 2007-03-31
Prem Ctrl+Alt+f8 a veure que diu.

---

### Post by manelolesa on 2007-04-02
Donç no em dona tems de veure res ja que per la consola começa a corre un scroll de paraules que no puc aturar ni amb pausa ni control break ni mandanges.

Penso que deu ser algun problema amb el tema del PowerACPI.

Salut

PD. Una coseta vaig probar de instalar el SUSE i aquest si que xutaba bé.

---

### Post by manelolesa on 2007-04-04
Be, el problema es va solucionar al treure una tarja PCI, concretament una Capturadora de Vídeo. 
En l'engegada del Ubuntu, vaig veure alguna coseta que em va fer sospitar que  ACPI Power i la Capturadora de Vídeo feien servir la mateixa interrupció IRQ i aixó li feia mal a l'Ubuntu .

Pere fi puc deixar de  matxucar el botó del Power.

Salut

Manel

---

### Post by patrickfromspain on 2007-04-04
per a solucionar aixo podries probar a arrancar amb l'opcio irqpoll al grub.

---

