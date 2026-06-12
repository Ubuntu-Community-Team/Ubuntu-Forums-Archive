---
title: "Como instalar Thunderbir 2.0.0.12"
date: 2008-04-18
forum: Argentina Team
---

### Post by Elrengo on 2008-04-18
Buenas a todos, acudo a ustedes nueamente, con el objeto de DESNOVATIZARME un poco mas, les comento q voy un poco mejor, y q como les digo a todo el mundo, solo es un poco de practica.

Tengo un pequeño problema, (es pequeño porque tengo alternativas, ya q sigo utilizando windows porq todavia no estoy listo para sacarlo, pero yo me tiento), quiero instalar THUNDERBIRD 2.0.0.12, pero desde SYNAPTICS me instala la version 1, 

Baje el .tar.gz de la pagina mozilla, y este archivo comprmido no hay q ejecutarlo segun lei, as q lo descomprimi desde la consola en la carpeta /opt, pero ya no se que hacer, cree un lanzador para el archuvo THUNDERBIR en el escritorio, pero nada, lo ejectuto y no pasa absolutamente nada,

Alguna soga para salvarme por ahi????


Muchisimas gracias

Matiass

:guitar::guitar:

---

### Post by vk-cdg on 2008-04-18
Fijate [acá]("http://www.fabio.com.ar/verpost.php?id_noticia=2058") que explican como hacerlo. Cambiá los números de versión por el que vos bajaste y tendría que caminar solito.

Chiflá cualquier cosa!

Muchos caminamos el mismo camino hace un tiempo (no mucho en mi caso). Yo no saqué Windows, pero todas mis cosas (archivos, mails, etc) están en ubuntu ya.

---

### Post by sajnox on 2008-04-18
Rengo,

El tema es que lo que te bajaste son las fuentes del sistema pero no los binarios. Basicamente (si me equivoco algun amigo me corrije) Las fuentes son el codigo del programa pero no es un archivo que puedas ejecutar sino que tenes que compilarlo para que pase a Binarios y pueda ser interpretado por la maquina (sino es puro texto pero no ceros y unos).

El metodo que yo uso para compilar desde fuentes es con el comando alien, para esto podes hacer lo siguiente.

1) Instalar alien en el equipo ya que no viene por defecto en la instalacion

```
sudo apt-get install alien
```

2) Convertir el paquete tar.gz en un archivo .deb (lo mas parecido a un .exe en Ubuntu) Recorda que tenes que ejecutar alien desde el mismo directorio donde esta el archivo tar.gz

Para asegurarte que el tar.gz esta en el directorio

```
dir *thunderbird*
```

Si te muestra el nombre del archivo que bajaste es que estas ahi, sino move el tar.gz a tu carpeta personal

Ahora si convertis el archivo en un .deb

```
sudo alien -v "nombre del archivo tar.gz"
```

Y te va a aparecer en la carpeta un archivo .deb con el que le das un simple doble click y te lo instala.

Probablemente te agregue un lanzador en aplicaciones/internet, sino lo hace lo que vas a tener que crear vos

---

### Post by Mauro22 on 2008-04-18
Yo me lo bajo de la pagina oficial. Lo descomprimo y lo muevo a /opt.

Despues solo basta con ejecutar ./opt/thunderbird/thunderbird



Salu2

---

### Post by pablo0469 on 2008-04-19
Mi synaptic anda mal, o yo leere mal, pero lo tengo disponible bien claro en mis repositorios.


Saludos.

---

