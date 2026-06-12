---
title: "Instalar Xubuntu arriba de Ubuntu"
date: 2006-12-31
forum: Argentina Team
---

### Post by Nemesis Teufel on 2006-12-31
Hay alguna forma de instalar Xfce y elegir con que sesion deseo entrar, ya sea gnome, kde (que ya lo tengo) y ahora VAMOS POR MAS! (que feo suena eh) quiero probar xubuntu.

---

### Post by Piti on 2006-12-31
Mira, yo tengo un problema (estoy en win ahora) en gnome que no se bien que es, pero no me deja hacer nada, asi que agarre una consola y mande apt-get install xubuntu-desktop. Con eso ya te queda en la pantalla de login, en opciones, para elegir la sesion de Xfce.

Lo estuve probando un rato y xfce esta bueno, es muy rapido (en mi maquina hay diferencia, es medio viejita) y se ve bastante bien, tiene muy linda pinta.

---

### Post by jpmorelli on 2006-12-31
sudo apt-get install xubuntu-desktop

El gdm o kdm según tengas instalado despues te deja elegir.

---

### Post by Hex_Mandos on 2006-12-31
Sobre todo para algo pesado como xfce, yo usaría aptitude en lugar de apt-get. Instala librerías y progrmas varios, así que mejor asegurarse que si lo desinstalás salga todo.

---

### Post by felipelerena on 2006-12-31
> **jmorelli said:**
> sudo apt-get install xubuntu-desktop
please, dejen de usar atz-get, usen aptitude en su lugar
y mas con esos paquetes con tantas dependencias

---

### Post by Piti on 2006-12-31
Pero no hay problema en comenzar con aptitude si uno venia usando apt-get?

---

### Post by felipelerena on 2006-12-31
nop, para anda.

---

### Post by beuno on 2006-12-31
> **Piti said:**
> Pero no hay problema en comenzar con aptitude si uno venia usando apt-get?

No se genera ningun problema *nuevo*, sencillamente hay muchos paquetes que ya van a quedar huerfanos por el uso de apt.
Siempre es recomendable usar aptitude.
Si sos un poco obsesivo y queres tener todo limpio para empezar a usar aptitude siempre, aca te explican como limpiarlo:  [http://www.debian-administration.org/articles/462](http://www.debian-administration.org/articles/462)

---

### Post by jpmorelli on 2007-01-01
Algo de eso me habían comentado sobre el apt o el aptitude, pero varias veces aptitude me hizo unos bardos terribles... me desinstaló cosas que no quería porque dependían de otras, etc. :(
Realmente vale la pena ? Porque en varios sitios de Ubuntu el comando es apt-get install .... ?:confused:

---

### Post by felipelerena on 2007-01-01
[jmorelli]("http://ubuntuforums.org/member.php?u=98913") el aptitude te pregunta que queres ahcer, tenes que evaluar bien tu respuesta...

---

### Post by Nemesis Teufel on 2007-01-01
Bueno, lo hice con aptitude y funcionó de maravilla.
Que lindo que es Xfce! Tan simple, nada que moleste, pura velocidad. A mi me gusta incluso mas que Kde (ahora se arma lio por esto :D).

Resolved.

---

### Post by beuno on 2007-01-01
Ahi estoy instalando yo tambien.
Me canse que todos esten encantados con el xfce y yo no.

---

### Post by elgatogordo on 2007-01-01
me habia propuesto instalar beryl pero parece que mi tarjeta de video es demasiado berreta y no lo soporta, leyendo esto me baje xubuntu y me gusto así que yo tambien lo estoy instalando, eso si para ser diferente desde el synaptic

---

### Post by Nemesis Teufel on 2007-01-01
Instalalo de la terminal.. es mas fácil y rapido todavia.. va digo, como quieras.

---

### Post by elgatogordo on 2007-01-01
> **Nemesis Teufel said:**
> Instalalo de la terminal.. es mas fácil y rapido todavia.. va digo, como quieras.

tardo 9 minutos

---

### Post by lavaramano on 2007-01-02
es que el xfce es lo que se viene, es como el tema del verano pero menos careta (?)
offtopiqueando un poco:
digamos que en el ultimo mes solamente use xfce, este fin de semana use un toque el gnome, y no se. me dio bronca (?) de lo lento que me iba comparado con el xfce.
y eso que el gnome me va lo mas bien, sin problemas ni esos 'lags' al cambiar de ventanas.

en conclusion, una belleza el xfce. y por lo que voy leyendo del xfce diary, cada vez mas bonito (tambien un poco mas pesadito, pero bueh..)

---

