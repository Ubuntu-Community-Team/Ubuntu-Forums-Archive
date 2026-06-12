---
title: "Problemas al compilar"
date: 2008-03-07
forum: Argentina Team
---

### Post by Elrengo on 2008-03-07
Buenas a todos, me veo obligado a acudir a ustedes una vez mas, 
Soy bastante nuevo en esto de linux y descargue algunas aplicaciones en formato tar.gz y no las puedo instalar, 

encontre un tutorial en donde lo explica, lo puse a funcionar y me tira error al realizar el comando ./compile, me dice q el comando no se encuentra, es decir escribo esto yo en la consola:


         tar -zxvf xxxxxxx.tar.gz   (al realizar esto la consola muestra algunas acciones, parece q esta descomprimiendo una larga lista de archivos)


         sudo ./configure      (ahi es donde tira error)  (COMMAND NOT FOUND


          y despues tendria q realizar estos comandos segun el tutorial


          make
          make install


La verdad ni idea q pasa, 
         
Espero ayuda, muchas gracias

:guitar:

---

### Post by spg76 on 2008-03-07
Después de descomprimir el archivo, tenés que ubicarte en la carpeta del programa. Por lo general, con hacer **cd "nombre del archivo tar.gz"** (sin comillas y sin tar.gz) es suficiente, si no, poné **dir** para listar los directorios así sabes cual es el nombre de la carpeta.

---

### Post by Elrengo on 2008-03-07
Me sigue tirando el mismo error, entro a la carpeta q crea al descomprimir y al tirar el comando ./COMPILE sigue no encontrandolo

GRacias por responder

---

### Post by spg76 on 2008-03-07
En general el comando es  **./configure**.
Por otro lado, si bien hay un método generalizado, no todos los programas se compilan de la misma manera. Si seguís teniendo problemas deci que porgrama es el que queres instalar.

---

### Post by santiagoward2000 on 2008-03-07
> **Elrengo said:**
> Me sigue tirando el mismo error, entro a la carpeta q crea al descomprimir y al tirar el comando ./COMPILE sigue no encontrandolo

GRacias por responder

Hola!
¿Qué programa estás tratando de compilar? Tratá de abrir la carpeta que descomprimiste y ver si ahí está el archivo **./compile** (va a estar oculto, asique tocá CTRL+H).
En algunos programas el archivo puede tener otro nombre.
Saludos

---

### Post by margori on 2008-03-07
Estoy seguro que el paquete que descargaste no tiene script de configuración ./configure.

Proba directamente hacer

make
sudo make install

Esto parado en la carpeta en donde están los archivos descomprimido, claro.

Es mejor que nos pases la URL del archivo que descargaste, así te decimos bien que es lo que necesitas hacer.

---

### Post by sajnox on 2008-03-07
En primer lugar, estas seguro que los programas que queres no estan en los repositorios??

Si lo que te bajaste es un archivo tar.gz, en mi opinion lo mas facil es usar el comando alien para pasarlo a un .deb (lo mas parecido a un exe en windows)

No viene instalado por defecto asi que lo tenes que instalar

```
sudo apt-get install alien
```

Ahora usas el comando alien

en una terminal (fijate que estas en la carpeta donde esta el archivo)

```
sudo alien -v "nombre del archivo.tar.gz"
```

Te genera un archivo.deb al que le das un doble click y te lo instala automaticamente.

Fijate como te funciona

---

### Post by margori on 2008-03-07
Estoy seguro que el paquete que descargaste no tiene script de configuración ./configure.

Proba directamente hacer

make
sudo make install

Esto parado en la carpeta en donde están los archivos descomprimido, claro.

Es mejor que nos pases la URL del archivo que descargaste, así te decimos bien que es lo que necesitas hacer.

---

