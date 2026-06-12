---
title: "Problema particion"
date: 2008-03-16
forum: Argentina Team
---

### Post by xpelaox on 2008-03-16
Hola, que tal gente?

Me surgio el siguiente problema: Primeramente tenia windows vista, particione el disco y  le saque 15 gb al disco del vista para ubuntu, instale ubuntu ahi y todo bien. Despues quize agrandar la particion de ubuntu, entonces desde vista, le agregue 15 gb mas a la particion de ubuntu.

ahora bien, desde vista, con el partition magic, se ve que todos los cambios se hizieron, desde el Gparted en UBUNTU tambien,  pero usando ubuntu, las particiones siguen igual, como si fuese necesario actualizar o algo:P

hay alguna forma de hacer esto?

Desde ya, gacias!

---

### Post by Mauro22 on 2008-03-16
No creo que haya que hacer algo.


Corriste un fsck ?? con sudo desde consola para verificar los discos?

---

### Post by newtonfn on 2008-03-16
No tengo idea cual es el problema, pero al ver la sugerencia que te hicieron, simplemente te advierto que no ejecutes fsck en un disco montado a menos que quieras arriesgarte a perder toda la partición (lo digo por experiencia.. a veces no pasa nada.. pero a veces suceden cosas muy feas si se fuerza un fsck sobre un disco montado)

Si no tienes idea de lo que estoy hablando, primero reinicia la pc usando el livecd de Ubuntu y desde el livecd ejecutá el fsck

---

