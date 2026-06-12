---
title: "Ubuntu - VNC y DSM PlugIn"
date: 2007-07-05
forum: Argentina Team
---

### Post by vk-cdg on 2007-07-05
Estoy dando mis primeros pasos con Ubuntu y la mayoría de las cosas de configuración fueron respondidas por este maravilloso foro. 
La cosa es que estoy instalando Ubuntu en la PC del laburo y la única complicación que tengo para devolver el disco donde tengo instalado el XP (tengo dos discos, uno solito para Ubuntu y el otro para el XP) es que en el trabajo nos conectamos a las estaciones de trabajo (red LAN) de los usuarios mediante el VNC con el plugIn de encriptación.
Hasta ahora no he encontrado solución a esto, pero de encontrarla migro definitivamente a ubuntu.

Si alguien puede tirarme una soga, estaré agradecido.

---

### Post by vk-cdg on 2007-07-07
A la pelotita, parece que tiré una que nadie sabe.

Veré si puedo con el wine o con el crossover.

---

### Post by Gideon26 on 2007-07-07
Hola recien hoy vi tu post veras en ubuntu en la version Feisty Fawn al menos tienes una aplicacion que dice cliente de Terminal Server que usa el protocolo de conexion VNC, RDP y RDPv5. Yo te diria que pruebes conectarte a las pcs atravez de esa aplicacion deberia poderse, bueno cualquier cosa postea y veremos como solucionar

---

### Post by Al_maverick on 2007-07-08
Tenes idea que plugin usa, y que protocolo de encripcion es el que utiliza?

---

### Post by Kantier on 2007-07-08
> **vk-cdg said:**
> Estoy dando mis primeros pasos con Ubuntu y la mayoría de las cosas de configuración fueron respondidas por este maravilloso foro. 
La cosa es que estoy instalando Ubuntu en la PC del laburo y la única complicación que tengo para devolver el disco donde tengo instalado el XP (tengo dos discos, uno solito para Ubuntu y el otro para el XP) es que en el trabajo nos conectamos a las estaciones de trabajo (red LAN) de los usuarios mediante el VNC con el plugIn de encriptación.
Hasta ahora no he encontrado solución a esto, pero de encontrarla migro definitivamente a ubuntu.

