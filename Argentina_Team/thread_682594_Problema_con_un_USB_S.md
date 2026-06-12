---
title: "Problema con un USB :S"
date: 2008-01-30
forum: Argentina Team
---

### Post by niko_3100 on 2008-01-30
Tengo una compaq v3415 y uno de los puertos usb me esta andando mal o no se si se quedo como trabado... es un puerto usb 2.0 pero en xp me lo reconoce como 1.1 :mad: Y en feisty no me levanta el pendrive y le conecto un hub usb de 4 bocas y tampoco lo levanta, es como si estubiera trabado o algo porque trata de levantar los dispositivos pero nada... Alguien sabe donde estan los archivos que controlan los usb??  Es un chipset nvidia nvidia mcp51 usb controller, lo saque desde el sysinfo. Por lo menos para ver si es un problema del usb o de feisty, la notebook todavia la tengo con garantia pero no se que me diran por el feisty y por el xp que tienen instalado cuando venia con el vista...

---

### Post by clasificado on 2008-01-30
1) Llamalos por lo del SO y cerciorate :)
Seria bastante injusto que no puedas elegir.

2) fijate con el lsusb (en un terminal) que devuelve el estado de los dispositivos.
Entre enchufado y desenchufado vas a ver las diferencias.
O postealas por acá y te decimos que onda

clasificado

---

### Post by niko_3100 on 2008-01-30
no conocia el lsusb, nono aparentemente me fije que hacia el LiveCD y parece ser un problema de mi feisty instalado porque en el LiveCD me lo tomo joya aca dejo lo que me tira el lsusb con un mouse y el pendrive kingston enchufados:

Bus 002 Device 003: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Me toma solo el mouse :S

---

### Post by rojojuan on 2008-01-31
Con el comando lsusb tampoco me aparece el pen drive. Con el programa "sys info" veo que esta reconocido como SCSI. Podés ver esto también en Sistema-Preferencias-Información del Hardware.

---

