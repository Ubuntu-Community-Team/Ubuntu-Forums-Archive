---
title: "Problemas al instalar ubuntu en hd ide"
date: 2008-04-18
forum: Argentina Team
---

### Post by mansaneitor on 2008-04-18
Hola a todos soy nuevo en el foro...Quería consultarles un temilla XD:

Tengo un hd s-ata de 160gb con windows xp instalado, y tmb un hd ide en el cual quiero instalar ubuntu (y posteriormente configurar compizfusion, pero bueno con eso me volveré loco luego de instalarlo jeje)... el tema es q finalmente instalé ubuntu 8.04 edición 64bits (alternate, release candidate) en el hd ide...

pero el problema es el siguiente, luego de esperar a q se instale todo (elegí utilizar todo el disco en las opciones de instalación... y todo lo demás creería q lo configuré bien)... me tiraba un error q decía "no se pudo instalar el grub..." (mi objetivo es instalar ubuntu en un hd y al otro dejarlo como esta, es decir con windows... sin instalar ningún gestor de arranque como lo es el "grub", lo cual no sé si es posible)...
luego de buscar y tocar todo, encontré una opción q decía "no instalar ningún gestor de arranque" (o algo similar, no lo recuerdo textualmente), despues de esto me salió un cartel q decía q la instalación había finalizado... entonces se reinicia la pc... y en el momento en el q esta booteando el hd ide me tira el error "Reboot and Select proper Boot device...":confused::(, reinicie mil veces, le toqué todo en la bios y nada, ni idea que puede ser... (windows sigue funcionando normalmente cuando quiero q botee desde el sata)

si alguien tiene alguna idea... desde ya muchas thx ;)

off: x si ayuda en algo mi pc es la siguiente

amd64 3000+
mb asus k8v-x
1gb ddr 400mhz
2 hd's (1 sata de 160 y 1 ide de 80gb)
ati 9600xt

off2: me leí toda la documentación y no encontré nada&#8230; x eso mi consulta
off3: es la primera experiencia q tengo con linux... 0 idea =/

off4: existe manera de instalar ubuntu sin el grub? (lo digo pq lo estoy instalando en un hd aparte y tenía entendido q el grub es utilizado principalmente cuando hay particiones con distintos S.O en un mismo hd)

---

### Post by faktorqm on 2008-04-18
Hola, tenes un par de problemas conceptuales, asi que voy a intentar desaznarte al respecto. GRUB es un gestor de arranque, esto es, no solo es multi-SO sino que aparte linux lo necesita para arrancar SI O SI. No podes ponerle al bios que arranque derecho por que no va a andar nunca.
Ahora bien, vos no querias instalar el grub, pero lo tendrias que haber hecho no en el sata, sino en el ide. Se entiende? Vos cdo arrancas la compu te arranca con el sata y win y nadie se entero de nada. Cuando queres arrancar tu linux, le pegas al F8 (f8 era? no me acuerdo) o a la tecla que te permita elegir de donde bootear y ahi te arranca el grub, luego ubuntu. 
Repasemos, tenes que instalar el grub, pero en el ide. No en el sata. De todas maneras vas a seguir teniendo que arrancar con la tecla. por que no lo instalaste de una en el sata? si es lo mismo! lo dejas para que arranque automatico en win y listo. Cuando queres arrancar vos lo cambias a mano. Salu2!

---

### Post by vk-cdg on 2008-04-18
> **mansaneitor said:**
> off4: existe manera de instalar ubuntu sin el grub? (lo digo pq lo estoy instalando en un hd aparte y tenía entendido q el grub es utilizado principalmente cuando hay particiones con distintos S.O en un mismo hd)

No necesariamente, yo tengo en un disco de 160 a "las ventanitas del Sr. Gates" y en uno de 250 a Ubuntu y uso el grub.
En su momento pensé en no instalarlo y arrancar con la opción de buteo del bios (así lo tengo en el trabajo) pero me pasaba (en el trabajo) que le daba al botón de encendido, me ponía a charlar y me olvidaba del F9 del bios y arrancaba en Windows. Finalmente terminé poniendo el grub con un delay de 30 seg para mis "colgadas" matutinas. :)

---

### Post by mansaneitor on 2008-04-18
es que mi miedo es el siguiente: leí x allí que si tenes 2 hd's (en uno ubuntu y en otro windows) con grub instalado, si retiras de la pc el hd que tiene linux, entonces grub tira error y no carga windows, es decir a partir del momento en el que instalo grub no me puedo despegar más de ubuntu xD... 

lo que yo no quiero es que mi pc se vuelva ubuntu-dependiente ajja =P, la onda sería que funcionen los 2 en paralelo sin que uno dependa de otro =P

si yo instalo grub como me dijiste (faktorqm) en el sata para no tener q andar apretando f8, dps no hay problemas si lo quiero desinstalar?, como sería la onda 

off: grax faktorqm y vk-cdg x responder =)

off2: traté de instalar grub en el ide y me decia que era imposible :| WTF asd, tuve q poner q no lo instale... y de nuevo lo mismo jaja "Reboot and Select proper Boot device..."

---

### Post by faktorqm on 2008-04-18
Hola, no se es muy caprichoso el grub. Te recomiendo que uses supergrubdisk.

[www.supergrubdisk.org](www.supergrubdisk.org)

Para hacer lo que queres hacer vos, se hace asi (yo lo hice en el laburo cuando me di cuenta de lo que te diste cuenta vos, saque un disco y la compu no arrancaba jajaja)

1) Le pones en el bios que arranque desde el ide.
2) Instalas el grub en el ide, y le decis que tenes el windows en el sata y el linux en el ide.

