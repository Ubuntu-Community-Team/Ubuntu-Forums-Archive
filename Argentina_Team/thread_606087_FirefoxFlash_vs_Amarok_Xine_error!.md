---
title: "Firefox/Flash vs Amarok: Xine error!"
date: 2007-11-07
forum: Argentina Team
---

### Post by User21 on 2007-11-07
No importa el orden de inicio, Amarok YA NO PUEDE reproducir audio cuando hay contenido FLASH en Firefox; o viceversa. 
 Amarok lanza el error : XINE PARAMETERS.Por lo cual vuelvo a elegir cualquier extension de salida, y reiniciar Amarok, para recuperar el audio.
Por mas que he googleado, no he encontrado solucion. Alguna idea ???

---

### Post by clasificado on 2007-11-07
Solo por saber, si replicas la instalacion que tenes pero en un live cd ¿tenes el mismo problema?

Solo para descartar que no sean incompatibilidades de software / hardware

Clasificado

---

### Post by kowal on 2007-11-08
Probá instalar el paquete **alsa-oss** y después modificar el archivo** /etc/firefox/firefoxrc** donde dice **FIREFOX_DSP="none"** por** FIREFOX_DSP="aoss"** y reiniciá Firefox.

Saludos

---

### Post by User21 on 2007-11-08
Ya habia encontrado esa solucion, pero NO SIRVIO DE NADA! Pareciese que funcionaba en Dapper...

---

