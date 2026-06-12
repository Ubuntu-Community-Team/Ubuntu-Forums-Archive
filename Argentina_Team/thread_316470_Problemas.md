---
title: "Problemas"
date: 2006-12-10
forum: Argentina Team
---

### Post by MaReaDo^ on 2006-12-10
Soy nuevo en Ubuntu y tengo un par de problemas a ver si me pueden ayudar, desde ya les agradezco mucho:

1-Azureus: de un dia para el otro cuando lo abri, me aparecio la ventana de downloads y se cerro sola, pasa siempre que lo abro, adjunto el log del error. (Le borre al log la parte THREAD porque si no ocupaba mucho y no lo podia adjuntar)

2-Gnome-Panel: me tira error y se reinicia muchas veces, tambien adjunto el log del error.

3-Hamachi: es un programa para hacer una VPN, y cosas asi. Si alguien lo conoce mejor, y si no creo que tambien me pueden ayudar. Trae unas instrucciones y un Makefile, pero no puedo hacer el make, me tira errror. Adjunto las instrucciones y el error.

4-DOSBox: este es un emulador de DOS que tambien usaba en Windows para jugar Abandonware. Pero en win en la parte Display yo ponia Direct3d y andaba bien. Aca no se que poner, en un foro recomiendan openglhq, y no me funciona, no se me abre el juego, con opengl a secas anda maso. No se bien cual poner ni como configurarlo bien, ya que la misma conf que usaba en win no me anda bien. Si alguien lo conoce y le anda bien, y me puede decir que config usa mejor, o si no por lo menos si alguien conoce openglhq y sabe porque puede ser que no se me abra.

5-Necesito compartir internet con maquinas que usan Windows XP, y no quiero usar Firestarter ni ningun soft, se que se puede hacer con algun script para el iptables, si alguien sabe uno o me puede ayudar con eso.


Desde ya muchas gracias por todo, y perdonen por tantos problemas.



Edit: TODOS RESUELTOS

---

### Post by marianom on 2006-12-11
Problema 3: no dice mucho el error. ¿Estás corriendo el make con sudo? sin eso no creo que te deje entrar a usr/bin.
confirmame y trato de ayudarte.

---

### Post by MaReaDo^ on 2006-12-11
asi puse, graias por ayudar:



facu@Facundo:~$ sudo make -f /home/facu/Desktop/hamachi-0.9.9.9-20-lnx/Makefile
Copying hamachi into /usr/bin ..
install: no se puede efectuar `stat' sobre `hamachi': No existe el fichero ó directorio
make: *** [install] Error 1

---

### Post by marianom on 2006-12-11
Pero el installation de las instrucciones que posteaste dice que tenes que ejecutar "make install"
¿Por que estas ejecutando otro comando? ¿hay algo que me perdí?

---

### Post by MaReaDo^ on 2006-12-11
porke no hace nada poner "make install" y entre al manual del make y decia ke se usa asi nose xd

edit: tenes razon, ya lo resolvi, descubri algo en ubuntu ke no sabia xD

---

### Post by marianom on 2006-12-11
Copado. Me alegro por vos.

PD: ¿parece que estamos en la misma provincia, no?

---

### Post by MaReaDo^ on 2006-12-11
si eso me fije
pasa que no entendia bien lo de marplatense y cordoba :o

---

### Post by marianom on 2006-12-11
Pasa que me engañaron... pero ya voy a volver a morirme de frío a Mar del Plata en algún momento de mi vida.

---

### Post by MaReaDo^ on 2006-12-11
y por casualidad no tenes un script para el iptables para compartir internet de esta pc a otras con win xp?

---

### Post by marianom on 2006-12-11
No, nunca tuve la necesidad así que nunca usé nada de ese estilo pero de todos modos te doy una mano para buscar, veamos que se encuentra.

---

### Post by marianom on 2006-12-11
Hice una búsqueda con "iptables script share internet linux windows" en google y está repleto de scripts. Incluso uno en Debian que parece muy completo: [http://www.aboutdebian.com/proxy.htm](http://www.aboutdebian.com/proxy.htm)
Te sugiero lo pruebes y cualquier problema tires la duda. Seguro que con algunos temas más puntuales podes encontrar mucha ayuda aca.

---

