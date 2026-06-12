---
title: "VMware y Win98 - Como compartir la red?"
date: 2007-03-31
forum: Argentina Team
---

### Post by quaid on 2007-03-31
Como va? 
Bueno hace 2 o 3 dias instale Vmware server , instale win98 ahi adentro y todo bien, el problema es q no puedo compartir la red, ni en bridge n ien nada, siempre me salta q no existe el vmnet0. 

Hay algo q en ubuntu tengio q hacer con la red para q la vea el vmware?

edit: 
Ya solucione ese tema
Lo solucione coriendo de nuevo el congil.pl de vmware sol oq esta vez de las 500 q lo corri andubo bien de una

Ahora el preoblema es q no puedo conectar en red a win98 osea ya no me sale el cartel de eth0 no se conecto y bla bla. Pero ambas pcs no se ven, va, ambos OS no se ven y es la unica manera q tengo de pasarle archivos.

Alguna sugerencia?

---

### Post by jpmorelli on 2007-04-01
Hay un lugar dentro de los seteos de la máquina virtual ( en la configuración ) donde le decís que carpetas son las que shareas, una vez que hagas esto arrancas la máquina , y desde Ubuntu Servidores de Redes vas a ver que esa carpeta compartida aparece. Obvio que en Ubuntu tenes que tener cargado el paquete smbclient ( samba client ) para que se vean win y lin.
Suerte !

---

### Post by quaid on 2007-04-02
ya logre hacer q se vean

Solucion para q se vean:
Lo de ambas redes lo solucione xq el vmware me buscaba vmnet0, no se xq pero yo n ola tenia, cosa q si tenia la vmnet1 y 8 , asi q setie a vmware para q use la 1 y listop, ambas pcs se vieron.

Ahora mi problema es q linux ve la de win98 y accede y puede escribir ahi, el problema es q la de win98 ve la carpeta de linux pero dice q no tiene permisos y etc..

Donde se tocan estos permisos? cuando la compartis pude "q pasen todos" y sigue sin caminar.

---

