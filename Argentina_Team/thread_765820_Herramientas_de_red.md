---
title: "Herramientas de red??"
date: 2008-04-24
forum: Argentina Team
---

### Post by .NicK_LoVe on 2008-04-24
Hola!!! alguien conoce herramientas de red, por ejemplo para ver las ip de las makinas que están en mi lan y otras cosillas???
Saludos!

---

### Post by .NicK_LoVe on 2008-04-25
Ayuda!!!!!!!!!!!!!!

---

### Post by fmsismo on 2008-04-25
Para ver que equipos están andando en tu red podes hacer.

sudo nmap -v -sP 10.0.0.0/24 |grep 'appears to be up.'

Donde 10.0.0.0 es la red que estas escaneando y el 24 define la máscara (255.255.255.0)

Saludos

---

### Post by euzkoarima on 2008-04-25
También podes isntalar [Ethereal]("http://www.ethereal.com/") que está en los repositorios.

Saludos.

---

### Post by Mister X on 2008-04-25
el nmap es una herramienta muy poderosa, si queres algo grafico, tenes el nmapfe, que es justamente un frontend para el nmap

---

### Post by .NicK_LoVe on 2008-04-25
Gracias a todos!! Estoy instalando y probando.

Saludos.

---

### Post by faktorqm on 2008-04-26
No vi tu post. busca nubuntu. una distro basada en ubuntu para redes. No tengo mucho tiempo, bajala grabala y probala. Sino tb t recomiendo pfsense, aunke no se si trae tantas herramientas (base bsd). Salu2!

---

