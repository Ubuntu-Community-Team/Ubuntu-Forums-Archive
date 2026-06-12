---
title: "Problemas con Wine Windows Emulator y Registros de Sistema."
date: 2008-03-31
forum: Argentina Team
---

### Post by APHOLOS on 2008-03-31
Estimados Amigos,

En primer lugar los saludo y les aclaro que soy totalmente nuevo en Linux y para ser más preciso en Ubuntu.

Solicito, de ser posible, con mi más sentida sencillez, me ayuden con lo siguiente:

Acabo de instalar Wine Windows Emulator porque me parece haber entendido que permite operar aplicaciones para entornos Windows que de otra manera no podría correr en Linux, con el propósito de poder utilizar SmartFTP.

El problema es el siguiente:

1. Instalé el Wine Windows Emulator.
2. Descargué el ejecutable SmartFTP.exe (32 bit) y lo ejecuté.
3. Hasta aquí todo en orden.
4. Quiero iniciar el SmartFTP, haciendo doble click en el acceso directo o bien desde Aplicaciones, Wine, Programas, SmartFTP... y no sucede absolutamente nada... no inicia el programa para nada.
5. Ahora bien, al querer desintalar el SmartFTP lo hago desde Aplicaciones, Wine, Uninstall Wine Programs... y el acceso al SmartFTP sigue apareciendo en el menu Aplicaciones.
6. Si me expliqué bien, alguien puede decirme cómo hago para Instalar/Desinstalar el SmartFTP con Wine de un modo efectivo?

Por favor perdonen mi ignorancia... son las 2:31 AM del LUN 31 de Marzo 2008 y aún no logro resolver esta situación.

Por último:

[LIST] Alguien puede decirme si existe algún modo de limpiar los registros en Ubuntu de modo que al Instalar/Desinstalar software no quede ningun registro del mismo en mi PC?
[/LIST]

Desde ya gracias por vuestra paciencia y espero noticias.

Un abrazo y un saludo para todos!

---

### Post by margori on 2008-03-31
Voy a darte una mano y mas que nada voy a intentar mostrarte como comportarte frente a linux.

> 1. Instalé el Wine Windows Emulator.

1- Wine no es un emulador. (Wine Is Not an Emulator) Es una implementacion de windows en unix. Lo programas corren nativamente.
2- Esta bien, pero utilizalo como ultimo recurso y para programas que no tienen una version para linux.

> 2. Descargué el ejecutable SmartFTP.exe (32 bit) y lo ejecuté.

3- Para que querrias usar un cliente FTP, si en ubuntu ya viene un cliente. Anda a Lugares -> Conectar con el servidor y pones los datos del servidor FTP en cuestión. Te crea una carpeta que tratas como cualquier otra carpeta.

Admito que hablo con solo teoria, ya que no lo he hecho y llamo a otra persona que si lo haya hecho que lo confirme, por favor.

4-Por otro lado tenes algo ya listo para linux sin necesidad de sudar con wine. FireFTP y gFTP son algunos, aunque no tengo referencias de ellos y algunos están en los repositorios de Ubuntu.

> 5. Ahora bien, al querer desintalar el SmartFTP lo hago desde Aplicaciones, Wine, Uninstall Wine Programs... y el acceso al SmartFTP sigue apareciendo en el menu Aplicaciones.

5- Normalmente, wine no saca los iconos del menu principal. Lo tenes que hacer a mano en Sistema -> Preferencias -> Menu principal.

> existe algún modo de limpiar los registros en Ubuntu

6- No existe ese termino "Registro" en linux. Lo más parecido son las carpetas ocultas de tu home (carpeta de usuario) En nautilus (el visor de carpetas) las podes ver apretando CTRL + h.

7- Lo mas comun para instalar y desinstalar programas es usar archivos .deb, que contienen la información para instalar y desinstalar totalmente un programa o parte de el. Te voy a dejar a vos que busques más información de esos paquetes.

8- Usa synaptic si sos muy nuevo. Es como un supermercado. Tenes mucho de lo que necesitas en un principio, luego te vas a buscar mas programas por otros lados más especializados.

> son las 2:31 AM del LUN 31 de Marzo 2008 y aún no logro resolver esta situación.

9- Tendrás que armarte de paciencia y leer mucho.
10- Linux es diferente a windows. Antes de buscar lo que se parece a windows, busca saber como es linux. Es como una novia nueva: si la comparas con la anterior, la cosa no anda. Busca como es ella individualmente.

Espero te sea util.

(En realidad me tome la molestia de contestarte bien, porque preguntaste muy bien. No todos lo hacen)

---

### Post by MeduZa on 2008-03-31
> **APHOLOS said:**
> Estimados Amigos,

En primer lugar los saludo y les aclaro que soy totalmente nuevo en Linux y para ser más preciso en Ubuntu.

Solicito, de ser posible, con mi más sentida sencillez, me ayuden con lo siguiente:

Acabo de instalar Wine Windows Emulator porque me parece haber entendido que permite operar aplicaciones para entornos Windows que de otra manera no podría correr en Linux, con el propósito de poder utilizar SmartFTP.

El problema es el siguiente:

1. Instalé el Wine Windows Emulator.
2. Descargué el ejecutable SmartFTP.exe (32 bit) y lo ejecuté.
3. Hasta aquí todo en orden.
4. Quiero iniciar el SmartFTP, haciendo doble click en el acceso directo o bien desde Aplicaciones, Wine, Programas, SmartFTP... y no sucede absolutamente nada... no inicia el programa para nada.
5. Ahora bien, al querer desintalar el SmartFTP lo hago desde Aplicaciones, Wine, Uninstall Wine Programs... y el acceso al SmartFTP sigue apareciendo en el menu Aplicaciones.
6. Si me expliqué bien, alguien puede decirme cómo hago para Instalar/Desinstalar el SmartFTP con Wine de un modo efectivo?

Por favor perdonen mi ignorancia... son las 2:31 AM del LUN 31 de Marzo 2008 y aún no logro resolver esta situación.

Por último:

[LIST] Alguien puede decirme si existe algún modo de limpiar los registros en Ubuntu de modo que al Instalar/Desinstalar software no quede ningun registro del mismo en mi PC?
[/LIST]

Desde ya gracias por vuestra paciencia y espero noticias.

Un abrazo y un saludo para todos!

hola xD te comiste un par de pasos, primero instalas el wine
despues como se hace en windows, tenes que instlaar algunas librerias necesarias, para ello te recomiendo que instales el WINEDOORS, una vez que le pongas las librerias necesarias (mete todo lo que te parezca necesario, VB runtime, dlls y otros) instala el internet explorer aunque no lo bajas a usar (solo por las librerias)

una vez que tenes eso te deberia andar cualquier o casi cualquier cosa.

pero para ello te conviene hacer una configuracion para el EXE que vas a ejecutar, por ejemplo decirle que Windows queres que simule (XP, 2000, 98, 95, Vista, 3.11 etc)

Si algo no te anda, tenes que ver el error ya que solo te lo tira en consola, capas te esta pidiendo un DLL

para correr wine en consola (recomendado si no nada de una)

abris la consola
haces cd hasta llegar a donde esta el EXE (algunos programas no andan si no estas parado en su path) y ahi pones:

wine nombre.exe

con eso te va a arracar el programa y ademas te va a tirar informacion util y si crashea te va a decir porque fue.

Suerte

---

### Post by APHOLOS on 2008-03-31
Gracias por vuestra paciencia y por las respuestas.

Me pondré a hacer los deberes entonces.

Un saludo a ambos.

---

