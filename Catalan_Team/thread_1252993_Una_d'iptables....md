---
title: "Una d'iptables..."
date: 2009-08-29
forum: Catalan Team
---

### Post by anigwei on 2009-08-29
Hola bones,

Estic flipant de com una cosa tant senzilla m'està donant tants maldecaps!!

Em podeu donar una pista amb el tallafocs de casa? Comparteixo internet amb els veïns, i a més ara m'han donat una Fonera, l'he posat a la terrassa a veure si els veïns m'ajuden a pagar la factura d'internet, que no és barata ;)
Llavors, he tret l'Access Point que tenia pels veïns i he posat la Fonera, que té doble SSID i la situació serà la mateixa: SSID pels veïns i SSID d'Accés "condicional" ($$).

Us explico la situació:

+ Sortida Internet: 192.168.1.1 a eth0
+ Servidor/Firewall: 192.168.1.9 a eth0
+ Xarxa meva: 192.168.1.0/24

+ Xarxa Veins/Fonera: 192.168.2.0/24 eth1
+ Fonera WAN: Pilla el DHCP del servidor a eth1
+ Fonera LAN privada: 192.168.2.3
+ Servidor/Firewall: 192.168.2.1 a eth1
+ Sortida internet: 192.168.2.1 a eth1, el mateix servidor fa de router.

Em pensava que ho tenia solventat però avui jugant amb la FON m'he donat compte de que no: M'interessa separar les dues xarxes. O sigui, que 192.168.2.x no vegi a la 192.168.1.x.

Ja tenen DNS i sortida a internet pel servidor per eth1, llavors entenc que desde eth1 no és necessari "veure" la xarxa eth0 (tot i que a la pràctica internet vé per eth0).

Tinc política ACCEPT per defecte, i les regles que corresponen als veïns:

```

iptables -A INPUT -s 192.168.2.0/24 -i eth1  -j ACCEPT && echo "   * Acceptar entrada desde ETH1"

iptables -t nat -A POSTROUTING -o eth0 -s 192.168.2.0/24 -j MASQUERADE && echo "   * Activar sortida a internet via ETH0"

echo 1 > /proc/sys/net/ipv4/ip_forward

iptables -A FORWARD -s 192.168.2.0/24 -d 192.168.1.0/24 -j REJECT && echo "   * Denegar acces subxarxa veins -> subxarxa Andreu"

```


Gràcies!!

---

### Post by anigwei on 2009-08-29
Bé, em responc a mi mateix...

Sembla que és correcte, el que m'ha fet dubtar a mi és que des de la xarxa eth1 puc fer un ping al servidor en la IP de eth0 (192.168.1.9), però suposo que és inevitable... :?

Salut,

---

### Post by akyra on 2009-08-31
Hola,
Jo per evitar ping tinc això posat.
/bin/echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all

Salutacions

---

### Post by PatrickVogeli on 2009-08-31
aixo de separas les subxarxes, de manera que una no pugi accedir a l'altra ho podries provar canviant la màscara de subxarxa. En una connexió posa-hi 255.255.255.0 i a l'altra 255.255.0.0, a veure si funciona.

---

