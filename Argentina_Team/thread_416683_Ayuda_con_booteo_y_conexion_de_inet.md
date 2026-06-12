---
title: "Ayuda con booteo y conexion de inet"
date: 2007-04-21
forum: Argentina Team
---

### Post by sebas.rhcp on 2007-04-21
Yo tengo el modem USB Huawei de Arnet, lo logre configurar y todo funca muy bien :)

Mi problema es que cada vez que inicia ubuntu yo tengo que escribir estos comandos:

sudo modprobe br2684
sudo br2684ctl -c 0 -b -a 0.33
sudo ifconfig nas0 up

y despues para que se conecte...

sudo pppd call adsl

Lo que necesito es que estos comandos los haga automaticamente :o 

Gracias

---

### Post by Al_maverick on 2007-04-21
probaste de poner estos comandos en un script /etc/init.d?

Es una opcion, aunque no estoy seguro de como seria exactamente.

---

### Post by sebas.rhcp on 2007-04-21
Explicame como porque nose, en estos momentos estoy tambien instalando el ntfs-3g

---

### Post by sebas.rhcp on 2007-04-23
nadie sabe como hacer que estos 3 comandos los haga automaticamente al bootear?

sudo modprobe br2684
sudo br2684ctl -c 0 -b -a 0.33
sudo ifconfig nas0 u

---

### Post by kowal on 2007-04-23
Editá el archivo /etc/rc.local y agregá ANTES de **exit 0** los comandos

PD: No hace falta ponerle "sudo" adelante. También podés agregar el otro comando para que arranque conectado (pppd call adsl).

---

### Post by Tinchio on 2007-04-23
te haces un script en e init.d por ejemplo
mas o menos asi

sudo gedit /etc/init.d/internet

dentro del archivo poner

#!/bin/bash

sudo modprobe br2684
sudo br2684ctl -c 0 -b -a 0.33
sudo ifconfig nas0 u

guardas, cerras y le das permisos

sudo chmod +x /etc/init.d/internet

reinicias y fijate si andubo

---

### Post by sebas.rhcp on 2007-04-23
Gracias voy a probar y comento :)

---

### Post by sebas.rhcp on 2007-04-25
> **kowal said:**
> Editá el archivo /etc/rc.local y agregá ANTES de **exit 0** los comandos

PD: No hace falta ponerle "sudo" adelante. También podés agregar el otro comando para que arranque conectado (pppd call adsl).

Listo, solucionado. Ahora Ubuntu arranca conectado a internet. Gracias :)

---

