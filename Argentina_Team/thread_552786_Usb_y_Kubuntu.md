---
title: "Usb y Kubuntu"
date: 2007-09-16
forum: Argentina Team
---

### Post by Duckzito on 2007-09-16
Les cuento el problema que estoy teniendo, hace dos dias empece con el kubuntu a meterme un poco en esto, todo venia de 10, hasta que se me dio por conectar la camara digital, kubuntu hizo el montaje correspondiente, entro a la memoria de la camara............y de repente, se frizzo todo, y empezaron a parpader las luces de capslock y scrolllock, reinicio, pruebo otra vez, y volvio a pasar :S. Entonces probe con un celular y me hizo lo mismo! 
Segun lei este tipo de error, con las luces parpadeando indica un problema grave en el kernel, pero no tengo ni la mas minima idea de por donde empezar a tocar! a alguien le paso algo similar? Gracias!

---

### Post by leo_rockway on 2007-09-17
Lo mio no va a ser de mucha ayuda... yo uso kubuntu y nunca me paso nada igual. Cuando conecto mi camara la monta y me abre el digikam y me pregunta si quiero bajar las fotos.

Yo tb tengo entendido que lo de las luces parpadeando es un kernel panic (pero no podria aseverarlo, nunca me paso).

me parece que lo mejor es que describas tu hardware, para ver si alguien tiene hardware similar a vos e ir descartando eso por partes.

---

### Post by Duckzito on 2007-09-17
> **leo_rockway said:**
> Lo mio no va a ser de mucha ayuda... yo uso kubuntu y nunca me paso nada igual. Cuando conecto mi camara la monta y me abre el digikam y me pregunta si quiero bajar las fotos.

Yo tb tengo entendido que lo de las luces parpadeando es un kernel panic (pero no podria aseverarlo, nunca me paso).

me parece que lo mejor es que describas tu hardware, para ver si alguien tiene hardware similar a vos e ir descartando eso por partes.

Gracias por la respuesta, en cuanto al hardware, es un P4 2.4Mhz, mother MSI chipset via, con sonido y red onboard, la placa de video es una radeon 9600pro agp, un disco ATA y un disco SATA, lo unico a lo que le podria hechar la culpa es al chipset, pero lo raro es que se monta la unidad y llego a ver las cosas, y ahi muere!

---

### Post by por100pre1 on 2007-09-17
Haz una copia de respaldo de tu carpeta de usuario en un medio externo, y si estas usando Feisty, instala este otro kernel:

```
sudo aptitude install linux-image-lowlatency
```

Esto agrega un kernel diferente a Ubuntu Feisty, uno de baja latencia. Prueba entonces si hay alguna diferencia al usar este otro kernel.

---

