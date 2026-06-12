---
title: "Abiri puertos"
date: 2007-11-14
forum: Argentina Team
---

### Post by benzema on 2007-11-14
Bueno la cosa es asi,no puedo abir programas de torrents o p2p porque tengo los puertos cerrados,probe con firestarter aver si habia alguna opcion para abirlo pero no nada tengo ubuntu gutsy gibon , me conecto a internet por medio de la tarjeta de red,saludos


Edit: Lo siento escribi mal el titulo es que estaba mirando para otro lado ..

---

### Post by por100pre1 on 2007-11-14
```
sudo iptables -A INPUT -p tcp --dport *numero-de-puerto* -j ACCEPT
```

o

```
sudo iptables -A INPUT -p udp --dport *numero-de-puerto* -j ACCEPT
```

---

### Post by benzema on 2007-11-14
> **por100pre1 said:**
> ```
sudo iptables -A INPUT -p tcp --dport *numero-de-puerto* -j ACCEPT
```

o

```
sudo iptables -A INPUT -p udp --dport *numero-de-puerto* -j ACCEPT
```


Gracias ,ya lo habia usado pero sigue sin abrirlo .saludos

---

### Post by por100pre1 on 2007-11-14
> **benzema said:**
> Gracias ,ya lo habia usado pero sigue sin abrirlo .saludos

Verifica si tienes un cortafuegos en un router o módem. Puede que tengas que abrir los puertos en algún aparato. :-k

---

### Post by benzema on 2007-11-14
> **por100pre1 said:**
> Verifica si tienes un cortafuegos en un router o módem. Puede que tengas que abrir los puertos en algún aparato. :-k


No tengo modem ni router, me conecto por el adaptador de red osea meto el cable,pongo mi ip los dns la puerta de enlace en configuracion de red y ya tengo internet ..

---

### Post by margori on 2007-11-14
Estimado Benzema:

Fijte si tu servidor de internet no te da un IP privado. Contanos cual es tu servidor, porque puede ser que te este filtrando paquetes.

---

### Post by benzema on 2007-11-14
> **margori said:**
> Estimado Benzema:

Fijte si tu servidor de internet no te da un IP privado. Contanos cual es tu servidor, porque puede ser que te este filtrando paquetes.

Es uno bien trucho, se llama COESA ,y es de mi localidad suipacha,buenos aires, a por cierto es una cooperativa,y creo que le provee internet a ellos telecom

---

### Post by ScottBernard on 2007-11-15
Pero tu pc la ke tiene Ubuntu, esta directamente conectada con internet, o se conecta a otra pc ke te provee internet?

---

### Post by benzema on 2007-11-15
> **ScottBernard said:**
> Pero tu pc la ke tiene Ubuntu, esta directamente conectada con internet, o se conecta a otra pc ke te provee internet?


Directamente, tengo el cable que baja de la antena

---

### Post by matlnx on 2007-11-17
Como dijeron en otro post fijate si tu ip es privada o publica... eso lo haces en una terminal mediante el comando #ifconfig y fijate el ip que aparece...

si es del rango por ejemplo 192.168.X.X o 10.X.X.X o 172.X.X.X (lo hago bien general porque no se que conocimientos tenes, espero no ofender a nadie)... si no es de ese rango es muy probable que tengas una publica. Si es privada como las mecionadas anteriormente te deben estar filtrando desde el proveedor.

Sds
MatLnx

[EDIT] perdon me olvide de poner que en las X puede existir cualquier valor.

---

### Post by faktorqm on 2007-11-18
hola benzema! busca en este mismo sub-foro, que yo conteste la misma pregunta a otro chabon que pregunto lo mismo que vos y le hice un mini-tuto de como abrir el puerto con el firestarter. una vez que aprendes uno, depsues te salen todos. salu2!

---

### Post by fscodelaro on 2007-11-18
La explicacion de faktorqm esta aca:

[http://ubuntuforums.org/showthread.php?t=577416&page=2](http://ubuntuforums.org/showthread.php?t=577416&page=2)

---

### Post by benzema on 2007-11-18
> **fscodelaro said:**
> La explicacion de faktorqm esta aca:

[http://ubuntuforums.org/showthread.php?t=577416&page=2](http://ubuntuforums.org/showthread.php?t=577416&page=2)

oka saludos luego probare

---

