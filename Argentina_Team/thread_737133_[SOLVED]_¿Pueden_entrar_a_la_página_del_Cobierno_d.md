---
title: "[SOLVED] ¿Pueden entrar a la página del Cobierno de la Ciudad desde Ubuntu?"
date: 2008-03-27
forum: Argentina Team
---

### Post by faustileon on 2008-03-27
Hola:
Tengo Ubuntu 7.10 Gutsy Gibbon instalado en la máquina de mi trabajo (lo instalé yo de prepo) y en casa.  Desde diciembre de 2007 (es decir, desde que asumió la nueva gestión en el Gobierno de la Ciudad de Buenos Aires) que no puedo entrar a la página [www.buenosaires.gov.ar](www.buenosaires.gov.ar) desde Ubuntu, ya sea usando Firefox, Opera e, incluso, IE6 e IE7 instalados en Wine (a través de IEs4Linux), ni desde el trabajo, ni desde mi casa.  En casa tengo el XP en otra partición y no tengo problemas para entrar con el Firefox ni con el IE.  Lo mismo pasa en mi trabajo, pero probando desde la máquina de al lado, que está conectada al mismo HUB de la red que mi máquina.
Me llama la atención que empezara a pasar a partir de diciembre (antes no tenía ningún problema) y que en otra página del gobierno [www.rentasgcba.gov.ar](www.rentasgcba.gov.ar) no tengo problema.
¿Les pasa lo mismo a todos? En caso positivo, ¿qué deberíamos hacer para reclamar?  En caso negativo, ¿a alguien se le ocurre qué me puede estar pasando?
Muchísimas gracias.
Santiago.

---

### Post by sajnox on 2008-03-27
Me paso exactamente lo mismo!!!

Quize entrar con mi maquina el martes a la noche y no abria la pagina, agarre la maquina de mi mujer con windows y entro perfecto.

Sinceramente pense que fue cosa del momento, pero aparentemente no....

---

