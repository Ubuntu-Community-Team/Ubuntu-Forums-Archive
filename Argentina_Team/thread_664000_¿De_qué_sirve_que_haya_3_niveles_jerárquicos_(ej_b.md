---
title: "¿De qué sirve que haya 3 niveles jerárquicos (ej: /bin - /usr/bin - /usr/local/bin)?"
date: 2008-01-10
forum: Argentina Team
---

### Post by v1ncent on 2008-01-10
Tal ves los desarrolladores de pura cepa le vean completo sentido, pero desde mi perspectiva solo parece ser para separar la importancia o propósito de cada archivo que use determinado programa, es decir, para que el desarrollador sepa para que sirve cada cosa o en donde encontrar lo que se busca 'fácilmente', generando -de alguna manera- menos confución.

¿Si todos las carpetas que contienen binarios se simplificaran a SOLO /bin, esto traería algún problema al sistema?
 - - - - -
Sé que a muchos la sola idea les parece nefasta, pero he estado pensando que Linux necesita cambios que le permitan más versatilidad, sin perder potencial ni facilidad para los desarrolladores, sino todo lo contrario.

El mayor problema que veo en esta jerarquía de sistema es que gran parte de los directorios destinados al funcionamiento de Aplicaciones parecen perfectos para un sistema que no ostenta a un alto nivel de flexibilidad, es decir:
Es espectacular para un programa como -por ejemplo- el Firefox el tener un lugar 'a mano' para separar sus binarios, archivos de configuración y demás... PERO, en un sistema con decenas de programas se complica, no solo por los conflictos entre librerías (que es uno de los atrasos a mi parecer), sino por como se dispersan los componentes de X aplicación por TODO el sistema.

Mi propuesta es desplegar esa jerarquía directorios dentro de la carpeta del mismo programa, es decir:
Dentro de la carpeta del firefos tienes a /etc, /bin, /sbin, /man, /lib... En esas carpetas están todos los componentes que necesita la aplicación, y linkean a sus correspondientes carpetas en el sistema, sin generar conflictos.

De esa forma se siguen categorizando los componentes de las aplicaciones y se puede seguir teniendo compatibilidad con la jerarquía de directorios estándar.
Más sobre mi idea, inspirada en GoboLinux (en un principio), entre otras cosas: [B][http://docs.google.com/View?id=dff6bkv5_58gj9c5vgb]("http://docs.google.com/View?id=dff6bkv5_58gj9c5vgb")
 - - - - -[/B]
Sé que puede sonar rebuscado, pero no lo es. Confío en que puede ayudar mucho a TODOS, puede significar una evolución en los sistemas Linux.
El problema es que se necesita un buen debate, con gente abierta a pensar en ideas nuevas, AÚN sin estar del todo convencidos del cambio... Actualmente solo se dice 'No me gusta' y se acabó, se quedan recios en esa posición.

Espero que haya respuestas serias, porque generalmente suelen responder algo como **'hacéte tu propia distro'**, pero el problema es que --los que pensamos de esta manera-- no queremos algo para nosotros, sino que buscamos un avance que ayude a todos, porque sin esa <b>unión</b> puede que Linux nunca llegue a ser una alternativa con la cual los usuarios no tengan que preocuparse por muchas cosas, es decir, hay que hacer un sistema fuerte, eficaz, flexible (más allá del kernel, que es maravilloso), en donde no haya esa separación entre los que tengan tal distro, entre los que usen tal o tal 'Package Manager'.

Me gustaría que los responsables y desarrolladores de las grandes distros y de Linux en general se reunieran y pensaran en hacer cambios (junto a la Linux Fundation) como para lograr, por ejemplo:
Que algo como 'PackageKit' sea un estándar, haciendo que todas las distros tengan soporte para Yum, APT y demás, **al mismo tiempo**.
Crear estándares en ciertas cosas es clave para el avance, sin significar el estancamiento de la diversidad en Linux, sino uniendo a las distintas alternativas, proporcionando una BASE en común.

Saludos!

---

### Post by faktorqm on 2008-01-10
Por lo que leo no sos programador. Asi que te voy a decir 3 cosas:

1) el nucleo de linux NO es maravilloso. si queres ver algo realmente maravilloso proba cualquier sistema basado en BSD. (freeBSD es uno de ellos)
2) Ya existe un proceso de estandarizacion hace bastantes años y es para estandarizar todo lo que vos nombras. [http://es.wikipedia.org/wiki/Linux_Standard_Base](http://es.wikipedia.org/wiki/Linux_Standard_Base)
Tambien es cierto que se arrastran problemas de compatibilidad, por eso hacen las carpetas, y demas blabla. Será que deberias haber leido esto antes de postear? [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
3) con respecto a lo de la flexibilidad no estoy de acuerdo. Me parece que vos tenes ganas de un install shield y de agregar o quitar programas... un "uno" que haga todo en todas las distros, me equivoco? 
Salu2!

---

### Post by v1ncent on 2008-01-10
1) No estoy de acuerdo.
2) La LSB es un buen proyecto, pero en mi opinión le falta mucha iniciativa. Todos lo conocen, pero realmente a pocos le importa. Por eso los que colaboran con la LSB toman el camino con más posibilidades de aceptación, y ese camino suele ser una mi*rda la mayoría de las veces. Como por ejemplo, el basar todo el proyecto para la estandarización de la instalación de software en usar /opt para 'no joder a nadie'.
Recién ahora veo que hablan de un proyecto más innovador, con más expectativa (ver los últimos dos meces en la lista de correo del proyecto de '[Packaging]("https://lists.linux-foundation.org/mailman/listinfo/packaging/")' de la LSB).

