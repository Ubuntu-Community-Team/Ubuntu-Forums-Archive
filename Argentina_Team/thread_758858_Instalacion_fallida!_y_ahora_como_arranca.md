---
title: "Instalacion fallida! y ahora como arranca??"
date: 2008-04-18
forum: Argentina Team
---

### Post by leonardo83 on 2008-04-18
Buenas gente, les cuento lo que me paso.
Despues de dias de intentar pelear con Linux, despues que instale, probe, casi tiro mi pc, desconecte, etc etc , hoy me decidi a ver si podia instalar de nuevo Ubuntu.
Cuestion que como seguro nadie lo recordada, tengo un rigido de 60 con win ME y un rigido de 80 vacio, o casi, donde siempre intente instalar linux.
Hoy agarre el cd de win xp, bore la particion de ese rigido y probe el cd de ubuntu 7.10... y para mi sorpresa arrano... live cd... joya.
Lo primero es que como pense que NO iba a arrancar, como lo hacia siempre ( tiraba error de bash, error de cd, etc ), no configure ni el ididoma ni la resolucion, arranco asi y chau, entonces loq ue vi cuando me aparecio el escritorio es una imagen toda desfigurada del mimso, asi como gigante y corrida, como fuera de foco.
Lo que hice fue ir a propiedades, la cambie a una que me gustaba (no me pregunten cual era, creo que 800 x 600 o 1024 x algo, no recuerdo bien) , y procedi a instalar.
Instalo todo bien, perfecto, reinicio, saco el cd.
El glorioso grub me aparecio (cosa que antes no aparecia, tenia error 18 y demas) , eligo arrancar ubuntu, carga, y me aparece en un cuadro color violeta, con fondo negro lo siguiente:

ATENCION = 63 K / 59 HZ FRECUENCIA FUERA DE IMAGEN

WTF ??? pense que era que cambie en l ainstalacion, revise, intente arrancar win me y arranca ok, entonces me fije las opciones del monitor (philips) y veo que ahi en propiedades dice resolucion 800 x 600 , frecuencia 38 k / 60 hz.
Me parece que ahi esta el error, lo raro de esto es que ya instale ubuntu oootras veces peroe ste mensaje no me habia aparecido nunca, es como que mi monitor ahora no lo soporta, la imagen o vaya a saber uno que cosa.
Lei un post parecido sobre otra persona que tenia problemas con el monitor que le aparecia un codigo y un error, que no es lo mio.
No se si hay que instalar algun driver, tal vez se puede modificar desde el grub, algun valor, no se, si alguien me puede ayudar se lo voy a agradecer, por fin que instala ok y ahora me aparece esto !!! AAAAAAHHHH :( !!!!!!!

Saludos, espero respuesta, si necesitan mas informacion diganme..

---

### Post by malangaman on 2008-04-18
Me parece que el error surge de aqui:
[I]Lo primero es que como pense que NO iba a arrancar, como lo hacia siempre ( tiraba error de bash, error de cd, etc ), no configure ni el ididoma ni la resolucion, arranco asi y chau, entonces loq ue vi cuando me aparecio el escritorio es una imagen toda desfigurada del mimso, asi como gigante y corrida, como fuera de foco.
Lo que hice fue ir a propiedades, la cambie a una que me gustaba (no me pregunten cual era, creo que 800 x 600 o 1024 x algo, no recuerdo bien) , y procedi a instalar.[/I]

Porque no instalar de nuevo con la informacion de Win ME? :
800 x 600 , frecuencia 38 k / 60 hz.

Que PC tienes?

---

### Post by sajnox on 2008-04-18
Leonardo,

Arranca el sistema normalmente, cuando te tira el error apretas ctrl + alt + f1 y te pide que des tu nombre de usuario y contraseña, una vez que te logueaste escribis

1) Back del xorg.conf (aunque no ande lo dejamos como esta)

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf
```

2) Paras las x

```
sudo /etc/init.d/gdm stop
```

3) Reconfigurar el xorg en forma automatica

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

4) Reiniciar las X

```
startx
```

Aca deberia arrancar el monitor normalmente (muchas veces pasa que detecta mal el monitor por algun motivo despues de la instalacion y hay que reconfigurar)

Si lo anterior no funciono, volve al paso 1) y cambias el paso 3 por el siguiente

```
sudo dpkg-reconfigure xserver-xorg
```

De esta manera reconfiguras el xorg.conf pero a mano, por lo que te pide muchos datos, generalmente podes tomar los que da autoamticos pero estate atengo a la frecuencia del monitor

Espero te sirva

---

### Post by faktorqm on 2008-04-18
Leo! sajnox tiene un bug! no le des bola! no mentira! se ekivoco EN EL PASO 1.

lo correcto debe ser:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_1_18-04-08
```

Con lo de sajnox estarias copiando un archivo, y guardandolo con el mismo nombre, y eso no se puede hacer. Es más, no deberia dejarte hacerlo, pero bueno, todos sabemos que linux no es windows por suerte.

Si volves a hacer un backup, deberias poner:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_2_18-04-08
```

Para poder tener un backtracing de lo que vas cambiando. 

Bug de sajnox reportado y solucionado!! :D Salu2!!

---

### Post by leonardo83 on 2008-04-26
Primero que nada disculpen por la demora pero tuve parcial en la facu y no tuve tiempo de "jugar" un rato con linux ni postear aca :(.
Lescomento que descargue el archivo de la pagina de NVidia pero segui unos pasos que vi por internet y pude instalar los controladores!!!

Paso a indicarles lo que hice:

* fui a origenes de software y vi que no estaba nada tildado asi que tilde TODOS, todas las fuenets descargables de internet
* entonces ipso facto, fui de nuevo a activar la placa desde elo gestor de controladores, como estaba conectado a internet se descargo solito el archivo y para terminar me pidio reiniciar
* al reiniciar mi pantalla se ve medio rara, es decir, se ve muy grande pero no lo puedo configurar mas pues desaparecieron pantallas como 1024 x etc, solo tengo dos pero no problem! ah y un mensaje en la barra de gnome que dice "controlador restringido activado" y me aparace que el controlador de nvidia esta activoooo :):):)

Peeeeero (siempre hay un pero) si por ejemplo desde efectos eligo cualquiera, sea normal o extra, me aparece el mensaje ```
desktop effects could not be loaded
```

Que pasa? pense que activando esto ya estaria, porque si instalo beryl o compiz lo voy a tener que activar de ahi, falta hacer algo?

Bueno gracias, espero me ayuden, como dije me demore y recien este finde volvi a atacar con ubuntu, que se me va a demorar unos meses en que lo tenga todo configurado como quiera, pero no importa, me gusta jajaj :)
Saludos

---

