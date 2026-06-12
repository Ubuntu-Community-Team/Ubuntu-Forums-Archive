---
title: "Ubuntu 9.10 es congela"
date: 2009-12-29
forum: Catalan Team
---

### Post by antoniu on 2009-12-29
Hola, no sé si la paraula correcta és dir que es congela però bé, ho explico.

Des de que tinc la 9.10 bastant sovint em passa que es queda com bloquejat, puc moure el ratolí i tal però no funciona. La barra on hi ha aplicacions, llocs i sistema per molt que apreti no s'em desplega la barra, com tampoc per apagar; els programes que tinc oberts reaccionen al cap de molta estona, etc.

Això em sol passar quan intento tancar una terminal o quan borro algun arxiu o tanco l'amule, però també en altres ocasions que no feia res d'especial.
Per apagar o reiniciar haig d'apretar el botó per encendre l'ordinador, de vegades m'avisa que el gnome panel o el keyring no sé què no responen. Em surti aquest missatge o no, quan sembla que va a apagar es queda la pantalla negra, a on diu rebooting for halt NOW (o quelcom semblant) de vegades amb més text, i es queda així indefinidament, per apagar-lo haig de desendollar-lo.

Ja sé que no està molt ben explicat, m'ho havia apuntat tot en un paper però l'he perdut, si algú té una solució, li estaré mil cops agraït!

---

### Post by quitus on 2009-12-30
En el visualitzador de registres (sistema/administració) pots trobar més informació.

Quan més acurada sigui la informació, més fàcil serà trobar el problema, els noseque i els de vegades solen ser dificultosos.

salut

---

### Post by antoniu on 2009-12-31
I de tot lo que surt què representa que haig de mirar?

---

### Post by Diegstroyer on 2010-01-03
Instal·lació nova o actualització de la 9.04?

Del dmesg tria els resultats amb "grep | error" (sense cometes).

Salutacions.

---

### Post by antoniu on 2010-01-04
Actualització, però no sé si la 9.04 també passava perquè només la vaig tenir 3 o 4 dies.

Al dmesg no em surt cap grep | error

---

### Post by Diegstroyer on 2010-01-10
No volia dir això, em referia a que posessis a la terminal:

dmesg | grep error

Salutacions.

PD: lamento trigar en respondre, però no tinc internet a ksa.

---

### Post by antoniu on 2010-01-11
Si faig dmesg | grep error no fa res
si faig dmesg  grep | error em diu
No command 'error' found, did you mean:
 Command 'perror' from package 'mysql-server-5.1' (main)
 Command 'perror' from package 'mysql-server-5.0' (universe)
error: command not found

---

