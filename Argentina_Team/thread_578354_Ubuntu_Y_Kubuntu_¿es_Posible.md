---
title: "Ubuntu Y Kubuntu ¿es Posible?"
date: 2007-10-17
forum: Argentina Team
---

### Post by mauro7g on 2007-10-17
BUENAS... KERIA SABER SI ES POSIBLE UNA VEZ INSTALADO "UBUNTU" CON "WINDOWS" SE LE PUEDE AÑADIR EL "KUBUNTU" EN PARALELO CON LOS OTROS DOS.... Y YO PUEDA ASÍ ELEGIR COMO INICIAR LA PC. DESDE YA MUCHAS GRACIAS.:lolflag:

---

### Post by leo_rockway on 2007-10-17
por favor no grites.

en ubuntu desde consola escribi

```
sudo apt-get install kubuntu-desktop
```

eso te va a instalar kde

---

### Post by tzulberti on 2007-10-17
Ademas, en el GDM (donde te logueas) vas a  tenes la opcion de elegir cual de los dos vas a querer usar: Kde o Gnome.

Saludos,
TZ

---

### Post by mauro7g on 2007-10-17
Muchas gracias por la info...y lo de gritar lo voy a tener en cuenta...disculpen...pero es la 1ra. vez que hago una pregunta en el foro...prometo no volverlo a hacer :^o Muchas gracias x la info!!!

---

### Post by mauro7g on 2007-10-17
Perdón X molestar otra vez...pero y si no me gusta Kde??? Se puede llegar a desinstalar sin necesidad de quitar Gnome??? Grax!

---

### Post by tzulberti on 2007-10-17
Si. Lo podes desinstalar usando el synaptic, o desde la linea de comandos: apt-get remove kde

No me acuerdo si era exactamente asi, o kde3.

Como comentario: es posible que por mas de que borres kde, te queden varios de los programas instalados cuando se instalo Kde.

---

### Post by ubuntu27 on 2007-10-17
yo recomiendo que uses aptitude en vez de apt-get

Instalar Kubuntu
```
sudo aptitude install kubuntu-desktop
```

Desinstalar Kubuntu

```
sudo aptitude remove kubuntu-desktop
```


aptitude memorisa los todos los paquetes incluyendo las dependencias cuando instalas. Asi que cuando desinstalas, no te deja paquetes huerfanos.
Con apt, si desinstalas normalmente, lo unico que hace es desinstalar el paquete mencionado, y te dejara los demas paquetes como huerfanos. 

El problema con apt ha sido solucionado con las versiones recientes (desde Feisty)  con el comando "autoremove" 
A mi no me gusta esto, ya que a mi me dio problemas. cuando intente desinstalar KDE, no solo desinstalo KDE< sino TODO paquete instalado (incluyendo GNOME) y me dejo on un Sistema no funcional.  Creo que eso es un signo de inmadures de parte de apt-get autoremove. 

Talves eso aya sido coregido para Gutsy. No lo se.  

Bueno eso es mi opinion y experiencia.  Antes de Ubuntu Feisty Fawn, muchos han recomendado usar aptitude en vez and apt-get. Pero desde Feisty, los grupos se han dividido.

---

### Post by leo_rockway on 2007-10-17
yo dije apt-get mas por costumbre que por otra cosa, no lo recomiendo ni lo dejo de recomendar. yo tb escuche de esas bondades de aptitude pero no las probe por mi mismo.

para lo de los paquetes huerfanos yo uso:

```
#deborphan | xargs sudo apt-get -y remove --purge
```

---

