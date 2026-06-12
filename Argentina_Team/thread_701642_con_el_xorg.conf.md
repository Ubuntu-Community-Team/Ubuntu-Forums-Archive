---
title: "****** con el xorg.conf"
date: 2008-02-19
forum: Argentina Team
---

### Post by sebaxxxtian on 2008-02-19
me mande una ****** modificando el xorg.conf y ahora se cago la resolucion del monitor en mi ubuntu.

como hago para restablecer los settings del dia de ayer?

gracias!!!

---

### Post by pol666 on 2008-02-19
Me tente con el titulo :P


Creo que no podes.
Siempre que edites el xorg.conf hace back up 
 :(

---

### Post by User21 on 2008-02-19
En la carpeta /etc/X11 debes tener un backup de xorg.conf automatico. Entra a una consola con Ctrl + Alt + F1 ... F6 . Logueate con tu user.
Entra a /etc/X11 y ls mediante, busca el mas reciente por su fecha. Los archivos se guardan como xorg.conf.aaaammddhhmm 
Obtenés algo asi como: 
```
user@Machine:~$ cd /etc/X11
user@Machine:/etc/X11$ ls

app-defaults             xorg.conf.19              xorg.conf.failsafe.1
cursors                  xorg.conf.2               xorg.conf.failsafe.10
default-display-manager  xorg.conf.20              xorg.conf.failsafe.2
fonts                    xorg.conf.20080202071733  xorg.conf.failsafe.3
rgb.txt                  xorg.conf.20080202072301  xorg.conf.failsafe.4
X                        xorg.conf.20080202073959  xorg.conf.failsafe.5
xinit                    xorg.conf.20080202075221 
```Buscas el mas reciente...a ese archivo, lo renombras xorg.conf con permisos de root. Por ejemplo:
```
sudo /etc/X11/xorg.conf.20080202071733 /etc/X11/xorg.conf
```Luego, reinicias las X con ctrl + alt + backspace... 
Si eso no funciona, vas a tener que reconfigurar todo a mano con sudo dpkg-reconfigure xserver-xorg , paso a paso y atentamente. 
Suerte!

---

### Post by leo_rockway on 2008-02-19
> **User21 said:**
> Buscas el mas reciente...a ese archivo, lo renombras xorg.conf con permisos de root. Por ejemplo:
```
sudo /etc/X11/xorg.conf.20080202071733 /etc/X11/xorg.conf
```

```
sudo **mv** /etc/X11/xorg.conf.20080202071733 /etc/X11/xorg.conf
```
;-)

---

### Post by User21 on 2008-02-19
jajaa, gracias!

---

### Post by sebaxxxtian on 2008-02-19
ya lo habia arreglado, encontre el back up automatico y pise el q tenia q generaba el conflicto. gracias.

pero sigo sin poder saber pq se me queda el mouse muerto.

---

### Post by User21 on 2008-02-19
Ponele SOLVED al hilo, desde el menu "Thread Tools" , asi ya solo entran aquellos que buscan una respuesta similar. Veremos que sucede con el mouse...

---

