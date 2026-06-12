---
title: "sipX en Ubuntu Feisty"
date: 2007-05-24
forum: Argentina Team
---

### Post by nopibecore on 2007-05-24
Hola luego de largo tiempo pude convenser a la empresa de instalar linux  mas preciso ubuntu pero necesito instalar sipX y se me complica .Probe con virtualbox y nada si alguien sabe y me puede ayudar les agradezco .saludos

---

### Post by kalel on 2007-05-24
cual es el problema que tenes?

---

### Post by nopibecore on 2007-05-24
Donde bajo las fuentes para ubuntu o si tengo que instalar desde los binarios y como instalarlos

---

### Post by ariel on 2007-05-27
Las fuentas las bajas de sourceforge pero tenes que tener idea de como resolver las problemas de dependencias etc. 

Los pibes de sipx tambien postean binarios (debs) para ubuntu:

[http://scm.calivia.com/pub/sipx/ubuntu/dists/stable/main/binary-i386/](http://scm.calivia.com/pub/sipx/ubuntu/dists/stable/main/binary-i386/)

Si vas a usar una virtual machine para tu SIP pbx te recomendaria que en lugar de ubuntu uses un live CD cd SIPX or (mas popular y mejor soportado) te bajes e instales Asterix@Home en la virtual machine.

---

### Post by nopibecore on 2007-05-28
ok lo pruebo y les avise

---

### Post by nopibecore on 2007-05-28
como descargo e instalo los paquetes que me aparecen en esa pagina?

---

### Post by lavaramano on 2007-05-29
> **nopibecore said:**
> como descargo e instalo los paquetes que me aparecen en esa pagina?

descargalos como lo harias con cualquier archivo y para instalarlos:
```
sudo dpkg -i *nombre_del_paquete*
```
por cierto, los paquetes que se llaman algo**-dev** son para desarrolladores, y probablemente no los necesites.

cualquier cosa avisa.

---

### Post by nopibecore on 2007-05-29
muchas gracias

---

