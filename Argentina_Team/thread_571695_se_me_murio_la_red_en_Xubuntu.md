---
title: "se me murio la red en Xubuntu"
date: 2007-10-09
forum: Argentina Team
---

### Post by ideafix on 2007-10-09
Buenas gente, no se q paso, pero de un dia para el otro no tengo mas red en Xubuntu, y por lo tanto, no tengo mas internet!. Recibo internet por la red, desde un switch. Y en este tema estoy frito, porq mucho no entiendo de estas configuraciones de IP y todo eso. Una lastima, porq desde q lo habia instalado funcionaba todo bien nunca tuve q tocar nada, entraba y y estaba todo ok. Si me pueden explicar q hacer para que funque todo de nuevo y no tener q entrar al wi... para navegar! ja. Y otra cosa, ya q estoy, si se puede instalar algo, como un iconito para ver cuando hay y cuando no hay conexion?? Gracias!!

---

### Post by manzuk on 2007-10-09
Desde una consola hace:
```
ifconfig
```

Te va a dar información de las interfaces de red que tengas activadas.
Copiá y pegá lo que te tire.

Hacete también ya que estamos:
```
ping 216.239.51.99
```

Copiar/Pegar y vemos que está pasando.

---

### Post by ideafix on 2007-10-09
ifconfig larga esto

eth0      Link encap:Ethernet  HWaddr 00:16:EC:7B:88:83  
          inet6 addr: fe80::216:ecff:fe7b:8883/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49034 (47.8 KiB)  TX bytes:6380 (6.2 KiB)
          Interrupt:22 Base address:0xb000 

eth0:avah Link encap:Ethernet  HWaddr 00:16:EC:7B:88:83  
          inet addr:169.254.8.15  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0xb000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1000 (1000.0 b)  TX bytes:1000 (1000.0 b)

 ping 216.239.51.99 larga esto

PING 216.239.51.99 (216.239.51.99) 56(84) bytes of data.
From 169.254.8.15 icmp_seq=2 Destination Host Unreachable
From 169.254.8.15 icmp_seq=3 Destination Host Unreachable
From 169.254.8.15 icmp_seq=4 Destination Host Unreachable
From 169.254.8.15 icmp_seq=6 Destination Host Unreachable
From 169.254.8.15 icmp_seq=7 Destination Host Unreachable
From 169.254.8.15 icmp_seq=8 Destination Host Unreachable
From 169.254.8.15 icmp_seq=10 Destination Host Unreachable
From 169.254.8.15 icmp_seq=11 Destination Host Unreachable
From 169.254.8.15 icmp_seq=12 Destination Host Unreachable
From 169.254.8.15 icmp_seq=14 Destination Host Unreachable
From 169.254.8.15 icmp_seq=15 Destination Host Unreachable
From 169.254.8.15 icmp_seq=16 Destination Host Unreachable
From 169.254.8.15 icmp_seq=18 Destination Host Unreachable
From 169.254.8.15 icmp_seq=19 Destination Host Unreachable
From 169.254.8.15 icmp_seq=20 Destination Host Unreachable
From 169.254.8.15 icmp_seq=22 Destination Host Unreachable
From 169.254.8.15 icmp_seq=23 Destination Host Unreachable
From 169.254.8.15 icmp_seq=24 Destination Host Unreachable
From 169.254.8.15 icmp_seq=26 Destination Host Unreachable
From 169.254.8.15 icmp_seq=27 Destination Host Unreachable
From 169.254.8.15 icmp_seq=28 Destination Host Unreachable
From 169.254.8.15 icmp_seq=30 Destination Host Unreachable
From 169.254.8.15 icmp_seq=31 Destination Host Unreachable
From 169.254.8.15 icmp_seq=32 Destination Host Unreachable
From 169.254.8.15 icmp_seq=34 Destination Host Unreachable
From 169.254.8.15 icmp_seq=35 Destination Host Unreachable
From 169.254.8.15 icmp_seq=36 Destination Host Unreachable
From 169.254.8.15 icmp_seq=38 Destination Host Unreachable
From 169.254.8.15 icmp_seq=39 Destination Host Unreachable
From 169.254.8.15 icmp_seq=40 Destination Host Unreachable
From 169.254.8.15 icmp_seq=42 Destination Host Unreachable
From 169.254.8.15 icmp_seq=43 Destination Host Unreachable
From 169.254.8.15 icmp_seq=44 Destination Host Unreachable
From 169.254.8.15 icmp_seq=46 Destination Host Unreachable
From 169.254.8.15 icmp_seq=47 Destination Host Unreachable
From 169.254.8.15 icmp_seq=48 Destination Host Unreachable
From 169.254.8.15 icmp_seq=50 Destination Host Unreachable
From 169.254.8.15 icmp_seq=51 Destination Host Unreachable
From 169.254.8.15 icmp_seq=52 Destination Host Unreachable
From 169.254.8.15 icmp_seq=54 Destination Host Unreachable
From 169.254.8.15 icmp_seq=55 Destination Host Unreachable
From 169.254.8.15 icmp_seq=56 Destination Host Unreachable
From 169.254.8.15 icmp_seq=58 Destination Host Unreachable
From 169.254.8.15 icmp_seq=59 Destination Host Unreachable
From 169.254.8.15 icmp_seq=60 Destination Host Unreachable
From 169.254.8.15 icmp_seq=62 Destination Host Unreachable
From 169.254.8.15 icmp_seq=63 Destination Host Unreachable
From 169.254.8.15 icmp_seq=64 Destination Host Unreachable
From 169.254.8.15 icmp_seq=66 Destination Host Unreachable
From 169.254.8.15 icmp_seq=67 Destination Host Unreachable
From 169.254.8.15 icmp_seq=68 Destination Host Unreachable
 y lo corte porq no paraba mas je