Si alguien puede tirarme una soga, estaré agradecido.
danos más detalles, links a las páginas de los programas (especialmente ese misterioso plugin de encriptación). por lo menos yo no estoy muy seguro de sobre qué estas hablando específicamente =(  (y por ende, no puedo aportar una solución)

---

### Post by vk-cdg on 2007-07-11
Buenas, volví luego de un fin de semana de estudio.
Acá tengo los sitios web del VNC que usamos y del plugIn.

UltraVNC
[http://www.uvnc.com/](http://www.uvnc.com/)
Estoy usando la úlltima versión estable.

DSM PlugIn
[http://msrc4plugin.home.comcast.net/index.html](http://msrc4plugin.home.comcast.net/index.html)

Usamos el MSRC4Plugin que se puede descargar de acá [http://msrc4plugin.home.comcast.net/msrc4plugin.html](http://msrc4plugin.home.comcast.net/msrc4plugin.html)

Les cuento un poco acerca del entorno donde usamos esto. Es una red LAN corporativa muy grande, mas de 1000 estaciones de trabajo. Con este soft nosotros nos conectamos a las estaciones y realizamos tareas de mantenimiento cuando es requerido, (es mas óptimo que ir piso por piso, estación por estación). La mayoría son Windows XP, pero hay alguna que otra 9X. 
Con las que tienen 9X no hay problema porque no usan el plug in de encriptación y me puedo conectar perfecto con lo que trae ubuntu, pero con las XP, que usan ese plug in no hay forma.

Si llegan a saber algo, se agradece. Yo mientras sigo probando con el wine, pero por el momento tampoco tuve suerte.

---

### Post by vk-cdg on 2007-07-12
Les cuento un poco mas sobre el tema...
El VNC que trae el Ubuntu (por terminal vncviewer ip_equipo) solo funciona con servidores VNC de la versión que tenemos instalada (que es la que puse en el post anterior). Da este error "Not a valid VNC server".

Probé instalar un cliente un poco mas viejo (el Real VNC) y anda perfecto, siempre sin plugIn obvio.
Como en mi trabajo es una necesidad constante, instalé el WINE y el CROSSOVER y probé instalar el cliente que usamos en windwos con el plug in.
El resultado es que anda pero muy lento y además tiene cierto asuntillo con la ruta a donde va a buscar el plugin, ya que es una ruta "windows" (C:\Archivos de programa\bla bla bla).

En fin, seguiremos investigando.

Por lo pronto veré si en el synaptic hay algo nuevo de VNC y ver que onda.

---

### Post by Al_maverick on 2007-07-12
Probaste instalar el VNC desde el source? El de ubuntu es bastante viejo. Y por lo que se, el desarrollador esta bastante activo. Al menos lo vi respondiendo posts en el foro de ubuntu hace un tiempo.

---

### Post by vk-cdg on 2007-07-12
No, sinceramente no probé. 
Recién estoy empezando con Linux y hoy me la mandé, actualicé el driver de nvidia y ahora se fue de viaje el entorno gráfico así que primero tengo que remarla con eso.

---

### Post by vk-cdg on 2007-07-14
> **Al_maverick said:**
> Probaste instalar el VNC desde el source? El de ubuntu es bastante viejo. Y por lo que se, el desarrollador esta bastante activo. Al menos lo vi respondiendo posts en el foro de ubuntu hace un tiempo.

Me colgué con el problema de la interfaz gráfica y no leí bien tu post. Actualizarlo desde donde? Estuve buscando algún cliente de VNC pero o es el X11vnc o el que trae ubuntu por consola.
De donde lo puedo actualizar?

---

### Post by Al_maverick on 2007-07-14
desinstala el que tenes instalado desde los repositorios, y proba bajarlo desde la pagina oficial.

[http://www.realvnc.com/](http://www.realvnc.com/)

No te digo que sea la solucion, pero mi experiencia con el VNC es que el paquete de Ubuntu tenia varios problemas y estaba desactualizado. En particular el de 64 bits estaba roto y la ultima vez que vi no lo habian corregido. Desde la pagina esa bajate el tarball. Eso debería tener para compilar desde el codigo fuente, o con suerte, un ejecutable stand alone. Si necesitas ayuda para compilar, solo pregunta. Somos varios los programadores por aca, y no es dificil darte las indicaciones basicas para que lo puedas hacer sin problemas.

---

### Post by vk-cdg on 2007-07-16
Bueno, les cuento que en principio (al menos de forma provisoria) solucioné el tema del VNC con este bendito plugIn que se usa en mi trabajo.
Le heché mano al wine para hacer funcionar la versión de windows sobre linux y por fin puedo conectarme a las PC. Con las que no usan el plug in, me conecto por consola, ya que es mucho mas rápido y anda mejor.

De todas formas seguiré investigando a ver si aparece algo o si el desarrollador le pone onda y crea una versión nativa para linux que permita usar dicho plugIn de seguridad.

Saludos

PD: gracias a todos por la ayuda.

---

### Post by Al_maverick on 2007-07-16
Lo interesante es que el plugin es GPL, o sea que no habria problema en portarlo. Podrias probar de contactar a la gente de realvnc, a ver si tienen algo similar, o si estan dispuestos a hacer la migración.

---

### Post by ariel on 2007-07-21
mis dos centavos,
en unix/linux la forma mas comun de segurizar VNC es usar vnc sobre un tunel ssh; es refacil. tambien es comun de hacer desde maquinas windows, usando putty.

hasta ahora no escuche de "encryption plugins" para vnc. Si en tu servidor podes instalar un openssh o vshell o algo asi, capaz que es lo mas facil

suerte!

---

### Post by vk-cdg on 2007-07-23
Nop, el tema es así. 
Las PC's que usan el plugIn (las de los usuarios) son las que tienen el UltraVNC Server corriendo, usan Win XP como operativo (son mas de 5000 PCs). Lamentablemente no está a mi alcance modificar la política con la cual se securiza la conexión. 
Todas nuestras PC (las del área de sistemas) usan Windose, pero a mi me pintó instalar Ubuntu para probarlo y luego instalarlo en casa.

El problema se da en que no encuentro un cliente para hacer lo mismo que hacemos desde Windows en Ubuntu.
El plugIn es gratuito hasta donde entiendo y el link del sitio está en el primer post mio.

En fin, a seguir buscando, pero por el momento, wine de por medio, lo tengo mas o menos solucionado.

---

