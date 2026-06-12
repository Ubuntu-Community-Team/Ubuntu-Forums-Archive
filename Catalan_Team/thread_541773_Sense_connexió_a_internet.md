---
title: "Sense connexió a internet"
date: 2007-09-03
forum: Catalan Team
---

### Post by Urfe on 2007-09-03
Hola.

Sense causa aparent, he perdut la connexió a internet. Mentre que quan arrenco amb Windows si que hem funciona.

Algú té idea de quina pot ser la causa?

Va coincidir més o menys, però no exactament, amb la configuració de Evolution per un compte de gmail. Durant un parell de dies tot va anar bé i després ja no.

Gràcies.

---

### Post by papapep on 2007-09-03
Quina versió d'Ubuntu fas servir? 
Com tens connectat l'ordinador (directament a un router, tens un hub/switch al mig)? 
Si fas un ping a l'ip del router et funciona? 
Si fas un ping a [www.google.com](www.google.com) funciona?

Dóna'ns pistes, si us plau.

---

### Post by Urfe on 2007-09-03
La meva versió és la 7.04

Tinc l'ordinador connectat directament a un router.

He estat investigant i m'he adonat que si obro l'Ubuntu i no obro l'Evolution  internet funciona. Però quan obro l'Evolution i faig enviar i recibir es traba al moment de enviar missatges. No envia.

A partir d'aquest moment el Firefox deixa de funcionar.

És cert que l'Evolution l'he configurat al tun-tun per al gmail. Aquí deu ser el problema. Però en les instrucciones de gmail no expliquen com es configura l'Evolution.

Hi han instruccions de com fer-ho en cap altre banda?

Gràcies.

---

### Post by ArcA on 2007-09-03
ostres! però que té a veure que hagis configurat malament l'evolution amb que se't peti la conexió a inet?

has provat el que et diu en papapep? de fer un ping a google?

---

### Post by Urfe on 2007-09-03
No, no ho he fet. És que no sé com es fa.

Si em dius com es fa...

Gràcies.

---

### Post by papapep on 2007-09-03
Obre un terminal i fes:

```
ping www.google.com
```

Si canvies [www.google.com](www.google.com) per qualsevol altra url o per una ip, fa la mateixa feina.

Pel terminal veuràs que el teu ordinador intenta enviar paquets de dades al destí que li has indicat, i et dirà si arriben bé o no.

Així vol dir que va bé:

```
root@helm:~# ping www.google.com
PING www.l.google.com (66.249.93.99) 56(84) bytes of data.
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=1 ttl=240 time=91.6                                               ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=2 ttl=240 time=89.6                                               ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=3 ttl=240 time=89.8 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=4 ttl=240 time=91.3 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=5 ttl=240 time=90.8 ms
64 bytes from ug-in-f99.google.com (66.249.93.99): icmp_seq=6 ttl=240 time=90.3 ms
```

I així que no:

```
pujoldebian:~/scripts# ping www.google.com
PING www.l.google.com (64.233.183.147) 56(84) bytes of data.

--- www.l.google.com ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3008ms

```

---