---

### Post by manzuk on 2007-10-10
Ok, ahora veamos esto:
Desde una consola hace:
```
cat /etc/network/interfaces
```
Y copiame lo que te tira.

Hace tambíen
```
cat /etc/resolv.conf
```
y pega lo que escupa.

No te digo de hacer nada todavía porque quiero ver que está pasando.
Espero la info nomas!

---

### Post by faktorqm on 2007-10-10
hola, para mi es tan simple como que el cable no tiene conexion. lo probaste en otro lado? tenes ip fija o dhcp? salu2!

---

### Post by ideafix on 2007-10-10
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


 cat /etc/resolv.conf 
search mshome.net
nameserver 192.168.0.1

> faktorqm  	
Re: se me murio la red en Xubuntu
hola, para mi es tan simple como que el cable no tiene conexion. lo probaste en otro lado? tenes ip fija o dhcp? salu2!

El cable tiene conexion. Es mas, estoy en windows escribiendo esto desde la misma computadora. Cuando cambio a Xubuntu no tengo mas conexion. Gracias

---

### Post by manzuk on 2007-10-10
OK, hagamos una pausa y te cuento que es cada cosa de lo que hicimos.

Al principio con el comando **ifconfig** obtuvimos información de los dispositivos de red que estaban activos en tu equipo. Activo no quiere decir que tengan conexión a la red.
*(Nota: si quisiera ver todos los dispositivos de red, activos o no, hubieramos usado **ifconfig -a**)*

Nos interesó solamente los que nos dijo sobre **eth0**, ya que suele ser la placa de red. Fijate lo que te tiro:

```
eth0 Link encap:Ethernet HWaddr 00:16:EC:7B:88:83
inet6 addr: fe80::216:ecff:fe7b:8883/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
```

y fijate lo que tira en general:

```
eth0 Link encap:Ethernet  HWaddr 00:11:09:D1:DD:0F
**inet addr:192.168.1.3  Bcast:192.168.1.255 Mask:255.255.255.0**
inet6 addr: fe80::211:9ff:fed1:dd0f/64 Scope:Link
```

Lo que está en negrita es la dirección IPv4, y es lo que te está faltando a vos (a menos que utilices solo IPv6, cosa media rara).

Ahora, que hicimos con **ping 216.239.51.99**?
Intentaste mandarle paquetes a esa dirección IP (que es de uno de los servidores de Google). El mensaje que recibiste (*From 169.254.8.15 icmp_seq=2 Destination Host Unreachable*)significaba en gaucho "no puedo llegar a esa dirección".

Para que fue el **cat /etc/network/interfaces**.
Primero: el comando **cat** imprime el contenido de un archivo. Si el contenido es texto, entonces imprime texto.
Ok, entonces con **cat /etc/network/interfaces** obtuvimos el contenido del archivo "/etc/network/interfaces". De vuelta nos fijamos en las líneas que contengan eth0.

```
**auto** eth0
iface eth0 inet **dhcp**
```

Por lo marcado en negrita nos damos cuenta que la placa intenta obtener una dirección IP automáticamente a través de DHCP (y debería obtener también la dirección de un servidor DNS).

