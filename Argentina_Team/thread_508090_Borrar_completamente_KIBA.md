---
title: "Borrar completamente KIBA"
date: 2007-07-23
forum: Argentina Team
---

### Post by aceki on 2007-07-23
Gente quiero sacar la barra de KIBA y toda su configuracion, ya que me mande un pequeño lio y si solo le hago apt-get remove kiba, solo me saca el acceso, y yo lo que quiero es que borre toda la configuracion cosa de hacer una instalacion limpia.

---

### Post by Mauro22 on 2007-07-23
Hace

```
sudo synaptic
```

en la consola.


Despues buscas kiba-dock, y con el clic derecho elegis, "Marcar para eliminar completamente"


Salu2

---

### Post by Hei Ku on 2007-07-23
sino podes hacer sudo apt-get purge kiba
eso deberia limpiarte la configuracion.

---

### Post by aceki on 2007-07-23
La primera forma no funciono, y lo del purge siempre me dice esto:

aceki@aceki-desktop:~$ sudo apt-get purge kiba
Password:
E: Operación inválida: purge
aceki@aceki-desktop:~$

---

### Post by marianom on 2007-07-23
Sería

```
sudo dpkg purge paquete
```

---

### Post by spg76 on 2007-07-23
Creo que es:
```
sudo apt-get --purge remove kiba
```

---

### Post by aceki on 2007-07-23
Bien, lo que me pasa es que reinicio ubuntu y cuando instalo nuevamente kiba, me queda como antes, no puedo agregar mas iconos a la barrar

---

### Post by kowal on 2007-07-24
Probá borrando el directorio .kiba de tu home (o uno similar.. nunca instalé kiba) o el directorio /usr/share/apps/kiba (si es que existe)

---

### Post by MeduZa on 2007-07-24
tenes que borrar la carpeta ~/.kiba-dock/ que es donde tenes tu configuracion guardada (yo creo ^_^ )

---

