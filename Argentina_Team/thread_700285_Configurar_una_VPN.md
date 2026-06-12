---
title: "Configurar una VPN"
date: 2008-02-18
forum: Argentina Team
---

### Post by YOGUI on 2008-02-18
Bueno, de a poco estoy haciendo mi mudanza a Ubuntu 7.10 desde el arcaico winXP en la PC de mi laburo. Uno de los pocos problemas con los que me he encontrado es el tema de las VPN. 

El tema es que me tengo que conectar a una VPN y desde win era muy sencillo: Creaba una nueva conexión de red como VPN configuraba la IP y listo. Cómo hago en Ubuntu? Que paquetes debo instalar?

Gracias por la ayuda

---

### Post by faktorqm on 2008-02-18
La verdad la verdad, nunca me toco armar una, pero alguna idea te puedo dar.

```

faktorqm@ttheedge:~$ aptitude search vpn
p   grml-vpn                        - program to establish encrypted communicati
p   kvpnc                           - vpn clients frontend for KDE              
p   network-manager-openvpn         - network management framework (OpenVPN plug
p   network-manager-vpnc            - network management framework (VPNC plugin)
p   openvpn                         - Virtual Private Network daemon            
p   secvpn                          - Secure Virtual Private Network            
p   vpnc                            - Cisco-compatible VPN client               
faktorqm@ttheedge:~$

```

Yo te diria que primero hagas 

```
sudo apt-get install network-manager-openvpn openvpn
```

y te fijes en el network manager como hacer. Supongo que debe ser asi de facil como lo describis vos, igual como te dije antes nunca me toco hacerlo. Salu2!!

---

### Post by marianom on 2008-02-18
El openvpn es un cliente / servidor vpn en si mismo y solo sirve para conectarse a servidores openvpn.
Si la conexión la estás haciendo directamente por windows sin instalar otros productos, eso quiere decir que estás posiblemente usando el inefable pptp de windows.
Por suerte para vos hay varios productos en linux que lo implementan y es posible que con un par de clicks lo tengas andando.
[Esto]("http://ubuntuforums.org/showthread.php?t=91249") podría ser de ayuda.

---

### Post by faktorqm on 2008-02-18
Bueno, entonces necesitas el plug-in para el networks manager que soporte pptp

```

faktorqm@theship:~$ aptitude search pptp
p   network-manager-pptp            - network management framework (PPTP plugin)
p   pptp-linux                      - Point-to-Point Tunneling Protocol (PPTP) C
p   pptpd                           - PoPToP Point to Point Tunneling Server    
faktorqm@theship:~$ 

```

asi que probaria

```
sudo apt-get install pptpd network-manager-pptp
```

Gracias marianom por el tip, AMO ESTA COMUNIDAD!! :KS

---

### Post by YOGUI on 2008-02-18
**Bueno muchas gracias a los dos!**

Ejecuté > sudo apt-get install pptpd network-manager-pptp y después siguiendo la guía que indicó marianom, hice clic en Conexión de red en el panel de notificaciones. Ahí aparece Conexiónes VPN -> Configurar VPN.. y listo en dos clics con el asistente quedó configurada! Mucho mas fácil que en win! 
La verdad no dejo de sorprenderme con Linux
A parte, que buena comunidad! Todos dispuestos a ayudar, estoy en el paraiso!

---

