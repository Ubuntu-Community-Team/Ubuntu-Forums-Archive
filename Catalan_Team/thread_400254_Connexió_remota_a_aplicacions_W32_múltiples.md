---
title: "Connexió remota a aplicacions W32 múltiples"
date: 2007-04-03
forum: Catalan Team
---

### Post by basdala on 2007-04-03
Atenció a la paranoia:

Tinc una clienta (treballo a un servei tècnic) que té el següent:
- 20 estacions linux
- 1 servidor Windows 2003 Server
- 1 aplicació "windows only"

Necessita imperiosament la aplicació per Windows, però no vol posar Windows a les estacions, només linux (un Ubuntu). El servidor continúa sent un Windows 2003 Server.

El cas és que volem instal·lar l'aplicació al servidor Windows i **accedir remotament **des de Linux, a ser possible sense fer servir llicències de Terminal Server -que són massa cares.

Hi ha alguna alternativa a Terminal Server? Funcionaria instal·lant un servidor X a Windows i "clonant" les sessions d'usuari? El que necessiten, bàsicament, és fer servir **el mateix programa** des de varis clients Linux alhora.

Alguna sol·lució?

Gràcies per avançat.

---

### Post by manelolesa on 2007-04-04
Podries mirar el VNC Server, que es gratuit i pot donar servei desde un Windows 2003.


[http://www.realvnc.com/products/free/4.1/winvnc.html](http://www.realvnc.com/products/free/4.1/winvnc.html)


Salutacions

---

### Post by CarlesOriol on 2007-04-04
La versió lliure del realvnc et permet concurrencia d'usuaris no presencials en w2003?

---

### Post by manelolesa on 2007-04-04
Tens rao, no es pot fer mes d'una sesió. Al menys en la versió free.

Salut

---

### Post by basdala on 2007-04-10
O sigui, que estic "condemnat" a haber d'adquirir llicències de Terminal Server, per nassos.

En fi, gràcies de tota manera. Al menys ho hem intentat :)

Gràcies a tots.

---

### Post by CarlesOriol on 2007-04-11
Quina aplicació és la que et limita?

---

