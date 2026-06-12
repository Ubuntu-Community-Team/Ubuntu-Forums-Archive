---
title: "Error al instalar xubuntu 7.04!!!"
date: 2007-06-18
forum: Argentina Team
---

### Post by ezequiel_sail on 2007-06-18
Hola Gente,
al tratar de instalar xubuntu, me tiró la primera vez un error que no anoté pero algo así como falló al instalar el sistema de archivos, o imposible instalar el sistema de archivos. Pero dandole adelante me pidió que defina el particionado del disco, le puse usar todo el disco, modo guiado..y me salió que no había espacio suficiente o algo asi (es un disco de 40 gb, e iba a usar 1.4 gb para swap). Los intentos posteriores de empezar de cero, aunque sea para anotar bien el tipo de errores que me tira y poder comentarles con datos más específicos, fallaron todos porque detecta la partición anterior y dice que es preciso corregirla para continuar, pero no encuentro como. Probé de editarlas y cambiar los tamaños, pero nada..además me dice que debo configurar una partición como raíz, pero tampoco sé como. 
Al que pueda orientarme, le agradezco desde ya.
Datos de la pc: Athlon 2200, placa asus a7n266vm, ram 512, disco maxtor 40 gb.

Ezequiel

---

### Post by ezequiel_sail on 2007-06-18
Yo de nuevo...como me mata la ansiedad de verlo funcionando, y no tuve respuestas aun, seguí probando e investigando en la net, y me enteré que configurar la raiz es simplemente escribir "/" en mount (creo haber entendido bien) y con eso y asignando 33 gb a la particion ext3 y 1 gb a swap, logré avanzar hasta que me tira nuevamente el error (paso 7 de 7) solo que ahora copié lo que dice:
"falló la creación del sistema de ficheros ext3 en la particion #1 de maestro IDE (hda). Por otro lado en la ventana del administrador de archivos dice "20 elementos 144 kb" "espacio libre 34,2 gb". No sé de donde salen esos 34,2 gb de espacio libre ya que cuando empieza me dice que mi disco tiene 41,3 gb, pero por las dudas basado en esa info fue que asigne solo 33 gb a la particion #1 y 1 gb a swap...para no pasarme de esos supuestos 34,2 gb. No se si estoy confundiendo peras con manzanas, no se donde estoy parado..asi que ahora sí lo único que puedo hacer es esperar que alguien me tire una mano.
Gracias desde ya!

Ezequiel

---

### Post by Al_maverick on 2007-06-18
podes hacer lo siguiente. borrar todas las particiones, y asignarle al root 15GB y y el resto dejarlo sin particionar. El particionado del resto lo podes hacer despues, y asi te evitas complicaciones. Al swap dejale 2GB y estas mas que tranquilo. Fijate si asi podes instalarlo.
Otra cosa, que estas usando para instalar? El Live CD o el alternate? Cuanta RAM tenes?
Yo tuve problemas instalando xubuntu cuando la PC tenia menos de 196MB de RAM. Tuve que usar el alternate, que es en modo texto, pero mas confiable para casos complicados.

---

### Post by ezequiel_sail on 2007-06-19
Muchísimas gracias Al!

probé de asignar solo 15 gb y 2gb para swap como me dijiste y funcionó!!! Me rechazó la primera vez diciendo que tenia que ser usuario root pero la siguiente anduvo. Ya terminó la instalación y ahora estoy agregando algunas cosas via synaptic. Lo que no encontré por ningún lado en synaptic fue el easy ubuntu, para agregar el tema multimedia de un saque. 
Los mantengo al tanto de como sigue todo. 
Salu2

Ezequiel

---

### Post by Apipote on 2007-06-19
Ezequiel, es un bug que esta bien documentado en Xubuntu Festy. Las 3 distros ubuntu, xubuntu, y kubuntu, tienen sus "cositas" que las corrigen cada 6 meses. Creo que aún linux no puede superar a windows en facilidad. No es para alguien que no sabe nada de computación.
Cuando instalás xubuntu, anda con el explorador ( thunar ) y hace esto home-preferences-advanced-configure y ahi destildá los 2 primeros "mount" cerra y listo, hace lo que quieras con las particiones.
Saludos..

---

### Post by ezequiel_sail on 2007-06-20
Gracias Apipote!
si bien ya lo habia resuelto en base a la sugerencia de Al-maverick, tengo en cuenta lo que me decis para cuando instale xubuntu en la proxima pc. Obviamente que todavia es  mas complicado linux que windows para un lego como yo, pero con ganas de aprender, y sobre todo con la buena voluntad y excelente onda de todos los que dan una mano desde el foro, es una alternativa viable...con la satisfaccion que te da poder elegir y no depender de los antojos de Bill...
Cuando encuentre los acentos y arroba ser un poco mas prolijo, jeje. (Y eso que eleji Latinoamerica como opcion de teclado!)
Saludos

Ezequiel

---

