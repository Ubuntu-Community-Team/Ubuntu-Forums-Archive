---
title: "D'altre fòrum [la leyenda de Ubuntu]"
date: 2007-06-20
forum: Catalan Team
---

### Post by prostata on 2007-06-20
Què en penseu d'aquesta apreciació sobre la distro Ubuntu???, la poso tal qual està escrit, i no tradueix-ho res per tal de no "desvirtuar" el context:


Los que se quedan, disfrutarán de su tiempo libre, y aprenderán todo cuanto puedan y les caiga en sus manos. Algunos, ante lo mal que pinta Windows Vista (muchísimos recursos de máquina que obligan a un nuevo ordenador y la imposibilidad del pirateo) habrán optado por dar el paso definitivo a Linux. Puede que hayan oído de las excelencias de Ubuntu/ Kubuntu como me sucedió a mí. Así que quise probarlo para ver qué había en torno a la leyenda. Tropecé con un sistema operativo apto para quienes comienzan, por su facilidad de uso, pero poco más.

Kubuntu me decepcionó. La versión KDE (mi escritorio favorito) era fea de narices. Nunca había visto nada tan horroroso en mi vida. Para colmo, aquí el Centro de control se llama Preferencias. Pero no funciona. Hay un bug inmenso en Dapper. Y tienes que llamas, desde shell, a kconsole para que puedas personalizarte el entorno. Eso sí, después de haber pasado por Kde-look.org y haber cambiado el tema de escritorio, el inicio de sesión, el splashimages de la careta de entrada en Grub... Que por cierto, el gestor de arranque se esconde por sí solo. Hay que tocarlo para añadirle lo que le falta: menús visibles, una contraseña MD5 y varios parámetros para que el llamado “Recovery Mode” opere con permisos de lectura y escritura. Que no entiendo por qué Ubuntu denomina a eso “Recovery Mode” cuando sólo trabaja en modo lectura.

Pero hay montones de fallos. Kubuntu está optimizado para su propio KDE y por eso va rápido. Pero un simple “apt-get install kde” para instalar el verdadero KDE te demuestra que ahí se termina la optimización. Además, Ubuntu/ Kubuntu no respeta los estándares. Arranca en modo runlevel 2 por defecto, pero tienes entorno gráfico. ¿No se supone que el llamado runlevel 5 es para el entorno gráfico? Así que busca el etc/rc2.d que hace referencia al runlevel 2 y elimina o deshabilita con una K el daemon gdm o kdm. Si cada cual hace lo que quiere en Linux, mal vamos.

Si se deshabilitan las X es con la finalidad de convertir a Ubuntu/ Kubuntu en servidor. Pero cuando se le instala la plataforma eBox, o se intenta instalar LAMP y otros servicios, el sistema operativo se vuelve inestable, con continuos cuelgues.

Tampoco se soportan el arranque de daemos concurrentes desde el fichero rc. No pido que haga esos arranques inmediatos de Gentoo, pero al menos que venga preparado para shell. Tampoco sirven para nada las personalizaciones en Autostart desde Preferencias de Kubuntu, porque sólo se pueden tocar desde Nano o vi, ya que no añade el “Type=Application” que permite que esté allí, una vez más, mi amado Yakuake.

Un desastre. Aún no entiendo cómo hay legiones de seguidores de Ubuntu/ Kubuntu. Supongo que por su facilidad, si no se le exige demasiado. Una distro para novatos, pero poco más.

Así que vuelvo a mi Linspire y Debian. Todo funciona a la primera. Todo es estable. Linspire está personalizado, y debería pagar por CNR, pero tocando sources.lst, puedo disponer de los repositorios de Debian, sin problemas. Y al disponer de drivers propietarios no tengo problemas con los drivers de Nvidia, ni tengo que matarme con ndiswrapper para que reconozca mi tarjeta wireless.

Afortunadamente para muchos, Linspire ya cuenta con versión gratuita, Freespire, eso sí libre de CNR y de drivers propietarios. Freespire podrá convertirse, sin lugar a dudas, en el perfecto competidor de Ubuntu/ Kubuntu, con una distro estable y muy comprobada. Sus campañas de marketing no serán tan efectivas en Europa, como lo puedan ser en América, pero ello no es óbice para reconocer su superioridad.

A todo esto, esta misma semana aparecía la primera beta de un driver que permite la lectura/ escritura en particiones NTFS de Windows XP bajo Linux. Nada de activar el módulo experimental en el kernel de Linux para acabar comprobando que sólo funciona medianamente bien en Windows 2000; ya tenemos un driver open source con reconocimiento de escritura en NTFS. Un buen punto de partida para las futuras Live CD que surjan con este driver.

Hay trabajo para este verano con Linux. Así que, de verdad, querido lector, que te recomiendo elijas una distribución y comiences a estudiarla en profundidad. Da igual cuál sea, mientras te encuentres a gusto; como puedes ver se augura un precioso futuro para este magnífico sistema operativo. ¡Aprovecha el verano!

Nada más por el momento. Nos vamos a refrescar a las playas de Mallorca, y esperamos que todos los lectores puedan sobrepasar este calor europeo en piscinas y playas, aprendiendo todo cuanto puedan en esas tardes de ocio. Gracias por estar siempre ahí y nos vemos en septiembre.

Por Carlos Mesa
Director técnico de Seguridad0®
Fuente

---

### Post by scrooge_74 on 2007-06-20
Es la opinión de un usuario.

Dapper lo encontré bastante bueno después de usar Debian, Feisty me facilita ciertas cosas.  Sobre LAMP server puede que quiso instalarlo sobre la version Desktop y no sobre la server.

El ntfs driver funciona muy bien (experiencia propia)

El Recovery Mode lo he visto resolver algunos problemas cuando se cometieron errores de configuración.

En mi opinión van por buen camino, pero no a todos les resulta igual

---

### Post by crazyserver on 2007-06-20
Aix.. akestes opinions... sense crear flames, a mi mp'anava a la mar de bé la Dapper i crec que es una de les versions més bones i estables.. tot depeén de l'ordinador on s'executi suposo...
A viam si aquest home és el senyor Bill disfressat...;)

He trobat l'original a: [http://www.elistas.net/lista/informativos/archivo/msg/115/](http://www.elistas.net/lista/informativos/archivo/msg/115/)
Per qui vulgui saber més!

---

### Post by PellRoja on 2007-06-20
Simplement la seva opinió , respectable com totes les altres.

com molt be diu, tot el que esmenta son coses tecniques que l' usuari novell no veu casi. I kde per alguns serà lleig per altres maco.

La meva opinió és que ubuntu per a novells es la més adient. Tampoc he provat moltes altres, però ubuntu s' ha dedicat a simplificar les coses.  Qui vulgui alguna cosa en especial, tindra la seva distro dirigida en aquell tema. Com és Debian com a servidor, per la estabilitat, o Gentoo per els que volen aprendre com funciona tot el sistema.

Un usuari novell, realment el que busca es un sistema ple de pijades per defecte, com més millor, seguretat per si sola, que ell no hagi de fer res, i que les guies no passin de dobleclick, que no els i facin tocar molta consola.

en difinitiva, el millor sistema, i que el novell no hagi de fer res.

simple opinió:p

---

