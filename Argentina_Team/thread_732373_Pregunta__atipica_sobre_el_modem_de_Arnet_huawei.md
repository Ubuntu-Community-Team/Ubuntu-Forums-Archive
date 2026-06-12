---
title: "Pregunta  atipica sobre el modem de Arnet huawei"
date: 2008-03-22
forum: Argentina Team
---

### Post by UBUjuan on 2008-03-22
Hace 2 años que tengo el modem huawei smartAX MT810, lo probé con Ubuntu, openSuSE y Debian y me anda bien. Pero desde hace unas horas que las lucen de "power" y "link" estan comportándose algo extraño, como si parpadearan, pero no igual que la luces de "data" (conectado a internet), o sea creo que mi modem usb se va a ir para simpre y voy a tener que comprarme otro. La pregunta es ¿cuál? uso el servicio de Arnet Highway y me gustaria que me recomienden los usuarios de arnet que modem es mejor.
Otra duda con este modem es que al desconectarlo y conectalo nuevamente ya no puedo conectarme a internet, probé los pasos "inversos", es decir: 
1)killall pppd 
2)ifconfig nas0 down 
3)kill br2684ctl (el numero de pid) 
4)rmmod br2684 y luego los pasos tipicos para conectarme, pero no se conecta ¿por que es esto? ¿que es lo que hago mal?

---

### Post by leonardo83 on 2008-03-22
Yo que trabajo para arnet te recomiendo pidas el huawei 882 dual, que es el mas simpatico de los duales, ademas lo conectas por placa y sale con fritas.
Tene cuidado que no te enchufen el pirelli dual que es una **** !!!

Saludos :)

---

### Post by megatux on 2008-03-23
Yo lo habia conseguido, si recuerdo bien, la cuestion era que la segunda deteccion quedaba como nas1 en lugar de nas0.
Cuando pueda voy a volver a intentarlo.

---

### Post by guisheca on 2008-03-23
Yo tengo el huawei mt882 dual y me anda de 10, según tengo entendido cualquier modem que se conecte por placa de red es mejor. Sobre todo en linux, ya que la gran mayoría de las placas de red son reconocidas de forma inmediata. Entonces sólo conectás el modem y listo ya anda todo (previa configuración claro)

---

### Post by leonardo83 on 2008-03-25
> **guisheca said:**
> Yo tengo el huawei mt882 dual y me anda de 10, según tengo entendido cualquier modem que se conecte por placa de red es mejor. Sobre todo en linux, ya que la gran mayoría de las placas de red son reconocidas de forma inmediata. Entonces sólo conectás el modem y listo ya anda todo (previa configuración claro)

Y CLAAAAAAAAA, lo que yo decia, ese modem es una masa, ademas no tenes que hacer nada casi por placa, pppoe y sale asi nomas :)
Yo estoy viendo porque no me deja reinstalar Ubuntu 7.04. Despues que actualice me aparecieron dos ubuntu en el grub y ninguna arranca .... :(

Saludos

---

