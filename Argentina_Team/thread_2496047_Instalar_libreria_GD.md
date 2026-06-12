---
title: "Instalar libreria GD"
date: 2024-03-12
forum: Argentina Team
---

### Post by franjgg on 2024-03-12
Buenas,

Pues eso estoy intentando instalar la librería GD para convertir imágenes desde PHP, la cosa es que lo he intentado de varias formas y nada.

Tengo ubuntu 16.04 con PHP 7.4.13, decir que no tengo demasiados conocimientos con bash.

Lo he intentado instalar de este modo: 

sudo apt-get update
sudo apt-get install php7.4-gd
sudo systemctl restart apache2
service apache2 restart

Obtengo esta respuesta:

unable to locate package php7.4-gd
couldn't find any package by glog 
couldn't find any package by regex

He leido que debía actualizar el repositorio o añadir el adecuado, y he probado: 

sudo apt-add-repository ppandrej/php    
sudo apt-get update
sudo apt-get install -y php7.[FONT=inherit]4[/FONT]-gd

Pero sigo con el mismo resultado.

He probado también a instalar la versión php7.0-gd pero nada.

A ver si alguien puede orientar un poco, todo lo he hecho desde conexión vnc y siendo root.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293484&stc=1[/IMG]

---

