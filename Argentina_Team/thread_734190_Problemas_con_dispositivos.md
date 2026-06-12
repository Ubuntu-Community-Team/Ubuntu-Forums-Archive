---
title: "Problemas con dispositivos"
date: 2008-03-24
forum: Argentina Team
---

### Post by MaReaDo^ on 2008-03-24
queria saber dos cosas:

1)como puedo deshabilitar mi conexion firewire
2)como puedo poner prioridad a mis interfaces de red, cuando pongo ifconfig eth0 metric 2, no funciona

desde ya gracias por su ayuda

---

### Post by faktorqm on 2008-03-24
Hola, para desactivar el firewire mas facil desactivalo del Bios.
La metrica de las conexiones de las placas de red nada tienen que ver con la prioridad. Que queres hacer? salu2!

---

### Post by MaReaDo^ on 2008-03-24
vos en windows en coenxiones de red avanzado bla bla tenes para poner como un orden de prioridad, entonces yo pongo hamachi primero asi me lo reconoce como la red, si no algunos programas y juegos, te reconocen primero la red fisica en vez de la virtual ¬_¬
en internet busque y decia que la metrica era la prioridad, pero si vos decis que no, te creo xD
la cosa es que supongo que si win tiene para poner prioridad de interfaces de red, ubuntu tambien, aunque sea por consola

---

### Post by faktorqm on 2008-03-25
O sea, la metrica es el numero de saltos que tenes que dar antes de llegar a donde queres llegar. Asi, si tenes por ejemplo un gateway a 1 salto, y otro a 3, primero va a usar el que esta mas cerca, por obvias razones.
La prioridad es otra cosa, es para hacer balance de carga o cbq o priq, y/o esas cosas. Eso lo que hace es, por ejemplo, si viene un paquete p2p mandalo a la primera placa, y limita el trafico ftp a 30kb/s en la segunda placa de red, y bloquea todo el trafico ssh en los dos. Asi varias cosas. No confundir con firewall ni nada por el estilo.

Dicho esto, me creo en condiciones de explicar lo que haces vos en windows. Vos le pones una metrica mayor a la placa de red "real", entonces obviamente el SO va a buscar la ruta que tenga mas cerca, utilizando la virtual del hamachi primero. Es una tramoya digamos, pero por ejemplo cada vez que queres irte afuera de tu red, primero busca en la virtual, como no lo encuentra recien ahi va a la real, y eso tiene un retardo en el tiempo. capaz sea minimo, no se, pero existe.

Si lo queres hacer en linux, el comando es ifconfig, ahora a mi tampoco me deja, aun dando de baja la interfaz primero. que raro! el comando que usaste esta bien, pero no me deja. (ni c t ocurra hacerlo con sudo/root)

igual yo probaria algo asi: ifconfig eth0 <direccion ip> netmask <mascara> broadcast <direccion de broadcast> metric 1 up

Salu2!!

---

### Post by MaReaDo^ on 2008-03-25
que raro. tampoco me funciono
no se como sera
encima no se si hay algun archivo de conf para hacerlo con editor de texto :S

sudo ifconfig vmnet1 172.16.197.1 netmask 255.255.255.0 broadcast 172.16.197.255 metric 4 up
SIOCSIFMETRIC: Operación no soportada


supongo que te debe decir lo mismo

---

### Post by Hei Ku on 2008-03-25
el archivo a tocar es /etc/network/interfaces

---

### Post by MaReaDo^ on 2008-03-25
el archivo ese no tiene la metrica y me aparecen los dos dispositivos fisicos nomas :(

---

### Post by faktorqm on 2008-03-26
si, es ese archivo, hei ku una vez mas grosso en redes :D

escribi en un terminal "man interfaces" que ahi te explica todo. salu2!!

---

### Post by MaReaDo^ on 2008-03-27
el fireware ya lo saque en el menu de la bios
y encontre el archivo tipo interfaces pero de los vmnet pero lo abre solo lectura hasta con gksudo, terminal de root, bla bla
como puedo hacer para modificarlo?

---

### Post by faktorqm on 2008-03-27
creo que te deberia funcionar esto:

```
sudo gedit /etc/network/interfaces
```

Salu2!

---

### Post by MaReaDo^ on 2008-03-27
eso me funciona con ese archivo, pero con el archivo /etc/vmware/vmnet1/dhpcblablabla
si lo abro con sudo me sigue diciendo solo lectura :P

---