Me alegra que me hayas dado un link con info (o un manual de 300 paginas, que con tiempo voy a leer), pero hubiera sido de más ayuda que (con un poquito de voluntad) me dijeras en unas lineas en qué parezco estar equivocado.
3) **SÍ**, efectivamente estás equivocado.
No se trata de "--quiero hacer todo parecido a Windows para ser feliz e instalar todo con *siguiente > siguiente* sin saber a donde van las cosas ni cómo funciona mi sistema"... Se trata de encontrar formas de solucionar problemas.
Claro, pareciera ser que vos nunca vas a admitir que existen problemas en este sentido, pero ciertamente los hay. NO porque esté mal hecho, sino porque podría ser mejor.

Si no me equivoco, el FreeBSD (u alguna de las otras 2 variantes de BSD) están implementando una forma de instalación que permite ubicar todos los componentes de X programa en un sólo lugar (sea una carpeta o un *bundle*, no me acuerdo en este momento)... Que lindo AVANCE, yo aprecio a BSD, y ciertamente soy agnóstico en cuanto a sistemas operativos, pero apuesto por Linux, por su filosofía y por sobretodo porque la gente lo necesita; instituciones gubernamentales, escuelas, y gente común elije Linux cada vez más, y la mayoría de ellos siente que podría ser mejor en algunos aspectos (lo que -repito- **NO SIGNIFICA cambiar la filosofía del sistema ni sacarle potencial al sistema a costa de obtener más usabilidad**)...
Con eso ultimo me refiero a que un cambio bien pensado no significaría perder esa cualidad de invitar a los usuarios a entender al sistema lo más posible.
Yo confió de que si le das a los usuarios un sistema sólido, confiable y flexible, ellos se se animarán con entusiasmo (aunque sean novatos) a descubrir el sistema.

Si hablamos de Windows sería diferente, porque los usuarios saben que muchas veces las cosas no funcionan, no se sienten muy confiados ni logran conocer el sistema aunque se lo propongan, y si lo logran entonces renuncian a seguir haciéndolo, porque les resulta **frustrante** el hecho de que muchas cosas no funcionen o sea simplemente ineficaz...
... Por eso, no hay que pensar que en Linux (u otros sistemas basados o inspirados en UNIX) puedan llegar a generarse los típicos usuarios de Windows, porque son cosas totalmente diferente los sistemas, y por ende los usuarios también..

Saludos!

---

### Post by brunovecchi on 2008-01-11
Mi muy mísera interpretación del problema:
Linux es un sistema operativo pensado para multiusuario. El hecho de que hoy en día mucha gente (como yo) lo esté usando en una computadora personal es una circunstancia. De ahí que haya una carpeta /home/{usuarios} y luego... el RESTO. Yo convivo con el RESTO como si fuera una inhóspita selva con la cual no simpatizo pero convivo. Salvo alguna visita al /etc/X11/Xorg.conf, algún /usr/share/doc/* o algo por el estilo, dejo que Apt y el resto de los muchachos manejen todo eso. Yo supongo que esa es la actitud de alguien que es el 99% de las veces usuario, y el 1% (o menos) administrador.
Con respecto a la unificación de las carpetas orientadas a programas, creo que eso depende un poco de la filosofía del programa en si. El famoso "Estilo Windows", en el que cada aplicación quiere hacer TODO, genera programas más grandes y con menos interrelación que el resto. En Linux, una aplicación puede ser simplemente una implementación de GUI utilizando aplicaciones de consola independientes. (Ejemplo, el aspell es un corrector ortográfico de consola que puede ser implementado por TODOS los programas que quieran hacer corrección ortográfica). Por esta hecho es que creo que cobra sentido tener una (unas) carpeta */bin con todas las aplicaciones.
De todas maneras, entiendo muy bien lo que vos decís; en mi caso particular, yo intento lo más posible utilizar el Synaptic para la instalación de aplicaciones por el manejo limpio de paquetes. Si hay un programa que debo compilar o instalar manualmente, lo pienso dos, tres, cuatro veces. Porque no tengo el conocimiento suficiente como para hacerlo de manera sistemática y después poder volver a localizar los programas y desinstalarlos LIMPIAMENTE. Supongo que debe haber una manera; sin embargo, la selva asusta de noche.

