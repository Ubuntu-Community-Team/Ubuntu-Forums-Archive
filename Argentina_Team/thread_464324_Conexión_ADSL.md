---
title: "Conexión ADSL"
date: 2007-06-04
forum: Argentina Team
---

### Post by jajajavi on 2007-06-04
Hace unos días hice cambiar mi nombre de usuario de ADSL (para poder usar un router wifi) y desde entonces no puedo conectarme desde Ubuntu, aunque sí puedo hacerlo desde Windows. Modifiqué **dsl-provider **(nombre de usuario nuevo) y **chap-secrets** (nombre de usuario y contraseña nuevos).

dsl-provider
```

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so eth0
user "n16@ciudad-rosario-gld" 

```

chap-secrets
```
# Secrets for authentication using CHAP
# client	server	secret			IP addresses
"n16@ciudad-rosario-gld" * "[contraseña]"

```

El nombre de usuario y contraseña es el mismo que estoy usando ahora en WinXP para conectarme. Me parece que hice todo bien, controlé mil veces cada caracter, realmente no sé qué sucede. Si alguien puede ayudarme estaré muy agradecido, no soporto tener que usar esta porquería privativa, pirata y fea...

---

### Post by elrengo79 on 2007-06-04
Detalla un poco como tenes conectado todo, por lo que entendi la pc se conecta a un router por aire y el router al modem, esto es asi?
antes de la modificacion, como lo tenias conectado?

---

### Post by jajajavi on 2007-06-04
> **elrengo79 said:**
> Detalla un poco como tenes conectado todo, por lo que entendi la pc se conecta a un router por aire y el router al modem, esto es asi?
antes de la modificacion, como lo tenias conectado?

No, esto es una simple conexión con un modem adsl, lo del router wireless lo voy a hacer una vez que esto funcione. Antes de cambiar el nombre de usuario estaba conectado de la misma forma, desde windows se conecta sin problemas.

---

### Post by elrengo79 on 2007-06-04
hace un pppoeconf, decile que conecte cuando te pregunta y hace un ifconfig, fijate si tenes levantada la interface ppp0 (si tu modem es ethernet, si es usb no se como se configura =( )

---

### Post by jajajavi on 2007-06-04
ole ole ole pppoe!!! estoy conectado desde Ubuntu!!! gracias!!

---

### Post by jmarpu33 on 2007-06-07
Hola, tengo todo bien configurado en la wifi. kwifi, por ejemplo, me reconoce el router y la señal. Todo correctamente. Cuando intento navegar con Firefox es imposible.

Os envío el iwconfig y el ifconfig. A ver si me podéis ayudar.

asun@asun-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"WLAN_20"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:01:38:92:2C:DA   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=63/100  Signal level=-33 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:78  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

asun@asun-laptop:~$ 
asun@asun-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D4:07:E6:9A  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe07:e69a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4735 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5480498 (5.2 MiB)  TX bytes:677212 (661.3 KiB)
          Interrupt:22 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:A6:85:2B  
          inet6 addr: fe80::214:a5ff:fea6:852b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:78 overruns:0 frame:0
          TX packets:211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:14585 (14.2 KiB)
          Interrupt:10 Base address:0x8000 

eth1:avah Link encap:Ethernet  HWaddr 00:14:A5:A6:85:2B  
          inet addr:169.254.6.60  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4572 (4.4 KiB)  TX bytes:4572 (4.4 KiB)

---

### Post by jajajavi on 2007-06-07
jmarpu33;
Te recomiendo que abras un nuevo post con lo tuyo, o bien lo pases a [http://ubuntuforums.org/showthread.php?t=458157](http://ubuntuforums.org/showthread.php?t=458157) que es un post sobre wifi que aún no está resuelto, al menos es mantener el foro ordenado.

---

