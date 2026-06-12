---
title: "Gran pregunta para los que saben..."
date: 2007-01-15
forum: Argentina Team
---

### Post by MeduZa on 2007-01-15
**Kernel**. como soy un noob de linux y esto me interesa mucho para dejar de serlo, leí mucho y cada vez entiendo menos, o mejor dicho tengo mas dudas. Me interesan algunas cosillas que trae esa nueva vercion de linux y ademas quiero investigar y aprender (linux es mi nuevo hobby).
tengo el kernel: 2.6.17-10-generic #2 SMP

**1)** ¿puedo poner el kernel 2.6.19.2 en mi Ubuntu edgy? (estoy **casi** seguro que si segun leí)
**2)** ¿si lo hago ganaria todas las cosas que soluciona / trae esa verción? (se supone que si, perooooo como no lo se, pregunto)
Segun leí, puede que pierda cosas que ahora tengo o andan, y es ahi donde no entiendo nada, **3)** ¿que gano y/o que pierdo al cambiar de kernel y usar uno que no es el que trae la distro?
Yo se que tendria que recompilar mis alsa y el driver de video pero eso es lo de menos, y lo tengo a hacer cada tanto que sale un update del kernel o algo parecido (uso los que estan en la web de alsa y no los que estan en los repos)
Yo cuando cambié de micro puse el 2.6.17.10 generic SMP desde los repos y solo tuve que ponerle el alsa y el driver de video y quedo todo tal cual estaba en el anterior (creo que el mismo pero i386 sin SMP) Incluso otras cosas que habia compilado a mano andaban sin problemas (eso tampoco lo entendi se suponian que no iban a andar segun lei :P )
a lo que voy es que segun lei ( o entendi quisas mal quisas bien) **4)** ¿es verdad que no voy a poder usar los repos normales?
Yo baje el kernel 2.6.19.2 y le hice la configuracion activando las cosas que queria y sacando las que no queria, no lo llegue a compilar por las dudas q aca pongo, pero estaba listo para hacerlo.
En caso de que lograra compilar y hacer bootear el nuevo kernel** 5)** ¿el anterior me quedaria en la lista de kernels a bootear? esto lo se hacer y ya lo he echo anteriormente solo es una duda que quiero aclarar antes de probar ya que de no andar o no gustarme solo tendria q "quitarlo" y seguria todo normal como estaba

en caso de que la 1 sea no, **6)** ¿que tendria que hacer para que ande con ubuntu tal cual anda la 2.6.17 ?

Si alguno tiene buen material donde sopar mas info que me la pase, lei bastante de como funciona el kernel y lo de las capas y todo eso pero no tengo a nadie mas a quien preguntarle y los unicos qur tengo son ustedes :)

Bueno voy a seguir leyendo en la web, a ver q encuentro acerca de kernels y ubuntu en particular, y ver que sale de este cuestionario que desde ya gracias por la ayuda y aclaracion de dudas :) espero le sirva a muchos

---

### Post by BlackHero on 2007-01-15
por ser tan nuevo en esto creo que no tendria que responder pero te respondo un poquito :P

yo tambien me canse de leer y leer la cosa es que tanto te puede mejorar ese nuevo kernel el sistema? tenes muchos problemas con tus sistema actual? creo que lo que deverias hacer es compilar bien tu actual kernel y asi tu sistema quedaria perfecto tal cual esta es mi opinion =)

---

