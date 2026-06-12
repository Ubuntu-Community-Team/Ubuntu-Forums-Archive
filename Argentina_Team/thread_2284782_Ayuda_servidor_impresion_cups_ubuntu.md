---
title: "Ayuda servidor impresion cups ubuntu"
date: 2015-07-01
forum: Argentina Team
---

### Post by emilio9 on 2015-07-01
Hola, soy nuevo en el foro, disculpen si algo que publique esta mal o si no esta en el hilo correcto, necesito ayuda, tengo que configurar un servidor de impresion con cups, tengo una HP DESKJET 3515 y cuando la conecto la instalo y todo nunca manda a imprimir me dice " en espera- lista para usar" aunque le mande los archivos y en un momento me decia [COLOR=#111111][FONT=Times New Roman]PROCESANDO RECUPERABLE: el ordenador de red X esta ocupado (donde X es el ip de la impresora) 
Alguien me puede ayudar?[/FONT][/COLOR]

---

### Post by gmunioz on 2015-07-11
Verifica que este instalada la aplicación hplip y todas sus dependencias.
> sudo -i
apt-get update
apt-get install --reinstall hplip
Borra cualquier entrada para ésta impresora en Sistema---Administración----Impresoras.
Asegúrate de que la impresora está encendida y conectada. 
En caso de impresora en red wireless, ejecuta el Asistente de Configuración Wireless desde el menú de Configuración de la impresora.
Prueba ejecutar el Asistente de Configuración HP desde consola ejecutando:
> sudo -i
hp-setup 
Esto abrirá una ventana QT y te guiará a través de la configuración para todo tipo de impresoras. 
El escáner debería funcionar también cuando ésto esté hecho. 

Si esto no funciona, puedes hacerlo utilizando la aplicación impresoras de Ubuntu: 
En la ventana de Impresoras añade una impresora. 
En el asistente para Añadir una Impresora, haz uno de lo siguientes pasos:
Para impresoras USB, escoge una entrada bajo 'Usar una impresora detectada'
o selecciona la entrada seleccionada  'Utilizar otra impresora' debajo.
Para una impresora en red, selecciona 'Impresora en red/HP Jet``Direct' en 'Tipo de impresora', 
luego introduce la dirección IP de la impresora en el campo de 'URI'. 
Puedes obtener la dirección del menú de configuración de la impresora. 
El escáner funcionará sin hacer nada más.

---

