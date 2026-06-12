---
title: "Problemas con accesos directos"
date: 2015-05-07
forum: Argentina Team
---

### Post by sprbuli on 2015-05-07
Hola gente!!!! Espero puedan ayudarme y que sea de ayuda para otros...

 Tengo problemas con los accesos directos de carpetas que creo en el  Escritorio de lubuntu, estos aparecen con un icono de signo de admiracion y cuando lo quiero ejecutar con doble click, no pasa nada. 

Por consola entro como super usuario e ingreso esto:

ln -s  <DirOrigen >  <DirDestino>

Directamente me aparece un signo de admiracion. 

Este problema con aplicaciones no me pasa(ejemplo: firefox). Ejecutan sin ningun problema..

Otra duda es la siguiente,

intale una version de MATLAB me gustaria crearle un acceso directo para su ejecusion,
para ejecutarlo utilizo la siguiente linea por consola:

sudo sh /usr/local/MATLAB/R2011b/bin/matlab 

No puedo crearle un acc directo a ese archivo porque es un .sh y no ejecuta Matlab si le hago doble click sobre el mismo.

Cualquier guia me viene de 10 porque soy nuevo en esto..

Saludos...!!!

---

### Post by papibe on 2015-05-07
Hola prbuli.

Trata de crear un link especializado para el escritorio en vez de un link del sistema de archivos. [Aquí]("http://askubuntu.com/questions/67925/how-to-create-a-desktop-shortcut-in-unity") hay un ejemplo de como hacerlo.

Saludos,

---

