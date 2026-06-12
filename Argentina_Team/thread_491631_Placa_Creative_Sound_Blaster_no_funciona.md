---
title: "Placa Creative Sound Blaster no funciona"
date: 2007-07-03
forum: Argentina Team
---

### Post by ombú on 2007-07-03
Agradeceré si alguien puede ayudarme con el siguiente problema
Tengo una Pc que cuenta con una placa de audio Creative sound Blaster modelo CT4500 (Slot ISA), y he instalado Ubuntu 7.04. El sistema no reconoce la placa de sonido, y en la web del fabricante de la placa solo figura el drive para Windows 95/98. Debo admitir que esta placa es incompatible con Linux?, hay alguna forma de solucionar este problema?
Desde ya muy agradecido 
Ruben

---

### Post by gepatino on 2007-07-03
Ruben, 

las placas isa no son detectadas automaticamente, pero las sound blaster deberian funcionar.

Desde una consola, proba cargar el modulo manualmente (si mal no recuerdo era sb16 o sblaster):

sudo modprobe sb16

luego de esto, en Sistema/Preferencias/Sonido, proba la configuracion del sonido de tu sesion.

Si todo esto funciona bien deberías levantar el modulo automáticamente al inicio. Me parece que se hacia con el comando 'depmod -a' pero hace mucho que no hago algo parecido.

---

### Post by ombú on 2007-07-15
Muchas gracias, probe con el comando SUDO MODPROBE SB, que me distes, y el sonido aparecio Ok, pero luego al intentar escribir el archivo de inicio para que el modulo se cargue automaticamente puse el comando SUDO DEPMOD -a  SB, y me dice "depmod comando desconocido". Hice algo mal?
Gracias Gabriel por tu ayuda,
Ruben

---