### Post by felipelerena on 2007-01-16
Yo tengo el kernel 2.6.19.2 compilado en mi pc y la verdad que esta buenisimo, va mas rápido y además aproveche que lo compilaba para ponerle algunos drivers que me interesaban (como ser el que permite usar la ruedita del medio de mi teclado y etc.) si quieren saber como compilarlo hay un trhead bastante claro que lo explica [http://www.ubuntuforums.org/showthread.php?t=311158](http://www.ubuntuforums.org/showthread.php?t=311158)
**cualquier duda que tengan pregunten**. ah... podría aprovechar para traducirlo al espanish en algun momento.

> linux es mi nuevo hobby
JAJAJAJA. me rei mucho, no se por que.

---

### Post by MeduZa on 2007-01-16
> **felipelerena said:**
> Yo tengo el kernel 2.6.19.2 compilado en mi pc y la verdad que esta buenisimo, va mas rápido y además aproveche que lo compilaba para ponerle algunos drivers que me interesaban (como ser el que permite usar la ruedita del medio de mi teclado y etc.) si quieren saber como compilarlo hay un trhead bastante claro que lo explica [http://www.ubuntuforums.org/showthread.php?t=311158](http://www.ubuntuforums.org/showthread.php?t=311158)
**cualquier duda que tengan pregunten**. ah... podría aprovechar para traducirlo al espanish en algun momento.


JAJAJAJA. me rei mucho, no se por que.

gracias felipelerena esto es lo que necesitaba saber :) manos a la obra ;) despues les cuento como me fue

---

### Post by felipelerena on 2007-01-17
> gracias felipelerena esto es lo que necesitaba saber :smile: manos a la obra :wink: despues les cuento como me fue
suerte (?)... jajaj

---

### Post by felipelerena on 2007-01-17
cualquier duda si queres escribirme al gtalk o al mess ambos son felipelerena(arrrroba)gmail.com

---

### Post by MeduZa on 2007-01-17
> **felipelerena said:**
> cualquier duda si queres escribirme al gtalk o al mess ambos son felipelerena(arrrroba)gmail.com

I did it !!!!!!!!!

meduza@Xenoid:~$ uname -a
Linux Xenoid 2.6.19.2 #1 SMP Wed Jan 17 15:24:51 EST 2007 i686 GNU/Linux
meduza@Xenoid:~$ 

ya no soy mas una larba noob ya pase a gusano noob xD ya compile mi primer kernel y no dolio para nada :)
despues de 3 compiladas (15 a 20 minutos cada una) logre un kernel que bootee
despues de 5 logre sacar todo lo que no necesito.
en la 6 ya estoy metiendo casi todo lo que quiero en el kernel

tengo un problema se ve que los ic2 tienen que ser modulos si o si porque el lm-sensors me dejo de anda -.-
Basicamente lo que hice fue sacar todo lo que no tengo o no voy a usar nunca, sobre todo en la parte de drivers, saque muchas cosas (demaciadas xD ) pero es que solo tengo una nforce4 y un par de cachivaches mas, los alsa que estan ahi solo uso el de live!, lo que si deje son drivers para cosas enchufables, osea usb y otras, nunca se sabe cuando va a venir un amigo con un mp3 player sediento de mp3s, asi que algunas cosas las deje como modulo, las cosas que se que las tengo las puse en el kernel.

La verdad que el booteo ahora es demaciado rapido, me asombro, pense q ni se iba a notar, pero vuela, despues en el sistema en general, puede ser q este mas rapido pero no lo noto a simple vista (aun no hice nada intensivo) pero lo siento menos pesado, es a ojimetro pero se siente. 

Perdi el loguito de ubuntu con la barra de % naranja  T_T despues veo como lo reparo y de paso veo como se hace una nueva (el otro dia me tope con un how-to por aca)

Sugerencias:
el que tenga una placa de video nvidia no ponga los rivafb o nvidiafb porque despues no va a poder poner los drivers de nvidia nuevos, te sale un mensaje de error
Si tenes el linux en un SATA mete los drivers SATA en el kernel (en mi caso los SATA_nv) y no te olvides de hacerlo como me paso a mi o no te va a bootear, si lo tenes en un IDE ( PATA ) lo mismo no olvides poner eso en el kernel.
ahi demaciadas cosas que no sirven para nada ( por ejemplo token ring, x25, y cosas para computadoras que posiblemente nunca veamos) yo las quite, mi linux es de escritorio mas que nada y nunca voy a sacar una placa pci en hot, menos el micro y menos que menos las memorias, encontre una guia q mas o menos te decia q sacar y que poner pero perdi el link por salame ](*,) 
estaria bueno hacer una guia de que sacar y que poner porque el kernel tardaba unos 20 mins y yo tardaba 2 o mas horas en elejir q poner o sacar

sigo probando lo del lm-sensors a ver si lo hago re-andar

