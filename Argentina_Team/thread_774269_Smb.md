---
title: "Smb"
date: 2008-04-29
forum: Argentina Team
---

### Post by iguanargenta on 2008-04-29
Hola, es mi 1° post, espero expresarme bien, ya ke estoy ingresando en el ambiente linuxero, mi duda es la siguiente mas ke duda es un problema que tengo despues de tratar de instalar SMB y tratar de configurar mi equipo para poder compartir archivos desde linux a Windows y viceversa, ahora cada vez que arranco mi equipo en LINUX , llega un momento del inicio, en el cual tarda demasiado, aprox. 3 minutos, antes no lo hacia, empezo a hacerlos luego de instalar SAMBA, la cual, aun no pude hacer andar correctamente, luego (creo) haber podido desactivado el SMB, pero sigue siendo lena al inicio, se keda trabada en la parte de cuando levanta el demonio de compartir carpetas, como revierto la situacion?
Desde ya muchas gracias

---

### Post by faktorqm on 2008-04-29
Hola, bienvenido a la comunidad. Te expresas bien pero buscas poco :D

Al final no entendi si queres sacar el samba o compartir las carpetas.
Asi que te dejo mi propio tutorial para configurar samba y compartir carpetas: [http://ubuntuforums.org/showthread.php?t=697717](http://ubuntuforums.org/showthread.php?t=697717)

Para sacar el samba del inicio (O SEA, NO PARA DESINSTALARLO), vas a Sistema -> adminsitracion -> servicios y ahi buscas samba y lo desactivas, al igual que todos los que no uses, por ejemplo bluetooth y demases. Si tenes dudas sobre alguno, no lo saque o postea primero. 

Si queres desintalar samba, lo podes hacer con 

```
sudo apt-get remove samba --purge
```

Espero que te haya servido. Salu2!!

---

### Post by iguanargenta on 2008-05-10
anduvo de perlas!!!!!, muchisimas gracias, igualmente me pasare por tu instructivo para activarlo en la PC en vez de en la notebook

---

