---
title: "Compilando Kernel"
date: 2008-05-06
forum: Argentina Team
---

### Post by sdm_cacto on 2008-05-06
Hola, tuve un problema con mi kernel en Ubuntu 8.04 asiq decidi compilar la ultima version por mi cuenta.
A la hora de configurarlo no entendia nada, por lo q me surgio la duda: Hay alguna manera de cocnfigurar el kernel para q todo mi sistema vaya mas rapido?? alguien conoce alguna guia? realmente hace la diferencia o dejo la configuracion q traer ubuntu?

Siempre tuve esas dudas, gracias por leer y por favor respondan.

---

### Post by MeduZa on 2008-05-06
> **sdm_cacto said:**
> Hola, tuve un problema con mi kernel en Ubuntu 8.04 asiq decidi compilar la ultima version por mi cuenta.
A la hora de configurarlo no entendia nada, por lo q me surgio la duda: Hay alguna manera de cocnfigurar el kernel para q todo mi sistema vaya mas rapido?? alguien conoce alguna guia? realmente hace la diferencia o dejo la configuracion q traer ubuntu?

Siempre tuve esas dudas, gracias por leer y por favor respondan.

yo empece como vos, no sabia nada baje el ultimo y me puse a leer casa cosa, buscaba en internet, tardas muchisimo, yo basicamente lo que hice fue asi:

saque una lista de TODO lo que necesitaba mi PC en materia de drivers para el hardware, despues busque todo lo que necesitaba en materia de SOFTWARE, que iba a usar y que no (ejemplos, quite X25, IPX-SPX, appelTALK, [escribi aca el protocolo que no vas a usar] y deje TCP-IP v4 y v6 (aunque el v6 no lo uso aun pero nose sabe ;) )
despues me fui a la parte de CPU y quite todo lo que no iba con mi CPU y solo deje las caracteriscitas y preferencias que solo afetaban mi CPU.
Quite todo lo que crei que no servia (ahi hice varias macanas pero lo hacia de a poco para volver a poner probar y empezar otra vez)
Saque muchisimas cosas que no uso, la velocidad aumento en general al booteo y el sistema esta menos pesado (un kernel mas chico) cargo menos modulos y tengo menos archivos dando vuelta por el disco de cosas que nunca en la vida voy a usar.
Me paso tambien que por ahi algo que habia quitado en el pasado lo necesite en el futuro, no es problema, agregas, recompilas instalas y listo.
La semana pasada compile mas de 20 veces el kernel. porque estaba probando algo y hasta que lo hice andar.

Lleva mucho tiempo pero la verdad es algo que te hace aprender mucho de tu pc, necesitas sentarte y estar una hora leyendo que es cada cosa y decidir si quitarla o ponerla.

Te digo la verdad, de cada menu comunmente se quita casi todo y se deja una sola cosa. (ej: del menu "I2C Hardware Bus support" solo deje: Nvidia nForce2, nForce3 and nForce4 que es la que tiene mi motherboard)

y asi con todo, se te puede ir la mano pero como te dije se prueva y se puede volver atras, las primeras 3 veces que compile cuando empece hice 3 kernels panic xD pero claro puse cosas mal y me di cuenta que cosas van en el kernel y que cosas no (habia puesto los drivers sata como modulo sin darme cuenta) y si metes la pata booteas el kernel anterior y seguis probado.

PD: instalar el ultimo a veces te trae problemas con otras aplicaciones, ejemplo VMPLAYER deja de compilar y tenes que buscar en internet, pero nada grabe todo se consigue la red es grande y los locos que saben muchos ;)

Suerte
Saludos.

---

### Post by sdm_cacto on 2008-05-06
Gracias Medu me entendis a la perfeccion.

Buscando en ubuntuforums encontre el "Master Kernel Thread", donde hay mucha info para compilar, una guia de los modulos y cosas q no necestias y ademas proponen un script (Kernelcheck) q hace q todo sea mas facil, recomiendo chequearlo.

Bueno, me ovy a compilar a ver q onda.

---

### Post by leo_rockway on 2008-05-06
Yo acá ando en la misma, intentando compilar un Linux para mi LFS.

Me da panic porque es un pendrive y no le meti la parte de USB built-in. Tengo que sentarme un par de horas y ponerme a leer todos los menues pero ahora no tengo mucho tiempo.

Entre LFS y la compilada del Linux salgo guru guru heart punch seguro.

---

### Post by MeduZa on 2008-05-07
> **leo_rockway said:**
> Yo acá ando en la misma, intentando compilar un Linux para mi LFS.

Me da panic porque es un pendrive y no le meti la parte de USB built-in. Tengo que sentarme un par de horas y ponerme a leer todos los menues pero ahora no tengo mucho tiempo.

Entre LFS y la compilada del Linux salgo guru guru heart punch seguro.

ejjejje me paso igual, tres veces, hasta que me di cuenta que todo lo necesario para el booteo tiene que estar metido en el kernel si o si ajjajaja sino lucecitas titilando jajajaja

---