Entonces, analicemos que pasa :) Si arranco la pc desde el sata, arranca. Si arranco la pc desde el ide, me pregunta si arranco con el sata, o con el linux, pero el windows no lo toca. entonces puedo arrancar todo. El dia que necesite sacar el disco, saco el ide, le digo al bios que arranque desde el sata y todo solucionado! Espero haberte aclarado el panorama, cualquier cosa NO DUDES en preguntar. Salu2!

---

### Post by Elrengo on 2008-04-18
Yo antes lo tenia configurado como vos decis, y como te comento FAKTORQM, grub es indispensable para UBUNTU, 

pero una solucion facil para vos, si es que queres ubuntu a tu manera, es desconectando tu hdd sata antes de instalar ubuntu, 

asi elegis desde el bios quen bootea y listo

:guitar:

---

### Post by Elrengo on 2008-04-18
PARA SOLUCIONAR LO SEGUNDO.

o sea si optas instalar grub para q te de a elegir windows y ubuntu

y algun dia sacas el disco ide, windows por si solo no levanta

la solucion es bootear desde el cd de windows xp

entrar a la consola de recuperacion de errores

y ahi ejectuar el comando   FIXMBR

con eso win levanta solito sin porblemas
:guitar:

---

### Post by mansaneitor on 2008-04-18
ahora me quedo todo claro...

vuelvo de la facu y pruebo la que dijo faktorqm =D

thx a lot ;)

---

### Post by mansaneitor on 2008-04-19
bueno traté de instalar ubuntu de nuevo...
al grub no hubo forma de instalarlo (me decia q era imposible instalarlo en una pantalla roja), así q tuve q instalar "LILO" como gestor de arranque, pero fue peor el remedio q la enfermedad AJJAJA...

cuando carga lilo, lo carga en modo texto... y 0 idea de q tengo q hacer para launchear el modo gráfico, no se si hay algún comando o como es ='( alguna idea? =P

edit: perdon x el doble post

---

### Post by faktorqm on 2008-04-20
Ahhh bueno!! Si te aparece la misma pantalla que aparece en wikipedia ([http://es.wikipedia.org/wiki/Lilo_(Linux](http://es.wikipedia.org/wiki/Lilo_(Linux))) desde ya te estoy comentando que ese es la parte "gráfica" del lilo... jajjajaj
Intenta actualizar de lilo a grub desde el ubuntu mismo siguiendo el tutorial que aparece en la pagina ([http://ubuntu-ar.org/soporte/comos/reinstalar-grub](http://ubuntu-ar.org/soporte/comos/reinstalar-grub))
Salu2!

---

### Post by mansaneitor on 2008-04-20
me exprese mal me parece... osea, puedo elegir cargar linux... pero no me boteaa :S llega a un momento q no boteaa, no pude ni con supergrubdisk... no puedo llegar al entorno gráfico de ubuntu no se si se entiende

es decir resumo mi problema

-grub no me lo deja instalar xD (me tira una pantalla roja y me dice q no esta el /target/ algo así)
-lilo me lo instalo una vez (dps de reinstalar no me dejo x el mismo error de target...)
-supergrub disk me hace lo mismo q me hizo lilo... me carga hasta una parte y no carga más :S

ahora lo raro de todo esto es q con supergrubdisk me cargo el ubuntu perfectamente, UNA SOLA VEZ pero despues de un rato se me colgo :S y bueno nunca mas me booteo el hd...

toy sospechando q tengo una versión bugueada... pq no puede ser man :S

aca [http://ubuntuforums.org/showthread.php?t=753478](http://ubuntuforums.org/showthread.php?t=753478) hay otro loco q le paso lo mismo :S::S:S::S re pwneante, y ya probé todo ='( es mi "desvirgada" en linux jAJAJ y la estoy re comiendo jovenesSSs =P

off: windows me sigue funcionando perfectamente, así q creo q problema de mi hard no es :S voy a ver q onda ahora en 4 días q sale la versión final =(

---

### Post by faktorqm on 2008-04-20
Parece que hay algún otro problema además del de software. O sea, bajo ciertas circunstancias Grub deja de andar... a mi me paso en varias oportunidades y a veces "es de facil resolucion" y otras "es un bardo". Que quiero decir con esto? que a veces es una papa y otras tenemos que estudiar como funciona :S

Yo lei y recontra re lei la documentacion del grub y no pude solucionar mi problema. No hubo manera, pero quiza en este post tengas la solucion:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

(si t cuesta el ingles, decime y t lo traduzco, aunke te voy a insultar por eso... :KS)
Parece que se ha empezado a desaznar un poco este tema, por Dios que terminen Grub 2.....

Una teoria de lo que puede estar pasando, es que el grub reconozca mas el lugar a donde esta ubuntu, por que segun decis cuando le das a windows arranca perfecto. Ahora bien, con el supergrubdisk siempre te va a arrancar ubuntu y windows. Eso dalo por descontado. El tema pasa por averiguar cual es el error, es decir, si tu particion por algun motivo es inaccesible, o si vos estan tomando mal la referencia de las particiones. Lo que me paso a mi en su momento, que me rei mucho cuando lo descubri, era que (no me acuerdo bien) a vos te decia la particion 1 es la 1. Entonces yo iba al grub y ponia 1 y naranja fanta. Entonces descubri leyendo la documentacion que grub tomaba la particion 1 como 0. Y asi fui descubriendo muuuuuuchas cosas. No te digo que leas la documentacion, pero de ultima, arranca con el live cd y postea el archivo "/boot/grub/menu.lst". Vamo a darle masa al pancho ese del grub! :P:P:P Salu2!

---

