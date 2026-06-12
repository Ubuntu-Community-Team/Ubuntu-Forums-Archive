---
title: "He instalado Hardy Heron! Mi experiencia, pros y contras"
date: 2008-03-31
forum: Argentina Team
---

### Post by margori on 2008-03-31
Estimados amigos:

Voy a proponer un hilo para las experiencia argentina en la instalaciónde Hardy Heron. Así que paso a contar la mia, ya que me animé a instalar el beta.

Descargué con wget la versión 64 bits desktop desde la Universidad Federal de Paraná, Brasil, porque quería utilizar un servidor cercano. Debo decir que no era muy estable la conexión y varias veces se cortó pero wget se recuperaba perfectamente y continuaba la descarga.

Mientras tanto estaba haciendo los backups correspondientes y planeando la nueva disposición de la particiones y los archivos, ya que por un lado migraba de 32 a 64 bits y por otro necesitaba que las carpetas de usuarios no estuvieran duplicadas por el arranque dual Windows/Ubuntu.

Finalizó la descarga, verifique la suma MD5 y era felizmente era correcta, a pesar de la instabilidad de la descarga.

Quemé un CD con lo bajado.

Arranque la compu con el liveCD. Lo primero y es un Pro es que me pidio elegir idioma, luego decidir si instalar directamente o arrancar el SO.

Por error elegi la opcion de instalar, pero me habia olvidado de cambiar las particiones. Cancelé la instalción y directamente paso al SO.

Otro Pro es que GParted (administrador de particiones) se puede usar en el liveCD, así que movi, agrande y achique lo necesario y le di a aplicar los cambio. Lo principal era no perder la información de mi home, asi que cree una particion dedicada al home, la formatee a ext3 y movi todas las carpetas ahí, incluidas las ocultas.

Listas las particiones, mande a instalar. Proceso sin problemas y con mates en el medio, aunque en realidad nunca finalizo y me pidio resetear. Asi que yo manualmente cerre el programa y resetee.

La compu inicio sin problemas. Pantalla de login. Entro sin problemas y para mi sorpresa, todo estaba en el mismo lugar donde lo habia dejado. Tenia mi configuración de tema, iconos, programas al inicio, etc.

Cree los otros usuarios, pero no me aceptaba que la carpeta home de ese usuario existiese, así que tenia que renombrar la carpeta, crear el usuario y volcar toda la información, evitando que se hagan cambio de propietario y permisos. La verdad muy engorroso, debería aceptar la carpeta se existe, de manera que ese nuevo usuario tenga su configuración de una.

Configuré la red y habilite los repositorios correspondientes: main, restricted, universe, multiverse, security, updates, backports y partners.

Baje la información de paquetes e instale los controladores de NVidia. Todo sin problemas.

Resetee. Compiz sin problemas, sonido sin problemas.

Pedi las actualizaciones, y como contra, ya tenia que descargar 100MiB.

Lo más destacable es Firefox 3b4, anda que es una divinura, muy rapido, pero aun no tengo todos los plugin que me gustan. Será cuestión de esperar.

Lo que no me gusta es el policykit. Aunque piola, aun no está integrado con todas las aplicaciones (todavia están aquellas que usan gksudo) y cada vez te pide la contraseña (a diferencia de gksudo que no te la pide por 15 minutos)

Como información al margen, descargue la version 1.11 de etx2ifs para windows. En esta version las carpetas que comienzasn con "." son tratadas como ocultas, de modo que apunte en windows la carpeta mis documentos a la home de mi ubuntu, y logre que los mismos archivo y directorios esten disponibles en ambos SOs.

Bueno, eso es todo. Largo pero lo tenia que contar.

Nos vemos. Suerte.

---

### Post by PatoDB on 2008-03-31
Que buena experiencia!

Un amigo tambien instalo Hardy Heron y tambien quedo sorprendido!

Yo por mi parte no voy a instalar hasta que salga la version oficial, no soy muy experto como para manejarme en versiones Beta.

Y por lo pronto, estoy empezando a leer sobre Back-Ups de paquetes instalados y demas, para cuando salga 8.04... :)


Exitos!!!

---

### Post by sajnox on 2008-03-31
PatoDB,

Si bien siempre es aconsejable tener un backup hecho, la instalacion la podes hacer desde el SO andando normalmente, no es necesario pisar la instalacion que ya tenes hecha.

---