Con **cat /etc/resolv.conf** vimos el contenido de ese archivo.
```
nameserver **192.168.0.1**
``` significa que la dirección del servidor DNS es esa.

Bueno, explicación terminada. Ahora te digo mi hipótesis.
Por alguna razón parece que tu placa no está obteniendo la IP por DHCP.

Dijiste que en Windows todo anda bien. Entonces hagamos esto:
En Windows, desde "Simbolo del sistema" (Inicio > Todos los programas > Accesorios > Simbolo del sistema), escribí:

```
ipconfig /all
```

y postea lo que te tire.
Saludos!

---

### Post by ideafix on 2007-10-10
Configuración IP de Windows

        Nombre del host . . . . . . . . . : desktop
        Sufijo DNS principal  . . . . . . :
        Tipo de nodo . . . . . . . . . .  : desconocido
        Enrutamiento habilitado. . . . . .: No
        Proxy WINS habilitado. . . . .    : No

Adaptador Ethernet Conexión de área local          :

        Sufijo de conexión específica DNS :
        Descripción. . . . . . . . . . .  : SiS 900-Based PCI Fast Ethernet Adap
ter
        Dirección física. . . . . . . . . : 00-16-EC-7B-88-83
        DHCP habilitado. . . . . . . . .  : No
        Dirección IP. . . . . . . . . . . : 192.168.0.11
        Máscara de subred . . . . . . . . : 255.255.255.0
        Puerta de enlace predeterminada   : 192.168.0.1
        Servidores DNS . . . . . . . . . .: 200.51.211.7
                                            200.51.212.7

---

### Post by Oktubre on 2007-10-10
Pareciera que en Windows no tenes habilitado el DHCP sino que tenes fija la IP.
[B]
DHCP habilitado. . . . . . . . . : No
Dirección IP. . . . . . . . . . . : 192.168.0.11[/B]

Proba de fijarle la IP en el Ubuntu a ver que pasa o bien de habilitarle el DHCP en Windows.

Saludos,

---

### Post by manzuk on 2007-10-10
Exactamente como dice el amigo Oktubre, en Windows tenes IP fija.
Que vamos hacer? Configurar linux para que utilice una IP fija!

Vamos a editar un par de archivos de configuración; cada vez que queramos abrir un archivo para modificarlo, vamos a necesitar permisos de super usuario (root).
Para ejecutar algo con permisos de super usuario, debemos anteponer **sudo** al nombre del comando.

Bueno, manos a la obra!

Empecemos fijando la dirección IP para tu adaptador de red.
Desde una consola hacemos:
```
sudo nano /etc/network/interfaces
```
Editamos solo las lineas que contengan eth0.
Debería quedarnos algo asi:
```
iface eth0 inet **static**
address **192.168.0.11**
netmask **255.255.255.0**
```

[I]_Nota_: para guardar los cambios hacemos Ctrl + O y apretamos Enter
Para salir, Ctrl + X[/I]

Fijate lo que esta en negrita: el **static** es para que no usemos DHCP. Lo demás es la información que sacamos del Windows.

Ahora modifiquemos otro archivo; hacemos:
```
sudo nano /etc/resolv.conf 
```
para que qude algo asi:
```
nameserver 200.51.211.7
```

Perfecto, todo cambiado y salvado. Reinicia Xubuntu y contanos que pasa...

---

