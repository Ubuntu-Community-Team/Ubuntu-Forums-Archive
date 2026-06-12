---
title: "Problema con java"
date: 2007-08-30
forum: Argentina Team
---

### Post by arbusto on 2007-08-30
He instalado java y aparentemente no tuve problemas al hacerlo, pero al intentar abrir algunas aplicaciones desde una pagina, me da el siguiente error:

ERROR:

unable to read library libn

Mas precisamente en [www.managerzone.com](www.managerzone.com), supongo alguno lo conocera, al intentar ver un partido con el 3d, no tengo problemas con el live ni con el Analizer. (estas cosas solo los managerzonianos entenderan)

He entrado en otros lugares que utilizan java y no tuve problemas.

Ahora bien, esto es lo que arroja si pongo about:plugins en el firefox:

Nombre de archivo: libjavaplugin_oji.so
Java(TM) Plug-in 1.6.0_02

Tipo MIME Descripción Sufijos Habilitado
application/x-java-vm Java Si
application/x-java-applet Java Si
application/x-java-applet;version=1.1 Java Si
application/x-java-applet;version=1.1.1 Java Si
application/x-java-applet;version=1.1.2 Java Si
application/x-java-applet;version=1.1.3 Java Si
application/x-java-applet;version=1.2 Java Si
application/x-java-applet;version=1.2.1 Java Si
application/x-java-applet;version=1.2.2 Java Si
application/x-java-applet;version=1.3 Java Si
application/x-java-applet;version=1.3.1 Java Si
application/x-java-applet;version=1.4 Java Si
application/x-java-applet;version=1.4.1 Java Si
application/x-java-applet;version=1.4.2 Java Si
application/x-java-applet;version=1.5 Java Si
application/x-java-applet;version=1.6 Java Si
application/x-java-applet;jpi-version=1.6.0_02 Java Si
application/x-java-bean Java Si
application/x-java-bean;version=1.1 Java Si
application/x-java-bean;version=1.1.1 Java Si
application/x-java-bean;version=1.1.2 Java Si
application/x-java-bean;version=1.1.3 Java Si
application/x-java-bean;version=1.2 Java Si
application/x-java-bean;version=1.2.1 Java Si
application/x-java-bean;version=1.2.2 Java Si
application/x-java-bean;version=1.3 Java Si
application/x-java-bean;version=1.3.1 Java Si
application/x-java-bean;version=1.4 Java Si
application/x-java-bean;version=1.4.1 Java Si
application/x-java-bean;version=1.4.2 Java Si
application/x-java-bean;version=1.5 Java Si
application/x-java-bean;version=1.6 Java Si
application/x-java-bean;jpi-version=1.6.0_02 Java Si

Como puedo hacer para saber si las librerias estan bien???
O si no, que es lo que me recomiendan??

---

### Post by niko_3100 on 2007-08-31
apt-get install sun-java5-jre o algo asi si lo instalaste asi tendria que star bien.

---

### Post by arbusto on 2007-08-31
De hecho anda mal.
Lo instale bajando el archivo de la pagina de java y luego instalando y creando un enlace simbolico en el directorio del Firefox.

Ahora bien, puedo probar desinstalarlo y volver a instalaro de esa manera si es que alguien por favor me dice el comando correcto.

---

### Post by Hei Ku on 2007-08-31
Fijate que en la wiki de ubuntu hay un instructivo para instalar el plugin de java.

---

### Post by arbusto on 2007-09-02
He instalado el jre desde sinaptic y el problema sigue.
Alguna sugerencia?

---

