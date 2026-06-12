---
title: "M'he quedat sense wifi"
date: 2013-06-07
forum: Catalan Team
---

### Post by U-Joan on 2013-06-07
Hola, he vist uns quants fils de gent amb problemes concrets amb la wifi, però no he vist cap solució que em funcioni. Des d'ahir a la nit, no sé si va ser després d'una actualització de seguretat, la connexió wifi m'ha desaparegut. Puc navegar amb la connexió amb cable, i he comprovat que amb el windows en canvi sí que va la wifi. No puc connectar l'opció de "habilita la xarxa sense fils".

Encara estic amb la versió 12.04. Des del terminal em surt la següent informació:

joan@U-Joan:~$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


joan@U-Joan:~$ rfkill list all
1: sony-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by wgarcia on 2013-06-08
A l'última sortida, la línea que diu "Soft blocked:yes" indica algun problema amb el controlador del wifi. Saps quin model de targeta wifi tens? Ho pots esbrinar donant la següent instrucció des d'una terminal:

```
sudo lshw -C network
```

Si et diu que no troba "lshw" primer fes "sudo apt-get install lshw", ara no recordo si està instal·lat per defecte o no.

---

### Post by U-Joan on 2013-06-09
Hola wgarcia,

He recuperat la wifi. Estava provant solucions i no sé exactament com, però crec que es va desbloquejar amb l'ordre: [FONT=Helvetica]

sudo rfkill unblock all

[/FONT]No n'estic molt segur, però la qüestió és que ja funciona de nou.

Moltes gràcies!

---

