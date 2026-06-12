---
title: "Problemes amb l'upgrade a Ubuntu 7.10"
date: 2007-10-19
forum: Catalan Team
---

### Post by josep314 on 2007-10-19
Be despres de actualitzar a Ubuntu 7.10, fen servir el gestor de actualitzacions, al iniciar , surt el missatge que diu:

udevd = event [2200] :
run program ´/sbin/modprobe c´ abnormal exit

BusyBox v1.1.3 (Debian 1:1.1:3= 5ubuntu 7) Built in shell (ash)
Enter ´help´ for a list of built in commands

---

### Post by papapep on 2007-10-19
En quin moment et surt? Ens has de donar pistes per a poder ajudar-te.

---

### Post by josep314 on 2007-10-19
Be, primer , al encendre l ordinador, i despres de la pantalla inicial, surt el GURB, que em demana si vull arrencar el Ubuntu 7.10, normal o amb seguretat, o lo que sigui, o si vull arrencar el Windows XP.
Clico, sobre qualsevol opcciço del Ubuntu, i surt la pantalla del logo de Ubuntu, amb el marcador de progres de l proces (aquella barra vertical, que es va omplint ..), despres surt un llistat de operacions, o de comprovacions, que a costat surt, OK. Fins aqui igual que abans. pero a partir de aqui, el lloc de surtir la pantalla inicial de Ubuntu (la de color marron, amb les icones dels programes etc.), surt, pantalla negre amb el text abans esmentat.Pantalla on puc escriure, es com a la consola de linux.

Dons aixço.

Gracies per endevant ...

---

### Post by papapep on 2007-10-19
Com que tens un altre fil actiu que parla d'un problema amb un disc dur, jo provaria a treure aquest disc dur que no et reconeix el SO i provar a veure si arrenca correctament.

---

### Post by josep314 on 2007-10-19
Segueixo casi igual.
sence el HD surt el tex seguent:

udevd=event [2209]: run program:´/sbin/modprobe´ abnormal exit

Bus Box v1. ,,, (igual que abans)


i gracies..

---

### Post by josep314 on 2007-10-19
run program:´/sbin/modprobe´ abnormal exit

---

### Post by papapep on 2007-10-20
Prova posant l'opció "noapic" (sense cometes, clar) quan arrenca el sistema, editant la línia d'arrencada.

---

### Post by josep314 on 2007-10-27
Hola. 
Segueixo sense poguer arrencar  Ubuntu 7.10.

m explicare lo millor que pugui ..

Engego, surt la pantalla drl gurb, amb una pila d opcions.
Ubuntu 7.10. Kernel 2.6.22 Generic
Ubuntu 7.10. Kernel 2.6.22 Recoveri sistem
Ubuntu 7.10. Kernel 2.6.20 Generic
Ubuntu 7.10. Kernel 2.6.20  Recoveri sistem
Ubuntu 7.10. Kernel 2.6.17 Generic
Ubuntu 7.10. Kernel 2.6.17 Recoveri sistem
Windows XP 
alter

La versio Kernel 2.6.22 Generic   i la
La versio Kernel 2.6.17  Generic,
 Arrenca be  pantalla de Ubuntu amb la linea horitzontal de progres ,..Demana el login i el pasword, i ...surt una pantalla il legible, amb ratlles horitzontals de colors verds, grocs i blancs,..

Les altre versio de Generic surt un missatge de text que diu

BusyBox 1.2 ...
/bin/sh: can t acces tty; job control turned off

(initramfs)

Les versions de Recoveri mode, acaban demanant root i pasword, pero no reconeixel el que els hi donc.

Uff 
Gracies per endevant

---

### Post by jaume69 on 2007-10-27
Mira si pots entrar al kernel 2.6.22 Genèric i abans d'entrar-li usuari.,contras.,mira les opcions que hi ha a baix per entrar en mode segur o consola.
Si això t'ho deixa fer,mira aviam quin controlador de targeta gràfica tens o SI EL POTS CANVIAR.(Edita el Xorg)
I per últim formategar,si no tens més remei...
No sé.

---

