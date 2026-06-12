---
title: "No puedo desbloquear el puerto 27015"
date: 2008-04-22
forum: Argentina Team
---

### Post by SLA_leandrin on 2008-04-22
Holas.

Estuve tratando de desbloquear el puerto 27015 (para poder jugar al CS, claro...), por ahora infructuosamente. Por eso espero que algún entendido me de una mano.

Primero que nada, tengo un router D-Link DSL-500B, y ahí le hice un forward a los puertos, de la siguiente manera:
[[img]http://xs126.xs.to/xs126/08172/roter_cfg963.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs126&d=08172&f=roter_cfg963.png)

Luego, en la configuración  del iptables le agregué lo siguiente:

```
 sudo iptables -A INPUT -p tcp --dport 27015 -j ACCEPT
```

Cuando hago iptables -L:

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.1.1          anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       0    --  anywhere             255.255.255.255     
DROP       0    --  anywhere             192.168.1.255       
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
LSI        0    -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Input' 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:27015 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:27015 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.2          192.168.1.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.1.2          192.168.1.1         udp dpt:domain 
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       0    --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       0    --  255.255.255.255      anywhere            
DROP       0    --  anywhere             0.0.0.0             
DROP       0    --  anywhere             anywhere            state INVALID 
OUTBOUND   0    --  anywhere             anywhere            
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:6881:6889 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:27000:27015 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:27000:27015 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:27020:27039 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:27020:27039 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4662 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4662 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4672 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4672 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1200 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:1200 
LSI        0    --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       0    --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  anywhere             anywhere            
LOG        0    --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere    
```

Obiamente no cazo un fulbo, pero no parece liberado el puerto...

Lo probé en la página [http://www.canyouseeme.org/ ]("http://www.canyouseeme.org/")y nada.


Al que pueda ayudar... gracias!

---

### Post by SLA_leandrin on 2008-04-22
Nadie che?? Lo postearé in english entonces...

---

### Post by faktorqm on 2008-04-22
Estas muy apurado? Pasaron 5 horas entre post y post.....

Para mi esta mal en el linksys. Tenes que ponerle el 27015 en los 4 lugares como tenes en el de 1200. Por las dudas si no lo sabias, cada vez que reinicias el sistema la configuracion que vos pones "a mano" se borra, para evitar eso tenes que armar un script y ponerlo en el inicio, pero capaz ya sabes todo esto. Con respecto a la linea que abris el puerto, me parece que esta todo ok. Salu2!!

p.d.: que hiciste con la pagina? salu2!

---

### Post by clasificado on 2008-04-22
Desconozco completamente la configuración por IPTables directamente

Pero GuardDog siempre me ha dado buenos resultados, y de alguna forma se arregla para recuperar las reglas al reiniciar la machine.

clasificado

---

### Post by Hei Ku on 2008-04-22
Tambien podes probar firestarter. Es solo un frontend para Iptables y anda joya.

---

### Post by SLA_leandrin on 2008-04-23
> **faktorqm said:**
> Para mi esta mal en el linksys. Tenes que ponerle el 27015 en los 4 lugares como tenes en el de 1200.


Mmmmm sabés que ya lo había probado, pero igual nada... esas indicaciones las saqué de la página [www.portforwarding.com](www.portforwarding.com) 


> **Hei Ku said:**
> Tambien podes probar firestarter. Es solo un frontend para Iptables y anda joya.

Yap, de hecho todo el chorro que sale cuando hago el comando iptables -L es la configuración que le puse en el firestarter.

> **clasificado said:**
> Desconozco completamente la configuración por 
IPTables directamente

Pero GuardDog siempre me ha dado buenos resultados, y de alguna forma se arregla para recuperar las reglas al reiniciar la machine.

clasificado

Voy a ver que eso de GuardDog, no lo conocía, lo pruebo y aviso.

PD: la página, por ahora en la nada... mucho laburo che, por suerte.

---

### Post by Hei Ku on 2008-04-23
En firestarter fijate de activar la politica despues de agregarla. Y un buen lugar para fijarte es la lista de eventos bloqueados. Con eso podes saber si es que el problema esta en iptables, o es antes, en el router.

---

