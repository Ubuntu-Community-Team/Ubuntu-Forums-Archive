---
title: "no funciona wifi en dell INSPIRON 640m"
date: 2007-03-08
forum: Argentina Team
---

### Post by zspikes on 2007-03-08
buenas gente!!! este problema es ajeno jeje. Resulta q moleste mucho a un amigo para q ponga ubuntu en su dell INSPIRON 640m, y le gane por cansancio, la cosa es q no le anda wifi y yo soy el responsable. Asiq si me ayudan a solucionar esto me salvan las papas :P

Alguien sabe como lo puedo hacer andar? mil gracias!!!

---

### Post by beuno on 2007-03-08
Tendrias que averiguar el modelo de la placa wifi.
(System > Hardware Information) o (Device Information).

Buscala y con eso te podemos indicar para donde disparar.

---

### Post by zspikes on 2007-03-09
ahi me fije y dice "pro/wireless 3945ABG network" la placa es una pci de intel.

---

### Post by spg76 on 2007-03-09
> **zspikes said:**
> ahi me fije y dice "pro/wireless 3945ABG network" la placa es una pci de intel.

Los drivers para ese adaptador están en [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

---

### Post by zspikes on 2007-03-09
buenisimo, tb habia encontrado los drivers en la pagina de intel, pero como se instalan? :S

gracias!

---

### Post by ariel on 2007-03-11
Los drivers (modules) que necesitas ya vienen junto con el kernel de edgy por default, es raro que no te ande.

Estos pibes tuvieron un problema que puede ser el tuyo (pasaba en dapper, creo que en edgy ya no pasa):
[http://ubuntuforums.org/showthread.php?t=214463](http://ubuntuforums.org/showthread.php?t=214463)


Si el LED de "wifi" de la dell prende (cuando activas el switch), lo mas probable es que tengas el driver correcto ya instalado, y un problema de configuracion.

Para ver si la placa esta funcionando, tira un 'iwconfig' en una consola. Al menos una de las interfaces te deberia salir como IEEE 802.11.

Si es asi, una manera facil de configurar la interfaz (y escanear la redes wireless disponibles) is wifi-radar (instalalo via synaptics); te va a mostrar todas las redes disponibles y la configuracion es muy intuitiva.

Suerte!

---

### Post by zspikes on 2007-03-12
vamos a probar, como dije, la dell es de un amigo y tengo q esperar a verlo para probar cualquier cosa.
El flaco tiene edgy, pero es dapper actualizado digamos, vos decis q instalandole edgy de una se soluciona? Le pasamos la pc a un profe y no se q toco q ahora la ve a la placa, y ve las redes y todo pero no se conecta, rarisimo.

bueno, sigo escuchando sugerencias, gracias!!!

---

