---
title: "problema con script"
date: 2007-12-02
forum: Argentina Team
---

### Post by sdn8904 on 2007-12-02
Hola.

En mi casa uso arnet y utilice una guia para instalar el modem. Para conectar internet hay que poner algunos comandos en el terminal. la guia dice que se puede automatizar todo modificando el archivo rc.local o creando un script que contenga lo siguieente (es casi lo mismo que hay que agregar en el archivo rc.local):

#! /bin/bash

sudo modprobe br2684

sudo br2684ctl -c 0 -b -a 0.33

sudo ifconfig nas0 up

sudo pppoe-start

sudo exit 0

El problema es qui internet no se conecta automaticamente (con Ubuntu 7.04 lo hacia) ni puedo utilizar el script.

Cuando apago la pc aparecen unas lienas y una dice algo asi:
not found le.br2684                                         (fail)

Y cuando quiero ejecutar el script aparece el mismo error y se cierra el terminal. Pero cuando escribo los comandos en el terminal los toma sin ningun problema. Ojala puedan ayudarme.

---

### Post by Mauro22 on 2007-12-02
[FONT=monospace][FONT=Tahoma,Sans,Arial,Helvetica,sans-serif]Hola!


Trata probando sacandole el sudo exit 0

:confused:
[/FONT][/FONT]

---

### Post by sdn8904 on 2007-12-02
Ya probé. El problema está en el primer comando, que cuando lo quiero ejecutar de forma automática da error

---

### Post by User21 on 2007-12-03
Es tan solo una idea, quizas no tiene nada que ver, pero deberias cargarte el modulo desde el archivo de inicio de modulos!
```
sudo gedit /etc/modules
```

y alli, en la ultima linea, escribir br2684 .
Si no viene al caso, disculpas! Solo quería ayudar! u_U

---

