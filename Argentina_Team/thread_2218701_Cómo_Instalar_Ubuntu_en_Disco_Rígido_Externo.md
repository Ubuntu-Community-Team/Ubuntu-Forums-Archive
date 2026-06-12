---
title: "Cómo Instalar Ubuntu en Disco Rígido Externo?"
date: 2014-04-21
forum: Argentina Team
---

### Post by nacho4 on 2014-04-21
Buenas tardes gente.
Mi pregunta está en el título...

Hace poco me compré un disco externo USB de 1TB y me gustaría tener instalado el Ubuntu en el mismo.
Cuáles son los pasos que tengo que hacer?

Seguro estarán cansados de responder siempre las mismas preguntas, pero la verdad no me gustaría perder un disco de $1300 como me pasó con 2 pendrives de 16 GB.

Si se pudieran meter varias distros en un mismo arranque, estaría de lujo, como para ir variando.

Desde ya, Muchas Gracias.
[CENTER][IMG]https://mesajilhnos.com/files_productos/galeria/10703-GALHDE1-2.jpg[/IMG][/CENTER]
Atte. Nacho.

---

### Post by asterix77 on 2014-04-22
Te cuento mi experiencia con mi disco de un tera: primero que nada una vez descargada la iso de Ubuntu, la grabé en un pendrive (o cd si prefieres); luego apagué mi pc; luego para no confundirme con tanto disco duro, desconecté todos los HD internos. Acto seguido conecté mi pendrive e ingresé a la bios para asegurarme de que arranque mi pendrive. Una vez que ubuntu arranca, conecté mi HD externo, y al cabo de unos segundos me lo reconoció. Posteriormente, abrí el programa Gparted he hice 4 particiones en mi disco externo del siguiente modo: una partición de 40 gigas para el directorio raiz (/) con formato ext4, otra de 4 gigas para la memoria swap, otra partición de 200 gigas para mi directorio personal (/home), y el resto lo dejé tal cual (formato ntfs). Una vez realizado esto, comencé con la instalación que la hice de tipo personalizada, seleccionando las particiones realizadas para montar / mi /home y mi swap.

La gracia de todo esto, es que ando con mi ubuntu portatil por todos lados, lo conecto a una laptop, pc de escritorio, y tengo todo tal cual con todos mis programas y configuraciones.

Saludos y espero que te sirva

---

