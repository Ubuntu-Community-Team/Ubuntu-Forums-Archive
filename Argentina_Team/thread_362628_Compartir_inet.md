---
title: "Compartir inet"
date: 2007-02-15
forum: Argentina Team
---

### Post by Ciego_SPU on 2007-02-15
Como comparto internet a una PC con windows? ya tilde el boton del firestarter pero no pasa nada... la conexion viene por USB de un router Amigo CA80U funcionando... y la otra maquina se conecta derecho a esta...

---

### Post by lavaramano on 2007-02-16
> **Ciego_SPU said:**
> Como comparto internet a una PC con windows? ya tilde el boton del firestarter pero no pasa nada... la conexion viene por USB de un router Amigo CA80U funcionando... y la otra maquina se conecta derecho a esta...

digamos, que ahora tenes red, pero no logras compartir internet?
despues me fijo si encuentro un script de unas lineas que te sirve para compartir internet, siempre use eso y nunca me fallo.

---

### Post by Ciego_SPU on 2007-02-16
Uy dale, la verdad que me vendria al pelo!!

---

### Post by lavaramano on 2007-02-16
> #### Script que configura iptables ####
#!/bin/bash

iptables --table nat --append POSTROUTING --out-interface **ppp0** -j MASQUERADE
iptables --append FORWARD --in-interface **eth0** -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward

donde dice **ppp0**, deberias cambiarlo al device que se conecta a internet
y donce dice **eth0** deberias ponerle al device que esta conectado a la red (gralmente suele ser eth0, pero a veces no, asi que fijate bien)

guardalo como iptablesconf.sh en /etc/init.d y dale permisos de ejecucion ( chmod +x o chmod 755)
despues lo ejecutas con sudo y deberia salir andando.


pd: este script lo saque navegando, no lo hice yo. 

tambien hay otro script para configurar iptables, pero me parece excesivamente largo al pedo. con estas 3 lineas funciona lo mas bien.

saludos

---

### Post by BlackHero on 2007-02-17
muy buen script =)

---

