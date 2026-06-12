---
title: "CUPS, SAMBA y FIRESTARTER"
date: 2007-01-17
forum: Argentina Team
---

### Post by MeduZa on 2007-01-17
todo imprimiar bien y bla bla bla en la red hasta que puse firestarter y ahora no encuentro donde decirle que deje imprimir a las pc de mi LAN :confused: 

todo anda perfecto sin firestarter asi que eso no es, tiene que ser en las iptables o algo por el firestarter pero no lo encuentro :-k 
alguno que me tire una soga?

---

### Post by godzeus on 2007-01-17
yo tengo otro problema con firestarter, no me deja agregar reglas,la opcion aparece en gris, y para poder conectar el amule sin Low-id tengo que parar el firewall. Alguien me podra dar una manito.?

---

### Post by jpmorelli on 2007-01-17
> **MeduZa said:**
> todo imprimiar bien y bla bla bla en la red hasta que puse firestarter y ahora no encuentro donde decirle que deje imprimir a las pc de mi LAN :confused: 

todo anda perfecto sin firestarter asi que eso no es, tiene que ser en las iptables o algo por el firestarter pero no lo encuentro :-k 
alguno que me tire una soga?

Seguramente tenes que abrir los puertos ( decirle al firestarter que no los bloquee ) por los que van los datos de las impresoras, si son del tipo Jetdirect usan el puerto 9100, si son compartidas por Windows del estilo están instaladas en otra máquina con Windows, habría que averiguar que puerto usan si es que lo hacen (???)
Si averiguo algo te chiflo.

---

### Post by MeduZa on 2007-01-17
> **jmorelli said:**
> Seguramente tenes que abrir los puertos ( decirle al firestarter que no los bloquee ) por los que van los datos de las impresoras, si son del tipo Jetdirect usan el puerto 9100, si son compartidas por Windows del estilo están instaladas en otra máquina con Windows, habría que averiguar que puerto usan si es que lo hacen (???)
Si averiguo algo te chiflo.

O sea yo veo e imprimo en todas las pc windochiton pero los windochotin no pueden hacerlo en mi porque el firewall los frena (si apago el firewall todo anda a la perfeccion)
ahora veo lo del puerto 9100, porque yo le abri solo los de samba que vienen por defecto pero parece q no es eso, porque sigue sin andar y para imprimir o lo que sea tengo que apagar el firewall

---

### Post by jpmorelli on 2007-01-17
> **MeduZa said:**
> O sea yo veo e imprimo en todas las pc windochiton pero los windochotin no pueden hacerlo en mi porque el firewall los frena (si apago el firewall todo anda a la perfeccion)
ahora veo lo del puerto 9100, porque yo le abri solo los de samba que vienen por defecto pero parece q no es eso, porque sigue sin andar y para imprimir o lo que sea tengo que apagar el firewall

Aaaah, son los otros los que no pueden imprimir en tu impresora que está bajo Linux, ok mejor, porque el puerto que usa CUPS en Linux es el 631 , por lo menos para administración.
Date una vuelta por aca [http://home.swbell.net/berzerke/printing.html]("http://home.swbell.net/berzerke/printing.html")
es viejito pero esta piola el tutorial.

---

