---
title: "Lineage2 Kamael y Wine"
date: 2008-03-27
forum: Argentina Team
---

### Post by Omnibilion on 2008-03-27
Hola a todos. Estoy muy contento de haber instalado Ubuntu y probar que funciona a las mil maravillas. Como todo usuario nuevo, tengo 2 millones de preguntas, pero, empesemos de a poco. Instale Wine para poder jugar al Lineage2 Kamael, ya que, Segun la pagina de WineHQ funciona sin problemas. Copie el juego a una carpeta y lo actualice mediante Wine sin inconvenientes. Pero, cuando arranco el juego, aparece una ventana que dice textualmente "The game may not be consistant because AGP is deactivated. Please activate AGP for consistancy." Segun lo que llego a comprender, algo referente a la placa de video me esta faltando. Ahora bien, que es lo que falta? Cargar los drivers de mi placa en el Ubuntu o cargar los drivers en el Wine? Vale aclarar que hace solo 2 dias que instale Ubuntu y todavia no estoy muy familiarizado que digamos.
Toda ayuda sera agradecida (y si funciona, voy a subir mi foto de usuario feliz, je)

---

### Post by sajnox on 2008-03-27
Bienvenido!!!

Vamos por lo basico, que placa de video tenes?? Configuraste algo o simplemente la detecto ??

---

### Post by TopoCiego on 2008-03-27
> **Omnibilion said:**
> Hola a todos. Estoy muy contento de haber instalado Ubuntu y probar que funciona a las mil maravillas. Como todo usuario nuevo, tengo 2 millones de preguntas, pero, empesemos de a poco. Instale Wine para poder jugar al Lineage2 Kamael, ya que, Segun la pagina de WineHQ funciona sin problemas. Copie el juego a una carpeta y lo actualice mediante Wine sin inconvenientes. Pero, cuando arranco el juego, aparece una ventana que dice textualmente "The game may not be consistant because AGP is deactivated. Please activate AGP for consistancy." Segun lo que llego a comprender, algo referente a la placa de video me esta faltando. Ahora bien, que es lo que falta? Cargar los drivers de mi placa en el Ubuntu o cargar los drivers en el Wine? Vale aclarar que hace solo 2 dias que instale Ubuntu y todavia no estoy muy familiarizado que digamos.
Toda ayuda sera agradecida (y si funciona, voy a subir mi foto de usuario feliz, je)

Hola!!! bienvenido! espero que no te desesperes como me paso a mi, que me habia puesto loko con el tema de mi placa de video...mira si tenes una ATI o una NVIDIA tenes que descarga e instalar los drivers con [ENVY]("http://albertomilone.com/nvidia_scripts1.html"), descargalo y tenes gran informacion ademas te va a ir  guiando por el tema de la instalacion y descarga del driver correspondiente.

bueno espero que te sirva... :D

---

### Post by Omnibilion on 2008-03-27
Bueno, instale el Envy, reconocio la placa de video (Gforce 6200 AGP), pero sigue apareciendo la misma ventana. En Ubuntu quedo configurada lo mas bien, pero aparentemente el Wine, o el juego, no se entera

---

### Post by MaReaDo^ on 2008-03-28
primero baja esto: [http://www.threelights.de/page/projects/d3dx9_xx_dll_files/D3DX9_dll_update.zip](http://www.threelights.de/page/projects/d3dx9_xx_dll_files/D3DX9_dll_update.zip)
descomprimilo y abris el setup y te instala los ultimos dlls de directx, o la mayoria por lo menos (osea en wine te lo instala)
despues antes de instalar kamael tenes que buscr un server, no podes jugar al oficial desde ubuntu con wine porqeu no se puede usar el gameguard
aca te paso dos links de la carpeta system del kamael version live Eng 828 parcheado sin gameguard:
[http://www.megaupload.com/?d=WTPP81GA](http://www.megaupload.com/?d=WTPP81GA)
[http://dump.ru/files/n/n191780067/](http://dump.ru/files/n/n191780067/)
[http://depositfiles.com/en/files/2844894](http://depositfiles.com/en/files/2844894)
para que funcione mejor y no haya crashes del wine podes deshabilitar del l2.ini "UseHardwareTL" y "UseHardwareVS" 
te dejo el link de un system como los de arriba pero con esto deshabilitado:
[http://www.megaupload.com/?d=9E907V24](http://www.megaupload.com/?d=9E907V24)
el server que elijas si no tiene una carpeta system modificada y te pide modificar el archivo host esta en /etc/hosts
poens en la consola sudo gedit /etc/hosts
(esto lo saque ed la pagina de wine)

supongo que esos pasos los hiciste
te recomiendo para abrir el juego poner en la terminal desde tu home: WINEDEBUG=-all wine '../.wine/drive_c/Lineage II/system/l2.exe'
creo que es asi la ruta, no tengo el juego para probar

proba y contanos

---