### Post by ideafix on 2007-10-10
che no paso naranja. Q macana :(

---

### Post by Oktubre on 2007-10-10
Que hiciste, le pusiste fijo el mismo IP que tiene en Windows?

Una vez que hiciste esto, al hacer ifconfig te aparece el IP asignado? 

Que pasa si le haces un ping a 192.168.0.1?

Saludos,

---

### Post by ideafix on 2007-10-11
> **Oktubre said:**
> Que hiciste, le pusiste fijo el mismo IP que tiene en Windows?

Una vez que hiciste esto, al hacer ifconfig te aparece el IP asignado? 

Que pasa si le haces un ping a 192.168.0.1?

Saludos,

ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:EC:7B:88:83  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ecff:fe7b:8883/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:489 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68479 (66.8 KiB)  TX bytes:4033 (3.9 KiB)
          Interrupt:21 Base address:0xb000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

 ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

y ahi se quedo... cuando lo corte me largo

--- 192.168.0.1 ping statistics ---
1790 packets transmitted, 0 received, 100% packet loss, time 1789698ms

---

### Post by Oktubre on 2007-10-11
Ahora que lo tenes configurado igual que Windows - suponiendo que el ping a 192.168.0.1 en Windows anda, chequealo por las dudas -, fijate si tenes algun filtro en Linux levantado.

Quizas tengas algun firewall sobre Linux y esta sea la causa del problema.

Saludos,

---

### Post by ideafix on 2007-10-11
Haciendo ping a 192.168.0.1 con 32 bytes de datos:

Tiempo de espera agotado para esta solicitud.
Tiempo de espera agotado para esta solicitud.
Tiempo de espera agotado para esta solicitud.
Tiempo de espera agotado para esta solicitud.

Estadísticas de ping para 192.168.0.1:
    Paquetes: enviados = 4, recibidos = 0, perdidos = 4
    (100% perdidos)

Esto me lo largo Windows.

---

### Post by Oktubre on 2007-10-11
Entonces no soporta ping el equipo 192.168.0.1. Busca en Windows un IP dentro de tu red que soporte ping y que te responda. 

Hace la prueba ahi y en Linux a ver que pasa.

Saludos,

---

### Post by ideafix on 2007-10-11
ni idea como hacerlo. Lo unico q se me ocurrio es probar con 192.168.0.11 y ahi responde el ping en los dos, pero no se si tiene algo que ver je. Como busco otro?

---

### Post by Oktubre on 2007-10-11
La 192.168.0.11 responde porque es tu misma maquina. Tenes otras maquinas conectadas a esa red? 
Si es asi fijate el IP de alguna otra y hacele un ping. Sino proba haciendo ping [www.google.com](www.google.com) (o al IP que te responda en Windows).

Saludos

---

### Post by Hei Ku on 2007-10-11
proba a hacer un ping al 200.51.211.7, que es el DNS. Generalmente, no siempre, tienen el ping habilitado.

Una pregunta mas: en Windows la conexion se habilita apenas empieza? No tenes que usar un discador ni nada de ese estilo?

---

### Post by ideafix on 2007-10-11
en windows:


Haciendo ping a 200.51.211.7 con 32 bytes de datos:

Tiempo de espera agotado para esta solicitud.
Tiempo de espera agotado para esta solicitud.
Respuesta desde 200.51.211.7: bytes=32 tiempo=503ms TTL=123
Respuesta desde 200.51.211.7: bytes=32 tiempo=471ms TTL=123

Estadísticas de ping para 200.51.211.7:
    Paquetes: enviados = 4, recibidos = 2, perdidos = 2
    (50% perdidos),
Tiempos aproximados de ida y vuelta en milisegundos:
    Mínimo = 471ms, Máximo = 503ms, Media = 487ms

en Xubuntu

connect: Network is unreachable

Al principio mencione, por ahi no me explique bien. Hay una compu qrecibe internet. De ahi va a un switch que distribuye a varias computadoras, entre esas la mia. O sea, tengo internet por la red. Cuando entro a Windows no toco nada. Abro el Mozilla y navego. Y lo mismo hacia en Xubuntu hasta q paso esto q no carga nada. No se si hay actividad de red porq no tengo un iconito que me diga si esta o no conectada, eso es otra cosa q queria saber como podia hacer (en Xubuntu)

---

### Post by ideafix on 2007-10-17
Se me ocurrio probar dos live cd, uno de ubuntu y otro de musix, para ver que pasaba (me acorde q cuando los habia probado por primera vez podia navegar en internet). Ahora pasa lo mismo q con xubuntu, no reconocen nada de red. ¿me queda como unica alternativa reinstalar?

---

### Post by santiagoward2000 on 2007-10-17
> **ideafix said:**
> Se me ocurrio probar dos live cd, uno de ubuntu y otro de musix, para ver que pasaba (me acorde q cuando los habia probado por primera vez podia navegar en internet). Ahora pasa lo mismo q con xubuntu, no reconocen nada de red. ¿me queda como unica alternativa reinstalar?

Hola Ideafix,
Mirá, no sé cómo solucionar tu problema, pero i con los LiveCD no anda tampoco, no creo que se solucione reinstalando...

---

### Post by ideafix on 2007-10-20
Solucionado gente!!!!! hice un camino facil: me meti en windows en la configuracion de tcp/ip, copie los numeros de ip, mascara, puerta de enlace, y los dns. En xubuntu, fui a aplicaciones-sistema-red, en la pestaña connections, doble clic en wired conecction, en configuration selleccione static IP adress y copie los numeros. Despues en la pestaña DNS agregue los numeros de DNS y listo.
Gracias a los q me explicaron y respondieron, aprendi un monton.

---

