---
title: "ver el equipo en una red Microsoft Windows"
date: 2007-07-27
forum: Argentina Team
---

### Post by ricardovg1 on 2007-07-27
Hola a todos, soy nuevo en Ubuntu 7.04 y tengo una pequeña red Microsoft Windows con un Grupo de 
Trabajo llamado WORKGROUP, y mi problema es que no veo el equipo con Ubuntu en la red desde los equipos con Windows XP pero en el equipo con Ubuntu veo la red Microsoft, el Grupo de Trabajo y puedo acceder a Internet a traves de un router ¿Como tengo que hacer para que el equipo con Ubuntu se vea
en el Grupo de Trabajo llamado Workgroup?Gracias

---

### Post by kowal on 2007-07-27
Desde la consola:

```
sudo aptitude install samba samba-client smbfs
```

Después editás smb.conf

```
sudo nano /etc/samba/smb.conf
```

Buscás la línea que diga *workgroup = MSHOME* y reemplazás *MSHOME* por tu workgroup (en este caso *WORKGROUP*)

Y le agregás a lo úlimo de smb.conf la partición que querés compartir. 
Algo así para que se pueda leer/escribir:

```

[c]
path = /media/sda1
read only = no
create mask = 0644
force user = (tu_usuario)
force group = (tu_usuario)

```

Grabás.. y reiniciás samba con 

```
/etc/init.d/samba restart
```

Saludos

---

### Post by valucha on 2007-07-27
> **kowal said:**
> Desde la consola:

```
sudo aptitude install samba samba-client smbfs
```

Después editás smb.conf

```
sudo nano /etc/samba/smb.conf
```

Buscás la línea que diga *workgroup = MSHOME* y reemplazás *MSHOME* por tu workgroup (en este caso *WORKGROUP*)

Y le agregás a lo úlimo de smb.conf la partición que querés compartir. 
Algo así para que se pueda leer/escribir:

```

[c]
path = /media/sda1
read only = no
create mask = 0644
force user = (tu_usuario)
force group = (tu_usuario)

```

Grabás.. y reiniciás samba con 

```
/etc/init.d/samba restart
```

Saludos

[COLOR="DarkOrchid"]¿Esto funciona con Vista?[/COLOR]

---

### Post by Hei Ku on 2007-07-28
Jua. No, eso es para que el ubuntu pueda actuar como un cliente de red de windows. De esa forma lo vas a poder ver desde el Vista sin tener que hacer ningun cambio.

---

### Post by kowal on 2007-07-28
> **valucha said:**
> [COLOR="DarkOrchid"]¿Esto funciona con Vista?[/COLOR]

Debería funcionar en LANs con Vista, si. 

Pero ojo, que en algunas versiones de Vista "limitadas" (Home) hay que hacer un paso más: [http://www.multingles.net/docs/jmt/wvsmb.html](http://www.multingles.net/docs/jmt/wvsmb.html)

Saludos

---

### Post by lugonesjoaquin on 2007-07-28
> **ricardovg1 said:**
> Hola a todos, soy nuevo en Ubuntu 7.04 y tengo una pequeña red Microsoft Windows con un Grupo de 
Trabajo llamado WORKGROUP, y mi problema es que no veo el equipo con Ubuntu en la red desde los equipos con Windows XP pero en el equipo con Ubuntu veo la red Microsoft, el Grupo de Trabajo y puedo acceder a Internet a traves de un router ¿Como tengo que hacer para que el equipo con Ubuntu se vea
en el Grupo de Trabajo llamado Workgroup?Gracias
[http://revoltion.wordpress.com/2007/04/02/compartir-carpetas-en-red-con-windows-usando-ubuntu/](http://revoltion.wordpress.com/2007/04/02/compartir-carpetas-en-red-con-windows-usando-ubuntu/)

Esto tambien te puede servir :) Mas grafico :)

---

### Post by sharkg on 2007-09-28
yo quiero entrar desde ubuntu a un disco compartido,  hacerle backup y grabarlo en otro disco.... q mas deberia hacer con samba y si hay algun programita q haga el backup o mejor hago un scrip y listo......
aclaro q toda la red donde estoy esta con W03 server y las terminales con XP por las dudas...

---

### Post by sajnox on 2007-09-28
Hago mi aporte en lo que configurar samba respecta, a mi me resulto muy util.

[http://www.vensign.com/2007/03/18/instalando-samba-en-ubuntu-debian-para-compartir-archivos-e-impresoras-en-redes-windows/]("http://www.vensign.com/2007/03/18/instalando-samba-en-ubuntu-debian-para-compartir-archivos-e-impresoras-en-redes-windows/")

---

