---
title: "Server VPN con SSL que demonio recomiendan?"
date: 2007-02-20
forum: Argentina Team
---

### Post by Ethome on 2007-02-20
Estoy Armando un server VPN para mis clientes hagan resplando en el raid 5 que tengo armado por medio de SAMBA cual es el Demonio mas recomendado o cual usarian UD?

Estoy esperimentando con TINC ya que trae un cliente for windows, pero no encuentro suficiente informacion

---

### Post by BlackHero on 2007-02-21
haber si entiendo vos estas armando un server para storage nada mas? ovbio para tus clientes pero para base de datos propia de ellos nada mas verdad eso entendi?

---

### Post by marianom on 2007-02-21
Yo digo [OpenVpn]("http://openvpn.net/"). 100% documentado, para linux y windows.

---

### Post by Ethome on 2007-02-22
BlackHero, es correcto justo lo que quiero hacer

Gracias :D

---

### Post by Ethome on 2007-02-22
Gracias Mariano voy a tenerlo en cuenta a la hora de decidir tu opinion, pero quisiera mas opiniones a ver cuales probaron los demas

---

### Post by BlackHero on 2007-02-22
pero no entiendo bien la idea lo mejor que podes hacer para storage seria un ftp man es universal eso

---

### Post by ariel on 2007-02-25
Yo use openvpn en un linux server durante anios, en un entorno de lab.

Les daba acceso a gente que usaba windows desktops, hay un cliente para windows muy piola y muy estable. 

obviamente la ventaje de openvpn/ssl es que no tenes que pedirle a los pibes de seguridad informatica de tu empresa que abran puertos en el firewall, it just works.  la desventaja que es que el tunel va sobre tcp, lo que jode aplicaciones de real time como voz sobre ip. Sin embargo yo use muchas veces clientes de voz sobre ip a traves del tunel openvpn y anduvieron mas que aceptables.

---

