---
title: "Error fent l'instal-lació de Thunderbird Jaunty"
date: 2009-05-11
forum: Catalan Team
---

### Post by prostata on 2009-05-11
En voler instal-lar Thunderbird synaptic em retorna aquest messatge: ¿cóm puc arreglar-lo..???

Gràcies


E: ca-certificates-java: el subproceso post-installation script devolvió el código de salida de error 1

E: ttf-bengali-fonts: el subproceso post-installation script devolvió el código de salida de error 2

E: ttf-kannada-fonts: el subproceso post-installation script devolvió el código de salida de error 2

E: ttf-oriya-fonts: el subproceso post-installation script devolvió el código de salida de error 2

E: ttf-telugu-fonts: el subproceso post-installation script devolvió el código de salida de error 2

---

### Post by marteljorge on 2009-05-11
> **prostata said:**
> En voler instal-lar Thunderbird synaptic em retorna aquest messatge: ¿cóm puc arreglar-lo..???

Gràcies


E: ca-certificates-java: el subproceso post-installation script devolvió el código de salida de error 1

E: ttf-bengali-fonts: el subproceso post-installation script devolvió el código de salida de error 2

E: ttf-kannada-fonts: el subproceso post-installation script devolvió el código de salida de error 2

E: ttf-oriya-fonts: el subproceso post-installation script devolvió el código de salida de error 2

E: ttf-telugu-fonts: el subproceso post-installation script devolvió el código de salida de error 2

En una terminal:```
sudo dpkg --configure-a
```

---

### Post by prostata on 2009-05-12
Fent per consola el que m'has dit em dona la següenta sortida, és  normal?? o bé, ¿quina opció hauria de fer servir..??

Moltes gràcies


josep@josep-desktop:~$ sudo dpkg --configure-a
[sudo] password for josep: 
dpkg: opción --configure-a desconocida

Escriba dpkg --help para ayuda sobre instalar y desinstalar paquetes [*];
Use `dselect' o `aptitude' para una gestión más amigable de los paquetes;
Escriba dpkg -Dhelp para una lista de los valores de depuración de dpkg;
Escriba dpkg --force-help para una lista de opciones para forzar cosas;
Escriba dpkg-deb --help para obtener ayuda sobre manipulación de archivos .deb;
Escriba dpkg --license para ver la licencia (GPL de GNU), el copyright y la
ausencia de garantía [*].

Las opciones marcadas con [*] producen una salida extensa,
¡fíltrela con `less' o con `more'!

---

### Post by oriolsbd on 2009-05-12
Hola, et falta un espai entre el "--configure" i el "-a".  :-)

Salut!

---

### Post by prostata on 2009-05-12
Dons això és el que em retorna la consola.....

Error occurred during initialization of VM
java/lang/ClassNotFoundException: error in opening JAR file /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
  error adding signet.pl/signet_tsa1_pem.crt
Error occurred during initialization of VM
java/lang/ClassNotFoundException: error in opening JAR file /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
  error adding spi-inc.org/spi-ca-2003.crt
Error occurred during initialization of VM
java/lang/ClassNotFoundException: error in opening JAR file /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
  error adding spi-inc.org/spi-cacert-2008.crt
Error occurred during initialization of VM
java/lang/ClassNotFoundException: error in opening JAR file /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
  error adding telesec.de/deutsche-telekom-root-ca-2.crt
failed.
dpkg: error al procesar ca-certificates-java (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Configurando ttf-bengali-fonts (1:0.5.4ubuntu2) ...
dpkg (subproceso): no se puede ejecutar post-installation script: Error de formato ejecutable
dpkg: error al procesar ttf-bengali-fonts (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2
Se encontraron errores al procesar:
 ttf-telugu-fonts
 ttf-kannada-fonts
 ttf-oriya-fonts
 ca-certificates-java
 ttf-bengali-fonts
josep@josep-desktop:~$

---

