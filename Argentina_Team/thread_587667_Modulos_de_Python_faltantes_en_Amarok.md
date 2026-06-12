---
title: "Modulos de Python faltantes en Amarok"
date: 2007-10-22
forum: Argentina Team
---

### Post by lordpuppet on 2007-10-22
Buenas;
Buenas, vengo usando gutsy desde el mismo dia que salio. He instalado el amarok y funciona, pero al querer instalar algunos de sus scripts por ejemplo para poder ver las letras de las canciones, me da error. Uno de los errores que me muestra es este:

"Some needed Python modules could not be found.
Python output: No module named kdecore"

También sale este al intentar instalar otro script:

"Sorry, you need QtRuby, RubyGTK or TkRuby to execute this program"

No encontre de donde descargar e instalar estos modulos, por eso acudo a ustedes.

---

### Post by marianom on 2007-10-23
Según puedo ver en la [busqueda de paquetes]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=kdecore&searchmode=searchword&case=insensitive&version=gutsy&arch=i386"), kdecore está literalmente por todos lados.

¿Cual es el correcto? Esperemos que alguno de la tribu de Amarok nos lo diga,

---

### Post by lordpuppet on 2007-10-23
Es que a mi no me aparecen esos paquetes en el synaptic.

He intentado sudi apt-get install y no ha encontrado los paquetes.

---

### Post by leo_rockway on 2007-10-23
a mi me paso lo de ruby.

no me acuerdo que paquete instale, pero esto probablemente te sirva:

```
apt-cache search ruby | grep qt
```

lo de kdecore es la primera vez que lo veo... pero yo estoy en kde, asi que no tuve que instalar nada especial para usar amarok.

---

### Post by kowal on 2007-10-23
Creo que debería instalar automáticamente esos paquetes apt-get, synaptic o aptitude.

Pero se me ocurre que puede faltar python-kde3, python-qt3, libpythonize0, libqt0-ruby1.8, ruby o algún otro.

---

### Post by faktorqm on 2007-10-24
Hola, yo cuando un programa me tira ese tipo de errores, voy al gestor de paquetes, busco todos los paquetes que se llaman ruby, qt o tk, y instalo todo jajajajaj si, es un mal consejo y yo soy un kbzotas, pero me funciono todas las veces que lo hice!!!! y mas cuando a veces tenes que compilar cosas, que te dice que te falta, y lo instalas y no anda, bue, me bajo 600mb de cosas, y arranca sin error :D
es mas, con el apt on cd, me salvo para las proximas instalaciones xD igual no es la idea pero a veces encontrar el paquete correcto es imposible. un dia estaba compilando algo que me pedia gtk2+. no exisitia ningun paquete, ni parecido, que se llamara asi, asi que le di masa a todo lo que se llama gtk en el gestor jajajaja :P

---

