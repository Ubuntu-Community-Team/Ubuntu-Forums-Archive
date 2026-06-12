---
title: "Como hago para usar la placa de sonido tanto en Ubuntu como en el Vmware Player???"
date: 2007-10-19
forum: Argentina Team
---

### Post by sebadigri on 2007-10-19
Lo que quiero hacer es que el vmware player no me diga que el sonido esta busy cuando lo toy usando con Ubuntu escuchando por ej un mp3 y viceversa... 
(Estoy usando Vmplayer sobre la particion sda5 donde tengo instalado un XP)

Alguien sabe como hago para q me funcionen los 2 al mismo tiempo?

El error que tira cuando lo intentas habilitar y esta usandose ya en Ubuntu el siguiente:

-----------------------
Failed to open sound device /dev/dsp: Device or resource busy
Failed to connect virtual device sound.
-----------------------

PD: Aprovecho para preguntar 2 preguntas más jaja....
a) ¿por q a veces con cierto hotkey me desaparecen las opciones de la barra de titulo de cada cosa y no me deja maximinizar ni minimizar ni apretar la cruz....? (La solucion q hago por ahora cuando me pasa eso es reiniciar la compu jaja)
b) ¿por q aveces cuando reinicio ubuntu no me carga las particiones NTFS?
Saludos!

---

### Post by faktorqm on 2007-10-22
hola, lo del sonido, creo que es mas o menos asi, si por ejemplo usas alsa, y estas escuchando musica con un programa, y queres usar otro que usa oss, no podes, por que te dice que esta ocupado el dispositivo. entonces le pones que use alsa y a traves del alsa-mixer se escucha todo ok.
no use vmware, pero capaz tenes alguna opcion para elegir el servidor de sonido, si es asi, fijate que usa lo que uses vos para escuchar musica, y ponele el mismo servidor a ver que pasa.

lo de las hotkeys ni idea, lo de las particiones ntfs, a mi tambien me pasa, no se por que pasa, pero la seguridad que tengo es que cuando, ponele, usas linux, te pasa a windows, y despues queres volver a linux, no te la monta, reincias linux y la monta. a veces me dice que esta mal desmontada la particion, a veces me dice que no existe el superbloque, pero bueno, es cuestion de paciencia. salu2!

---

### Post by vk-cdg on 2007-10-23
> **sebadigri said:**
> ... 
(Estoy usando Vmplayer sobre la particion sda5 donde tengo instalado un XP)



Perdón por la pregunta, quizás algo idiot*, pero o yo entendí mal, o vos desde el vmplayer estás usando la instalación de XP que tenés en otra partición?

Si es eso, me interesa saber como se hace.

---