### Post by margori on 2008-03-31
No se puede hacer un backup de los paquetes instalados, ya que al actualizar el SO se pisan los paquetes anteriores. Lo que si se hace es hacer una lista d elos paquetes que ya tenes instalador para que despues sea más rápido dejar la compu como antes, aunque no hay garantías que esten todos los paquetes o que mantengan las dependencias.

---

### Post by sajnox on 2008-03-31
> **margori said:**
> No se puede hacer un backup de los paquetes instalados, ya que al actualizar el SO se pisan los paquetes anteriores. Lo que si se hace es hacer una lista d elos paquetes que ya tenes instalador para que despues sea más rápido dejar la compu como antes, aunque no hay garantías que esten todos los paquetes o que mantengan las dependencias.

Tal vez estoy equivocado pero el programa AptonCD te hace un backup de los paquetes instalados y te lo podes quemar en un cd para usar como repositorio en otra maquina

---

### Post by --Lutari-- on 2008-03-31
Justo que Instalo el Ubuntu 7.10 Gusty Gibbon Sale el Hardy Heron ¬¬

¿Como haré para Actualizarlo a la Nueva Versión?

---

### Post by sajnox on 2008-03-31
> **--Lutari-- said:**
> Justo que Instalo el Ubuntu 7.10 Gusty Gibbon Sale el Hardy Heron ¬¬

¿Como haré para Actualizarlo a la Nueva Versión?

Cuando la nueva version este disponible, el update manager te dara la opcion de actualizar. Tarda un buen rato en bajar todo y lo instala.

Ya esta !!! viste que facil

---

### Post by guisheca on 2008-03-31
El aptoncd te hace un backup de los paquetes instalados, pero sólo los que se encuentran en caché. Cuando instalas un programa mediante paquetes, el sistema primero descarga el paquete luego lo instala. El paquete descargado no se borra (a menos que lo hagamos manualmente o que la cantidad de paquetes sobrepase un límite que desconozco). Aptoncd copia esos paquetes que están en caché y crea un repositorio en formato .iso.
Aclaro esto porque si son como yo, que no tengo un disco grande (40gb) esos paquetes no los conservo y el aptoncd no puede hacer nada en ese caso. Lo que si se puede hacer es, en ves de borrarlos como yo, ir copiando los paquetes a medios opticos en la medida que los vayamos descargando.
Saludos.

---

### Post by niko_3100 on 2008-03-31
y como borramos los paquetes descargados? sudo apt-get clean y con autoclean? o de otra forma??

---

### Post by guisheca on 2008-03-31
Con sudo aptitude clean, el comando para apt-get no se como es.

---

### Post by margori on 2008-04-01
La otra muy buena a mi ver: Flash con sonido en Firefox.

Aun no he probado el Java Runtime, pero seguro tambien tiene sonido...

---

### Post by margori on 2008-04-02
Estoy teniendo problemas con Hardy. Creo que se cuelga el Xorg aunque no estoy seguro cuando y porque. La computadora se inutiliza totalmente.

Asi que concluyo que un beta no es para computadoras que tiene que funcionar o funcionar.

Hardy beta, beba con moderacion.

---

### Post by malbecar on 2008-04-03
> **--Lutari-- said:**
> Justo que Instalo el Ubuntu 7.10 Gusty Gibbon Sale el Hardy Heron ¬¬

¿Como haré para Actualizarlo a la Nueva Versión?

Por si todavia no lo hiciste, aca va el link que detalla todo el proceso:

[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

La contra, tarda mucho en bajarlo.

---

### Post by Apipote on 2008-04-04
Alguien tiene idea si en Hardy Heron, existen ya drivers nativos de linux, que funcionen como deben, y que soporten la despreciable placa wifi Broadcom ??
Gracias y slds

---

### Post by niko_3100 on 2008-04-04
Che no se porqeu decis despreciable, esta bien tenes razon tube que meterle drivers de windows pero me anda mejor en linux que en windows la broadcom y tiene  muy buena señal.

---

### Post by leo_rockway on 2008-04-04
> **Apipote said:**
> Alguien tiene idea si en Hardy Heron, existen ya drivers nativos de linux, que funcionen como deben, y que soporten la despreciable placa wifi Broadcom ??
Gracias y slds

Yo venía usando bcm43xx y ahora pasaron a b43. Ambos drivers me funcionaron siempre bien.

Nunca probé ndiswrapper porque no me interesó la idea.

---