---

### Post by clasificado on 2008-01-12
Las ubicaciones de los archivos dentro de las carpetas es circunstancial a la distribución. 

Ubuntu parte de debian, por lo que ahi es un buen lugar para comenzar a buscar los motivos de la jerarquización actual.

Hay distribuciones mas radicales que otras en el orden de las carpetas.

Yo creo que tiene mucho que ver con la filosofia de software libre: "Si tenes ganas de hacerlo distinto, hacelo nomás. Ahora si queres que se implemente de forma masiva vas a tener que convencer a toda la comunidad". Es tan distinto que hay quien no lo tolera.

Clasificado

---

### Post by pante on 2008-01-14
**[[COLOR="#0000ff"]Filesystem Hierarchy Standard[/COLOR]]("http://www.pathname.com/fhs/2.2/")**

"...Estas guías intentan dar soporte a la **interoperabilidad** de las aplicaciones, herramientas de administración de sistema, herramientas de desarrollo y scripts, así como una mayor **uniformidad** de documentación para estos sistemas..."

[[COLOR="#0000ff"]3.4 /bin : Essential user command binaries (for use by all users)[/COLOR]]("http://www.pathname.com/fhs/2.2/fhs-3.4.html")

"[FONT="Courier New"]/bin[/FONT] contiene comandos que pueden ser usados tanto por el administrador del sistema como por los usuarios, pero que son requeridos cuando ningún otro sistema de archivos está montado (e.g. en modo de usuario único)..."

[[COLOR="#0000ff"]4.5 /usr/bin : Most user commands[/COLOR]]("http://www.pathname.com/fhs/2.2/fhs-4.5.html")

"[FONT="Courier New"]/usr/bin[/FONT]  Binarios que no se necesitan en modo de usuario único..."

[[COLOR="Blue"]4.9 /usr/local : Local hierarchy[/COLOR]]("http://www.pathname.com/fhs/2.2/fhs-4.9.html")

"...La jerarquía [FONT="Courier New"]/usr/local[/FONT] está para ser usada por el administrador del sistema cuando instala software localmente. Es necesario protejerla de ser sobreescrita cuando el software de sistema sea actualizado..."
________________________________________

No tengo conocimientos técnicos suficientes como para afirmarlo rotundamente pero:

De lo anterior es evidente que las jerarquías están para mantener las cosas ordenadas/separadas y para evitar que **cualquier cambio** en el sistema (aún los cambios locales) modifiquen **todo** el sistema. Hace al sistema más seguro.

Pensemos en un sistema muy vulnerable: Windows 98. Cada vez que se instalaba un programa nuevo se te modificaba "Archivos de programa", "Windows", "Windows\System", etcétera. Si actualizabas el sistema (incluso si reinstalabas el mismo sistema, sin formatear) la mayoría de los programas instalados dejaban de funcionar. Los Windows de la familia NT (2000, XP) imitan la manera de funcionar UNIX con la carpeta "Documents and settings", donde se guardan las configuraciones para todos los usuarios (All users) y para cada usuario particular, todo fuera de la carpeta "Windows". ¿No te preguntas por qué Microsoft copió eso?

Saludos

---

### Post by felmasper on 2008-01-22
Jo soy brasilero, mi español no es bueno :-) Pero voy hablar un poco.

Separa-se /bin de /usr/bin porque muchos administradores quieren separar los programas en otras particiones (disk partitions) pues /usr/bin es muy grande. Entonces en /bin fican los programas más basicos, necesarios a la montagen de otras particiones, posiblemente lo /usr/bin.

Lo mismo se puede hablar de /lib y /usr/lib. De facto, administradores acostumbraran-se a separar lo /usr en otra particione.

/usr/local/lib, hablaran aqui, es para los programas que no fueran instalados por las vias normales. En ubuntu, el metodo correcto es apt-get o aptitude o synaptics. Se no es un pacote .deb, mejor no instalar en /usr/bin, pues vas olvidar-te de los arquivos instalados na ora de la desinstalacion. Vay a ver lo programa llamado "stow", que gerencia ese tipo de instalacion manuale.

Perdona-me mi pessimo español.

---