### Post by faktorqm on 2008-03-27
[http://imageupload.com/out.php/i91923_Pantallazo.png](http://imageupload.com/out.php/i91923_Pantallazo.png)

aguante opera! :KS Salu2!

---

### Post by InsektO on 2008-03-27
Buenas a todos, de paso me presento en estos foros... :D

Yo pude entrar sin ningún inconveniente (también con Gutsy y Firefox). No séra un problema particular de los DNS de sus respectivos ISPs? Probaron usando directamente la ip [http://190.3.109.212](http://190.3.109.212) ?

Saludos!

---

### Post by niko_3100 on 2008-03-27
Recien acabo de entrar con edgy y firefox 2.0.13...

---

### Post by marianom on 2008-03-27
¡Pude! Firefox-Vimperator desde 7.10
Se nota que el problema no es con la gente del interior :)

---

### Post by jorgito on 2008-03-27
Buenas, 

Yo no pude...
Mozilla/5.0 (X11; U; Linux i686; es-AR; rv:1.8.1.13) Gecko/20080325 Ubuntu/7.10 (gutsy) Firefox/2.0.0.13
Desde Buenos Aires para ver si tiene algo que ver.

Saludos!

---

### Post by sajnox on 2008-03-27
> **faktorqm said:**
> [http://imageupload.com/out.php/i91923_Pantallazo.png](http://imageupload.com/out.php/i91923_Pantallazo.png)

aguante opera! :KS Salu2!

Faktor

Entraste al pagina de rentas y a la que queremos entrar es a la del gobierno de la ciudad [www.gcba.gov.ar](www.gcba.gov.ar)

Desde el laburo y con la maquina con Windows no tengo problemas

---

### Post by rojojuan on 2008-03-27
Nunca tuve problema para entrar. Recién, para probar, volví a entrar sin problemas. (Gusty + Firefox)
Esta bastante pesada, pero bueno, debe ser la hora (16.00)

---

### Post by facundocorradini on 2008-03-27
No puedo entrar, esto es rarísimo. 

Desde cualquier navegador que use, aún los IE "emulados". Estoy en Mar del Plata. 

Ya veo que hay negocios entre Microsoft y Macri.... :p

---

### Post by jdcane on 2008-03-27
Que raro!

Buscando por Google, encontre esto:

[http://www.psicofxp.com/forums/gnu-linux.50/599237-sitios-webs-no-accesibles-gnu-linux.html]("http://www.psicofxp.com/forums/gnu-linux.50/599237-sitios-webs-no-accesibles-gnu-linux.html")

---

### Post by User21 on 2008-03-27
Yo tampoco pude, ni de Firefox 2.0.0.13, ni desde Opera 9.25 ! Dale, Macri, deja la mafia!

---

### Post by spg76 on 2008-03-27
Che, al principio pensé que estaban medio paranoicos pero yo tampoco pude entrar ni con Opera, ni con Firefox, ni con Epiphany.
De la única manera fue con un web proxy ([http://www.laigoo.com/proxy/](http://www.laigoo.com/proxy/)).
Yo mandé un mail a [email]webmaster@buenosaires.gov.ar[/email] para ver que me responden. Si quieren pueden hacer lo mismo, así somos más los que nos quejamos.

---

### Post by tzulberti on 2008-03-27
Perdon, pero acabo de poder entrar y me dejo:
[http://imageupload.com/out.php/i92208_Screenshot.png](http://imageupload.com/out.php/i92208_Screenshot.png)

O es un una parte especifica en donde no se puede entrar?

---

### Post by leo_rockway on 2008-03-28
> **jdcane said:**
> Que raro!

Buscando por Google, encontre esto:

[http://www.psicofxp.com/forums/gnu-linux.50/599237-sitios-webs-no-accesibles-gnu-linux.html]("http://www.psicofxp.com/forums/gnu-linux.50/599237-sitios-webs-no-accesibles-gnu-linux.html")

Pero si en el link que dejó jdcane está la respuesta...

```
$ cat /proc/sys/net/ipv4/tcp_window_scaling
1
# echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

Ver: http://lwn.net/Articles/92727/
```

---

### Post by euzkoarima on 2008-03-28
Acabo de entrar sin problemas, al del gobierno y al del banco (en el link de psicofxp daba uno de un banco como que tenía el mismo problema) usando 7.10 32bits con gnome y firefox 2.0.0.13

---

### Post by faustileon on 2008-04-07
Hola:
Problemas resuelto.  ¡Muchas gracias a todos por responder! La solución fue la del link de jdcane que cita leo_rockway.  Funcionó al instante en el trabajo y en casa.  Una vez más, demostradísimo porque este SO (a pesar del problemita) es superior.  Aclaro por las dudas: porque cuenta con una comunidad que lo respalda.  Saludos.

---

### Post by MeduZa on 2008-04-07
> **faustileon said:**
> Hola:
Tengo Ubuntu 7.10 Gutsy Gibbon instalado en la máquina de mi trabajo (lo instalé yo de prepo) y en casa.  Desde diciembre de 2007 (es decir, desde que asumió la nueva gestión en el Gobierno de la Ciudad de Buenos Aires) que no puedo entrar a la página [www.buenosaires.gov.ar](www.buenosaires.gov.ar) desde Ubuntu, ya sea usando Firefox, Opera e, incluso, IE6 e IE7 instalados en Wine (a través de IEs4Linux), ni desde el trabajo, ni desde mi casa.  En casa tengo el XP en otra partición y no tengo problemas para entrar con el Firefox ni con el IE.  Lo mismo pasa en mi trabajo, pero probando desde la máquina de al lado, que está conectada al mismo HUB de la red que mi máquina.
Me llama la atención que empezara a pasar a partir de diciembre (antes no tenía ningún problema) y que en otra página del gobierno [www.rentasgcba.gov.ar](www.rentasgcba.gov.ar) no tengo problema.
¿Les pasa lo mismo a todos? En caso positivo, ¿qué deberíamos hacer para reclamar?  En caso negativo, ¿a alguien se le ocurre qué me puede estar pasando?
Muchísimas gracias.
Santiago.

me va de 10 en seamonkey 2.0 alpha de ultima instala el user agent swtcher y proba, aunque no creo que sea eso porque yo no lo use para verla:

---

### Post by margori on 2008-04-07
La verdad que me encantaria sabes porque una configuracion como esta

```
$ cat /proc/sys/net/ipv4/tcp_window_scaling
1
# echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
```

es necesaria para ver una pagina de acceso tan masivo y publico?

Si me pueden explicar que es lo que hace y porque razon se requiere para ver esa pagina, se lo agradecería.

Por otro lado, es un problema de configuración del servidor? Como se arreglaría?

---

### Post by faustileon on 2008-04-07
No tengo idea Margori.  En el link de leo_rockaway está explicado en inglés.  Se soluciona tipeando eso en un terminal.  Y gracias tambiéna a Meduza.  Pero como escribí más arriba ya lo solucioné.
El link específico en Inglés es:  [http://lwn.net/Articles/92727/](http://lwn.net/Articles/92727/)

---

### Post by faktorqm on 2008-04-08
Basicamente lo que estas haciendo ahi es cambiando el tamaño de la ventana tcp (la que recibe, no la de control). Es para que si la conexion tuya es muy lenta no le ocupes ancho de banda al servidor durante mucho tiempo digamos. Entonces si esta desactivado el tamaño por defecto de la ventana creo que era de 64k. Si lo habilitas este valor cambia y se pone uno tal que te ande todo bien para tu conexion.

Lo que estas haciendo con el cat blablabla es fijarte si esta activado o no. Lo que cualquiera llamaria "carpeta" y "archivo", en realidad es el mismisimo kernel de linux. 
Ahora bien, vos cuando haces echo blabla escribis el valor "uno" en la variable ipv4.tcp_window_scaling en el kernel. Eso se hace "on the fly", es decir, cuando reinicias, el cambio se pierde. Para que no se pierda editas el archivo /etc/sysctl.conf y agregas esta linea: 

```
net.ipv4.tcp_window_scaling=1
```

El windows Vista lo trae activado por defecto, y tienen 1000 problemas con los dns, o con los routers que no lo bancan. Aguante linux :D

Espero que te haya servido, en wikipedia no hay articulo en castellano, asi que resumi & traduje una parte. Salu2!!

---

