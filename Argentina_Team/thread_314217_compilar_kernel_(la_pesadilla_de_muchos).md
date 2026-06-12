---
title: "compilar kernel (la pesadilla de muchos)"
date: 2006-12-07
forum: Argentina Team
---

### Post by lavaramano on 2006-12-07
compilar el kernel para el que jamas lo hizo puede parecer una pesadilla, despues de haberlo hecho varias veces no es tan doloroso.
para 'introducir' a aquellos con poca experiencia en esto:

[http://www.howtoforge.com/kernel_compilation_debian](http://www.howtoforge.com/kernel_compilation_debian)

ahi explican como compilar un kernel a la manera debian (tb sirve para ubuntu :KS)

lo unico, esta en ingles. :-?  estaria bueno traducirlo y meterlo en los howtos del futuro sitio de ubuntu-ar

saluditos.

---

### Post by DuckMan on 2006-12-07
estoy con linux hace casi 1 año, especificamente con ubuntu, pero nunca pude entender las ventajas de compilar un kernel, alguien me lo explicaria?

---

### Post by Nemesis Teufel on 2006-12-07
Asi brutamente con lo poco que se te puede decir esto:
El kernel es una parte esencial del sistema operativo; es el intermediario entre el software y el hardware, administra los recursos y cuando hay muchos programas, limita el acceso al hardware que mantiene cada uno.

Supongo que compilar el kernel con el tipo de procesador que uno tiene, optimiza el sistema y el uso del hard.

Completen los que saben..

---

### Post by kalel on 2006-12-07
esta bueno que posten esto, pk muchos de los que empiezan con ubuntu, como DUckMan que empezo hace 1 año, pero el tema de emepzar con ubutnu o distros sencillas es que no adquiris este tipo de conocimientos, a mi me vino muy bien empezar de lleno con gentoo en lo que tenes que compilar a lo loco, y en la instalacion compilas el kernel y asi te keda bien adaptado a tu hard =)

---

### Post by lavaramano on 2006-12-07
claro
yo la 1era vez compile kernel de 2.2 pasaba a 2.4 x_x!!! (como sufri esa vuelta, btw)

por ejemplo en breezy tuve que compilar el kernel para poder hacer funcionar al modem zyxel 630-c1 (el de speedy...)
hace poco tb, compile al kernel como 20 veces para poder hacer funcionar al dapper en una pentium 233 y como no tiene soporte para acpi y el kernel de dapper si, no podia booter entonces tenia que deshabilitarselo.
y blah.

en realidad es eso, poder aprovechar el hardware de tu maquina "al maximo".

---

### Post by BlackHero on 2006-12-07
gracias por la info eso voy a hacer =)

---

### Post by jpmorelli on 2006-12-07
Jamas pude lograr ni compilar el gtetris y voy a ponerme a compilar el kernel, pero pofavooo !!! jajaja, algún día...;)

---

### Post by daniminas on 2006-12-07
he compilado el kernel.. y siempre he querido que me quede con la imágen de Tux en la consola... nunca dí con esa opción.. ](*,)

---

### Post by lavaramano on 2006-12-07
@daniminas:
[http://bulma.net/body.phtml?nIdNoticia=1071](http://bulma.net/body.phtml?nIdNoticia=1071) aca explican eso que queres :P

[http://www.todo-linux.com/modules.php?name=News&file=print&sid=1201](http://www.todo-linux.com/modules.php?name=News&file=print&sid=1201)
sino aca tb, pero el de bulma.net me parecio mas completo

suerte con eso.

---

### Post by DuckMan on 2006-12-07
aja, entiendo

osea, por ej, yo tengo un escaner y una camara q no funcionan, podrian funcionar? (acer scanprisa 640p y una anycam de samsung)


mi grabadora hace poco tenia el mismo problema, pero descubri q solo graba con nerolinux

---

### Post by nbayiha on 2006-12-07
i think you can write in english so other people can benefit from it:confused: :confused: :confused: :confused:

---

### Post by Nemesis Teufel on 2006-12-07
> i think you can write in english so other people can benefit from it   

WTF?! 
The intention of this LoCo is the only proposit to comunicate about this SO in Spanish.. You have a great portion of the forum to speak English.. 

Espero vos enteder a yo..ok?

---

### Post by lavaramano on 2006-12-07
@nemesis: hahahah :KS

@duckman: no se, deberias fijarte en particular de tu scanner y tu camara.
es decir, el modem que a mi no me funcionaba, es porque le faltaba un modulo para modems conexant en el kernel para que cuando arranque el sistema operativo, pueda trabajar con los 'drivers' del modem que antes 'no existian' en el sistema operativo.

pero en cierta forma, si. es una de las razones por la cual compilar un kernel. 
no es 100% necesario, pero siempre viene bien saber esto porque te puede salvar de mas de un dolor de cabeza en el momento que todo se derrumba ;P


igualmente, si hay actualizacion de kernel. el ubuntu te lo baja y lo compila solo... asi que si no pensas meter mano en el sistema, hasta te diria que lo dejes pasar por alto (no lo recomiendo de todas formas)

---

### Post by DuckMan on 2006-12-07
> **nbayiha said:**
> i think you can write in english so other people can benefit from it:confused: :confused: :confused: :confused:

exactly, you have aaaallllll the forum for "english benefits"

Spanglish:

well, ahora entiendo, dudo q los haga funcionar pero bueno :P jeje por ahora no me muero, mas cuando estoy por comprar una multifuncion q OBVIAMENTE chequie su compatibilidad

---

### Post by daniminas on 2006-12-09
> **lavaramano said:**
> @daniminas:
[http://bulma.net/body.phtml?nIdNoticia=1071](http://bulma.net/body.phtml?nIdNoticia=1071) aca explican eso que queres :P

[http://www.todo-linux.com/modules.php?name=News&file=print&sid=1201](http://www.todo-linux.com/modules.php?name=News&file=print&sid=1201)
sino aca tb, pero el de bulma.net me parecio mas completo

suerte con eso.

Gracias... está todo hecho! :) .. ahora me gusta más mi arranque.. porque SI!.. pude compilarlo! :).. no se si viene al tema, pero el splash de ubuntu no me gusta mucho.. no sé, prefiero 'ver' lo que está haciendo ;)

---

### Post by Takmadeus on 2006-12-10
Yo aprovecho para plantear un problema.....

Recientemente recompilé el kernel (2.6.19) de kernel.org.... todo iba bién, es más todo funciona, pero no me deja accesar las particiones en windows..... si lo hago desde usuario me dice "solo el usuario root puede montar el dispositivo /dev/hda1 en /media/C" si lo hago como root me dice que /dev/hda1 ya está montado o está ocupado..... cuando uso el kernel normal si me deja accesar..... en fin, saben cual es el problema?.... como lo soluciono?

---

### Post by jpmorelli on 2006-12-10
> **nbayiha said:**
> i think you can write in english so other people can benefit from it:confused: :confused: :confused: :confused:

Perhaps other people don't know english, and they only know spanish.:neutral:

---

