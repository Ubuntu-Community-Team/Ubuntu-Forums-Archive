---
title: "Help!!! No puedo configurar el modem en Ubuntu"
date: 2007-06-25
forum: Argentina Team
---

### Post by gpone on 2007-06-25
Hola gente les escribo de nuevo porque sigo con el mismo problema, no puedo configurar la conexion a internet (uso dial up). En la lista de hardware el modem me aparece como instalado, pero cuando me quiero conectar usando wvdial (uso wvdial porque no me deja instalar el gnomeppp) no me deja porque dice que no encuentra el modem en ningun puerto. 
El modem es un Intel 536ep si me pueden dar una mano se los agradeceria byeee.

---

### Post by faktorqm on 2007-06-27
Hola, lo mas probable es que no lo tengas bien instalado.

Driver original de Intel:

[http://downloadmirror.intel.com/6497/eng/intel-536ep-4.69.tgz](http://downloadmirror.intel.com/6497/eng/intel-536ep-4.69.tgz)

Readme de Intel: 

[http://downloadmirror.intel.com/6497/ENG/readme.txt](http://downloadmirror.intel.com/6497/ENG/readme.txt)

Guias que encontre por ahi:

[http://www.ubuntu-es.org/index.php?q=node/46348](http://www.ubuntu-es.org/index.php?q=node/46348) (la saque de aca)

*********************************************************************************************
Ya está resuelto el asunto, aquí los pasos tomados del wiki de ubuntu howto y la configuracion para GNOME PPP:

1.- Descargar la version mas nueva del driver en:
[http://linmodems.technion.ac.il/packages/](http://linmodems.technion.ac.il/packages/)
2.- Extraer con tar xzf name.tgz
3.- Abrir una terminal
4.- Entrar al directorio
5.- make clean
6.- make 536
(crear el archivo .ko)
7.- Verificar la creacion del archivo .ko con:
ls -l Intel536.ko
(Regresará los atributos del archivo)
8.- Copiar el archivo al directorio correcto
sudo cp Intel536.ko /lib/modules/$(uname -r)/kernel/drivers/char
(le pedirá el password de instalación 'administrador')
9.- sudo depmod -a
10.- sudo modprobe Intel536
11.- sudo cp /etc/modules /etc/modules.backup
12.- sudo sh -c "echo Intel536 >> /etc/modules"
13.- Instalar GNOME PPP
14.- Ejecutar GNOME PPP
(Aplicaciones/Internet/GNOME PPP)
15.- Click en Configuracion
16.- Rellenar lo siguiente:
Dispositivo: /dev/536ep0
Tipo: Modem analogico
Velocidad: 460800
Linea telefonica: Tono
Volumen: Bajo
Esperar por tono de marcado: Si
17.- En la pestaña Red no hay cambios
18.- En la pestaña Opciones:
Minimizar: Si
Reconectar automaticamente: Si
Abortar conexion si la linea esta ocupada: Si
Abortar conexion si no hay tono de marcado: Si
Comprobar linea: No
Comprobar camino por defecto: No
19.- Click en Cerrar
20.- Escribir nombre de usuario, contraseña y telefono
21.- Click en Conectar
22.- A Navegar

La misma manera de instalar que en la version 6.10 pero con drivers actualizados desde el link exacto:

[http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-536EP-2.56.76.0_23_02_2007.tgz](http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-536EP-2.56.76.0_23_02_2007.tgz)

Esa pagina es perfecta para drivers, ya se pudo, les escribo desde la version 7.04 

*********************************************************************************************

Espero que te sirva, y si lo logras, escribi como lo hiciste. salu2!

---

### Post by Sepero on 2007-07-07
Intel 536ep modem - Ubuntu 7.04
[http://ubuntuforums.org/showthread.php?p=2930571](http://ubuntuforums.org/showthread.php?p=2930571)

---

