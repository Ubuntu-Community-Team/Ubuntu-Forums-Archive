---
title: "TDT woxter micro 50 usb no el detecta kaffeine"
date: 2009-08-16
forum: Catalan Team
---

### Post by pepeponce on 2009-08-16
Hola m'e comprat un adaptador usb per veure la tele en un portatil pero m'agradaria probar en la maquina amb ubuntu pero el kaffeine no el detecta i no se si sa de montar.
siusplau avere qui em pot ajudar.

gracies

---

### Post by papapep on 2009-08-16
Fes a un terminal, quan tinguis el bitxo aquest USB endollat:

```
lsusb
```

i enganxa aquí el que et surti.

---

### Post by pepeponce on 2009-08-16
Gracies per respondre tan rapid .Surt aixo:

Bus 002 Device 004: ID 10b8:1e80 DiBcom 
Bus 002 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 001: ID 0000:0000  

Penso que el bicho es el "DiBcom"

---

### Post by papapep on 2009-08-17
Per tot arreu on he buscat referències, kernel, V4L, etc, no trobo el model exacte que et llista l'lsusb. N'hi ha de molt semblants, però no el mateix. 
Has repassat la configuració de DVB-T del Kaffeine a veure si té alguna opció per a triar-lo?

---

