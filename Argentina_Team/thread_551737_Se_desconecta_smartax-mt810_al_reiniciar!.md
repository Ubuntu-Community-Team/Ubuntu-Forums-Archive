---
title: "Se desconecta smartax-mt810 al reiniciar!"
date: 2007-09-15
forum: Argentina Team
---

### Post by User21 on 2007-09-15
Conseguí conectarme con Arnet y el dichoso Smartax-mt810 a través de este [COMO]("http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810"). Estuve navegando durante horas PERFECTAMENTE, pero cada que vez que reinicio, pierdo la configuración. Como hago para mantenerla ? El asistente de  pppoeconf me pregunto si quería iniciar la conexión junto al sistema, pero al reiniciar, LA VUELVO a perder. Como debo proceder??? AYUDA, Please.

Es acaso que Ubuntu pierde el soporte para ese modem cada vez que reinicia ? Como puedo resolver esta cuestion ???

---

### Post by faktorqm on 2007-09-15
hola, me parece que lo que vas a tener que hacer es un script que se ejecute cuando arranque el sistema con un par de instrucciones. lo que no se es con que instrucciones exactamente, a ver si alguien que sepa mas de bash scripting que yo le puede dar una mano. si no en un rato trato de averiguar algo. salu2!!

---

### Post by User21 on 2007-09-15
Lo resolvi de esta forma:
Cargue los modulos en el inicio (/etc/modules) 

[B]ueagle-atm
br2684
[/B]**br2684ctl -c 0 -b -a 0.33**

Y despues, en el escritorio, me hice un archivo con permisos de ejecucion, con estos comandos:

**sudo ****ifconfig nas0 up**
# Inicia la interfase de red nas0 (asi es en mi caso)
**sudo ****pppoeconf**
# Inicia la conexion tomando el nombre de usuario y  contraseña desde "
gedit /etc/ppp/pap-secrets
 gedit /etc/ppp/chap-secrets"
[B]sudo pon dsl-provider 

[/B]Le di permisos de ejecucion, e hice un enlace en el escritorio.
Al ejecutarlo me pide la password de sudo. Se supone que si lo cargo al inicio, en Sesiones,
me la pedira?? En fin, en cada inicio lo ejecuto y asi tengo internet. :(

---

### Post by Montsegur87 on 2007-09-15
tengo el mismo modem y con esto se conecta de una. al bootear.

Aca va mi /etc/rc.local.

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#Conexion a Internet
br2684ctl -c 0 -b -a 0.33
ifconfig nas0 up
pon dsl-provider

exit 0

```

---

### Post by User21 on 2007-09-16
**Perfecto! MUCHISIMAS GRACIAS! ;) Mi amigo se va a poner muy contento, JEJEJE :D**

---