---

### Post by Benji86 on 2007-01-17
para el logo de ubuntu en el booteo fijate reinstalando el paquete usplash por synaptic que te hace una imagen nueva de booteo cuando lo configura (no estoy seguro si lo recuperaras pero no perdes nada)

---

### Post by MeduZa on 2007-01-17
> **Benji86 said:**
> para el logo de ubuntu en el booteo fijate reinstalando el paquete usplash por synaptic que te hace una imagen nueva de booteo cuando lo configura (no estoy seguro si lo recuperaras pero no perdes nada)

se reparo solo cuando quite el driver vesa y el ega16 que estaba probando :P

gracias de todas maneras lo que aun no me anda es el lm-sensors no me quiere andar el i2c-nforce2 y eso que lo detecta
ya probe de todas maneras, en el kernel, como modulo.
y me sale esto:
> meduza@Xenoid:~$ sudo sensors-detect 
# sensors-detect revision 1.413 (2006/01/19 20:28:00)

This program will help you determine which I2C/SMBus modules you need to
load to use lm_sensors most effectively. You need to have i2c and
lm_sensors installed before running this program.
Also, you need to be `root', or at least have access to the /dev/i2c-*
files, for most things.
If you have patched your kernel and have some drivers built in, you can
safely answer NO if asked to load some modules. In this case, things may
seem a bit confusing, but they will still work.

It is generally safe and recommended to accept the default answers to all
questions, unless you know what you're doing.

 We can start with probing for (PCI) I2C or SMBus adapters.
 You do not need any special privileges for this.
 Do you want to probe now? (YES/no): 
Probing for PCI bus adapters...
Use driver `i2c-nforce2' for device 00:01.1: nVidia Corporation nForce4 SMBus (MCP)
Probe succesfully concluded.

We will now try to load each adapter module in turn.
Module `i2c-nforce2' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.
...
....
...


cuando pongo sensors me sale:
> meduza@Xenoid:~$ sensors -s
General parse error


T_T

---

### Post by felipelerena on 2007-01-18
>  ya no soy mas una larba noob ya pase a gusano noob
COPADO!!!! congrats.
compilar el kernel exitosamente deberia ser el paradigma del paso de la adolescencia a la adultes o algo asi. JAJAJ

---

### Post by pump on 2007-01-18
> **felipelerena said:**
> Yo tengo el kernel 2.6.19.2 compilado en mi pc y la verdad que esta buenisimo, va mas rápido y además aproveche que lo compilaba para ponerle algunos drivers que me interesaban (como ser el que permite usar la ruedita del medio de mi teclado y etc.) si quieren saber como compilarlo hay un trhead bastante claro que lo explica [http://www.ubuntuforums.org/showthread.php?t=311158](http://www.ubuntuforums.org/showthread.php?t=311158)
**cualquier duda que tengan pregunten**. ah... podría aprovechar para traducirlo al espanish en algun momento.


JAJAJAJA. me rei mucho, no se por que.

Buenisimo ese link.
Me dieron ganas de probar, hoy voy a ver si compilo yo tambien y paso a la adultez :P

---

### Post by felipelerena on 2007-01-18
>  Me dieron ganas de probar, hoy voy a ver si compilo yo tambien y paso a la adultez :P
mmmm... lo veo complicado por tu parte... jajaja

---

### Post by pump on 2007-01-18
> **felipelerena said:**
> mmmm... lo veo complicado por tu parte... jajaja
Jaja. Bue, pero el kernel pude compilarlo :P

Linux XBoulevard 2.6.19.2 #1 Thu Jan 18 17:01:25 ART 2007 i686 GNU/Linux :)

---

### Post by MeduZa on 2007-01-19
parece que cree una onda compilera en el foro :D :biggrin:

---

### Post by screening on 2007-01-23
Aca esta el tutorial en español, lo traduje yo, cualquier error o correcion me avisan, no hay drama.
[http://laexprimidoradeneuronas.blogspot.com/2007/01/compilando-el-kernel-2619.html](http://laexprimidoradeneuronas.blogspot.com/2007/01/compilando-el-kernel-2619.html)

---

