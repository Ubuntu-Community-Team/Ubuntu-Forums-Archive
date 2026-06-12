---
title: "No puedo leer archivos php con Lamp en Feisty"
date: 2007-08-11
forum: Argentina Team
---

### Post by matog on 2007-08-11
Gente, instalé el servidor LAMP en Feisty y andaba todo de mil maravillas. Php y mysql, perfectos. Toque algo (no se que....) y ahora, cada vez que quiero cargar un archivo php en mi servidor, me lo quiere bajar.

Probé instalando y desinstalando el lamp mil veces y nada...[Acá]("https://help.ubuntu.com/community/ApacheMySQLPHP")
dice algo, pero no solucionó nada...

Como hago para borrar todo, que no queden rastros de nada, y poder instalar limpiamanete de nuevo lamp?

Gracias!

Aclaro: YA lei [este ]("http://ubuntuforums.org/showthread.php?t=515133&highlight=parse+php+files")post y no pude solucionar nada.
Ahora se enloquecio apache2 y cuando le doy restart me tira:
>  * Forcing reload of web server (apache2)...                                                                                                                        apache2: Syntax error on line 186 of /etc/apache2/apache2.conf: Syntax error on line 6 of /etc/apache2/mods-enabled/php.conf: Cannot load /etc/apache2/modules/libphp5.so into server: /etc/apache2/modules/libphp5.so: cannot open shared object file: No such file or directory


---

### Post by lavaramano on 2007-08-11
si tuviera mas idea de apache, te ayudaria (quasarfreak esta aca con nosotros en cordoba, despues le pregunto, el sabe mas de eso).

pero por lo pronto te puedo sugerir que pruebes con xampp, de apachefriends.org
simplemente bajas un tar.gz y lo descomprimis en /opt
despues le das:
sudo /opt/lampp/lampp start y arranca.

---

### Post by Hei Ku on 2007-08-11
postea esos archivos de configuracion, quizas haya algo que de una pista del error.

---

### Post by matog on 2007-08-14
Como dice lavaramano, probé con el xampp y funciona perfecto.

Gracias!

---

### Post by facundocorradini on 2007-08-14
> **matog said:**
> Como dice lavaramano, probé con el xampp y funciona perfecto.

Gracias!

Pues entonces hacele caso a los consejos de seguridad que te dá el XAMP...yo pensé q era paranoia, hasta el día en que un colega me empesó a divertirse instalandome cosas remotamente....
tratá de mantenerte al tanto con las actualizaciones... 
este soft no se actualiza automáticamente y podés llegar a tener problemas....

---

### Post by el_itur on 2007-08-15
Xampp está bien para un entorno de testeo, que me parece que es lo que vos estás buscando.

Si necesitas algo menos _enlatado_ te recomiendo en synaptic busques la opción de marcar paquetes por tareas y allí buscá Servidor LAMP o algo así.
Te baja apache PHP MySQL y casi todas las dependencias generales, después podés ir agregando paquete por paquete en función de tus necesidades.

Es una configuración optima para servidores de producción.

Saludos

---

### Post by jozelo on 2007-11-07
> **lavaramano said:**
> si tuviera mas idea de apache, te ayudaria (quasarfreak esta aca con nosotros en cordoba, despues le pregunto, el sabe mas de eso).

pero por lo pronto te puedo sugerir que pruebes con xampp, de apachefriends.org
simplemente bajas un tar.gz y lo descomprimis en /opt
despues le das:
sudo /opt/lampp/lampp start y arranca.

Despues de dos semanas de estar tratando de instalar LAMP de muchas maneras finalmete esta funciono de maravilla y a la primera de verdad muchas gracias

De la pagina

[http://www.apachefriends.org/en/xampp-linux.html#374](http://www.apachefriends.org/en/xampp-linux.html#374)
descargas el fichero tar
y lo descomprimes
sudo tar xvfz xampp-linux-1.6.4.tar.gz -C /opt
#Para Arrancarlo
sudo /opt/lampp/lampp start

---

